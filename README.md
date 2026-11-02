
- convolution: apply filters to generate feature maps
- Non-linearity: Often ReLU
- Pooling: Downsampling operation on each feature map

tf.keras.layers.Conv2D(filters=d, kernel_size=(h,w), strides=s)
tf.keras.activations.*
tf.keras.layers.MaxPool2D

Layer Dimensions: hxwxd (H AND W SPATIAL DIMENSIONS and d is number of filters). Stride is filter step size. Receptive Field: location in input image that a node is path connected to. 

Non linearity es after convolution operation (tf.keras.lauers.ReLU, replaces all negative values to zero). 

Pooling is for resducing dimensionality, Spatial invariance (downsample and preserve spatial invariance) --> tf.keras.layers.MaxPool2D(pool_size=(2,2), strides=2). 

Les primeres layers es low level features (eges, dark spots...), després eyes, ears, nose and finally facial structure. 

FEATURE LEARNING: learn features in input image trhough convolution, introduce non-linearity through activation function, and reduce dimentionality and preserve spatial invariace with pooling. 

For classification, we need class probabilities (for that we flatten, fully connected layer, and softmax). La part de clasification pot ser també object detection, segmentation, probabilistic control...


VGG: hacer una red profunda con bloques sencillos (VISUAL GEOMETRY GROUP). Muchas piezas pequeñas (facil y baseline, pero muchos parametros y puede requerir bastante memoria y computación). 

ResNet: Residual Network, añade conexiones que permiten que la información salte algunas capas (skip conections). La red puede aprender una modificación de la información original en lugar de tener que aprender toda la información desde cero. 

Inception: analizar patrones a diferentes escalas (GoogleNet). Procesa la misma entrada mediante varias ramas convolucionales en paralelo y combinar sus resultados. Usa filtros de diferentes tamaños, porque los patrones interesantes no siempre tienen el mismo tamaño. Varias ramas en paralelo para capturar patrones a diferentes escalas. 


import tensorflow as tf

def generate_model():
    model = tf.keras.Sequential([
        tf.keras.layers.Conv2D(32, filter_size=3, activation="relu")
        tf.keras.layers.MaxPool2D(pool_size=2, strides=2)

        tf.keras.layers.Conv2D(64, filter_size=3, activation="relu")
        tf.keras.layers.MaxPool2D(pool_size=2, strides=2)

        tf.keras.layers.Flatten(), 
        tf.keras.layers.Dense(1024, activation="relu")
        tf.keras.layers.Dense(10, activation="softmax")
    ])

    return model


