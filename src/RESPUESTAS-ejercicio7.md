# Ejercicio 7 — `type` vs `interface`

> Este archivo no se corrige con tests automáticos: lo lee el docente.
> Respondé con tus palabras, en base a lo que probaste en `ej07-tipos-interfaces.ts`.

## ¿Qué permite hacer `interface` que `type` no (o no tan bien)?

`interface` permite definir la estructura de un objeto y tiene la posibilidad de ser extendida mediante `extends`. También permite declarar varias veces una misma `interface`, y TypeScript combina sus propiedades (declaration merging).
  
Por eso resulta cómoda cuando estamos definiendo objetos o entidades que pueden necesitar ser ampliados.

## ¿Qué permite hacer `type` que `interface` no?

`type` permite definir otros tipos además de objetos. Por ejemplo, permite crear uniones:

```ts
type ID = number | string;
```

También permite definir tuplas:

```ts
type Coordenadas = [number, number];
```

Y alias de tipos primitivos:

```ts
type Nombre = string;
```
Además, permite trabajar con mapped types y combinar tipos mediante intersecciones.

## ¿Ambas se pueden extender? ¿Cómo se hace en cada caso?

Sí, ambas se pueden extender, pero de distinta manera.  
Con `interface` se utiliza `extends`:

```ts
interface Persona { nombre: string; }
```

```ts
interface Alumno extends Persona { legajo: number; }
```

Con `type` se puede utilizar una intersección `&`:

```ts
type Persona = { nombre: string; };
```

```ts
type Alumno = Persona & {
    legajo: number;
};
```

## ¿Cuál elegirían para representar una entidad del dominio (por ejemplo, `Alumno`)? ¿Por qué?

Elegiría `interface` para representar una entidad de dominio como Alumno, porque estamos describiendo la estructura de un objeto y `interface` está pensada especialmente para este propósito. Además, permite extender fácilmente la entidad si en el futuro necesitamos agregar nuevas propiedades.
