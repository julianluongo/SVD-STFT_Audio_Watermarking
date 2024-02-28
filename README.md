## Descripción general

Conjunto de Scripts realizado en Python 3.11.2 para el marcado de archivos de audio de corta duración, usando imágenes de 8x8 bits en escala blanco y negro como watermark, y las siguientes librerías;
- Numpy
- PIL
- Cv2
- Scipy 
- Matplot 
- Ipython

### 1er Script - Marcado del audio
![watermark-explained](https://raw.githubusercontent.com/julianluongo/SVD-STFT_Audio_Watermarking/master/extra/1-marking.png "watermark-explained")

Se genera el embebido del watermark aplicando STFT y SVD al audio, para luego agregar los bits de la imagen a la matriz resultante y, haciendo el proceso inverso, obtener el audio final marcado.
Para que el resultado sea imperceptible, los bits se añaden con una intensidad definida por el factor de fuerza ***a***  y por un conjunto de datos aleatorios que denominaremos **llave**. 


**Archivos de entrada**
- Muestra de audio a marcar.
- Imagen en blanco y negro de 8x8 bits (watermark).


**Archivos de salida**
-	Matriz embebida *Uₑ*.
-	Matriz embebida *Vₑᵗ*.
-	Llave *w*.
-	Audio marcado.
-	Numero de bits de la imagen watermark.



### 2do Script - Detección del watermark
 ![detection-explained](https://raw.githubusercontent.com/julianluongo/SVD-STFT_Audio_Watermarking/master/extra/2-detection.png "watermark-explained")
 
Teniendo el audio marcado y los archivos de salida del primer script, el procedimiento para la detección del watermark es el siguiente:

- Fragmentación de la STFT y SVD a cada fragmento.
- Producto matricial --> Wₑ = Uₑ . Dₑ . Vₑᵗ 

Los bits obtenidos se unen en un array, y se redimensiona el array según las dimensiones de la imagen.


**Archivos de entrada**
-	Audio Marcado.
-	Matriz embebida *Uₑ*.
-	Matriz embebida *Vₑᵗ*.
-	Llave *w*.
-	Numero de bits de la imagen watermark.


**Archivos de Salida**
-	Resultado de la correlación.
-	Imagen original watermark.
