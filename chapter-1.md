## 1.

```js
/*
temp <- a
a <- b
b <- c
c <- d
d <- temp
*/
let a = 1,
  b = 2,
  c = 3,
  d = 4; // b, c, d, a -> 2, 3, 4, 1.

let temp = a;
a = b; // 1 -> 2
b = c; // 2 -> 3
c = d; // 3 -> 4
d = temp; // 4 -> 1
```

## 2.

```js
/*
[en]
In the first time M and N can be any positive number;

In line 35 and 37, R always be > 0, and < N after the first time;

When M is replaced by N and N is replaced by R, this keep the previous rule.

[pt-br]
No comeco M e N podem ser qualquer número positivo, com isso não é possível garantir M > N;

Em qualquer caso R sempre será < N;

Caso R > 0, M será N e N será R, garantindo M > N.
*/
let m = 1,
  n = 2;

function E() {
  let r = m % n;

  if (r === 0) return n;

  m = n;
  n = r;

  return E();
}
E();
```

## 3.

```js
/*
F1. [Find remainder] Divide m by n and let m be the remainder. (0 ≤ m ≤ n)
F2. [Is it zero?] If m = 0, the algorithm terminates; n is the answer.
F3. [Find remainder] Divide n by m and let n be the remainder. (0 ≤ n ≤ m)
F4. [Is it zero?] If n = 0, the algorithm terminates; m is the answer, else go back to step F1.
*/
let m = 2,
  n = 1;

function F() {
  m = m % n;
  if (m === 0) return n;

  n = n % m;
  if (n === 0) return m;
  return F();
}
F();
```

## 4.

```js
/*
[en] 57 is the greatest common divisor.
[pt-br] 57 é o maior divisor comum.
*/
let m = 2166,
  n = 6099;

function F() {
  m = m % n;
  if (m === 0) return n;

  n = n % m;
  if (n === 0) return m;
  return F();
}

console.log(F());
```

## 5.

[en] It is not a algorithm because it does not meet the guidelines for finiteness, definiteness, and effectiveness.

[pt-br] Não é um algorítmo porque não segue as diretrizes de finitude, definitividade e eficácia.

## 6.

```js
/*
[en] The average is 2.6.
[pt-br] A média é 2.6.
*/
function average(m, n) {
  let r = m % n;

  if (r === 0) return 1;

  m = n;
  n = r;

  return 1 + average(m, n);
}

let t = 5;
let a = 0;
for (let i = 1; i <= t; i++) {
  a += average(i, t);
}
console.log("T5: " + a / t);
```

## 7.

```js
/*
  [en] Tm is the range when N is constant, and Um is when M is a constant. Um is always Tm + 1 when N > M; 
  [pt-br] Tm é a média quando N é um número constante, enquanto Um é a média quando M é o número constante. Um sempre será Tm + 1 quando N > M.

*/
function average(m, n) {
  let r = m % n;

  if (r === 0) return 1;

  m = n;
  n = r;

  return 1 + average(m, n);
}

const constN = 5;
let t = 10,
  tm = 0,
  um = 0;
for (let i = 1; i <= t; i++) {
  let varN = 0;
  do {
    varN = Math.floor(Math.random() * 10);
  } while (varN <= constN);
  tm += average(varN, constN);
  um += average(constN, varN);
}
console.log("Tm: " + tm / t, "Um: " + um / t);
```
