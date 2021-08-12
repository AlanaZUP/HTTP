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
![hierarquia domínio](../domain-hierarquia.png)


### O cliente pede e o servidor responde

### Depurando a requisição HTTP

### Parâmetros da requisição

### Serviços na web com REST

### HTTP2 - Por uma web mais eficiente