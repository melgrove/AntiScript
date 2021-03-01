# AntiScript

Compile English sentences into JavaScript. 

>  set number to 5. set exponentiate to function that inputs base, exponent then returns base to the exponent. set newNumber to result of exponentiate number, 3.

Should compile to:

```javascript
let number = 5;
let exponentiate = (base, exponent) => {
  return base**exponent
};
let newNumber = exponentiate(number, 3)
```

---

This is just kind of an idea right now. Not sure how hard it is to build a JavaScript compiler. After some initial research maybe I can use [this](http://zaa.ch/jison/about/).

Some interesting similar projects: 

- [pseudoscript](https://github.com/monkybrain/pseudoscript) (Concept of natural language scope here is really interesting)
- [pseudo-js](https://github.com/gabrielprc/pseudo-js)

## Goals

- Imitate how someone would say the code *out loud* as much as possible

  - Blocks of code should read like English sentences, and programs like stories

- Interoperate with JavaScript perfectly

  - ```javascript
    // You should be able to do this
    const oddsTimesTen = [1,2,3,4,5].filter(n => {
      if n is even then return true 
      else then return true.
    })
    .map(n => n times 10)
    ```

## Language

### assignment

#### `set`  `to`

- **`set`** a **`to`** b **`?forever`**
  - `forever` specifies if the variable is constant

*example*

| AntiScript           | JavaScript    |
| -------------------- | ------------- |
| set foo to 5 forever | const foo = 5 |

### operators

#### without assignment

- a **`plus`** n
- a **`minus`** n
- a **`times`** n
- a **`divided`** by n
- a **`to the`** n

*example*

| AntiScript | JavaScript |
| ---------- | ---------- |
| 2 to the 5 | 2**5       |

#### with assignment

- **`add`** n **`to`** a
- **`subtract`** n **`from`** a
- **`multiply`** a **`by`** n
- **`divide`** a **`by`** n
- **`raise`** a **`to the`** n

*example*

| AntiScript | JavaScript |
| ---------- | ---------- |
| add 3 to n | n += 3     |

### equality

#### `is` and `is not`

-  a **`is`** 5
-  a **`is not`** 5

#### `and`

- a **`is not`** 5 **`and`** 4

#### `or`

- a **`is`** 5 **`or`** 4

#### `in`

-  a **`is in`** 5
-  a **`is not in`** 5

#### `less than`

-  a **`is less than`** 5
-  a **`is not less than`** 5

#### `greater than`

-  a **`is greater than`** 5
-  a **`is not greater than`** 5

#### `even`

- a **`is even`**
- a **`is not even`**

#### `odd`

- a **`is odd`**
- a **`is not odd`**

*example*

| AntiScript              | JavaScript |
| ----------------------- | ---------- |
| 5 is not greater than 9 | !(5 > 9)   |

### control flow

#### `if` `then`

- **`if`** a **`is`** b **`then`** ***block***
- **`if`** a **`is`** b **`then`** ***block*** **`else then`** ***block***

All statements are seperated by either a newline `\n` or a comma `,`

*example*

| AntiScript          | JavaScript      |
| :------------------ | --------------- |
| 'Bob' is not 'Mark' | 'Bob' != 'Mark' |

#### `for every` `in` 

- **`for every`**  n **`in`** b ***block***

### functions

#### definition

**`function that inputs`** ***parameters*** **`then`** ***block***

#### calling

I'm not quite sure what to do here. Calling a function for its return value versus for its side effects is described differently in plain English. My solution right now is to have **`result of`** and **`call`** both call the function.

*example*

| AntiScript                                                   | JavaScript                                                   |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| set getArea to function that inputs length, width then returns length times width.<br />set rectangle to result of getArea 5, 10 | function getArea(length, width) {<br />    return length * width<br />};<br />let rectangle = getArea(5, 10) |

### parameters

Comma **`,`** separated values.

### block

All blocks begin with **`then`** and end with **`.`**. Within a block, all statements must be separated by a comma`,`. To return a value within a function, use  **`returns`** in the block.

### objects and arrays

1. **`set`** c **`to`** e: 4, c: 5
2. **`set`** b **`to`** 1, 2, 3, 5

