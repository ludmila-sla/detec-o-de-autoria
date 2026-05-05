# detecão-de-autoria
Esse codigo foi criado para o desenvolvomento do meu artigo em redes neurais

Resumo.
Esse trabalho investiga a utilização de redes neurais para a detecção de autoria de textos literários e compara 2 modelos: MLP e LSTM. Para isso, utilizou-se a base de dados pública Project Gutenberg. O modelo foi experimentado usando diferentes tamanhos de texto para avaliar qual têm a melhor acurácia. Os resultados demonstram diferenças no comportamento dos modelos, com variações de desempenho que ocorrem de acordo com tamanho dos textos analisados.

Base de dados
Os textos utilizados foram encontrados na base de dados pública Project Gutenberg para garantir que não houvesse textos com direitos autorais.
Foram selecionados textos de 3 autores: Edgar Allan Poe, Arthur Conan Doyle e Mary Shelley, todos autores de ficção para manter um padrão, com textos curtos publicados há mais de 100 anos, permitindo assim que fossem encontrados textos em domínio público com facilidade.
No entanto, são escritores de estilos literários diferentes, Poe escreve principalmente terror, Mary Shelley ficção científica e Doyle mistério, o que facilita a identificação da autoria.
Os textos utilizados nos treinos foram de livros diferentes dos testes, permitindo um acesso mais amplo de amostras para o modelo.
Outro ponto levado em consideração foi o tamanho dos textos, porque o desempenho do modelo pode variar de acordo com a quantidade de contexto disponível. Portanto, os modelos foram treinados e testados com blocos de 100 palavras, 200 e, por último, 300.


 Pré-processamento
Antes de realizar os testes foi necessário preparar os textos que seriam utilizados. Portanto, todo o texto foi convertido para minúsculas para garantir uma padronização.
Ruídos do texto, como números, símbolos e outras marcações foram removidos.
A princípio, cogitou-se tirar as pontuações para diminuir a quantidade de caracteres e facilitar o trabalho dos modelos, no entanto, algumas pontuações são características estilísticas de certos autores, e podem afetar o reconhecimento de autoria, portanto, vírgulas, pontos finais, exclamações e interrogações foram mantidas.
Os textos da fonte Gutenberg vem com um cabeçalho que também foi retirado, e, por fim, foi realizada a normalização do texto.


Modelos utilizados
No modelo MLP foi utilizada a tecnica TF-IDF (Term Frequency-Inverse Document Frequency, ou Frequência do Termo-Inverso da Frequência nos Documentos), ou seja, o texto foi transformado em um vetor e o modelo MLP calculou um peso para cada palavra, permitindo assim que ele entendesse quais termos tinham importância significativa para a análise e detecção da autoria.
Técnicas como TF-IDF destacam a importância relativa de termos em documentos (Spärck Jones, 1972).
A rede neural contém uma camada oculta com 100 neurônios, representando uma configuração intermediária que permite capturar os padrões relevantes sem aumentar a complexidade e gerar um overfitting.
 Foi utilizada a função de ativação padrão (ReLU) por sua eficiência e por facilitar o treinamento de redes neurais, e o otimizador Adam foi adotado por sua capacidade de ajustar automaticamente a taxa de aprendizado.
O modelo MLP foi escolhido por sua arquitetura simples e eficiência em tarefas de classificação textual quando combinado com representações baseadas em frequência, como o TF-IDF. 
Já no modelo LSTM, os textos foram convertidos em sequências de tokens numéricos, representando as palavras presentes no vocabulário.
Essas sequências foram então processadas por uma camada de embedding, responsável por mapear cada token para uma representação vetorial densa. Em seguida, uma camada LSTM foi utilizada para capturar dependências sequenciais e padrões ao longo do texto.
A saída LSTM foi conectada a uma camada densa com função de ativação softmax, responsável pela classificação dos textos entre os autores considerados.
Modelos LSTM foram escolhidos por sua capacidade de considerar a ordem e a dependência entre palavras, diferentemente de abordagens baseadas em vetores independentes como o TF-IDF. Dessa forma, sua utilização permite avaliar se informações sequenciais contribuem para a identificação de padrões estilísticos em textos literários.
