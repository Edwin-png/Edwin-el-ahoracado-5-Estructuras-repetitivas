import random

def seleccionar_palabra():
    palabras = ["Loja", "Esmeraldas", "Ambato", "Quito", "Cuenca", "Manabi", "Tulcan", "Los Rios", 
                "Guayaquil", "Zamora", "Sucumbios", "Napo", "El Oro", "Santa Elena", "Santo Domingo", "Riobamba"]
    palabra = random.choice(palabras)
    return palabra

def mostrar_progreso(palabra, letras_adivinadas):
    progreso = ""
    for letra in palabra:
        if letra in letras_adivinadas:
            progreso += letra
        else:
            progreso += "_"
    return progreso

def jugar_ahorcado():
    palabra_secreta = seleccionar_palabra()
    letras_adivinadas = []
    intentos_maximos = 6
    intentos = 0

    print("¡Bienvenido al juego del ahorcado!")
    print("Adivina la ciudad:")
    print(mostrar_progreso(palabra_secreta, letras_adivinadas))

    while intentos < intentos_maximos:
        letra_usuario = input("Ingresa una letra: ").capitalize()

        if letra_usuario.isalpha() and len(letra_usuario) == 1:
            if letra_usuario in letras_adivinadas:
                print("Ya has intentado con esa letra. Intenta con otra.")
            else:
                if letra_usuario in palabra_secreta:
                    letras_adivinadas.append(letra_usuario)
                    print("¡Correcto!")
                else:
                    intentos += 1
                    print("Incorrecto. Intentos restantes:", intentos_maximos - intentos)
        else:
            print("Ingresa una letra válida.")

        progreso_actual = mostrar_progreso(palabra_secreta, letras_adivinadas)
        print(progreso_actual)

        if "_" not in progreso_actual:
            print("¡Felicidades! Has adivinado la palabra:", palabra_secreta)
            break

    else:
        print("¡Oh no! Te has quedado sin intentos. La palabra correcta era:", palabra_secreta)

if __name__ == "__main__":
    jugar_ahorcado()
