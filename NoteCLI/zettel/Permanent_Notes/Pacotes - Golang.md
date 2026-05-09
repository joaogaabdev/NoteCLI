Referees: #Golang 
# Caso queira importar uma função de um pacote, segue a sintaxe:

``` go
import "fmt"

fmt.Println( )
//-> pacote.função_desejada( )
```

O nome do pacote é sempre o último no caminho de exportação, ex:

``` go
import "enconding/json"

json.Marshal( )
//-> json(último nome do caminho enconding/json)
```

## Exceções:

Pacotes "internal" não podem ser acessados diretamente fora do seu pacote mãe;
Pacote main não é "importável" ele é utilizado para criar o executável;
