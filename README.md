# flyer-integracao

Gerador de flyer de integração com **QR codes** gerados no navegador. Pensado pra onboarding de novos colaboradores: a pessoa escaneia os códigos pra baixar o app, conectar no Wi-Fi do local e preencher a declaração de treinamento.

Painel à esquerda pra configurar, preview do flyer à direita, e botão de imprimir/salvar PDF.

Desenvolvido por **Davi Senise — Técnico de Suporte TI**.

---

## o que faz

| QR code | Para que serve |
|---|---|
| Aplicativo | Aponta pro link de download do app |
| Wi-Fi | Conecta no Wi-Fi do local **automaticamente** ao escanear |
| Treinamento | Abre o formulário de declaração de treinamento |

Tudo é gerado no próprio navegador (HTML/CSS/JS), sem backend. Edite os campos no painel e o flyer atualiza ao vivo.

---

## o detalhe técnico: QR de Wi-Fi

O QR de Wi-Fi não é um link — ele usa um **formato padrão** que Android e iPhone reconhecem nativamente pra conectar sem digitar senha:

```
WIFI:T:WPA;S:NomeDaRede;P:senha;;
```

`T` é o tipo de segurança (WPA), `S` o nome da rede, `P` a senha. A câmera lê e oferece conectar direto.

---

## a automação por trás do formulário (Power Automate)

O QR de treinamento aponta pra um **Microsoft Forms**. Quando o colaborador preenche, um fluxo no **Power Automate** dispara e:

1. Captura o nome informado no formulário
2. Gera um arquivo `.txt` de declaração com um nome padronizado
3. Salva automaticamente numa pasta do OneDrive/SharePoint

O nome do arquivo segue um padrão fixo + a variável: `Treinamento - <Nome do colaborador>`. O prefixo `Treinamento - ` é fixo no fluxo; só o nome muda, vindo da resposta do formulário.

> Essa parte é um fluxo no Power Automate, não vive no HTML. O HTML só hospeda o QR que leva ao formulário. O fluxo em si não está neste repositório por conter caminhos internos.

---

## como adaptar

Os valores são **fictícios**. Edite ao vivo pelo painel ou troque os `value` padrão dos inputs no HTML:

- Marca, título e subtítulo do cabeçalho
- Link do app
- Rede e senha do Wi-Fi
- Link do formulário de treinamento

Troque também o logo (quadrado "EE" no topo).

---

## requisitos

Navegador com internet (a biblioteca de QR é carregada via CDN). Depois de aberto, funciona offline.

---

## nota sobre portfólio

Versão com dados fictícios. Se adaptar do real, remova antes de publicar: SSID/senha reais de Wi-Fi, links internos, URL real do formulário, caminhos de OneDrive/SharePoint e logos de terceiros.

---

## autor

**Davi Senise** — Técnico de Suporte TI
[LinkedIn](https://www.linkedin.com/in/davisenise/) · [GitHub](https://github.com/davisenise)
