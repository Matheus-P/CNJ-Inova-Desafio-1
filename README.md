# Sistema de Alerta Processual e Avaliação de Unidades Judiciais

Sistema construído para o Desafio 1 do [CNJ Inova](https://www.cnj-inova.com/), cuja problemática é:
>Como podemos, a partir da base do DataJud, identificar padrões e comparar o andamento de processos em cada unidade judiciária do Brasil, levando em consideração as peculiaridades locais e o nível de complexidade, em razão da competência e da matéria do direito?

Utilizamos, como recorte dos dados, processos e unidades da Justiça Trabalhista.

## Descrição

O sistema é um aglomerado de funções que executam funções distintas, mas dependentes. Podemos dividir o sistema em:
1. Importação e tratamento de dados
2. Limpeza de dados
3. Engenharia de recursos
4. Sistema de clusters
5. Sistema de avaliação

Esses módulos, juntos, produzem um sistema que gera:
* Alertas sobre processos que merecem atenção;
* Ranking de unidades judiciais;
* Agrupamento de processos semelhantes, mesmo que de unidades distintas;
* Agrupamento de unidades semelhantes.

Graças à clusterização, é possível comparar unidades judiciais semelhantes e criar um ranking que seja coerente com diferentes fatores que são polarizantes em unidades judiciais distintas (como, por exemplo, volume processual).

### Arquivos Disponibilizados
Neste repositório há, além dos códigos fonte:
* Todos os arquivos individuais de cada TRT, com todos os processos, em formato ```.pkl```;
* Arquivos finais do sistema, sendo eles os arquivos em formato ```.csv``` de ranking de unidades e o arquivo ```.csv``` com todos os processos em alerta;
* Imagens geradas em tempo de análise, utilizadas para compreender melhor os dados.

## Uso

### Recursos Utilizados

Utilizamos como ambiente de desenvolvimento o [Google Colab](https://colab.research.google.com/) e como ambiente de armazenamento de dados o Google Drive, pois ambos possuem compatibilidade. Distribuído sobre os Jupyter Notebooks, terão linhas de códigos como abaixo.

* Código que cria conexão com o Google Drive e monta uma pasta do drive no ambiente do Google Colab:
```python
drive.mount('/content/drive', force_remount=True)
```
* O caminho de determinado arquivo dentro do Drive montado no Google Colab. É possível ler arquivos do Google Drive e salvar arquivos para o Google Drive.
```python
path = '/content/drive/My Drive/Dados/movimentos.csv'
```

Para que fosse possível manipular os arquivos fornecidos, utilizamos a biblioteca [Pickle](https://docs.python.org/3/library/pickle.html) do Python. Em termos gerais, é possível ler e salvar arquivos no formato de arquivo ```.pkl``` utilizando muito menos espaço em disco. Deriva dessa biblioteca códigos que são utilizados para, iterativamente, ler e salvar os arquivos em formato pickle, como:

```python
with open('drive/My Drive/Dados/Processos/processos-trt'+trtnum+'.pkl','rb') as f:
    df = pd.read_pickle(f)
```

### Replicação do Código
O nosso fluxo de trabalho consistiu em modificar os arquivos, salvá-los no Google Drive e realizar a próxima etapa no fluxo do programa. Os códigos são modulares e podem ser modificados para que, mesmo rodando no Google Colab, os arquivos sejam lidos ou salvos de [outras fontes](https://colab.research.google.com/notebooks/io.ipynb).

O primeiro conjunto de códigos a ser executado é o que se encontra no Jupyter Notebook ```Manipulação de Arquivos.ipynb```. São funções cujo objetivo é descompactar o arquivo ```.zip``` fornecido, ler e tratar os arquivos ```.json``` e convertê-los para ```.pkl```. É também nesse notebook que são encontrados códigos para tratar os arquivos que ```.csv``` fornecidos, que elucidam o significado de movimentos, assuntos, classes e unidades.

Parte-se do pressuposto que os dados estão em formato que possa ser facilmente convertido para o formato ```DataFrame``` do ```Pandas```.

O código necessário para essa parte está no arquivo ```Modelo.ipynb```. São diversas funções, sendo seguidas de loops que as executam. Para que o código funcione, é necessário que os caminhos dos arquivos sejam alterados e a ordem de execução seja respeitada.

Ao final da execução, serão criados os seguintes arquivos:

* ```ranking-geral.csv```: contém todas as unidades trabalhistas, rankeadas com base na pontuação obtida.
* ```ranking-1grau.csv```: contém as unidades trabalhistas de primeiro grau, também rankeadas.
* ```ranking-2grau.csv```: contém as unidades trabalhistas de segundo grau, também rankeadas.
* ```ranking-trts.csv```: contém os TRTs, com estatísticas sendo a amalgamação das suas unidades filhas, também rankeados.
* ```ranking-3grau.csv```: contém as unidades trabalhistas de terceiro grau (superior), também rankeadas.
* ```processos-em-alerta.csv```: contém todos os processos em alerta.

Haverá, também, outros 25 arquivos ```.pkl```, correspondendo a cada um dos TRTs (sendo o arquivo 25 uma junção do TRT25 e do TST). Esses arquivos finais contém detalhes e estatísticas interessantes sobre os processos. Nós os incluímos neste repositório.


## Autores
[Gabriel Gonçalves de Oliveira](https://www.linkedin.com/in/gabriel-goliveira/)
[Matheus Morais Prado](https://www.linkedin.com/in/matheus-prado-397aa917b/)
[Pedro Hortêncio Moreira Rosa](https://www.linkedin.com/in/pedro-hort%C3%AAncio-70647a16a/)