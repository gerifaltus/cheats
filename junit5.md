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

Referencias:
```
@ValueSource
@CsvSource
@CsvFileSource
@MethodSource
```

## Tag
Sirve para nombrar o etiquetar pruebas y de esta manera seleccionar, dentro de un archivo, qué tests correr específicamente. En el ejemplo aparecen varios test con diferentes etiquetas. Por default cuando se ejecuta el archivo de test, se ejecutan todos los tests, pero en la configuración de la ejecución de tests (dependiendo del IDE) se puede seleccionar qué tags (tests) se van a probar. 
```java
@Tag("saldo") //probar saldos
void test1(){
}

@Tag("retiro")
void test2(){
}

@Tag("transferencia")
void test3(){
}

@Tag("saldo")
void test4(){
}
```

## TestInfo
Sirve para mostrar imprimir información descriptiva de la clase (el método test, los tags, argumentos, etc) dentro de cada test a probar. En el ejemplo en el siguiente método se puede incluir la información contenida en TestInfo:
```java
@Tag("saldo") //probar saldos
@DisplayName("Test para probar testInfo")
void test1(TestInfo testInfo){
  System.out.println("ejecutando:  "+testInfo.getDisplayNombre + " - "+ testInfo.getTestMethod().orElse(null).getName() + " con las etiquetas: "+testInfo.getTags())
}
```

El resultado cuando se ejecuta el test es el siguiente:
```
ejecutando: Test para probar testInfo - test1 con las etiquetas [saldo]
```
Aunque la funcionalidad de TestInfo puede usarse en cada método, no es factible repetir la misma línea de código en cada test, lo mejor es agregarlo dentro de un método anotado con @BeforeEach.


## TestReporter
Al igual que TestInfo, TestReporter funciona como una salida estandar tipo log, es decir en vez de usar `System.out.println()` para emitir la salida dentro de cada método, se puede usar testReporter.publishEntry(). En el ejmplo se muestra su funcionamiento.
```java
@Tag("saldo") //probar saldos
@DisplayName("Test para probar testInfo")
void test1(TestInfo testInfo, TestReporter testReporter){
  testReporter.publishEntry("ejecutando:  "+testInfo.getDisplayNombre + " - "+ testInfo.getTestMethod().orElse(null).getName() + " con las etiquetas: "+testInfo.getTags())
}
```

La salida sería algo como lo siguiente:
```
timestamp = 2021-02-18T08:32:58, value = ejecutando: Test para probar testInfo - test1 con las etiquetas: [saldo]
```

## Timeout
Esta anotación sirve para realizar pruebas con tiempo medido, es decir, en un test se puede probar la eficiencia de algún método y ese método no debe sobrepasar x cantidad de segundos, o por ejemplo realizar pruebas repetidas (con argumentos @ParametizedTest) y la bateria de pruebas no debe sobrepasar x cantidad de segundos. En el ejemplo se muestra cómo fuciona.
```java
@Tag("timeout")
@DisplayName("Test para probar timeout")
@Timeout(5)
void test1(){
  Timeout.SECONDSsleep(6);
}
```

En el ejemplo anterior se fija el timeout en 5 segundos pero la ejecución del test es de 6 segundos, entonces la prueba fallará.

Referencias:
```assertTimeout();
```


