# REGEX 


```js
 const regexPatterns = {
  pan: /^([a-zA-Z]){3}([pP]){1}([a-zA-Z]){1}([0-9]){4}([a-zA-Z]){1}?$/,
  pekrn: /^([a-zA-Z]){2}([a-zA-Z0-9_]){8}?$/,
  email: /@\S+\.\S+/,
  mobile: /^(\+91[\-\s]?)?[0]?(91)?[6789]\d{9}$/,
  bankAccountNumber: /^[0-9]{10,25}$/,
  folioNumber: /^[0-9]{1,15}$/,
  name: /^[a-zA-Z0-9_\s]{1,30}$/,
  multiple500: /^\d*[05]00$/,
  numeric: /^[0-9]*$/,
  password:
    /^(?=.*[0-9])(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*])[a-zA-Z0-9!@#$%^&*]{6,20}$/,
  passwordRegex: {
    lowerCase: /([a-z])/,
    upperCase: /([A-Z])/,
    numericChar: /([0-9])/,
    specialChar: /([$@#*()_+|/=[\]{}:])/,
  },
  alphaNumeric: /^[a-zA-Z0-9_]*$/,
  decimal: /^[0-9]+\.?[0-9]*$/,
  pincode: /^[1-9]{1}[0-9]{2}\\s{0, 1}[0-9]{3}$/,
};
```
