## Algoritmo de detecção de Códigos de Barra

O sistema usa técnicas de processamento de imagens, como a transformada de Hough e detecção de borda sub-pixel para o processamento da imagem de código de barras capturada por câmera.

Para fazer a segmentação a imagem foi transformada em tons de cinza, binarizada, e depois foi realizada uma operação chamada BLACKHAT, que corresponde a pegar o  resultado da operação de dilatação, erosão e, logo após, subtração da imagem original. Isto desenha apenas as bordas pretas da imagem.

A partir disso foi utilizada a transformada de Hough para detectar as linhas. O local que possui o maior número de linhas paralelas é entendido como o código de barras. Com uma dessas linhas é calculado a inclinação e por essa inclinação é calculado a angulação do código de barras. 

Com este ângulo a imagem é rotacionada de modo que o código fique na posição horizontal, e então é realizado operação de dilatação e fechamento apenas na horizontal e, ao fim, é aplicado uma operação de erosão e dilatação(nesta ordem) também com enfase na horizontalidade, para reunir as linhas horizontais próximas. Depois é feita uma operação de abertura com uma mâscara maior para reunir as áreas com muitas linhas.
