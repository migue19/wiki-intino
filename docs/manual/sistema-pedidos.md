### Proyecto de Ejemplo 2: Sistema de Pedidos

Este proyecto de ejemplo muestra cómo utilizar el Intino Framework para desarrollar un sistema básico de gestión de pedidos. El proyecto abarcará la definición del modelo en Legio DLS, la generación automática de código, la configuración de persistencia, y la personalización de la interfaz de usuario.

#### 1. Definición del Modelo en Legio DLS

Primero, definimos las entidades necesarias en el archivo `model.legio`. En este caso, necesitamos las entidades `Cliente` y `Pedido`.

**Archivo `model.legio`:**

```legio
entity Cliente {
    @Id int id;
    String nombre;
    String direccion;
    @Range(min=18, max=99) int edad;
}

entity Pedido {
    @Id int id;
    Date fecha;
    double total;
    Cliente cliente;
}
```

#### 2. Generación de Código

Ejecutamos el generador de código de Intino para transformar los modelos definidos en clases Java y otros componentes necesarios.

**Comando para Generar Código:**

```sh
intino generate
```

Este comando generará las clases Java para las entidades `Cliente` y `Pedido`, así como otras configuraciones necesarias para la persistencia y gestión de datos.

#### 3. Configuración de la Persistencia

Configuramos la persistencia de datos utilizando Spring Boot y una base de datos relacional como MySQL.

**Archivo `application.properties`:**

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/pedidosdb
spring.datasource.username=usuario
spring.datasource.password=contraseña
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

#### 4. Código Java Generado

Revisamos y ajustamos las clases generadas si es necesario.

**Clase `Cliente`:**

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "clientes")
public class Cliente {
    @Id
    private int id;
    private String nombre;
    private String direccion;
    private int edad;

    // Getters y Setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getDireccion() {
        return direccion;
    }

    public void setDireccion(String direccion) {
        this.direccion = direccion;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }
}
```

**Clase `Pedido`:**

```java
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.ManyToOne;
import javax.persistence.Table;
import java.util.Date;

@Entity
@Table(name = "pedidos")
public class Pedido {
    @Id
    private int id;
    private Date fecha;
    private double total;

    @ManyToOne
    private Cliente cliente;

    // Getters y Setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public Date getFecha() {
        return fecha;
    }

    public void setFecha(Date fecha) {
        this.fecha = fecha;
    }

    public double getTotal() {
        return total;
    }

    public void setTotal(double total) {
        this.total = total;
    }

    public Cliente getCliente() {
        return cliente;
    }

    public void setCliente(Cliente cliente) {
        this.cliente = cliente;
    }
}
```

**Repositorio `ClienteRepository`:**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface ClienteRepository extends JpaRepository<Cliente, Integer> {
}
```

**Repositorio `PedidoRepository`:**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface PedidoRepository extends JpaRepository<Pedido, Integer> {
}
```

#### 5. Desarrollo del Servicio y Controlador

Desarrollamos los servicios y controladores para gestionar las operaciones CRUD de `Cliente` y `Pedido`.

**Servicio `ClienteService`:**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class ClienteService {
    @Autowired
    private ClienteRepository clienteRepository;

    public List<Cliente> getAllClientes() {
        return clienteRepository.findAll();
    }

    public Cliente getClienteById(int id) {
        return clienteRepository.findById(id).orElse(null);
    }

    public Cliente saveOrUpdateCliente(Cliente cliente) {
        return clienteRepository.save(cliente);
    }

    public void deleteCliente(int id) {
        clienteRepository.deleteById(id);
    }
}
```

**Servicio `PedidoService`:**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class PedidoService {
    @Autowired
    private PedidoRepository pedidoRepository;

    public List<Pedido> getAllPedidos() {
        return pedidoRepository.findAll();
    }

    public Pedido getPedidoById(int id) {
        return pedidoRepository.findById(id).orElse(null);
    }

    public Pedido saveOrUpdatePedido(Pedido pedido) {
        return pedidoRepository.save(pedido);
    }

    public void deletePedido(int id) {
        pedidoRepository.deleteById(id);
    }
}
```

**Controlador `ClienteController`:**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/clientes")
public class ClienteController {
    @Autowired
    private ClienteService clienteService;

    @GetMapping
    public List<Cliente> getAllClientes() {
        return clienteService.getAllClientes();
    }

    @GetMapping("/{id}")
    public ResponseEntity<Cliente> getClienteById(@PathVariable int id) {
        Cliente cliente = clienteService.getClienteById(id);
        if (cliente == null) {
            return ResponseEntity.notFound().build();
        }
        return ResponseEntity.ok(cliente);
    }

    @PostMapping
    public Cliente createCliente(@RequestBody Cliente cliente) {
        return clienteService.saveOrUpdateCliente(cliente);
    }

    @PutMapping("/{id}")
    public ResponseEntity<Cliente> updateCliente(@PathVariable int id, @RequestBody Cliente clienteDetails) {
        Cliente cliente = clienteService.getClienteById(id);
        if (cliente == null) {
            return ResponseEntity.notFound().build();
        }
        cliente.setNombre(clienteDetails.getNombre());
        cliente.setDireccion(clienteDetails.getDireccion());
        cliente.setEdad(clienteDetails.getEdad());
        Cliente updatedCliente = clienteService.saveOrUpdateCliente(cliente);
        return ResponseEntity.ok(updatedCliente);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteCliente(@PathVariable int id) {
        Cliente cliente = clienteService.getClienteById(id);
        if (cliente == null) {
            return ResponseEntity.notFound().build();
        }
        clienteService.deleteCliente(id);
        return ResponseEntity.noContent().build();
    }
}
```

