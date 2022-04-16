# CYBERPUNK 2077 WHATS

### Envie o grande questionamento para os seu amigos, onde estão os outros 2076 Cyberpunks?

<p>Abra script.js</p>

<p>Copie todo o conteúdo (clique em raw -> ctrl+a -> ctrl+c)</p>

<p>No WhatsApp Web abra o console do Browser</p>

<p>Cole o código no console e aperte Enter</p>

<p>Pronto</p>

<p>Créditos:</p>

<p>Sricpt de mensagens do whatsapp: <https://github.com/Matt-Fontes></p>
  
<p>Edição Cyberpunk 2077: <https://github.com/TSPsoftware?tab=repositories></p>

### API voltada para vagas de emprego no Brasil 
<p>Esta API possuí dois níveis de autenticação para que ela possa ser utilizada, essa autenticação difere na quantidade de opções e recursos, se adequando as necessidades específicas de cada sistema.</p>  
<p>Para sistemas comuns: É possível buscar vagas de emprego disponíveis no Brasil com diversos filtros de refinamento para pesquisa, conseguindo inclusive os contatos das empresas ofertantes para mais detalhes, além de uma opção para chat ao vivo com esta.</p>
<p>Para sistemas de empresas: É possível cadastrar os dados da empresa, adicionar vagas, editar, excluir, pausar e concluir a seleção da vaga. Com a possibilidade de obter informações pertinentes de possíveis candidatos, como o currículo.</p>

## Endpoints

### POST /auth
Esse endpoind é responsável por realizar o processo de autenticação da API, se bem sucedido um token é gerado. Para obtenção deste token é necessário que você se cadastre no nosso sistema e requira a funcionalidade DEV. 

Este token poderá ser usado para acessar as rotas da API, sendo sub-divido em 2 categorias user e enterprise.

email: E-mail do usuário cadastrado no sistema;

password: Senha do e-mail cadastrado;

Exemplo:
```
{
  "email": "teste@gmail.com",
  "password": "senha123"
}
```
#### Respostas

##### 200 OK

A autentição foi realizada com sucesso e um token deve ser retornado.

Exemplo:

```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJsYXJhbmphQGdtYWlsLmNvbSIsImlhdCI6MTYzNDgyMTM4OCwiZXhwIjoxNjM0OTk0MTg4fQ.RgXyNcDjAMq7u9Dpf8ft7rxbT3pHJnr5w7VRmvmNx1w"
}
```

##### 404 Not Found

A autenticação falhou, com isso um objeto error é retornado, este objeto possuí a mensagem, msg, referente ao erro, podendo estar relacionado ao e-mail ou senha passados a API. Também é retornado uma informação booleana, registered, que informa se a conta está cadastrada no sistema:

Exemplos:

```
{
    "error": {
        "msg": "O e-mail passado não está cadastrado!",
        "registered": false
    }
}
```

```
{
    "error": {
        "msg": "Senha Incorreta!",
        "registered": true
    }
}
```

##### 500 Internal Server Error

O servidor se encontra indisponível no momento ou ocorreu um erro inesperado, com isso será retornado um objeto error.

Exemplo:

```
{
    "error": {
        "msg": "Houve um problema com a validação no servidor! Tente novamente mais tarde...",
        "registered": false
    }
}
```

### GET /jobs
Esse endpoint é responsável por retornar uma listagem de empregos cadastrados na base de dados da nossa API.
#### Parâmetros
##### Vazio
Retorna uma listagem com as últimas 10 vagas adicionadas a API, não havendo nenhuma filtragem por região ou demais informações das vagas.

#### Respostas


##### Filtros de Pesquisa
```
{
  "city": "São Paulo",
  "state": "SP",
  "career": "TI"
}
```
