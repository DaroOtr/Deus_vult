 Relaciones:	(Blanco : Agregación, negro : composición, Blanco potente : Herencia)

	- Base Game: Lo compone window y renderer (fuerte) (tiempo de vida dependiente)
	- Renderer: agregación con window (débil) (tiempo de vida independiente)
	- Game: Hereda de base game


windowsShouldClose() :
```
- Mantiene la ventana abierta y por ende el loop del juego o el Engine
```

Swap buffer(puntero de window) :
```
- Requiere un puntero a la ventana para evitar mover frame a frame la imagen a dibuja. asi que swapear las direcciones de memoria 	de los buffers front y back
```

glfwPollEvents():
```
- Desencola los eventos de inputs de el primero que llega, es el primero en salir
```

glClear(): [OpenGL_Docs_glClear](https://docs.gl/gl4/glClear)
```
- Requería que se incluya OpenGL ya que ya se viene incluida con los drivers de la grafica
- Este se encarga de limpiar lo dibujado en pantalla
```

OpenGL: [Learn OpenGL](https://learnopengl.com/Introduction)
```
- Es una interfaz (API)
- Contiene las herramientas para comunicarnos con la grafica
- Se rige por estados donde usa un programa hasta que se indique lo contrario
```

Gen Buffer : [OpenGL_Docs_Gen Buffers](https://docs.gl/gl4/glGenBuffers)
```
- Genera el buffer e indica que el objeto que recibe como parámetro es el contenido de ese buffer
```

BindBuffer : [OpenGL_Docs_Bind Buffers](https://docs.gl/gl4/glBindBuffer)
```
	- Bloquea el buffer que se usa en ese momento
```

VertexBuffer :
```
	- Almacena la información de los vertices
```

IndexBuffer :
```
- Requiere del vertex buffer y nos permite reutilizar los vertices ya creados para dibujar una figura
```

Shaders : [OpenGL_Docs_Shaders](https://learnopengl.com/Getting-started/Shaders)
```
- "Programa programado por un programador"
```

GLEW :
```
- Es una extensión de OpenGL
- Agrega glVertex[...] : Indica los vertices y sus atributos
- Agrega glProgram[...] : Que hace uso del shader previamente programado
```

Stride :
```
- Tamaño del vertice
```

Offset :
```
- Apartir de que Byte empieza el atributo buscado
```

Matrices :

Transformaciones : 