# JSvalidator
JS validate is a simple field validator in JS
#### JSvalidador é um validador simples de campos em JS

# Utilização
Import the Script file into your page
#### Importe o arquivo do Script em sua página
```html
<script src="https://cdn.jsdelivr.net/gh/hnrazevedo/JSvalidator/JSvalidator.js" type="text/javascript"></script>
```

## Standard options
```html
<script>
    Validator.options({
        alert : function(message, classMessage) {
            alert(m) 
        },
        submitter : function(formSubtEvt) {
            formSubtEvt.target.submit();
        },
        return: false
    });
</script>
```

### Setting options
```html
alert: Return function in case of input error. Alert (message_error) pattern
submitter: Return function if the form is valid. Default continues to submit form
return: Defines whether to execute the submitter or to return the validation result
```

## Rules
To determine a form for validation use the load function
#### Para determinar um formulário para validação utilize a função load
```html
<script>
  let form = document.querySelector(...);
  Validator.load(form,...);
</script>
```
The validation rules must be passed along with the form, following the standard
#### As regras de validação devem ser passadas junto com o formulário, seguindo o padrão
```html
<script>
  let form = document.querySelector(...);
  let rules = {
      email: {required:true, filter:274, regex:'/^[_a-z0-9-]+(\.[_a-z0-9-]+)*@[a-z0-9-]+(\.[a-z0-9-]+)*(\.[a-z]{2,3})$/', minlength:1},
      password: {required:true, maxlength:20, minlength:6},
      confirm_password: {required:true, equals:"password"},
      remember_login: {required:false, maxlength:2, minlength:2},
      birth: {required:true, type:"date", regex:'/^[0-9]{2}\/[0-9]{2}\/[0-9]{4}$/'}
  }
  Validator.load(form,rules);
</script>
```

## Supported rules
```
required: Used to define whether information is mandatory
minlength: Tests if the minimum number of characters has been reached
maxlength: Tests if the character limit has been exceeded
regex: Tests regular expression
equals: Used to confirm some information
```

### Events
Validation is triggered in the Input blur and Form submit events
#### A validação é disparada nos eventos Input blur e Form submit

### Input blur
Tests the input that triggered the event
#### Testa o input que disparou o evento

### Form submit
Tests all inputs passed for validation
#### Testa todos os inputs passados para validação

### Error message
In the event that a field does not pass validation, an element ```<p>``` is sought within the form, which has the ``name`` attribute identical to that of the input and which has the class ```inputMessage```, if it does not exist and the alert function with the error message is triggered.
#### No caso de um campo não passar na validação, é buscado um elemento ```<p>```, dentro do formulário, que tenha o atributo ```name``` idêntico ao do input e que tenha a class ```inputMessage```, caso o mesmo não existá e disparada a função alert com a mensagem de erro.

### Credits
- [Henri Azevedo](https://github.com/hnrazevedo) - Developer
