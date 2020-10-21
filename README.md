# Sistema de Alerta Processual e Avalia��o de Unidades Judiciais

Sistema constru�do para o Desafio 1 do [CNJ Inova](https://www.cnj-inova.com/), cuja problem�tica �:
>Como podemos, a partir da base do DataJud, identificar padr�es e comparar o andamento de processos em cada unidade judici�ria do Brasil, levando em considera��o as peculiaridades locais e o n�vel de complexidade, em raz�o da compet�ncia e da mat�ria do direito?

Utilizamos, como recorte dos dados, processos e unidades da Justi�a Trabalhista.

## Descri��o

O sistema � um aglomerado de fun��es que executam fun��es distintas, mas dependentes. Podemos dividir o sistema em:
1. Importa��o e tratamento de dados
2. Limpeza de dados
3. Engenharia de recursos
4. Sistema de clusters
5. Sistema de avalia��o

Esses m�dulos, juntos, produzem um sistema que gera:
* Alertas sobre processos que merecem aten��o;
* Ranking de unidades judiciais;
* Agrupamento de processos semelhantes, mesmo que de unidades distintas;
* Agrupamento de unidades semelhantes.

Gra�as � clusteriza��o, � poss�vel comparar unidades judiciais semelhantes e criar um ranking que seja coerente com diferentes fatores que s�o polarizantes em unidades judiciais distintas (como, por exemplo, volume processual).

### Arquivos Disponibilizados
Neste reposit�rio h�, al�m dos c�digos fonte:
* Todos os arquivos individuais de cada TRT, com todos os processos, em formato ```.pkl```;
* Arquivos finais do sistema, sendo eles os arquivos em formato ```.csv``` de ranking de unidades e o arquivo ```.csv``` com todos os processos em alerta;
* Imagens geradas em tempo de an�lise, utilizadas para compreender melhor os dados.

## Uso

### Recursos Utilizados

Utilizamos como ambiente de desenvolvimento o [Google Colab](https://colab.research.google.com/) e como ambiente de armazenamento de dados o Google Drive, pois ambos possuem compatibilidade. Distribu�do sobre os Jupyter Notebooks, ter�o linhas de c�digos como abaixo.

* C�digo que cria conex�o com o Google Drive e monta uma pasta do drive no ambiente do Google Colab:
```python
drive.mount('/content/drive', force_remount=True)
```
* O caminho de determinado arquivo dentro do Drive montado no Google Colab. � poss�vel ler arquivos do Google Drive e salvar arquivos para o Google Drive.
```python
path = '/content/drive/My Drive/Dados/movimentos.csv'
```

Para que fosse poss�vel manipular os arquivos fornecidos, utilizamos a biblioteca [Pickle](https://docs.python.org/3/library/pickle.html) do Python. Em termos gerais, � poss�vel ler e salvar arquivos no formato de arquivo ```.pkl``` utilizando muito menos espa�o em disco. Deriva dessa biblioteca c�digos que s�o utilizados para, iterativamente, ler e salvar os arquivos em formato pickle, como:

```python
with open('drive/My Drive/Dados/Processos/processos-trt'+trtnum+'.pkl','rb') as f:
    df = pd.read_pickle(f)
```

### Replica��o do C�digo
O nosso fluxo de trabalho consistiu em modificar os arquivos, salv�-los no Google Drive e realizar a pr�xima etapa no fluxo do programa. Os c�digos s�o modulares e podem ser modificados para que, mesmo rodando no Google Colab, os arquivos sejam lidos ou salvos de [outras fontes](https://colab.research.google.com/notebooks/io.ipynb).

O primeiro conjunto de c�digos a ser executado � o que se encontra no Jupyter Notebook ```Manipula��o de Arquivos.ipynb```. S�o fun��es cujo objetivo � descompactar o arquivo ```.zip``` fornecido, ler e tratar os arquivos ```.json``` e convert�-los para ```.pkl```. � tamb�m nesse notebook que s�o encontrados c�digos para tratar os arquivos que ```.csv``` fornecidos, que elucidam o significado de movimentos, assuntos, classes e unidades.

Parte-se do pressuposto que os dados est�o em formato que possa ser facilmente convertido para o formato ```DataFrame``` do ```Pandas```.

O c�digo necess�rio para essa parte est� no arquivo ```Modelo.ipynb```. S�o diversas fun��es, sendo seguidas de loops que as executam. Para que o c�digo funcione, � necess�rio que os caminhos dos arquivos sejam alterados e a ordem de execu��o seja respeitada.

Ao final da execu��o, ser�o criados os seguintes arquivos:

* ```ranking-geral.csv```: cont�m todas as unidades trabalhistas, rankeadas com base na pontua��o obtida.
* ```ranking-1grau.csv```: cont�m as unidades trabalhistas de primeiro grau, tamb�m rankeadas.
* ```ranking-2grau.csv```: cont�m as unidades trabalhistas de segundo grau, tamb�m rankeadas.
* ```ranking-trts.csv```: cont�m os TRTs, com estat�sticas sendo a amalgama��o das suas unidades filhas, tamb�m rankeados.
* ```ranking-3grau.csv```: cont�m as unidades trabalhistas de terceiro grau (superior), tamb�m rankeadas.
* ```processos-em-alerta.csv```: cont�m todos os processos em alerta.

Haver�, tamb�m, outros 25 arquivos ```.pkl```, correspondendo a cada um dos TRTs (sendo o arquivo 25 uma jun��o do TRT25 e do TST). Esses arquivos finais cont�m detalhes e estat�sticas interessantes sobre os processos. N�s os inclu�mos neste reposit�rio.


## Autores
[Gabriel Gon�alves de Oliveira](https://www.linkedin.com/in/gabriel-goliveira/)
[Matheus Morais Prado](https://www.linkedin.com/in/matheus-prado-397aa917b/)
[Pedro Hort�ncio Moreira Rosa](https://www.linkedin.com/in/pedro-hort%C3%AAncio-70647a16a/)