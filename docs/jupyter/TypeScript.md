---
title: Jupyter - TypeScript
---

```typescript
function generateId(length: number = 11): string {
    let result: string = '';
    const characters: string = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    for (let i = 0; i < length; i++) {
        result += characters.charAt(Math.floor(Math.random() * characters.length));
    }
    return result;
}

console.log(generateId());
```

    xjX6biooWaK
    


```typescript
// https://en.wikipedia.org/wiki/Linear_congruential_generator
class SeededRNG {
    constructor(private seed: number | undefined | null = null) {
        if (seed === null || seed === undefined) {
            this.seed = globalThis.crypto.getRandomValues(new Uint32Array(1))[0];
        }
        this.nextFloat();
    }

    #a = 48271;
    #c = 0;
    #m = Math.pow(2, 31) - 1;

    public nextFloat(): number {
        this.seed = (this.seed * this.#a + this.#c) % this.#m;
        return this.seed / this.#m;
    }
}

function generateSeededId(length: number = 11, seed?: number): string {
    let result: string = '';
    const characters: string = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    const rng: SeededRNG = new SeededRNG(seed);
    for (let i = 0; i < length; i++) {
        result += characters.charAt(Math.floor(rng.nextFloat() * characters.length));
    }
    return result;
}

console.log(generateSeededId());
const seed = 100;
const testSeeded1 = generateSeededId(11, seed);
const testSeeded2 = generateSeededId(11, seed);
console.log({testSeeded1, testSeeded2, equal : testSeeded1 === testSeeded2 });
```

    SCpEUp235Ic
    { testSeeded1: [32m'fIJx8exSV7C'[39m, testSeeded2: [32m'fIJx8exSV7C'[39m, equal: [33mtrue[39m }
    


```typescript
class LCG {
    private _seed: number;
    private _a: number;
    private _c: number;
    private _m: number;
    constructor(seed: number = Date.now()) {
        this._seed = seed;
        this._a = 1664525;
        this._c = 1013904223;
        this._m = Math.pow(2, 32);
    }

    public next(): number {
        this._seed = (this._a * this._seed + this._c) % this._m;
        return this._seed / this._m;
    }
}

// Usage
let generator = new LCG();
console.log(generator.next());  // Outputs a pseudorandom number between 0 and 1
let seededGenerator = new LCG(100);
console.log(seededGenerator.next()); // will be the same each time as the seed doesn't change
```

    [33m0.821491003036499[39m
    [33m0.2748232155572623[39m
    


```typescript
const vals = new Uint32Array(10);
globalThis.crypto.getRandomValues(vals);

console.log(vals);
```

    Uint32Array(10) [
      [33m1287065518[39m, [33m3184436673[39m,
      [33m2820440769[39m, [33m4127699734[39m,
      [33m1759577503[39m,  [33m574560478[39m,
      [33m4010494916[39m, [33m1246423558[39m,
      [33m4260730715[39m, [33m1460420101[39m
    ]
