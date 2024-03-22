# Custom Flatpickr Fork

This project is a customized fork of [flatpickr/flatpickr](https://github.com/flatpickr/flatpickr).

## Why Create This Fork?

In the original library, when a user entered an invalid date, for example, "22 marco 2021", the library was clearing this input even with the `allowInvalidPreload` flag enabled.

So, I decided to customize the library to allow the input to retain the invalid date if the parser couldn't translate the input into an appropriate format. This way, I can later validate the input using the `validation` feature of VueFormulate's `FormulateInput`. You can read more about it [here](https://vueformulate.com/guide/validation/#custom-validation-rules).

Here's an example of how I use custom validation rules:

```javascript
validation: 'custom',
validationRules: {
  custom: ({ value }) => {
    if (!value) return true;
    const date = moment(value, 'DD MMM YYYY HH:mm', true);
    return !!date?.isValid();
  },
},
validationMessages: {
  custom: `Provide a valid date. e.g. ${moment().format('DD MMM YYYY HH:mm')}`,
},
```

I welcome suggestions and improvements regarding this scenario! Feel free to contribute! 😊