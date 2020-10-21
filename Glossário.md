# Glossário
## Atributos do Datajud
**millisInsercao**: campo interno com data e hora em milissegundos que representa quando o arquivo foi indexado no Datajud; 
**grau**: Campo identificador do grau de jurisdição em que o processo se encontra; valores possíveis: 
- 'SUP': Tribunal Superior 
- 'G2': 2º Grau 
- 'TR': Turma Recursal 
- 'G1': 1º grau, justiça comum 
- 'JE': Juizados Especiais (inclusive os regidos pelas leis dos Juizados Especiais 9.099/95 e 12.153/2009 que tramitam em varas de juízo único ou em varas que acumulam competência de juizado especial) 
- 'TRU': Turma Regional de Uniformização 
- 'TNU': Turma Nacional de Uniformização 
- 'TEU': Turma Estadual de Uniformização 
- 'CJF': Conselho da Justiça Federal 
- 'CSJT': Conselho Superior da Justiça do Trabalho; 
**siglaTribunal**: campo identificador da sigla do Tribunal em que o processo se encontra.

### Cabeçalho Processual
**dadosBasicos.assunto**: (Lista de assuntos do processo - relação com sgt_assuntos.csv) 
> **dadosBasicos.assunto.principal**: atributo do tipo boolean que informa se o assunto referido é o assunto principal do processo.
> Pela estrutura do XSD é possível informar o assunto local, com referência ao assunto nacional, ou, o assunto nacional: 
>[**dadosBasicos.assunto.assuntoLocal**:  
>**dadosBasicos.assunto.assuntoLocal.codigoAssunto**: atributo destinado a incluir a informação relativa ao código numérico utilizado localmente pelo tribunal. 
>**dadosBasicos.assunto.assuntoLocal.codigoPaiNacional**: atributo destinado à entrada do código de assunto nacional de que o assunto local é filho. 
>**dadosBasicos.assunto.assuntoLocal.descricao**: atributo destinado à entrada da descrição textual do assunto local.] 
>ou 
>[**dadosBasicos.assunto.codigoNacional**: elemento destinado a que se informe o código de assunto existente na tabela nacional unificada decorrente da Resolução 46;] 

**dadosBasicos.processoVinculado**: elemento destinado a permitir a indicação da existência de um ou mais processos judiciais vinculados;
**dadosBasicos.relacaoIncidental**: elemento destinado a permitir identificar se existe algum elemento incidental que tenha gerado novo processo judicial, em razão da existência de uma nova relação processual jurídica (por exemplo, como pode ocorrer em embargos à execução de títulos extrajudiciais, embargos de terceiro, em recursos internos, impugnações ao valor da causa, entre outras Situações, em que há criação de novos autos vinculados ao processo principal); 
**dadosBasicos.prioridade**: Elemento destinado a permitir a identificação da existência de propriedades processuais não óbvias, ou seja, aquelas que não são resultado direto da identificação da classe processual (ex.: habeas corpus ou mandado de segurança). Na versão 2.0, será texto livre, mas é recomendável utilizar os seguintes textos identificadores: "IDOSO" "RÉU PRESO" "PERECIMENTO" "MENOR"; 
**dadosBasicos.valorCausa**: valor da causa; 
**dadosBasicos.orgaoJulgador.nomeOrgao**: descrição textual da Unidade Judiciária constante no Módulo de Produtividade, Anexo II da Resolução 76; 
**dadosBasicos.orgaoJulgador.codigoMunicipioIBGE**: município-sede da unidade judiciária, conforme código de municípios definidos pelo IBGE. Usar código com sete dígitos. Fonte: www.ibge.gov.br; 
**dadosBasicos.orgaoJulgador.codigoOrgao**: código da Unidade Judiciária constante no Módulo de Produtividade, Anexo II da Resolução 76; 
**dadosBasicos.orgaoJulgador.instancia**: os tipos de instância podem ser: 
- ORIG: instância originária em que o processo teve início; 
- REV: instância de revisão direta de um processo originariamente proposto em outra instância; 
- ESP: instância de revisão especial de processo submetido ou não à revisão direta; 
- EXT: instância de revisão extraordinária 
- ADM: instância administrativa de análise; 

