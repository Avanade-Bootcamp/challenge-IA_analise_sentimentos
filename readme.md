# 🤖 Challenge - Análise de Sentimentos

Este repositório contém um projeto desenvolvido como parte do desafio **"Análise de Sentimentos com Language Studio no Azure AI"**. O objetivo foi criar análises e insights de avaliações reais retirada de plataformas como [Google](www.google.com) e [Reclame AQUI](https://www.reclameaqui.com.br/).

## :telephone_receiver: Contato
Caso tenha dúvidas ou sugestões, fique à vontade para entrar em contato comigo através das minhas redes sociais:

[![LinkedIn](https://img.shields.io/badge/LinkedIn-gabriel--rosaa-blue?logo=linkedin)](https://www.linkedin.com/in/gabriel-rosaa/)
[![GitHub](https://img.shields.io/badge/GitHub-Gabriel--Pink-black?logo=github)](https://github.com/Gabriel-Pink)
![Discord](https://img.shields.io/badge/Discord-gabriel.tec-%237289DA?logo=discord)
[![Whatsapp](https://img.shields.io/badge/Whatsapp-(11)%2091356--4300-%237289DA?logo=whatsapp)](https://wa.me/+5511913564300)

## :rocket: Tecnologias Utilizadas
- **Azure**
- **cognitiveservices**

## 🚧 Disclamer

Neste desafio, a plataforma https://language.cognitive.azure.com/ estava com erro no meu acesso. Portanto, tive a necessidade de fazer o consumo desse serviço via API. Por esta razão, as respostas estarão sendo enviadas em json.

## ⚓ Language cognitive via API

Basta acessar a plataforma **Develop** do recurso criado, e lá estarão todas as informações para acesso.
![image](https://github.com/user-attachments/assets/c1c4f859-bf98-41bd-be4b-d3a4f82bb21b)

Todavia, não há uma documentacao com todas as rotas que podem ser consumidas ou como realizar a requisicao autenticada. Por isso, estarei deixando uma tabela abaixo com as rotas e o header mesário para fazer uma requisição autenticada.

```json
{
	"Ocp-Apim-Subscription-Key": "CHAVE 1"
}
```

### Rotas

| 📌 **Funcionalidade**                                | 🌍 **Rota**                                       | ✨ Método |
| ---------------------------------------------------- | ------------------------------------------------- | -------- |
| Detecção de Idioma                                   | /text/analytics/v3.1/languages                    | POST     |
| Análise de Sentimentos                               | /text/analytics/v3.1/sentiment                    | POST     |
| Extração de Palavras-chave                           | /text/analytics/v3.1/keyPhrases                   | POST     |
| Reconhecimento de Entidades                          | /text/analytics/v3.1/entities/recognition/general | POST     |
| Reconhecimento de Entidades PII (Dados Sensíveis)    | /text/analytics/v3.1/entities/recognition/pii     | POST     |
| Linkagem de Entidades na Wikipédia                   | /text/analytics/v3.1/entities/linking             | POST     |
| Análise de Opinião (aspect-based sentiment analysis) | /text/analytics/v3.1/sentiment?opinionMining=true | POST     |


## 🎯 Avaliações 

```json
{
    "documents": [
        {
            "id": "1",
            "text": "Se vc quiser comer as tortilhas com molho, que é o certo em todo restaurante mexicano, tem que pagar a parte. Cobram caro em um pingo de molho, um roubo.. totalmente desproporcional ao tamanho da porção de tortilhas.. e pedi um combo que não veio nenhum molho também, nem no taco e nem na quesadilha.. nunca vi isso, comida seca . Não tenho vontade de voltar"
        },
        {
            "id": "2",
            "text": "Achei simplesmente maravilhoso, recomendo. O atendimento foi o melhor que já vi naquela praça de alimentação. Quanto a comida .... Coisa mais deliciosa, eu amo o burrito de costelinha BBQ e a tortilha de kit kat não tem pra ninguém. Outra vez fui comer o burrito Giga, esse é pra quem come bastante mesmo. Meus parabéns."
        },
        {
            "id": "3",
            "text": "A comida estava deliciosa, e o ambiente muito acolhedor. Fui jantar com amigos e todos adoraram as opções do menu."
        },
        {
            "id": "4",
            "text": "O atendimento foi péssimo, a comida estava fria e sem gosto. Não recomendo."
        },
        {
            "id": "5",
            "text": "O atendimento foi muito bom, a comida estava deliciosa e o ambiente muito agradável. Recomendo."
        }
    ]
}
```

Resultado:

```json
{
    "documents": [
        {
            "id": "1",
            "sentiment": "negative",
            "confidenceScores": {
                "positive": 0.02,
                "neutral": 0.20,
                "negative": 0.78
            },
            "sentences": [
                {
                    "sentiment": "neutral",
                    "confidenceScores": {
                        "positive": 0.14,
                        "neutral": 0.82,
                        "negative": 0.04
                    },
                    "offset": 0,
                    "length": 110,
                    "text": "Se você quiser comer as tortilhas com molho, que é o certo em todo restaurante mexicano, tem que pagar à parte."
                },
                {
                    "sentiment": "negative",
                    "confidenceScores": {
                        "positive": 0.05,
                        "neutral": 0.24,
                        "negative": 0.71
                    },
                    "offset": 110,
                    "length": 45,
                    "text": "Cobram caro em um pingo de molho, um roubo..."
                },
                {
                    "sentiment": "negative",
                    "confidenceScores": {
                        "positive": 0.00,
                        "neutral": 0.02,
                        "negative": 0.98
                    },
                    "offset": 155,
                    "length": 63,
                    "text": "Totalmente desproporcional ao tamanho da porção de tortilhas."
                },
                {
                    "sentiment": "neutral",
                    "confidenceScores": {
                        "positive": 0.01,
                        "neutral": 0.68,
                        "negative": 0.32
                    },
                    "offset": 218,
                    "length": 84,
                    "text": "Pedi um combo que não veio com nenhum molho também, nem no taco e nem na quesadilla."
                },
                {
                    "sentiment": "negative",
                    "confidenceScores": {
                        "positive": 0.02,
                        "neutral": 0.47,
                        "negative": 0.52
                    },
                    "offset": 302,
                    "length": 29,
                    "text": "Nunca vi isso, comida seca."
                },
                {
                    "sentiment": "negative",
                    "confidenceScores": {
                        "positive": 0.00,
                        "neutral": 0.07,
                        "negative": 0.92
                    },
                    "offset": 331,
                    "length": 27,
                    "text": "Não tenho vontade de voltar."
                }
            ],
            "warnings": []
        }
    ],
    "errors": [],
    "modelVersion": "2025-01-01"
}

```

Com isso, conseguimos analisar que além da media geral do cliente, a IA faz uma avaliação isolada para cada sentença do texto, dando notas isolada para cada afirmação e classificando se o sentimento foi **Positivo**, **Neutro** ou **Negativo**.

## 🖼 Imagens de todas as sentenças 

![image](https://github.com/user-attachments/assets/e71babdc-8f40-466e-bc77-fd0de29e967e)
![image](https://github.com/user-attachments/assets/ade6bd20-1867-4e22-98cb-4bdd37a1d393)
![image](https://github.com/user-attachments/assets/c8ee2b77-5eb2-4901-aea5-7497694780ad)
![image](https://github.com/user-attachments/assets/6b07e553-1627-420a-8862-ca1132927afd)
![image](https://github.com/user-attachments/assets/33ecd85b-048f-4294-97ce-3d0bef190061)

---
:pushpin: **Nota:** Este projeto foi desenvolvido para fins educacionais e de aprimoramento técnico.
