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

[**Debatendo esse assunto em alguns fóruns, ouvi essa opinião que acho válido deixar registrado:**](https://www.tabnews.com.br/jayp/explicando-matematicamente-a-direfenca-do-bd-relacional-e-bd-nao-relacional)

A álgebra relacional é um conjunto de operações que atuam sobre relações e produzem outras relações como resultado. Estas operações são fundamentadas em conceitos matemáticos sólidos e fornecem a base teórica para os bancos de dados relacionais.

Estas operações têm definições matemáticas precisas, o que significa que, quando você executa uma operação em um banco de dados relacional, você está, de fato, aplicando operações matemáticas em seus dados.

A verdadeira distinção entre Bancos de Dados Relacionais e Não Relacionais:

Bancos de Dados Relacionais: São fundamentados na álgebra relacional. Cada operação que você realiza tem uma definição matemática precisa. Por exemplo, quando você faz uma junção entre duas tabelas, está aplicando a operação de junção da álgebra relacional.

Bancos de Dados Não Relacionais: Não são baseados na álgebra relacional. Eles podem estabelecer algumas relações entre os dados, mas essas relações não são definidas estritamente pela álgebra relacional. Portanto, as operações realizadas sobre essas relações não têm as garantias matemáticas que as operações em bancos de dados relacionais têm.

A álgebra relacional é o coração dos bancos de dados relacionais, e seu estudo é fundamental para compreender a teoria e prática por trás desses sistemas. Encorajo o autor a continuar sua jornada de aprendizado e a explorar ainda mais as profundezas da álgebra relacional e dos bancos de dados. Seu interesse e dedicação são louváveis e farão a diferença em sua trajetória profissional.

Para quem deseja aprofundar seus conhecimentos e compreender as fundações teóricas dos bancos de dados, sugiro a leitura dos seguintes artigos clássicos:

"A Relational Model of Data for Large Shared Data Banks" por Edgar F. Codd

Neste artigo, Edgar F. Codd introduz o modelo relacional, que se tornou a base para a maioria dos sistemas de gerenciamento de bancos de dados modernos. O artigo aborda os conceitos fundamentais da álgebra relacional e estabelece as bases teóricas para o armazenamento e manipulação de dados em bancos de dados relacionais.

"Organization and Maintenance of Large Ordered Indexes" por Rudolf Bayer

Este artigo apresentou ao mundo a estrutura e funcionamento das árvores B, que são amplamente utilizadas em sistemas de gerenciamento de bancos de dados para indexação e recuperação eficiente de dados. Rudolf Bayer introduz o conceito e as operações associadas às árvores B, proporcionando insights valiosos sobre sua importância e aplicação prática.

Ambos os artigos são leituras essenciais para estudantes, pesquisadores e profissionais da área de bancos de dados. Eles não apenas fornecem uma compreensão profunda dos conceitos fundamentais, bem como a inserem em seus contextos originais. Servindo como uma base sólida para futuras inovações e avanços no campo. Encorajo a leitura desses trabalhos para enriquecer ainda mais sua compreensão e apreciação dos bancos de dados e das teorias subjacentes.