**dadosBasicos.outrosnumeros**: outros números que o processo possa ter recebido durante sua vida; 
**dadosBasicos.numero**: numeração única do processo conforme determinado pela Resolução 65; 
**dadosBasicos.competencia**: identificador da competência a que pertence o processo, ou da competência a que ele se destina caso se trate de processo inicial; 
**dadosBasicos.classeProcessual**: código da classe processual conforme Resolução 46. Relação com sgt_classes.csv; 
**dadosBasicos.codigoLocalidade**: código identificador da localidade a que pertence ou deve pertencer o processo. Deve ser utilizado o código do município, segundo códigos do IBGE disponíveis em www.ibge.gov.br (usar códigos com sete dígitos); 
**dadosBasicos.nivelSigilo**: nível de sigilo a ser aplicado ao processo; 
**dadosBasicos.intervencaoMP**: atributo destinado a identificar que o processo exige a intervenção do Ministério Público; 
**dadosBasicos.tamanhoProcesso**: volume, em bytes, dos documentos existentes no processo judicial;
**dadosBasicos.dataAjuizamento**: indica a data em que o processo foi inicialmente recebido pelo Poder Judiciário no órgão consultado. Caso se trate de instância recursal, especial ou extraordinária, deve refletir a data de entrada do processo nessa instância; 
**dadosBasicos.procEl**: campo identifica se o processo tramita em sistema eletrônico ou em papel. São valores possíveis 
- 1: Sistema Eletrônico 
- 2: Sistema Físico; 

**dadosBasicos.dscSistema**: identifica qual o sistema eletrônico que o processo tramita. São valores possíveis: 
1. Pje, 
2. Projudi, 
3. SAJ, 
4. EPROC, 
5. Apolo, 
6. Themis, 
7. Libra, 
8. Outros.

