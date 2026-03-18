# Relatório sobre execução da Atividade Prática 01

**Aluno:** André Felipe de Oliveira Lopes

---

> **OBS.:** estes arquivos podem ser encontrados [aqui](https://github.com/andref03/Processamento-Digital-Imagens-PDI/tree/main)

## Questão 01

Nesta questão, eu me baseei no [Google Colab](https://colab.research.google.com/drive/1b7xJ_FxxSxpQpU6dquqdcWcBwjqmEwkv#scrollTo=5c389609) disponibilizado na sala de aula.

Primeiramente, eu fiz a instalação do ```numpy matplotlib```, e importei ambos.

Na **letra A**, o objetivo era criar uma máscara branca em cima de um quadrado preto 200x200 px. Inicialmente criei o quadrado preto de lado 200 px. multiplicando a matriz de ones por 0, para aplicar a cor preta. Depois, foi só criar uma máscara ```imagem_preta[50:150, 50:150] = 255```, que é igual a 255 porque possui a máxima intensidade (coloração branca).

Na **letra B**, gerei a imagem a partir da matriz de zeros (preta) no tamanho 200x200 px. Pra conseguir representar os níveis de intensidade do cinza, usei a função linspace, do np, o que fez a variação de cores acontecer (isso é basicamente o degradê). E o reshape usei para transformar o vetor do linspace em uma linha só. Pra aplicar essa linha na imagem inteira, usei o repeat com parâmetro 200.

Na **letra C**, usei a função do np where(), colocando primeiro a condição: onde houver pixels 0 (pretos) na imagem_preta. Se verdadeiro, então mantem a imagem_preta. Se false, então usa-se a imagem_degrade.

---

## Questão 02

Na **letra A**, apenas importei a imagem do diretório atual, com função do plt.imread, e depois imprimi na tela (saída) a imagem para verificar se estava ok.

Na **letra B**, usei a imagem original como base e inverti a ordem das suas cores primárias de [0,1,2] para [2,1,0]. Ou seja: de RGB para BGR.

Na **letra c**, basicamente zerei as cores primárias verde ([..., 1]) e azul ([..., 2]). Dessa forma, prevaleceu só a cor primária vermelha ([..., 0]), que serviu de filtro e "refletiu" somente as tonalidades de vermelho presentes na imagem.

---

## Questão 03

Na **letra A**, com uso da função da média pelo np (np.mean) em cima da imagem original, o que resulta em um único valor de intensidade. A imagem ficou acinzentada porque essa função da média retirou a informação das cores, mantendo somente a intensidade de cada pixel mesmo.

Na **letra B**, usei de novo a função da média, que retornou o valor da intensidade média global da imagem. Pra ver a distribuição dos níveis de cinza, criei o histograma solicitado, mostrando a distribuição dos pixels.

Na **letra C**, usei o valor da média como limiar, com ajuda da função where novamente. Ou seja: se os pixels (a partir da imagem cinza desta quetsão) forem maiores ou iguais ao limiar, então seriam convertidos para branco (255). Se forem menores do que o limiar, então seriam convertidos para preto (0).

---

## Questão 04

Na **letra A**, o objetivo era fazer uma máscara para o fundo (nesse caso da imagem, seria o céu). Usei uma linha para verificar qual é a intensidade da cor do céu, ou seja, o código RGB dele, para usar na máscara. Essa máscara é feita usando a sugestão do comando da questão, que era sobre usar lógica booleana com o operador &. Assim, foi só aplicar a máscara, com os valores encontrados dos pixels do céu, em cima da imagem original. No fim, o céu ficou "isolado" mesmo.

Na **letra B**, eu basicamente repliquei a lógica de importação da imagem presente na questão 2A. Claro que dessa vez mudando o nome do arquivo de origem.

Na **letra C**, apliquei uma lógica de Chroma Key. Criei uma cópia da imagem original, da questão 2, e utilizei a indexação booleana do np pra substituir os pixels da imagem original pelos pixels advindos da nova imagem carregada, que é o novo fundo (obtido na questão 4B). Como a máscara era somente do céu, então somente eles foram substituídos.