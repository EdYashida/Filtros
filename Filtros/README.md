
#  Processamento de Imagens com Python

Este repositório contém exemplos de código para manipulação e processamento de imagens usando as bibliotecas Pillow (PIL) e OpenCV. Abaixo está uma descrição dos algoritmos implementados e o que cada código faz.

##  Algoritmos

###  1-separacaorgb
Este algoritmo implementa a separação dos canais RGB (vermelho, verde e azul) de uma imagem usando a biblioteca Pillow (PIL).
Após a abertura e separação dos canais rgb com o método split(), são criadas novas imagens para cada canal,Novas imagens são criadas para cada canal de cor. 
Para destacar um canal específico, os outros dois canais são definidos como zero. Isto é feito usando Image.new("L", img.size), que cria uma nova imagem em escala de cinza (luminância) do mesmo tamanho com todos os pixels definidos para zero.
O método merge("RGB", ...) combina os três canais para criar uma nova imagem. Para a imagem do canal vermelho, por exemplo, o canal R é combinado com duas novas imagens com valores zero para os canais G e B.

###  2-rgb2gray
Este algoritmo converte uma imagem RGB (ou RGBA) para escala de cinza usando as bibliotecas Pillow (PIL) e OpenCV.
Após a abertura, a imagem PIL é convertida para um array NumPy usando np.array(img_pil). Isso facilita a manipulação da imagem com a biblioteca OpenCV.
O OpenCV espera que as imagens sejam no formato BGR em vez de RGB. Portanto, a imagem é convertida de RGB para BGR usando cv2.cvtColor(img_np, cv2.COLOR_RGB2BGR).
A imagem BGR é então convertida para escala de cinza usando cv2.cvtColor(img_bgr, cv2.COLOR_BGR2GRAY). Esta função converte cada pixel da imagem para um valor de luminância (intensidade), que representa a escala de cinza.

###  3-gray2bin
Este algoritmo converte uma imagem em tons de cinza para uma imagem binária usando um threshold (limiar) especificado, utilizando as bibliotecas Pillow (PIL) e OpenCV.
Inicialmente são realizados processos similares aos descritos no algoritmo 2, após isso a função cv2.threshold() é usada para aplicar a binarização com um threshold de 165. 
Todos os pixels com valores de cinza acima do threshold são definidos como 255 (branco) e os abaixo são definidos como 0 (preto).

###  4- Filtro de Media
Este algoritmo aplica um filtro de média a uma imagem em escala de cinza usando as bibliotecas Pillow (PIL) e OpenCV. O filtro de média é utilizado para suavizar a imagem, reduzindo o ruído.
Novamente são replicados os processos do algoritmo 2 inicilamente, e após isso o filtro de média é aplicado usando cv2.blur(gray, (3, 3)). 
Este filtro calcula a média dos pixels em uma janela de 3x3 ao redor de cada pixel, resultando em uma imagem suavizada.

###  5- Filtro de Mediana
Este algoritmo aplica um filtro de mediana a uma imagem em escala de cinza usando as bibliotecas Pillow (PIL) e OpenCV. O filtro de mediana é utilizado para reduzir o ruído enquanto preserva as bordas da imagem.
Novamente, os mesmos processos são novamente replicados de início e um filtro de mediana é aplicado usando cv2.medianBlur(gray, 3). 
Este filtro substitui cada pixel pelo valor mediano dos pixels vizinhos em uma janela de 3x3, reduzindo o ruído enquanto preserva as bordas.

###  6- Girar imagem 90º
Este algoritmo rotaciona uma imagem em 90 graus no sentido horário usando as bibliotecas Pillow (PIL) e OpenCV.
(processos antes citados...) e então a função cv2.rotate(img_bgr, cv2.ROTATE_90_CLOCKWISE) é usada para rotacionar a imagem em 90 graus no sentido horário.

###  7- Inverter imagem
Este algoritmo inverte uma imagem horizontalmente usando as bibliotecas Pillow (PIL) e OpenCV.
(processos antes citados...) e então a função cv2.flip(img_bgr, 1) é usada para inverter a imagem horizontalmente. 
O parâmetro 1 especifica a inversão horizontal, caso fosse utilizado o parâmetro 0, a inversão seria vertical.
