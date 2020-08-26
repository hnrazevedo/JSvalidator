# JSvalidator
JSvalidador é um validador simples de campos em JS

# Utilização
Importe o arquivo do Script em sua página
```html
<script src="https://cdn.jsdelivr.net/gh/hnrazevedo/JSvalidator/JSvalidator.js" type="text/javascript"></script>
```

## Opções padrão
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

### Definição de opções
```html
alert: Função de retorno em caso de erro em input. Padrão alert(message_error)
submitter: Função de retorno caso o furmulário seja valido. Padrão continua a submit do form
return: Define se é para executar o submitter ou se é para retornar o resultado da validação
```

## Regras
Para determinar um formulário para validação utilize a função load
```html
<script>
  let form = document.querySelector(...);
  Validator.load(form,...);
</script>
```
As regras de validação devem ser passadas junto com o formulário, seguindo o padrão
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

## Regras suportadas
```
required: Utilizado para definir se informação é obrigatória
minlength: Testa se atingiu o minimo de caracteres
maxlength: Testa se ultrapassou o limite de caracteres
regex: Testa expressão regular
equals: Utilizada para confirmar alguma informação
```

### Eventos
A validação é disparada nos eventos Input blur e Form submit
#### Input blur
Testa o input que disparou o evento
#### Form submit
Testa todos os inputs passados para validação

### Mensagem de erro
No caso de um campo não passar na validação, é buscado um elemento ```<p>```, dentro do formulário, que tenha o atributo ```name``` idêntico ao do input e que tenha a class ```inputMessage```, caso o mesmo não existá e disparada a função alert com a mensagem de erro.

### Créditos
- [Henri Azevedo](https://github.com/hnrazevedo) - Desenvolvedor
