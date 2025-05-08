# typescript-OOP-problems-solving-Blogs

# assignment-1-next-level-batch-5

## 📘 Description
assignment-1's all problems is here...!!!
---

## 🧩 answer List:
```ts

 // -------------------------------✅ Problem 1: solution-1:---------------------------
    const formatString = (input: string, toUpper?: boolean): string => {
        if (toUpper) {
            return input.toUpperCase();
        } else {
            return input.toLowerCase();
        }
    }

    const inputValue1 = formatString("assalamu alaikum")
    console.log(inputValue1)//  output: assalamu alaikum

    const inputValue2 = formatString("assalamu alaikum", true)
    console.log(inputValue2)//  output: ASSALAMU ALAIKUM

    const inputValue3 = formatString("assalamu alaikum", false)
    console.log(inputValue3)//  output: assalamu alaikum


    // ----------------------------✅ Problem 2: solution-2 -------------------------
    const books = [
        { title: "Unlock the Power of JavaScript", rating: 4.5 },
        { title: "Fun with HTML, CSS & JavaScript", rating: 3.2 },
        { title: "React Explained Simply", rating: 5.0 },
        { title: "Programming Life Story", rating: 3.0 },
        { title: "Think in a Coder’s Way", rating: 4.0 },
    ];


    type TypeAlias = { title: string; rating: number };

    const filterByRating = (items: TypeAlias[]): TypeAlias[] => {
 const topRatingbook1: TypeAlias[] = items.filter((singeBook: TypeAlias) => singeBook.rating >= 4);
        return topRatingbook1;
    }

    // -----------------------------✅ Problem 3: solution-3----------------------

    const concatenateArrays = <T>(...arrays: T[][]): T[] => {
        let fullArray: T[] = [];

        arrays.forEach((array1: T[]) => {
            fullArray.push(...array1)

        });

        return fullArray
    }

    const ifStirng = concatenateArrays<string>(["a", "b"], ["c"]); //output: [ 'a', 'b', 'c' ]
    console.log(ifStirng);
    const ifNumber = concatenateArrays<number>([1, 2], [3, 4], [5, 6]); // output: [ 1, 2, 3, 4, 5, 6 ] 
    console.log(ifNumber);


  // -----------------------------✅ Problem 4: solution-4----------------------

    class Vehicle {
        private _make: string; 
        public year: number;
        constructor(_make: string, year: number) {
            this._make = _make;
            this.year = year;
        }

        getInfo() {
             return `Vehicle Make: ${this._make}, Year: ${this.year}.`;
        }
    }

    class Car extends Vehicle { // child class

        constructor(_make: string, year: number, private model: string) {
            super(_make, year);
        }

        getModel() {
            return `The "Model is : ${this.model}" `;
        }

    }

    const myCar = new Car("Toyota", 2024, "Primio");

    console.log(myCar.getInfo()); // output: The Vehicle make: "Toyota, & year: 2025"
    console.log(myCar.getModel()); // outpu: the "model is : Primio"



   // -----------------------------✅ Problem 5: solution-5----------------------

    type TypeUnion = string | number;

    const processValue = (value: TypeUnion): TypeUnion => {

        return typeof value ==="string" ? value.length : value * 2;
        
    }

    console.log(processValue('alhadulillah'))//  output: 12
    console.log(processValue(7)) // ouptut: 14

    // -----------------------------✅ Problem 6: solution-6----------------------

  interface Product {
        name: string;
        price: number;
    }
    const products: Product[] = [
        { name: "Pen", price: 10 },
        { name: "Notebook", price: 25 },
        { name: "Quran", price: 1099 },
        { name: "Bag", price: 50 }
    ];

    const getMostExpensiveProduct = (products: Product[]): Product | null => {

        if(products.length == 0){ return null};
        
        const expensiveProdectIs: Product = products.reduce((maxExpensiveProduct: Product, currectExpensiveProduct: Product): Product => {
            const expensive = currectExpensiveProduct.price > maxExpensiveProduct.price ? currectExpensiveProduct : maxExpensiveProduct;
            return expensive;

        })
        return expensiveProdectIs;
    }

    const theExpensiveProductIs = getMostExpensiveProduct(products);
    console.log(theExpensiveProductIs) // output:  { name: 'Quran', price: 1099 }

    const ifArrayIsEmpty = getMostExpensiveProduct([]);
    console.log(ifArrayIsEmpty) // output: null




   // -----------------------------✅ Problem 7: solution-7----------------------


enum Day {
    Monday = "Monday",
    Tuesday = " Tuesday",
    Wednesday = " Wednesday",
    Thursday = " Thursday",
    Friday = " Friday",
    Saturday = " Saturday",
    Sunday = " Sunday"
}
const getDayType = (day : Day) :string => {
if(day ===Day.Friday || day ===Day.Saturday){
    return "Weekend"
} else {
    return "Weekday"
}
}

console.log(getDayType(Day.Friday))// output: Weekend
console.log(getDayType(Day.Monday))// output: Weekday


   // -----------------------------✅ Problem 8: solution-8----------------------

    const squareAsync = (value: number): Promise<number> => {

        return new Promise<number>((resolve, reject) => {

            if (value > 0) {
                setTimeout(() => {
                    resolve(value * value);
                }, 1000);

            }

            else if (value <= 0) {
                setTimeout(() => {
                    reject(`Error: Negative number not allowed`)
                }, 0);
            }
        })

    }

    const showOutput = async (value: number): Promise<number> => {
        const isValuePositive: number = await squareAsync(value);
        return isValuePositive;
    }

    showOutput(6).then(console.log) // output after 1s: 36
    showOutput(0).catch(console.error) // output: Error: Negative number not allowed


```
 end typescript--------------
 
----------- Now start Blogs details: --------------------------


--------------------------blog 1 --------------------
1. What are some differences between interfaces and types in TypeScript?
1.✒️📌.answer: In TypeScript, we use both interface and type to define the structure of an object. But there are some key differences between them.

The main difference is: interface is specifically used for objects, whereas type can be used for anything—like functions, arrays, strings, numbers, primitives, etc.

In real-world development, both are used, and each has its own benefits.

Using interface, we can easily extend or create a duplicate structure using another interface. But in the case of type, to extend it we have to use the intersection (&) operator to combine.

Even though interface is powerful, type is more flexible.

Example of interface and type:
```
interface Admin {
  role: string;
}

interface SuperAdmin extends Admin {
  accessLevel: number;
}

type Manager = {
  role: string;
};

type TeamLead = Manager & {
  teamSize: number;
};

```
Now, if you're working on an industry-level project, you need to have a good understanding of both interface and type. This will help you increase flexibility in your work. Depending on how your project is structured, you will need to follow that approach and use them accordingly.
--------------------blog 2--------------------
2. What is the use of the keyof keyword in TypeScript?
2.✒️📌.answer: In TypeScript, keyof is used for many useful things.

keyof is a utility type in TypeScript that takes an object type and produces a union of its keys (property names). That means you can check which properties exist in an object type using keyof.

As a result, you can dynamically access property names of an object type.

Example:
```
type Person = {
  name: string;
  age: number;
  isStudent: boolean;
};

type PersonKeys = keyof Person;
// Result: "name" | "age" | "isStudent"
```
So, by using keyof, we can write more dynamic and type-safe code when dealing with object properties.
