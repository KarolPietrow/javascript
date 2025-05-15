# JavaScript - powtórzenie
IDE Online - https://playcode.io/javascript
## Podstawy języka

Zmienna – const, let

let x = 5;

const name = "Jan";

Typy danych – string, number, boolean, array, object, null, undefined

Operatory – +, -, *, /, %, ===, !==, &&, ||

## Operacje na stringach
text.length – długość tekstu

text.substring(start, end) – wycina fragment tekstu

text.indexOf("a") – zwraca pozycję litery

text.split(" ") – dzieli tekst na tablicę

text.trim() – usuwa spacje z początku i końca

text.repeat(n) – powtarza tekst n razy

String.fromCharCode(x) – zamiana liczby na literę

## Tablice
Tworzenie: let arr = [1, 2, 3]

Rozpakowanie: [...txt] – np. zamiana stringa na tablicę znaków

arr.push(x) – dodaje na końcu

arr.pop() – usuwa ostatni

arr.join("") – łączy elementy w string

arr.sort() – sortuje

arr.map(x => x * 2) – przekształca każdy element

arr.filter(x => x > 0) – filtruje elementy

arr.reduce((acc, el) => acc + el, 0) – suma elementów

Iteracja: for, for..of, forEach

## Funkcje
Deklaracja:

```
function myFunc(x) {
  return x + 1;
}
```
Funkcja strzałkowa:

const double = x => x * 2;
🔄 Instrukcje warunkowe i pętle
if, else, else if

switch – szczególnie do mapowania np. liter rzymskich

for (let i = 0; i < n; i++)

while (warunek)

break, continue


## Inne
```
Palindromy (txt === txt.split('').reverse().join(''))

Usuwanie duplikatów z posortowanej tablicy

Wspólny prefiks w tablicy stringów

Zamiana rzymskich liczb na arabskie

Dekodowanie wartości z tablicy 2D po ruchach (r, d, l, u)

Liczenie długości ostatniego słowa

Liczenie sposobów wejścia po schodach (ciąg Fibonacciego)

const str = "rrrdddlld..." – poruszanie się po tablicy jak po mapie

String.fromCharCode() – odszyfrowywanie kodów ASCII
```

## Tworzenie obiektów
Literal obiektu:

```
const user = {
  name: "Jan",
  isActive: true,
  show() {
    console.log(this.name, this.isActive);
  },
  setActive(active) {
    this.isActive = active;
  }
};
```
Konstruktor + new:

```
function User(name) {
  this.name = name;
}
const u1 = new User("Ola");
```
Klasa (class) — syntactic sugar dla prototypów:

```
class Book {
  constructor() {
    this.users = [];
  }

  addUser(name, age, phone) {
    this.users.push({ name, age, phone });
  }

  showUsers() {
    console.log("Wszyscy użytkownicy w książce:");
    this.users.forEach(user => console.log(user));
  }

  findByName(name) {
    const found = this.users.find(u => u.name === name);
    console.log(found || false);
  }

  findByPhone(phone) {
    const found = this.users.find(u => u.phone === phone);
    console.log(found || false);
  }

  getCount() {
    console.log(this.users.length);
  }
}
```

## Tablice i operacje
const arr = [1, 2];
arr.push(3);
Pętla forEach():

arr.forEach((el) => console.log(el));
Przykład sprawdzania pustej tablicy:
```
if (arr.length === 0) {
  console.log("Brak użytkowników");
} else {
  console.log("Lista:", arr);
}
```

## Funkcje i domknięcia (closures)
### Closure = funkcja + zapamiętany kontekst

```
function createCounter() {
  let count = 0;
  return function () {
    return ++count;
  };
}

const counter1 = createCounter();
console.log(counter1()); // 1
console.log(counter1()); // 2

const counter2 = createCounter();
console.log(counter2()); // 1
```

## Prototype i dziedziczenie
Wszystkie obiekty mają łańcuch dziedziczenia (__proto__)
Klasy w JS to syntax sugar dla dziedziczenia prototypowego

```
String.prototype.mirror = function () {
  return this.split("").reverse().join("");
};

console.log("Ala ma kota".mirror()); // "atok am alA"
```


## Operacje na tekstach
Obiekt text z wieloma metodami:
```
const text = {
  check(txt, word) {
    return txt.includes(word);
  },
  getCount(txt) {
    return txt.length;
  },
  getWordsCount(txt) {
    return txt.trim().split(/\s+/).length;
  },
  setCapitalize(txt) {
    return txt
      .split(" ")
      .map(word => word.charAt(0).toUpperCase() + word.slice(1))
      .join(" ");
  },
  setMix(txt) {
    return txt
      .split("")
      .map((char, i) =>
        i % 2 === 0 ? char.toLowerCase() : char.toUpperCase()
      )
      .join("");
  },
  generateRandom(lng) {
    const letters = "abcdefghijklmnopqrstuvwxyz";
    return Array.from({ length: lng }, () =>
      letters[Math.floor(Math.random() * letters.length)]
    ).join("");
  },
};
```
