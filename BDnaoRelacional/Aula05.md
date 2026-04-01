# Aula 05 - Arquitetura de Banco de Dados não convêncionais 

**Evolução Do armazenamento de dados**:
|Modelo Tradicional | Novo Paradigma |
|-------------------|----------------|
|Estrutura rígida em tabelas e colunas | Banco de dados não convêncionais|
|Foco no modelo relacional estrito | Falta de estrutura rígida |
| | Formatos adaptáveis: Documentos, gráficos e objetos |

A arquitetura de _banco de dados não convencional_ é caracterizada pela **falta** de estrutura rígida de tabelas e colunas.
Em vez disso, os dados são armazenados em um formato mais flexível, como **documentos, gráficos ou objetos**.

Um exemplo de banco de dados não convencional é o _banco de dados orientado a documentos_.
Nesse modelo, os dados são armazenados em documentos que podem ter uma estrutura complexa, **com campos e subdocumentos aninhados.**
Cada documento é único e pode ser **indexado** para facilitar a recuperação de dados.

Outro exemplo é o **banco de dados orientado a grafos**, que armazena dados em _nós e arestas_ que representam **relacionamentos** entre eles.
Esse tipo de banco de dados é especialmente útil para a **análise de redes e dados relacionais complexos**.

Esses bancos de dados podem ser implementados em _ambientes distribuídos_, o que **melhora** o ***desempenho e a confiabilidade dos sistemas***.

**O paradigma não convencional(NoSQL)**:

Uma alternativa aos bancos de dados tardicionais, para empresas que precisem lidar com cenários complexos de dados.
* Flexibilidade: Sem estrutura rígida pré-definida. Armazena dados de diferentes tipos em formato adaptável.
* Escalabilidade: Capacidade de crescer e processar grandes volumes sem gargalos estruturais.
* Ambientes distribuídos: Melhora drástica no desempenho e na confiabilidade dos sistemas.

**Iniciando um projeto em BIG DATA**:

1. Definição: Quais tipos de dados serão guardados/armazenados?;
2. Origem: Onde será feita a busca e aquisição dos dados?;
3. Repositório: Desenvolvimento de um lago de dados(DATA LAKE);
4. Captura: Estabelecer formas de captura, como APIs(APPPLICATION PROGRAMMING INTERFACE);
5. Fontes: Pesquisar quais fontes disponibilizam as APIs;
6. Viabilidade: Analisar os custos e o tempo de operação;

Normalmente, para que as informações tenham uma _alta disponibilidade_, é ideal criar um **único repositório**.

No Data Lake, os dados são armazenados da mesma forma em que houve a aquisição, de maneira bruta. Esse tipo de repositório pode ser criado na nuvem.
No processo de criação do Data Lake, é importante que **todos** os membros da equipe, _desde desenvolvedores até os diretores_, participem e entendam como estão sendo organizados e armazenados os dados, para que seja eficiente a busca e resgate dos dados quando necessário.

**O conceito de Data Lake**:
* O que é: Um armazenamento que consolida grandes volumes de dados em um único local.
* A regra de Ouro: Os dados são mantidos em sua forma original/bruta no momento da aquisição, sem necessidade de estruturação ou conversão prévia.
* O benefício: Economia significativa de tempo e recursos computacionais, facilitando acesso e análise futura.
Diferente dos bancos de dados relacionais que exigem uniformidade, um data lake unifica os três tipos fundamentais de dados(estruturados, semi-estruturados, não estruturados)

**O fluxo de transformação dos dados**:

1. Fonte de dados: Múltiplas origens estrtuturadas e não estrtuturadas;
2. Data lake: Dados consolidados em formatos brutos;
3. Transformação/Poração dos dados: Processamento e higienização;
4. dados Prontos: Disponíveis para cada uso diferente - Data wareHouse(DW) e DataMarts(DM);

Outra vantagem do Data Lake é que ele é **escalável** e pode ***crescer com a quantidade de dados armazenados***. Isso significa que, à medida que seus dados crescem, você pode **adicionar mais capacidade de armazenamento ao Data Lake sem interromper o processo de análise ouo acesso aos dados**.

**A era da nuvem(Cloud computing)**

A infraestrutura essencial para bancos de dados, armazenamento e tratamento de grandes volumes de informação.

A definição oficial(NIST): Um modelo que permite acesso sob demanda via redes a um conjunto compartilhado de recursos computacionais, rapidamente provisionados e liberados com mínimo esforço administrativo.

**Modelos de nuvem**:
1. Nuvem Pública: Repositórios em servidores web destinados às pessoas como um todo.
2. Nuvem Privada: Infraestruturas exclusivas e utilizadas internamente pelas empresas.
3. Nuvem Híbrida: A combinação Estratégica de ambientes públicos e privados.

Com o Cloud Computing, as empresas podem alugar a capacidade de armazenamento e processamento de que precisam de provedores de serviços em nuvem.