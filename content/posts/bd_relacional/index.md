---
title: "Diferenciando Banco Relacional e não Relacional"
date: 2023-11-16
draft: false
---

## Banco de Dados Relacional vs Não Relacional: Compreendendo as Diferenças

{{< default "span__name_date" >}}
  @jayp | Novembro 16, 2023
{{< /default >}}

![Postgres vs Mongo](/img/mongodb-vs-postgresql.png)

Lembrando que esse artigo não tem o propósito de ensinar [**álgebra relacional**](https://pt.wikipedia.org/wiki/%C3%81lgebra_relacional). Enfim, vamos lá:

Gostaria de compartilhar um insight que tive durante minha recente sessão de estudo na madrugada. Enquanto estudava matemática e, mais especificamente, as  [**relações matemáticas**](https://pt.wikipedia.org/wiki/Rela%C3%A7%C3%A3o_(matem%C3%A1tica)), ocorreu-me um pensamento interessante.

Durante os estudos percebi que as relações matemáticas podem ser representadas por tabelas. Essa simples afirmação abriu uma janela de compreensão na minha mente, mostrando como conceitos aparentemente abstratos podem ser visualizados e organizados de forma mais tangível e é ai que entra os [**Bancos de Dados**](https://pt.wikipedia.org/wiki/Banco_de_dados).

#### Banco de Dados Relacional:

O modelo relacional é caracterizado por sua estrutura de armazenamento em "tabelas". Você pode se perguntar: "Por que é chamado de 'relacional' se os dados são armazenados em tabelas?"
Essa nomenclatura tem raízes na matemática, onde o conceito de relação se originou. Na matemática, uma tabela é formalmente chamada de relação, daí o termo "modelo relacional". Assim, quando utilizamos tabelas para organizar dados, estamos aplicando o conceito matemático de relação, mesmo que informalmente as chamemos de tabelas.

#### Banco de Dados Não Relacional:

A nomenclatura "não relacional" não implica que seja impossível estabelecer relações entre os dados, mas sim que os dados não são armazenados em tabelas, como ocorre no modelo relacional. Pode-se pensar nisso como a equivalência de um "banco de dados sem tabelas".
No contexto de bancos de dados não relacionais, os dados são frequentemente armazenados de maneira mais flexível, permitindo acomodar tipos de informações variados, como documentos, gráficos, pares chave-valor, entre outros. Essa flexibilidade é especialmente valiosa quando se lida com dados sem uma estrutura fixa ou quando é necessário dimensionar horizontalmente para acomodar o crescimento.

Portanto, a distinção entre bancos de dados relacionais e não relacionais não está relacionada à capacidade de estabelecer relações entre dados, mas sim à maneira como os dados são estruturados e organizados, bem como à flexibilidade que cada modelo oferece para lidar com diferentes tipos de informações e necessidades de escalabilidade.