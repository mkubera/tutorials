## RODZAJE FUNKCJI

```javascript
// FUNKCJE STRZALKOWE I "KLASYCZNE"
// note: strzalkowe dodano dopiero w 2015 (wersja ES6)

// anonimowa funkcja (strzalkowa) [anonymous arrow function]
(num1, num2) => num1 + num2;

// nazwana funkcja (strzalkowa) [named]
const add = (num1, num2) => num1 + num2;

// rozbicie syntaxu na czesci pierwsze:
const // stala
add   // nazwa (dowolna; wybierana przez developra)
=     // przypisanie
(num1, num2)  // parametry (argumenty) (input)
=>    // gruba strzalka [fat arrow]
num1 + num2  // wartosc do zwrocenia z funkcji
;     // konczacy srednik

// arrow functions (funkcje strzalkowe)
// dluzszy i krotszy syntax (wielolinijkowy i jednolinijkowy)

// jednolinijkowa
// slowo return istnieje "po cichu", zaraz po grubej strzalce (=>)
(num1, num2) => num1 + num2;

// wielolinijkowa
// note: wymaga uzycia slowa return
(num1, num2) => {
  return num1 + num2;
};

// nazwana funkcja "klasyczna"
function add(num1, num2) {
  return num1 + num2;
}

// nienazwana funkcja "klasyczna"
function (num1, num2) {
  return num1 + num2;
}

// FUNKCJE CZYSTE I NIECZYSTE (PURE vs IMPURE)
// pure functions (same input, same output) oraz (brak side-effects)
// impure functions (same input, not the same output) oraz (side-effects)

// pure
const add = (num1, num2) => num1 + num2;

// impure
let num2 = 1;
const add = (num1) => {
  num2 = num2 + 1;    // zmieniamy num2 poza funkcja (impure)
  return num1 + num2; // bierzemy wartosc num2 spoza funkcji
}

// CO ZWRACAJA FUNKCJE?
// funkcja, ktora nie zwraca niczego (brak slowa return),
// automatycznie zwraca undefined
// ponizsza funkcja zwrocilaby undefined, bo brakuje slowa return
const add = (num1, num2) => {
  num1 + num2;
};

// CZY FUNKCJE MUSZA COS ZWRACAC?
// nie, ale w programowaniu funkcyjnym zawsze cos zwracaja
// tylko czasem bedziemy chcieli, zeby tak nie bylo
// np. wtedy, gdy musimy manipulowac DOM przegladarki za
// pomoca JavaScript'owego DOM API
const changeDOMNodeColour = (newColour) => {
  document.querySelector('.box').style.backgroundColor = newColour;
}
// powyzsza funkcja:
// - jest nieczysta (ma side-effects (manipuluje DOM))
// - zwraca undefined (brak return)
// jest to jeden z przykladow na funkcje, ktore nie moga byc czyste.
// manipulacja DOM (czyms zewnetrznym) wymusza nieczystosc
// ta funkcja nic nie zwraca, bo sluzy wlasnie do zrobienia czegos
// "poza soba"


// DEFAULT PARAMETERS
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters
// mozemy nadac parametrom naszej funkcji domyslnych wartosci (default values)
const add = (num1 = 1, num2 = 2) => num1 + num2;
// wowczas przy wywolaniu bez argumentow
add();
// otrzymamy wynik 3 (poniewaz num1 to domyslnie 1, a num2 to 2)
// caly czas mozemy sami wprowadzic wlasne argumenty
add(2); // 2 + 2 = 4
add(2, 3); // 2 + 3 = 5
```
