# Lab-Seg.-INF
Laboratorio seguridad informatica
#LABORATORIO_1
#NOMBRES: CATALINA LEDESMA Y DENISSE TORRES

#DESAFIO 1
print("---------------------------------------------")
print("Desafio 1\n")

#ROT
def custom(i):
    if i>=0:
        return i%26
    return 26+i

def rot(r,n):
    if r>="a" and r<="z":
        return chr(custom(ord(r)+n-97)+97)
    if r>="A" and r<="Z":
        return chr(custom(ord(r)+n-65)+65)
    return str(r)

def Rot(cadenita,n):
    nuevo = ""
    for r in cadenita:
        nuevo = nuevo+rot(r,n)
    return nuevo

#VIGENERE

abc = ("abcdefghijklmnopqrstuvwxyz")

def cifrar(cadena,llave):
        texto = ""
        aux=0
        for letra in cadena:
                orden = abc.find(letra)+abc.find(llave[aux%len(llave)])
                modo = int(orden)%len(abc)
                texto = texto + str(abc[modo])
                aux = aux+1
        return texto

def descifrar(cadena,llave):
        texto = ""
        aux=0
        for letra in cadena:
                orden = abc.find(letra)-abc.find(llave[aux%len(llave)])
                modo = int(orden)%len(abc)
                texto = texto + str(abc[modo])
                aux = aux+1
        return texto

#CIFRADO

print("Cifrado en Rot(8)")
primer_paso = Rot("HolaMundo",8)
print(Rot("HolaMundo",8))
print("")
print ("Cifrado en Vigenere")
linea = str(primer_paso).lower()
clave = "heropassword"
segundo_paso = cifrar(linea,clave)
print (cifrar(linea,clave))
print("")
print("Cifrado en Rot(12)")
print(Rot(segundo_paso,12))

#DESAFIO 2

print("---------------------------------------------")
print("Desafio 2\n")

#DESCIFRADO

print("Descifrado en Rot -12")
primero = Rot("DuaqQbOzYukrcqgEnwdqjl",-12)
print(Rot("DuaqQbOzYukrcqgEnwdqjl",-12))
print("")
print ("Descifrado en Vigenere")
line = str(primero).lower()
llave = "finispasswd"
segundo = descifrar(line,llave)
print (descifrar(line,llave))
print("")
print("Descifrado en rot -8")
print(Rot(segundo,-8))
print("---------------------------------------------")
