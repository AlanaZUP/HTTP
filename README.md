# HTTP: Entendendo a web por baixo dos panos

# Java Servlet: Fundamentos da programação web Java

O foco deste repositório é servir como anotações das aulas oferecidas pelo curso [Alura](https://cursos.alura.com.br/course/http-fundamentos). Auxiliando na absorção e fixação do conteúdo, e também sendo um apoio nas horas de dúvidas ou esquecimento do assunto.

Tópicos abordados nessa aula:

### O que é HTTP?

O HTTP (***H****iper****T****ext* ***T****ransfer* ***P****rotocol* ) é um protocolo que define regras de comunicação entre o *Client-Server*. É possível consultar a especificação dessas regras neste [link](https://datatracker.ietf.org/doc/html/rfc2616)

### A web segura - HTTPS

Quando fazemos uma requisição pelo navegador para um servidor, pode haver N intermediários antes de realmente chegar ao seu navagedor. Assim surgiu o HTTPS (HTTP SSL/TLS: ***S****ecure* ***S****ockets* ***L****ayer* /  ***T****ransport*  ***L****ayer*  ***S****ecurity*), é o HTTP com uma camada adicional de segurança/criptografia.

Para ter um site seguro com o HTTPS é necessário ter um certificado digital, ele que irá gerar as chaves de criptografia. Os navegadores com a chave pública criptografam as informações e as enviam para o servidor que as descriptografa com a chave privada.

### Endereços sob seu domínio

Ao entrarmos um site, estamos no endereço desse site. O endereço começará com o nome do protocolo, no nosso caso `http` ou `https`. Após o nome do protocolo vem `://` seguido pelo nome do site, pelo `domínio`, esse domínio é formado pelo `www` (***W****ord* ***W****ide* ***W****eb*), e analizando da esquerda para direita teremos os níveis desse domínio:

<br>

![hierarquia domínio](https://github.com/AlanaZUP/HTTP/blob/master/domain-hierarquia.png)

<br>

Existe também subdomínios, que representam sessões específicas dentro de um site. Por exemplo, no caso do Gmail temos o endereço: `mail.google.com` , ou ainda no caso do Google Drive: `drive.google.com`. Tanto Gmail como Drive são subdomínios do domínio Google.

O domínio foi criado para organizar os sites na internet e para a gente ter algo fácil para se lembrar. As máquinas na internet têm uma outra forma de se endereçar. Elas usam o que se chama endereços de IP, números muitos difíceis para gente decorar.

A gente acessa os sites pelo URL. Quando realizamos uma requisição essa URL é transformada em um número por um serviço transparente chamado de DNS (***D****omain* ***N****ame* ***S****ystem*).

Esse serviço age como um grande banco de dados de domínios. 

Agora imagine que o servidor é uma casa: dependendo da casa há várias portas disponíveis. O que é preciso saber é qual porta devemos utilizar quando chegarmos na casa. A porta utilizada o protocolo HTTP é a `80` e a utilizada para o protocolo HTTPS é a `443`.

A URL é o endereço da WEB, ele possui o ***protocolo*** seguido pelo ***domínio***, após o domínios podemos ter um caminho para um ***recurso*** que se deseja acessar.

![HTTP-URL](https://github.com/AlanaZUP/HTTP/blob/master/http-url.png)

### O cliente pede e o servidor responde

Ao efetuarmos um login em um site, o navegador envia o nosso login e a nossa senha para o servidor através do protocolo HTTP. No mundo HTTP, a requisição enviada pelo navegador para o servidor é chamada de `HTTP REQUEST`. O que recebemos como resposta é chamada de `HTTP RESPONSE`. A comunicação segue sempre esse modelo `Request-Response`. O cliente pede as informações e o servidor responde o que foi requisitado e nunca inicia a comunicação!

Cada recurso é independente do outro e não depende do anterior. Cada requisição é independente da outra e ela sempre deve conter todas informações para o servidor responder. Chamamos essa característica de **stateless**.

Após fazermos um login em um site e termos acesso liberado, o servidor tem certeza que o usuário existe e gera uma identificação para o usuário que é devolvido na resposta, essa identificação é guardada dentro dos cookies, geralmente com o nome relacionado a `session-id`. Esse nome, PHPSESSIONID, JSESSIONID ou outro, é gerado pela ferramenta de gerenciamento de Sessão. Uma sessão HTTP é que um tempo que o cliente permanece ativo no sistema.

O cookie é um arquivo de texto criado pela aplicação web que guarda informações sobre usuário no navegador. Ele fica associado com um domínio que pode ter vários cookies.

<br>
<br>

### Depurando a requisição HTTP

Quando o servidor retorna uma resposta, ele envia um `status code` do HTTP indicando o que aconteceu no processamento do pedido. Pedemos catalogá-los como a seguir:

2XX -> Respostas de sucesso
3XX -> Mensagem de redirecionamento
4XX -> Respostas de erro do cliente
5XX -> Respostas de erro do servidor

A documentação mais completa e detalhada está neste [link](https://httpstatuses.com/)

### Parâmetros da requisição

Os parâmetros em uma requisição são usados para definir detalhes da pesquisa ou enviar dados de um formulário. Utilizando o método `GET` os atributos são passados como parâmetro na URL. O método `POST` deixa os parâmetros no corpo da requisição, assim evita que informações importantes, como a senha, fiquem explícitas na URL.

O `GET` é usado para receber dados, o `POST` para adicionar algo no servidor, o `DELETE` deleta um dado e o `PUT` edita um dado. Os dois últimos são importantes quando falamos de Web Services.

Um Web Service disponibiliza uma funcionalidade na web, através do protocolo HTTP. A grande diferença de um Web Service é que os dados não vem no formato HTML, e sim em algum formato independente da visualização, como XML ou JSON.

<br>
<br>

### Serviços na web com REST

O `REST` pe um padrão arquitetural para comunicações entre aplicações. Ele aproveita a estrutura proposta pelo HTTP, a URI define os recursos e as operações são expressadas através dos métodos do HTTP (GET/POST/PUT/DELETE). Nós podemos especificar o tipo de resposta que precisamos através dos cabeçalhos `Accept` e `Content-Type`. [Aqui](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) você verá alguns formatos aceitos e como expressa-los.


<br>
<br>

### HTTP2 - Por uma web mais eficiente

O HTTP2 não muda nada em relação ao que já conhecemos do HTTP. Ele especifica mais a nível de servidor, ele implementa algumas melhorais:
- `headers` são binários e comprimidos com o algoritmo `HPACK`
- Ele habilita o `GZIP` como padrão de resposta, sendo que o retorno vem zipado.
- As requisições e respostas podem paralelas.
- Os cabeçalhos guardam status, `Headers Stateful`.
- Ele especifica o `Server-push`, o ato do servidor enviar dados sem que o browser peça.

### Exercício Proposto

Você ficou responsável por definir o melhor uso do protocolo HTTP para possibilitar a criação de uma API que realiza pesquisas de passagens de avião e cadastro de compradores. 

Para a parte de pesquisa, nos diga qual verbo http você vai utilizar e também como vai passar os argumentos. Além disso, é necessário que você explique o motivo da decisão. 

Para a parte de cadastro, nos diga qual verbo http você vai utilizar e também como vai passar os argumentos. Outro ponto importante é:  Esse endereço pode receber dados via formulário normal(form-url-encoded) ou JSON. Como você vai adicionar essa flexibilidade? Explique o motivo da decisão. 

Para fechar, é necessário que sempre que possível a comunicação seja feita com os dados criptografados. O que você sugeriria aqui e por que?

<br>
<br>

### Minha Solução

Parte da pesquisa:
- Eu utilizaria o método GET passando os parâmetros pelo URL. Pois o protocolo HTTP tem como padrão o uso do GET para realizar uma visualização sem alterar algo e para pesquisar as passagens de avião não iremos informar nenhum dado comprometedor. 
 
<br>

Parte de cadastro:
- Eu utilizaria o método POST passando os parâmetros pelo corpo da requisição. Pois o protocolo HTTP tem como padrão o uso do POST para realizar cadastros e inserir novas informações, e, falando a nível de segurança, como pode envolver algum dado comprometedor, o POST por não enviar os dados pelo URL se torna uma opção mais segura.
- Para que o endereço seja capaz de receber dados via formulário normal(form-url-encoded) ou JSON eu irei adicionar essa funcionalidade através do cabeçalho `Accept`, dessa forma `Accept: application/x-www-form-urlencoded, application/json` 

<br>

- Para realizar uma comunicação segura e criptografada eu utilizaria o protocolo HTTPS, pois o primeiro, devido ao SSL/TLS realiza uma comunicação criptografada sendo que se alguém entre o cliente e o servidor interceptar a requisição não conseguira interpretar

### Solução Especialista

- Objetivo de aprendizado: Criar um endereço que recebe get e os parâmetros de pesquisa
    - Motivo da escolha: Escolhi o Get porque estamos fazendo uma busca. A semântica básica do HTTP sugere o uso de tal verbo para este tipo de operação. Além disso, o navegador suporta tranquilamente.
- Criar um endereço que recebe um post para o cadastro. Além disso, esse endereço vai analisar o content-type da requisição para saber como lidar com o formato do dado enviado.
- Necessário criar a estrutura de certificados para habilitar a criptografia via https nas comunicações. 

### Resultado

- Peso 2 (0): Utilização de content-type para definir o formato
Por ter interpretado errado, eu abordei como sendo o Accept para fazer essa configuração, Eu tenho consciência de que o Accept é uma configuração pelo lado do cliente que indica quais tipos ele aceita e que o Content-type é a informação que o servidor analisa. 

- Peso 2 (2): Utilização de https para criptografar a comunicação
Acredito que abordei o assunto, apesar de levar pelo lado do cliente

- Peso 3 (2): Utilização de get e parâmetros pela url para a pesquisa
Acredito que abordei o assunto, apesar de levar pelo lado do cliente

- Peso 3 (3): Utilização de post para o cadastro=
Acredito que abordei o assunto, apesar de levar pelo lado do cliente