# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome:
Matrícula:
Usuário do GitHub:
Usuário do Docker Hub:

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?


Usei a imagem base `nginx:1.27-alpine`.
O tamanho final da imagem foi 73.6mb.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.

   Os arquivos do site ficam em `/usr/share/nginx/html/` e usei docker exec -it teste-portal ls /usr/share/nginx/html/

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.

Imagem: jota1612/agrovale-portal:1.0-2628530
Link:  https://hub.docker.com/repository/docker/jota1612/agrovale-portal/general

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?

Usei um token para não utilizar a senha direta da minha conta, pois usando o token posso dar permissões epsecíficas a ele apaga-lo separadamente

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | WORKDIR /usr/share/nginx | O diretório de trabalho não era a pasta usada pelo Nginx para servir o site | Apareceu a página padrão "Welcome to nginx!" em vez de "Voltamos em breve" | Corrigi o caminho para /usr/share/nginx/html |
| 2 | WORKDIR /usr/share/nginx | O diretório de trabalho não era o diretório em que o Nginx serve os arquivos do site. | Mesmo com o Nginx funcionando, o arquivo precisava ficar em `/usr/share/nginx/html`. | Alterei para `WORKDIR /usr/share/nginx/html`. 
|| 3 | | | | |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

-p 7042:80 usa a porta 7042 do computador e a 80 do container. Em -p 80:7042, a porta do container é 7042. O segundo número sempre é a porta do container

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`?

Porque db é o nome do serviço do banco no Docker Compose. Os containers conseguem se comunicar pela rede usando o nome do serviço. localhost apontaria para o próprio container do WordPress, e não para o MariaDB.

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando.

Porque o banco só precisa ser acessado pelos containers da rede do Compose, então não é necessário expor a porta 3306 para o computador host. Para acessar o banco diretamente pelo container, posso usar:

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?

10. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
