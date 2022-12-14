# probabilitygacha


## Getting Started

### Installation


```shell
$ npm i pai-en/probabilitygacha
```

### Usage

```js
const GachaJS = require('probabilitygacha'); 

const rates = {
  ssr: 5.9,
  sr: 12.8,
  r: 18.8,
  c: 62.5,
}; // Should total to 100%

const gacha = new GachaJS(rates);

// Set new rates
gacha.setRates({
  ssr: 1.9,
  sr: 16.8,
  r: 18.8,
  c: 62.5,
});

console.log(gacha.getRates());
// output: { ssr: 1.9, sr: 16.8, r: 18.8, c: 62.5 }

console.log(gacha.getPullByRarity());
// output: c <- Random

console.log(gacha.getPullByRarity(10)); // 10 pulls
// output is random array
// [
//   'r', 'sr', 'sr',
//   'r', 'c',  'r',
//   'c', 'c',  'c',
//   'c'
// ]
```

```js
const gacha = new GachaJS(
  {
    ssr: 5.9,
    sr: 12.8,
    r: 18.8,
    c: 62.5,
  },
  {
    collection: [
      { name: 'ssr1', rarity: 'ssr' },
      { name: 'ssr2', rarity: 'ssr' },
      { name: 'sr1', rarity: 'sr' },
      { name: 'sr2', rarity: 'sr' },
      { name: 'sr3', rarity: 'sr' },
      { name: 'r1', rarity: 'r' },
      { name: 'r2', rarity: 'r' },
      { name: 'r3', rarity: 'r' },
      { name: 'r4', rarity: 'r' },
      { name: 'c1', rarity: 'c' },
      { name: 'c2', rarity: 'c' },
      { name: 'c3', rarity: 'c' },
      { name: 'c4', rarity: 'c' },
      { name: 'c5', rarity: 'c' },
    ],
    findKey: 'rarity',
  }
);

// If collection is something like `{ name: 'c5', rarity: { r: 'c' } }` (Notice `the rarity: { r: 'c' }`)
// `findKey` can be `rarity.r`

console.log(gacha.getPullByCollection());
// output: { name: 'c1', rarity: 'c' } <- Random

console.log(gacha.getPullByCollection(10)); // 10 pulls
// output is random array
// [
//   { name: 'r3', rarity: 'r' },
//   { name: 'c1', rarity: 'c' },
//   { name: 'r2', rarity: 'r' },
//   { name: 'ssr2', rarity: 'ssr' },
//   { name: 'c2', rarity: 'c' },
//   { name: 'c2', rarity: 'c' },
//   { name: 'c3', rarity: 'c' },
//   { name: 'c4', rarity: 'c' },
//   { name: 'c3', rarity: 'c' },
//   { name: 'c2', rarity: 'c' }
// ]
```