### Polos e Partes
**dadosBasicos.polo**: (Os dados de Polos e Partes não estão disponíveis nos metadados do Hackathon – LGPD)
### Movimentações Processuais
**movimento**: (Lista de movimentações processuais - relação com sgt_movimentos.csv) 
>**movimento.dataHora**: atributo destinado a indicar o momento em que foi realizada a movimentação. 
>**movimento.nivelSigilo**: nível de sigilo a ser aplicado ao processo; 
>**movimento.identificadorMovimento**: atributo incluído para permitir a atribuição de um identificador específico para a movimentação realizada em um determinado processo judicial. 
>**movimento.tipoResponsavelMovimento**: identificação do responsável pelo movimento: 
> -Servidor=0; 
>-Magistrado=1; 
>**movimento.complementoNacional**: (Lista de Complementos) - elemento destinado a permitir a inclusão dos complementos de movimentação conforme tabela nacional de complementos segundo novo modelo de dados. 
>**movimento.complementoNacional.codComplemento**: atributo destinado à entrada do código docomplemento do movimentonacional ou do movimento local; 
>**movimento.complementoNacional.descricaoComplemento**: atributo destinado à entrada da descrição textualdocomplemento do movimento nacional ou do movimento local; 
>**movimento.complementoNacional.codComplementoTabelado**: atributo destinado à entrada do código do complemento tabelado do movimento nacional ou do movimento local; 
>**movimento.idDocumentoVinculado**: elemento destinado a permitir a vinculação de um ou mais documentos à movimentação;
>Órgão Julgador Responsável pela movimentação (relação com mpm_serventias.csv) 
>**movimento.orgaoJulgador.dadosBasicos.nomeOrgao**: descrição textual da Unidade Judiciária constante no Módulo de Produtividade, Anexo II da Resolução 76; 
>**movimento.orgaoJulgador.dadosBasicos.codigoMunicipioIBGE**: município-sede da unidade judiciária, conforme código de municípios definidos pelo IBGE. Usar código com sete dígitos. Fonte: www.ibge.gov.br; 
>**movimento.orgaoJulgador.dadosBasicos.codigoOrgao**: código da Unidade Judiciária constante no Módulo de Produtividade, Anexo II da Resolução 76;
>**movimento.orgaoJulgador.dadosBasicos.instancia**: os tipos de instância podem ser: 
-ORIG: instância originária em que o processo teve início; 
-REV: instância de revisão direta de um processo originariamente proposto em outra instância; 
-ESP: instância de revisão especial de processo submetido ou não à revisão direta; 
-EXT: instância de revisão extraordinária 
-ADM: instância administrativa de análise; 
>**movimento.tipoDecisao**: atributo que permite a atribuição da decisão como sendomonocrática (proferida por um magistrado), ou colegiada;
Valores possíveis são numéricos (0 ou 1):
0.decisão MONOCRATICA
1.decisão COLEGIADA; 
>Pela estrutura do XSD é possível informar uma movimentação local, com referência ao movimento nacional, ou, a própria movimentação nacional: 
>[**movimento.movimentoNacional.codigoNacional**: atributo destinado à indicação do código do movimento previsto na tabela unificada de que trata a Resolução 46; ] 
>OU 
>[**movimento.movimentoLocal.codigoMovimento**: atributo destinado a incluir a informação relativa ao código numérico utilizado localmente pelo tribunal; 
>**movimento.movimentoLocal.codigoPaiNacional**: atributo destinado à entrada do código de movimento nacional de que o movimento local é filho; ]
## Tabelas SGT
As tabelas de Classes Processuais, Assuntos e Movimentos do Sistema de Gestão de Tabelas Processuais Unificadas (SGT) são organizadas de maneira hierárquica, sendo o último nível da hierarquia o mais específico e relevante, e o primeiro nível o mais genérico. 
A tabela de Serventias apresentará as informações de cada unidade judiciária (Órgão Julgador) cadastrado no Módulo de Produtividade do CNJ. 
### Classes Processuais (sgt_classes.csv)
O arquivo sgt_classes.csv contém uma estrutura simplificada da tabela de classes processuais disponível no SGT em: https://www.cnj.jus.br/sgt/consulta_publica_classes.php. 
Atributos: 
**CODIGO**: código identificador único da Classe Processual;
**DESCRICAO**: descrição da Classe Processual; 
**COD_PAI**: código identificador da Classe Processual pai; 
**COD_FILHOS**: lista com os códigos das Classes Processuais filhas daquela Classe.
### Assuntos Processuais (sgt_assuntos.csv)
O arquivo sgt_assuntos.csv contém uma estrutura simplificada da tabela de movimentos processuais disponível no SGT em: https://www.cnj.jus.br/sgt/consulta_publica_assuntos.php.
Atributos:
**CODIGO**: código identificador único do Assunto Processual;
**DESCRICAO**: descrição do Assunto Processual;
**COD_PAI**: código identificador do Assunto Processual pai;
**COD_FILHOS**: lista com os códigos dos Assuntos Processuais filhos daquele Assunto.
### Movimentações Processuais (sgt_classes.csv)
O arquivo sgt_movimentos.csv contém uma estrutura simplificada da tabela de movimentos processuais disponível no SGT em: https://www.cnj.jus.br/sgt/consulta_publica_movimentos.php. 
Atributos: 
**CODIGO**: código identificador único da Movimentação Processual;
**DESCRICAO**: descrição da Movimentação Processual; 
**COD_PAI**: código identificador da Movimentação Processual pai; 
**COD_FILHOS**: lista com os códigos das Movimentações Processuais filhas daquela Movimentação.
### Serventias (mpm_serventias.csv) 
O arquivo mpm_serventias.csv contém uma estrutura simplificada da tabela de órgãos julgadores disponível no painel do Módulo de Produtividade Mensal em: https://paineis.cnj.jus.br/QvAJAXZfc/opendoc.htm?document=qvw_l%2FPainelCNJ.qvw. 
Atributos: 
**SEQ_ORGAO**: código identificador Órgão Julgador (OJ)/Serventia;
**NOMEDAVARA**: nome do Órgão Julgador/Serventia;
**TIP_ORGAO**: tipo do Órgão Julgador;
**SEQ_CIDADE**: lista com os códigos dos movimentos processuais filhos daquele movimento;
**DSC_CIDADE**: nome da cidade do OJ;
**SIG_UF**: UF da cidade do OJ COD_IBGE: código IBGE da cidade do OJ;
**DSC_TIP_ORGAO**: tipo de OJ;
**TIP_ESFERA_JUSTICA**: esfera de justiça;
**INT_ORDEM_ORGAO**: atributo utilizado identificação ordinal da serventia (Ex: 1ª Vara);
**DSC_ORGAO**: nome da serventia sem identificação ordinal;
**DSC_DENOM_SERVENTIA_JUDICIAL**: especificação da serventia; 
**ENDERECO_SERVENTIA**: endereço;
**CEP_SERVENTIA**: CEP;
**LATITUDE**: coordenadas de latitude;
**LONGITUDE**: coordenadas de longitude.