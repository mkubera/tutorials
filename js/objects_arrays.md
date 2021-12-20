```javascript
// CRUD
// Read - get
// Create - new
// Update - set
// Delete - (new, but without a key)

// Object Literal

// new
let obj = { id: 1 }; // pary (klucz: wartosc) (key: value) (k: v)

// get
obj; // caly object
obj.id; // wartosc klucza (key / property (prop))

// set (add/update)
// BAD
obj.id = 2;

// GOOD
obj = { ...obj }; // spread operator (wynik: { id: 1 } )
obj = { ...obj, name: "Beata Czaja" }; // add
obj = { ...obj, id: 2 }; // update
obj = { ...obj, id: 3, hasPet: null }; // update + add

// delete
// BAD !!!!!
delete obj.id;

// create new obj without id
obj = { name: obj.name, hasPet: obj.hasPet }; // Much Better :)

// Array

// new
const arr = [{ name: "Joanna" }];
const arr2 = arr.map((name) => ({ name })); // [ {name: "Joanna"} ]

// get
arr[0]; // "Joanna" (uzywajac indeksu 0)

// uzywajac funkcji wyzszego rzedu (higher order functions)
// czyli takich, ktore przyjmuja funkcje callbackowa, jako argument
// np. (person) => person.name === "Joanna"
arr2.filter((person) => person.name === "Joanna"); // [{name: "Joanna"}]
arr2.filter((person) => person.name === "Joanna")[0]; // {name: "Joanna"}
arr2.find((person) => person.name === "Joanna"); // {name: "Joanna"}

// set (add)
// dodanie nowego obiektu w array
const arr3 = [...arr, { name: "Tomasz" }]; // add

// dodanie nowego klucza-wartosci do kazdego z obiektow w array
const arr4 = arr3.map((person) => ({ ...person, createdAt: "15/12/21" }));
// [ {name: "Joanna", createdAt: "15/12/21"}, {...} ]

// update klucza tylko wybranego elementu w array obiektow
const arr5 = arr3.map((person) => {
  // conditional (warunek)
  if (person.name === "Joanna") {
    return { ...person, name: `${person.name} Swiderska` };
  } else {
    return person;
  }
});

// powyzsze mozemy napisac latwiej uzywajac ternary operator (? :),
// ktory jest skrocona wersja if..else
let arr6 = arr3.map((person) => {
  // conditional (warunek)
  return person.name === "Joanna"
    ? { ...person, name: `${person.name} Swiderska` }
    : person;
});

// i mozemy nawet krocej, stosujac troche prostsza nazwe parametru funkcji,
// ale powinnismy to robic tylko w sytuacji, gdy inne nazwy sa dokladne
// (stosujemy tutaj rowniz krotszy zapis funkcji strzalkowej,
// ktory nie wymaga uzycia 'return', bo robi to za nas)
const people = [{ name: "Joanna" }, { name: "Krzysztof" }];

people.map((p) =>
  p.name === "Joanna" ? { ...p, name: `${p.name} Swiderska` } : p
);
// [{ name: "Joanna Swiderska" }, { name: "Krzysztof" }]
```
