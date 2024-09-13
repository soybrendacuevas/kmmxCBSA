Tets un contrato inteligente escrito en Solidity, diseñado para representar la propiedad y precio de un producto en la blockchain de Ethereum. Cada instancia de este contrato almacena el nombre del producto, su precio y la dirección del propietario actual. Además, permite al propietario transferir la propiedad del producto a otra dirección.

Características:
Nombre del producto: El contrato almacena el nombre del producto en una cadena de texto.
Precio: El precio del producto está almacenado como un número entero sin decimales.
Propietario: La dirección de Ethereum del propietario actual se almacena en el contrato.
Transferencia de propiedad: Sólo el propietario actual puede transferir la propiedad del producto a otra dirección.
Este contrato es adecuado para aplicaciones de rastreo de propiedad de productos, marketplaces descentralizados o cualquier aplicación que requiera vincular un producto digital o físico con un propietario en la blockchain.
-------------------------------
Requisitos previos
Solidity 0.8.0 o superior: Este contrato requiere la versión 0.8.0 de Solidity o superior.
Herramienta de desarrollo Ethereum: Para interactuar y desplegar el contrato, puedes usar herramientas como Remix, Truffle, o Hardhat.
Red Ethereum: Puedes desplegar el contrato en la red principal de Ethereum, redes de prueba (Ropsten, Rinkeby, etc.), o cualquier blockchain compatible con EVM.
-------------------------------------------
Funcionalidades del contrato
1. Constructor:
```constructor(string memory _nombre, uint _precio)```
El constructor inicializa el contrato con el nombre del producto, su precio y asigna la dirección del propietario como la dirección que despliega el contrato.

```_nombre:``` El nombre del producto.
```_precio: El``` precio del producto en enteros (puede representar la cantidad en wei, gwei, o la unidad elegida).
Ejemplo de uso:
```ProductoInteligente("Laptop", 500);```

2. Propiedades Públicas:
nombre: Devuelve el nombre del producto.
precio: Devuelve el precio del producto.
propietario: Devuelve la dirección del propietario actual del producto.

3. transferirPropiedad:
```function transferirPropiedad(address _nuevoPropietario) public```
Esta función permite al propietario actual transferir la propiedad del producto a una nueva dirección.
_nuevoPropietario: La nueva dirección a la cual se transferirá la propiedad.

Requisitos:
Solo el propietario actual puede llamar a esta función.
Si otra dirección intenta llamar a la función, se revertirá con el mensaje "Solo el propietario puede transferir el producto".
Ejemplo de uso:
transferirPropiedad(0x1234567890abcdef1234567890abcdef12345678);

4. Evento ProductoCreado:
```event ProductoCreado(string nombre, uint precio, address propietario);```
Este evento se emite cuando se despliega el contrato, registrando el nombre, el precio y el propietario original del producto.
-------------------------------------------
 Despliegue
Para desplegar el contrato, sigue estos pasos:

Configuración en Remix:

Copia y pega el código del contrato en el entorno de Remix.
Asegúrate de seleccionar la versión 0.8.0 de Solidity o superior.
Selecciona la red (red de prueba o red principal) desde la opción "Deploy & Run Transactions".
  Despliegue con constructor:
Ingresa los valores de los parámetros _nombre y _precio en la sección de "Deploy" y despliega el contrato.
Uso
  Consultar detalles del producto:
Una vez desplegado, puedes consultar los detalles del producto llamando a las variables públicas nombre, precio y propietario.
  Transferir propiedad:
Si eres el propietario del producto, puedes transferir la propiedad llamando a la función transferirPropiedad y proporcionando la dirección del nuevo propietario.
Ejemplo de interacción
Crear un producto con nombre "Bicicleta" y precio 1000:

```
ProductoInteligente("Bicicleta", 1000);
Transferir la propiedad de la "Bicicleta" a una nueva dirección:
```
```
transferirPropiedad(0xAbc1234567890def1234567890abcdef12345678);
```
Seguridad
Solo el propietario del producto puede transferir la propiedad.
Asegúrate de que las transacciones provengan de la dirección correcta para evitar la pérdida de control sobre el producto.
------------------------------------------------------------------------------------------
Licencia
Este contrato está licenciado bajo la MIT License, lo que permite un uso libre, con restricciones mínimas de redistribución y modificación.
