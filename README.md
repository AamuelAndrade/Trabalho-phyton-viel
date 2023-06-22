# Trabalho-phyton-viel
O código phyton demosntra vários tipos de manipulação de imagem que podem ser feitas utilizando phyton e susas bibliotecas. A primeira linha importa a biblioteca CV2, que contém uma varidedade de funções de
manipulação de imagem, como alteração de cor, matriz de cor, tipo de dado (8bit, 16bit, etc), tamanho, etc. A segujda linha importa a biblioteca numpy como np, para facilitar a escrita. Essa biblioteca trás recursos
de manipulção de conjuntos numéricos grandes, como arrays e matrizes, de forma mais simplificada e de processamento mais rápido devido à sua elaboração em C. As duas combinadas permitem que o programador altere
características de imagens de fomra mais simplificada. A terceira linha importa apenas o cv2_imshow, para exibir as imagens em janelas.
Em seguida, o programa importa 3 imagnes diferentes e le elas. A primeira é a imagem padrão, e fica armazenada na virável "img". A segunda é uma versão com ruído da primeira, ou seja, vários pontos e riscos finos
espalhados pela foto, dando uma impressão de sujeira. Essa imagem é lida de salva na variável "img_opening". A terceira imagem é uma versão furada da primeira imagem, cheia de falhas e buracos. Ela é lida e
armazenada na variável "img_closing". Na linha seguinte o programa salva as dimensões de altura e largura da imagem nas variáveis de mesmo nome. Depois o programa cria um Kernel, que é uma extrutura que vai ditar 
a natureza com a qual o sistema vai lidar com os pixels da imagem. O kernel usado é bem comum, e é uma matriz 5x5 com todos os números iguais a 1, e podendo receber valores entre 0 e 255, devido ao formato de dado
uint8. Logo em seguida o programa exibe esse Kernel na tela para indicar ao usuário o padrão adotado para trabalhar com a imagem. 
Nas três linhas consecutivas, a imagem padrão armazenada em "img" passa por três processos independentes. O primeiro é o de erosion. Nesse processo, um pixel só é considerado 1 se todos os pixels ao redor dele (esse
ao redor é ditado pelo kernel) também forem 1. Caso contrário, ele recebe um novo valor de 0. Na prática isso afina a imagem, retira as bordas. O segundo é o de Dilation. Nesse processo um pixel é considerado 1 se, 
pelo menos, 1 pixel ao redor dele (esse ao redor é ditado pelo kernel) for 1. Na prática, isso engrossa a imagem. O terceiro processo é o de Morphological Gradient. Nesse, o comptador executa tanto o de erosion
quanto o de dilation independentemente e calcula a diferença entre eles, de forma que um pixel que tenha valor 1 após os dois processos receba um valor de 0. Assim, sugre uma moldura, uma borda da imagem original. 
As imagens resultantes dos processos de erosion, dilation e gradient são salvas em variáveis de respectivos nomes.
Na linha seguinte, a imagem armazenada em "img_opening" passa pelo processo de opening. Esse processo executa em sequência o erosion e o dilation. No processo de erosion, as sujeiras da imagem desaparecem porque são
pequenas o suficiente para que nenhum dos pixels seja considerado 1. No processo de dilation, a figura principal retorna ao seu tamanho original, mas agora sem as sujerias, uma vez que elas foram completamente
eliminadas durante a erosion, e não possuem pixels 1 remanescentes. Na prática, esse processo limpa a imagem. Essa imagem nova sem sujeira é armazenada na variável "opening".
Depois, a imagem armazenada em "img_closing" passa pelo processo de closing. Esse processo é o inverso do opening. Nele, primeiro a imagem passa pelo processo de dilation. Isso garante que os buracos no objeto sejam
fechados, mas também faz com que as bordas sejam alargadas. Para resolver isso, é feito o processo de erosion, que retorna as bordas ao seu tamanho original. A imagem que passou pelo processo de closing é armazenada
na variável de mesmo nome. 
Por fim, a imagem original e todas as outras que passaram pelos diferentes processos são exibidas na tela. A primeria variação desses comandos (em laranja) indica também a janela em que essas imagens são exibidas. 
