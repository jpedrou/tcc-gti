# TÉCNICAS DE *MACHINE LEARNING* E MELHORIAS DE PERFORMANCE PARA O *PLUGIN SMART-MAP*

O Trabalho foi desenvolvido com a finalidade de otimizar o tempo de execução das operações de carregamento e processamento de dados do plugin Smart-Map do QGIS. [Repositório oficial do plugin](https://github.com/gustavowillam/SmartMapPlugin).

## <img align="center" width="50px" src="https://blog.qgis.org/wp-content/uploads/2016/12/qgis-icon_anita02.png" /> *Smart-Map* 

O *Smart-Map* é um *plugin* do QGIS, *software* para geração de mapas, que possibilita a interpolação de atributos do solo através do método geoestatístico Krigagem Ordinária e do algoritmo de *Machine Learning Support Vector Machines*. Porém, o *app* possui algumas limitações em relação ao número de pontos amostrados e tempo de execução.

Dessa forma, pretendeu-se otimizar a performance da ferramenta na duração do processamento e na quantidade de dadods a serem utilizados na realização das operações. As principais mudanças feitas na versão original foram:

- Troca da variação de Validação cruzada utilizada, antes *Leave-One-Out*, com as alterações a *K-Fold*;
- Alteração de códigos menos eficientes em termos de carregamento por técnicas mais atuais.


Com essas melhorias, observou-se um aumento significativo na velocidade de execução das funcionalidades do *plugin*, bem como o melhoramento do limite de dados usados para realizar as operações internas do *app*, na versão original 5.000 registros, com as atualizações, de acordo com as configurações do sistema computacional usados, até 50.000.

## Tecnologias Usadas

- [Python](): Linguagem de programação utilizada para o desenvolvimento original da aplicação.
- [Pandas](): Biblioteca do Python muito utilizada para carregamento de dados.
- [Scikit-Learn](): Biblioteca amplamente utilizada para lidar com processos que envolvam *Machine Learning*.
- [Visual Studio Code](): IDE escolhida para o desenvolvimento da aplicação.
- [Linux (Ubuntu)](): Sistema operacional utilizado para testar e desenvolver o projeto. Versão usada: **22.0.4**.


**Especificações da máquina utilizada para desenvolvimento**

Computador equipado com:
- `processador de 12th Gen Intel® Core™ i5-12450H × 12`,  
- `20GB de RAM`,
- `SSD de 500GB`.

## Técnicas utilizadas para otimizar os processos

### *K-Fold Cross-Validation*

Nesse método, os dados são divididos separados em *k* subconjuntos, ou *folds*. O modelo é treinado *k* vezes, e em cada uma delas utilizando *k-1 folds* para treino e o *fold* restante para teste. Dessa forma, existente um controle maior do número de treinos do algoritmo, o que contribui drasticamente para a redução do uso de memória do sistema.


<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/K-fold_cross_validation_EN.svg/1920px-K-fold_cross_validation_EN.svg.png"/>


### Paginação de dados

O conceito de paginação no contexto de grandes conjuntos de dados envolve dividir os dados em partes menores e mais gerenciáveis, chamadas de páginas ou blocos (chunks). Essa técnica pode ser especialmente útil, pois processar blocos menores de registros é mais rápido do que carregar o dataset por completo, além de reduzir a carga computacional no sistema.


<img src="https://media.licdn.com/dms/image/D5612AQGXiCbdSEcocw/article-cover_image-shrink_720_1280/0/1704707353160?e=2147483647&v=beta&t=19WgitqhCLY_vFi-YhDu_2L-0e59BTVg1Qujwtw53-s"/>