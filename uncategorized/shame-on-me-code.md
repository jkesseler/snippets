# Code I wrote but shouldn't have


## Numeric input values
Updating a controlled React input for numeric values that should allow both a comma and a period as decimal separator. The value is then used to calculate other numeric values.

```javascript
const value = {
  /* ... */
price: (
  // TODO: Figure out a nice way to do this
  // Take a value that might be a number or a string
  // cast to string, replace the comma with a dot so parseFloat().toFixed() won't err
  // parse string to Number and add 2 decimals
  // cast back to string
  // replace dot with comma
  parseFloat(d.currentPrice.price.toString().replace(',', '.')).toFixed(2).toString().replace('.', ',')
),
/* ... */
}
```
