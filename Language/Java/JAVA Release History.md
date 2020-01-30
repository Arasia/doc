# JAVA

---

## JDK 1.7

### Type Interface

``` java
List<Integer> list = new ArrayList<>();
```

- Generic Type Parameter can skip -> "<>"

### String value in Switch

``` java
switch(sport) {
    case "SOCCER" : 
    case "BASKETBALL" : 
    default : 
}
```

- String value can use Switch Value

### try-with-resource

```java
try(
   		FileInputStream fin = new FileInputStream("info.xml");
    	BufferedReader br = new BufferedReader(new InputStreamReader(fin));
   ) {
    if(br.ready()) {
        String line1 = br.readLine();
        System.out.println(line1);
    }
} catch (FileNotFoundException ex) {
    System.out.println("Info.xml is not found");
} catch (IOException ex) {
    System.out.printLn("Can't read the file")
}
```

- If Resource implement AutoCloseable or Closeable, try-with-resource can auto return that resource

### Underscore In Numeric literal

```java
// right Case
int billion = 1_000_000_000; // 10^9
long creditCardNumber = 1234_5678_9012_3456L; // 16 digit number
long ssn = 111_22_3333L;
double pi = 3.1415.9265;
float pif = 3.14_15_92_65f;
// wrong case
double pi = 3._1415_9265; // Underscore can't after dot
long creditCardNumber = 1234_5678_9012_3456_L; // Numeric literal can't end of Underscore
long ssn = _111_22_3333L; // Numeric literal can't start of Underscore
```

- Underscore can be used as display of numeric literal

### Catching Multiple Exception Type in Single Catch Block

```java
try {
    ...
} catch (ClassNotFoundExeption | SQLException ex) {
    ex.printStackTrace();
}
```

- Multi Exception in Single Catch Block
- If One Exception is Sub Class relationship of other Class, occur multi-catch error

### JAVA NIO 2.0

### More Precise Rethrowing of Exception

``` java
public void func() throws ParseException, IOException {
    try {
        new FileInputStream("abc.txt").read();
        new SimpleDateFormat("ddMMyyyy").parse("12-03-2014");
    } catch (Exeption ex) {
        System.out.println("Caught exception : " + ex.getMessage());
        throw ex;
    }
}
```

- Function can throw Precise Exception

### Update of Array List & Hash Map

- Array List initial capacity is modified ten to zero

---

## JDK 1.8

### Lambda Expression

### Stream API

### java.time Package

- Less than Java 7, almost developer uses Joda-Time
- In Java 8, java.time package is included 

### Java Script Engine Change

---

---

# Product  Use JAVA

---

## Spring Framework

### 4.3.x

- JDK 6 ~ 8
- Supported until 2020

### 5.0.x

- JDK 8 ~ 10

### 5.1.x

- JDK 8 ~ 12
    - JDK 11+를 위해 권장됨

### 5.2.x

- JDK 8 ~ 14

### 5.3.x

- JDK 8 ~ 17

---

## Open SAML

### 3.x

- java 7, 8, 11