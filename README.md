# WireMock Examples

Repositório que reproduz alguns exemplos de uso da ferramenta WireMock utilizando APIs abertas

## Getting Started

Clone o repositório

```
git clone https://github.com/wellrocha/wiremock-examples.git
```

Execute o jar

```
java -jar wiremock-standalone-2.26.3.jar
```

Para usar WireMock de forma prática, o caminho mais fácil é acessar a url http://localhost:8080/__admin/recorder/ preencha o endereço que deseja salvar as requisições. Ex: https://api.chucknorris.io/

1. Ative a opção Record
2. Vá no Postman ou alguma ferramenta de sua preferência
3. Faça as requisições para o endereço do seu WireMock. 
  Ex: 
    http://localhost:8080/jokes/random
    http://localhost:8080/jokes/random?category=career
    http://localhost:8080/jokes/categories
4. Selecione opção Stop para finalizar
5. Os novos arquivos serão criados na pasta mappings, agora você pode editar e fazer as customizações que fizerem mais sentido conforme a sua necessidade

## Exemplos Nesse Repositório

### [Chuck Norris Jokes Api](https://api.chucknorris.io/)

```
url: http://localhost:8080/jokes/categories
method: GET
status: 200

url: http://localhost:8080/jokes/random
method: GET
status: 200

url: http://localhost:8080/jokes/random?category=qualquer-nome-de-categoria
method: GET
status: 200

url: http://localhost:8080/jokes/random?category=idontknow
method: GET
status: 404

url: http://localhost:8080/jokes/random?category=1212
method: GET
status: 400

url: http://localhost:8080/jokes/search?query=
method: GET
status: 400

url: http://localhost:8080/jokes/search?query=hiho
method: GET
status: 200
```

### [Via CEP](https://viacep.com.br/)

```
url: http://localhost:8080/ws/01001000/json/
method: GET
status: 200

url: http://localhost:8080/ws/555/json/
method: GET
status: 400

url: http://localhost:8080/ws
method: POST
status: 201

url: http://localhost:8080/ws
method: POST
status: 400
detalhe: cep vazio
```

Repare que é possível ter um endpoint e retornar códigos diferentes conforme o que foi configurado. Sendo assim você pode mockar uma chamada para um endpoint POST e simular diversas situações conforme a necessidade, basta fazer a customização dos arquivos na pasta mappings.

## Links Úteis

* http://wiremock.org/docs/api/
* http://wiremock.org/docs/stubbing/
* http://wiremock.org/docs/request-matching/
* https://viacep.com.br/
* https://api.chucknorris.io/
* https://codebeautify.org/json-escape-unescape