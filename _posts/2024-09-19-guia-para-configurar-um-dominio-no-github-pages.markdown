---
layout: post
title:  "Guia para configurar um domínio no GitHub Pages"
date:   2024-09-19 13:00:00 -0300
categories: github
---

Você sabia que dá para configurar um domínio próprio personalizado na sua página no GitHub Pages? 🤯

Essa publicação é um guia para ajudar quem tiver dificuldade (assim como eu tive) na hora de configurar um domínio com sua página no GitHub Pages.

Antes, devemos saber sobre o GitHub Pages e qual o conceito de domínio.

# O que é um domínio?

**Domínio** é o que você digita na barra do navegador quando quer acessar um site. É através dele que as pessoas encontram e o acessam.

Ele é uma maneira de localizar e identificar, de forma mais amigável, os endereços de sites. Imagine a má praticidade ter que digitar um endereço de IP para acessar um site, como `163.116.227.13`.

Um domínio é dividido em duas partes variáveis: nome do domínio e sua extensão (conhecida como *TLD*).

## Subdomínio

**Subdomínio** é um endereço que faz parte do domínio, ou seja, é uma ramificação do mesmo. O subdomínio usa o domínio principal e se diferencia pela adição de um outro nome, além do nome do domínio.

Dentro de `www.seudominio.com`:
- `www` = subdomínio
- `seudominio.com` = domínio (domínio apex)
- `.com` = TLD

# O que é o GitHub Pages?

O **GitHub Pages** é um serviço de hospedagem de site estático que usa arquivos HTML, CSS e JavaScript diretamente de um repositório no GitHub e, como opção, executa os arquivos por meio de um processo e publica um site.

Por padrão, é possível hospedar seu site no domínio `github.io` do GitHub, mas pode-se hospeda-lo em um domínio personalizado próprio.

# Configurando um domínio personalizado

Pessoas com permissões de administrador para um repositório podem configurar um domínio personalizado de um site do GitHub Pages.

Primeiro, para configurar um domínio personalizado próprio, você deve possuir um, normalmente comprado através de provedores no mercado já estabelecidos, como a [Hostinger](https://www.hostinger.com.br/registro-de-dominio), [GoDaddy](https://www.godaddy.com/pt-br/dominios), [HostGator](https://www.hostgator.com.br/registro-de-dominio/) etc.

## Como obter um domínio?

Acesse a sua plataforma de compra de domínios preferida e escolha um nome para seu domínio, incluindo sua extensão, e efetue o pagamento da mesma.

Cada extensão possui diferentes precificações, estabelecidas pelas diferentes plataformas que as vendem.

Dicas para encontrar o nome de domínio perfeito:
- Priorize um nome de domínio curto, simples e fácil de lembrar;
- Evite hifens, números, gírias e palavras que têm muitas letras;
- Verifique a disponibilidade;
- Pense na sua localização.

## Configuração Inicial

Acesse o dashboard do seu provedor, na área de DNS / Nameservers, para começar a sua configuração.

Adicione um registro do tipo `CNAME` para fazer o apontamento do host para sua página, na qual deve-se adicionar um novo campo com o valor igual a `@`, no host, ou igual ao nome do seu endereço de acesso GitHub Pages `<nomedousuario>.github.io`.

Dessa forma:
> `@ | usuario.github.io`

Adicione um registro do tipo `A` (também chamado `ALIAS` ou `ANAME`), na qual deve-se criar 4 registros que apontam para os endereços IPv4 do GitHub Pages. Para cada um dos 4 campos adicione `@`, no host, e no valor aponte para cada um dos 4 IPs do GitHub Pages.

Na maioria das vezes, você tem que criar dois registros A para o seu domínio. Um com o subdomínio `www` e o outro sem.

Dessa forma:
- `@ | 185.199.108.153`
- `@ | 185.199.109.153`
- `@ | 185.199.110.153`
- `@ | 185.199.111.153`

No lugar dos registros A, pode-se criar registros do tipo AAAA para apontar para os endereços IPv6 do GitHub Pages.

Dessa forma:
- `@ | 2606:50c0:8000::153`
- `@ | 2606:50c0:8001::153`
- `@ | 2606:50c0:8002::153`
- `@ | 2606:50c0:8003::153`

Não esqueça de configurar o seu subdomínio `www`. Assim o seu site se torna acessível tanto como `seudominio.com` e como `www.seudominio.com`.

---

Endereços IPv4 do GitHub Pages:
- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

Endereços IPv6 do GitHub Pages:
- `2606:50c0:8000::153`
- `2606:50c0:8001::153`
- `2606:50c0:8002::153`
- `2606:50c0:8003::153`

## Configuração no GitHub

Dentro da área de configuração do seu repositório GitHub, acesse a opção "Pages" e vá no campo "Custom domain". É nela onde você irá inserir o nome do seu domínio.

A partir daí é só aguardar pela propagação do DNS e poderá acessar sua página com o nome que você escolheu. Isso pode demorar algum tempo para se propagar mundialmente.

Quando tiver terminado, no repositório da sua página será criado um arquivo `CNAME` onde irá conter o domínio do seu site, como por exemplo `seudominio.com`. Caso isso não ocorra, crie o arquivo manualmente, insira o seu domínio com o *TLD*, salve e suba o arquivo no repositório.

Lembre-se de deixar a opção *Enforce HTTPS* ativada se quiser o certificado SSL ativo em seu site.

---

Acesse a [documentação oficial do GitHub Pages para configurar um domínio personalizado](https://docs.github.com/pt/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages).
