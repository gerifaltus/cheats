# Junit5
## ParametizedTest
Sirve para proporcionar parametros de prueba a un test específico. En el ejemplo, se genera repetición de test dependiendo de la 
cantidad de parametros listados en @ValueSouces:
```java
@ParameterizedTest(name="numero {index} ejecutando con valor {0} - {argumentsWithNames}")
@ValueSource(strings = {"100", "200", "300", "500", "700", "1000"})
void testDebitoCuenta(String monto){
  cuenta.debito(new BigDecimal(monto));
  asertNotNull(cuenta.getSaldo());
  assertTrue(cuenta.getSaldo.compareTo(BigDecimal.ZERO) > 0);
}
```
El test se muestra más o menos así:
```
Numero 1 ejecutando con valor 100 - 100
Numero 2 ejecutando con valor 200 - 200
```
