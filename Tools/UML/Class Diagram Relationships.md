# Class Diagram Relationships

> This Document is Depended StarUML

## Association

### Association

> Class A ---- Class B

- Every object has each life cycle
- Any object doesn't contain other object

### Directed Association

> Class A ---> Class B

## Aggregation

> Class A ---◇ Class B

- "has-a" relationship
- Every object has each life cycle
- One object contain other object

``` Java
public Class Engine {
    ...
}
public Class Car {
    private Engine engine;
    
    public Car(Engine engine) {
        this.engine = engine;
    }
}
```



## Composition

> Class A ---◆ Class B

- If Parent Object is end of life, child Object is ended with Parent Object life cycle
- Child Object can't have it's own life cycle

```java
public Class Engine {
    ...
}
public Class Car {
    Engine engine = new Engine();
    ...
}
```



## Dependency

> Class A - -> Class B

## Generalization

### Generalization

> Class A ---▷ Class B

### Interface Realization

> Class A - -▷ Class B

