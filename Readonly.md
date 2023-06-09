## This type is used to make all properties defined in `T` readonly, except those defined in `P`
### Example:
```ts
export type PerformReadonly<T, P extends keyof T> = {
    readonly [Property in keyof T]: T[Property]
} & { -readonly [Prop in P]: T[P] };

// Creating a interface to test the type with
interface I {
    a: string;
    b: number;
    c: bigint;
}

// Creating an example variable to test the assignment
let i: PerformReadonly<I, "c">;

i.a = "Aw D:"; // Can't assign as it's Read-Only
i.b = 16; // Can't assign as it's Read-Only
i.c = BigInt(2382398); // Can assign as it's not Read-Only
```
#### P.S.: Properties defined in `P` also work if the properties in `T` are already Read-Only