**Controlador `PedidoController`:**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
@RequestMapping("/api/pedidos")
public class PedidoController {
    @Autowired
    private PedidoService pedidoService;

    @GetMapping
    public List<Pedido> getAllPedidos() {
        return pedidoService.getAllPedidos();
    }

    @GetMapping("/{id}")
    public ResponseEntity<Pedido> getPedidoById(@PathVariable int id) {
        Pedido pedido = pedidoService.getPedidoById(id);
        if (pedido == null) {
            return ResponseEntity.notFound().build();
        }
        return ResponseEntity.ok(pedido);
    }

    @PostMapping
    public Pedido createPedido(@RequestBody Pedido pedido) {
        return pedidoService.saveOrUpdatePedido(pedido);
    }

    @PutMapping("/{id}")
    public ResponseEntity<Pedido> updatePedido(@PathVariable int id, @RequestBody Pedido pedidoDetails) {
        Pedido pedido = pedidoService.getPedidoById(id);
        if (pedido == null) {
            return ResponseEntity.notFound().build();
        }
        pedido.setFecha(pedidoDetails.getFecha());
        pedido.setTotal(pedidoDetails.getTotal());
        pedido.setCliente(pedidoDetails.getCliente());
        Pedido updatedPedido = pedidoService.saveOrUpdatePedido(pedido);
        return ResponseEntity.ok(updatedPedido);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deletePedido(@PathVariable int id) {
        Pedido pedido = pedidoService.getPedidoById(id);
        if (pedido == null) {
            return ResponseEntity.notFound().build();
        }
        pedidoService.deletePedido(id);
        return ResponseEntity.noContent().build();
    }
}
```

#### 6. Generación y Personalización de la Interfaz de Usuario

Utilizamos la generación automática de interfaces para crear formularios básicos y vistas para las entidades `Cliente` y `Pedido`.

**HTML Generado para el Formulario de Pedido:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Pedido Form</title>
</head>
<body>
    <h1>Pedido Form</h1>
    <form id="pedidoForm">
        <label for="id">ID:</label>
        <input type="text

" id="id" name="id"><br><br>
        <label for="fecha">Fecha:</label>
        <input type="date" id="fecha" name="fecha"><br><br>
        <label for="total">Total:</label>
        <input type="number" id="total" name="total"><br><br>
        <label for="cliente">Cliente ID:</label>
        <input type="text" id="cliente" name="cliente"><br><br>
        <button type="submit">Enviar</button>
    </form>

    <script>
        document.getElementById('pedidoForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const pedido = {
                id: document.getElementById('id').value,
                fecha: document.getElementById('fecha').value,
                total: document.getElementById('total').value,
                cliente: { id: document.getElementById('cliente').value }
            };
            fetch('/api/pedidos', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(pedido)
            })
            .then(response => response.json())
            .then(data => console.log(data))
            .catch(error => console.error('Error:', error));
        });
    </script>
</body>
</html>
```

#### 7. Ejecución y Pruebas

Iniciamos la aplicación Spring Boot y accedemos a la interfaz de usuario generada para probar las funcionalidades CRUD de `Pedido`.

```sh
mvn spring-boot:run
```

Accedemos a la URL `http://localhost:8080/pedidoForm.html` para interactuar con la interfaz de usuario.

#### 8. Resumen

Este proyecto de ejemplo demuestra cómo utilizar el Intino Framework para desarrollar un sistema básico de gestión de pedidos. Desde la definición del modelo en Legio DLS hasta la generación y personalización de interfaces de usuario, el Intino Framework proporciona herramientas poderosas para acelerar el desarrollo y mantener la consistencia entre el modelo de datos y la implementación.