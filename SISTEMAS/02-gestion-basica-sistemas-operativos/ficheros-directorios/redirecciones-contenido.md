# Redirecciones y contenido de ficheros

## Qué es una redirección

Una redirección permite enviar la salida de un comando a un archivo.

## Sobrescribir

CMD:

    echo Hola > archivo.txt

PowerShell:

    Set-Content -Path archivo.txt -Value "Hola"

Bash:

    echo "Hola" > archivo.txt

## Añadir contenido al final

CMD:

    echo Nueva linea >> archivo.txt

PowerShell:

    Add-Content -Path archivo.txt -Value "Nueva linea"

Bash:

    echo "Nueva linea" >> archivo.txt

## Mostrar contenido

CMD:

    type archivo.txt

PowerShell:

    Get-Content archivo.txt

Bash:

    cat archivo.txt

## Unir archivos

CMD:

    type origen.txt >> destino.txt

PowerShell:

    Add-Content -Path destino.txt -Value (Get-Content origen.txt)

Bash:

    cat origen.txt >> destino.txt

## Paginar salida

CMD:

    type *.txt | more

PowerShell:

    Get-Content *.txt | Out-Host -Paging

Bash:

    cat *.txt | more

## Guardar árbol en archivo

CMD:

    tree viatges /f /a > estructura.txt

Bash:

    tree -a -A viatges > estructura.txt

## Símbolos importantes

| Símbolo | Función |
|---|---|
| > | Sobrescribe o crea archivo |
| >> | Añade al final |
| pipe | Encadena salida de un comando con entrada de otro |

## Cuidado

El símbolo > borra el contenido anterior del archivo.

Si quieres conservarlo, usa >>.
