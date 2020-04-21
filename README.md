# You Don't Need HTML Template

You Don't Need HTML Template

## <a name="TOC">Table of Contents</a>

1. [Interpolation](#interpolation)
1. [Condition](#condition)
1. [Array](#array)
1. [Object](#object)
1. [Filters](#filters)

### <a name="interpolation">Interpolation</a>

**HTML Template**

``` html
<div>{{first}} {{last}}</div>
```

**ES2015**

``` javascript
const str = `<div>${first} ${last}</div>`
```

**Data**

``` javascript
const first = 'Jim'
const last = 'Green'
```

**Output**

``` html
<div>Jim Green</div>
```

### <a name="condition">Condition</a>

**HTML Template**

``` html
<div>
  {{if condition}}
  <div>Something</div>
  {{else}}
  <div>Other</div>
  {{/if}}
</div>
```

**ES2015**

``` javascript
const str = `
<div>
  ${condition ?
    `<div>Something</div>` :
    `<div>Other</div>`
  }
</div>
`
```

**Data**

``` javascript
const condition = true
```

**Output**

``` html
<div>
  <div>Something</div>
</div>
```

### <a name="array">Array</a>

**HTML Template**

``` html
<ul>
  {{each lists}}
  <li>{{user}} is {{age}} years old.</li>
  {{/each}}
</ul>
```

**ES2015**

``` javascript
const str = `
<ul>
  ${lists.map((item) => {
    return `<li>${item.user} is ${item.age} years old.</li>`
  }).join('')}
</ul>
`
```

**Data**

``` javascript
const lists = [
  {
    user: 'Lee',
    age: 16
  },
  {
    user: 'Jim',
    age: 18
  }
]
```

**Output**

``` html
<ul>
  <li>Lee is 16 years old.</li><li>Jim is 18 years old.</li>
</ul>
```

### <a name="object">Object</a>

**HTML Template**

``` html
<ul>
  {{each obj}}
  <li>{{$key}}: {{$value}}</li>
  {{/each}}
</ul>
```

**ES2015**

``` javascript
const str = `
<ul>
  ${Object.keys(obj).map((key) => {
    return `<li>${key}: ${obj[key]}</li>`
  }).join('')}
</ul>
`
```

**Data**

``` javascript
const obj = {
  user: 'Lee',
  age: 16
}
```

**Output**

``` html
<ul>
  <li>user: Lee</li><li>age: 16</li>
</ul>
```

### <a name="filters">Filters</a>

**HTML Template**

``` html
{{100 | currency}}
```

**ES2015**

Just JavaScript function.

``` javascript
const currency = x => x.toFixed(2)

const str = `${currency(100)}`
```

**Output**

``` html
100.00
```

## License

MIT
