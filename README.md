# 📝 Relatório de Notas Enem

## 📓 Documentação
Esse projeto tem como objetivo fazer uma análise da base de dados de notas do enem do ano de 2022, trazer os indicativos mais persistentes, quanto aos inscritos e notas, para, ao final, criar um Dashboard trazendo essas visualizações. 
> **Ferramentas Utilizadas**: <br> | Power BI <br>| SQL Server  <br> | Figma  

> **Autoria**: Millena Thalyne <br>
> *Desafio disponibilizado pela empresa Mesha*
## 👷 Desenvolvimento do Projeto
### SQL Server
Esse foi o banco de dados utilizado por mim para fazer o armazenamento dos dados. Como a base era grande, preferi fazer a conexão dele para o Power BI e, assim, conseguir fazer os tratamentos necessários por lá, pois, atualmente, acho mais prático.  <br> Portanto, essa parte do projeto serviu somente para armazenamento dos dados. 
### Power BI
Já no Power BI, eu consegui fazer a separação das variáveis em tabelas dimensão, pois assim as informaçõese ficariam mais organizadas e facilitaria a posterior arquitetura de relacionamento (modelo estrela solicitado). <br> Dessa forma, separei a base em 4 tabelas dimensão e 1 fato, sendo estas: <br> **TABELA 1** - Aluno_Dim:
nu_inscricao;
tp_faixa_etaria;
tp_sexo;
tp_estado_civil;
tp_cor_raca;
tp_nacionalidade;
tp_st_conclusao;
tp_ano_concluiu;
tp_escola;
tp_ensino;
in_treineiro;

> Tratamento dessa tabela: tp_ensino, onde tiver nulo -> 0, pois tp_escola não foi respondido. E remoção de duplicados. 

**TABELA 2** - Escola_Dim:
nu_inscricao;
co_municipio_esc;
no_municipio_esc;
co_uf_esc;
sg_uf_esc;
tp_dependencia_adm_esc;
tp_localizacao_esc;
tp_sit_func_esc;

> Tratamento dessa tabela: Como as informações geográficas das variáveis de escola estão incompletas e existe as mesmas informações nas variáveis da tabela de prova (Localização_Dim), as referências de código de município, nome, uf e sigla serão excluídos. Será retirado os duplicado e onde tiver nulo adicionar "Não informado". 

**TABELA 3**- Prova_Objetiva (Fato):
nu_inscricao;
nu_ano;
co_municipio_esc;
co_municipio_prova;
tp_presenca_cn;
tp_presenca_ch;
tp_presenca_lc;
tp_presenca_mt;
tx_respostas_cn;
tx_respostas_ch;
tx_respostas_lc;
tx_respostas_mt;
tx_gabarito_cn;
tx_gabarito_ch;
tx_gabarito_lc;
tx_gabarito_mt;
tp_status_redacao;
co_prova_cn;
co_prova_ch;
co_prova_lc;
co_prova_mt;
tp_lingua;
nu_nota_comp1;
nu_nota_comp2;
nu_nota_comp3;
nu_nota_comp4;
nu_nota_comp5;
nu_nota_redacao;
nu_nota_cn;
nu_nota_ch;
nu_nota_lc;
nu_nota_mt;

> Tratamento dessa tabela: aplicação de 0 em variáveis numéricas em que o aluno não realizou a prova e "Não realizou a prova" em variáveis do tipo texto.

**TABELA 4** - Localização_Dim:
co_municipio_prova;
no_municipio_prova;
co_uf_prova;
sg_uf_prova.

> Tratamento dessa tabela: Remoção de duplicados. 

**TABELA 5** - Questionario_Dim:
nu_inscricao;
Q001;
Q002;
Q003;
Q004;
Q005;
Q006;
Q007;
Q008;
Q009;
Q010;
Q011;
Q012;
Q013;
Q014;
Q015;
Q016;
Q017;
Q018;
Q019;
Q020;
Q021;
Q022;
Q023;
Q024;
Q025.

>Tratamento dessa tabela: remoção dos nulos (considera-se não preenchimento do candidato) e adicionado "Questionário não realizado" aos que sobrarem. 

> OBS: Todos precisaram de tratamento de tipo. 

Ao final desse tratamento, fiz o relacionamento entre as tabelas e exclui maioria das variáveis, e a tabela de questionário, pois não serão utilizadas nesse projeto e, assim, reduziria drásticamente o tamanho do arquivo para melhorar a performance de consultas. 

### Indicativos
Os indicativos propostos para esse projeto são os seguintes:
- Qual a escola com a maior média de notas? 
- Qual o aluno com a maior média de notas e o valor dessa média? 
- Qual a média geral? 
- Qual o % de Ausentes? 
- Qual o número total de Inscritos? 
- Qual a média por disciplina? 
- Qual a média por Sexo? 
- Qual a média por Etnia? 
  
Para poder responder essas perguntas, eu montem gráficos e medidas, além de um mapa, para poder visualizar de maneira mais dinâmica (utilizando a ferramenta do Power BI, que, ao pousar o cursor em cima destes, mostrará uma legenda com as informações específicas). <br> Dentre os gráficos utilizados: barras, rosca, pizza, medidor, mapa coroplético e cartões.
## 📸 Imagens
Ao longo da finalização do dashboard, utilizei de artifícios gratuitos para melhorar a visualização. Essas imagens também estão disponibilizadas nesse repositório, além da capa e fundo de tela utilizado. <br> A ferramenta que utilizei para fazer essas criações foi o **Figma**, onde consegui utilizar *plugs* com diversas aplicações visuais de ícones e ferramentas de customização de imagem. 