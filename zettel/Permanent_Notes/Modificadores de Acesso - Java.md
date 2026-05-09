#Java 
# public
Pode ser acessado de qualquer lugar por quaisquer entidades que possa visualizar a classe que ela pertence.
# private
Os métodos e atributos da classe definidos como privados não podem ser acessados ou usados por nenhuma outra classe. Esses atributos e métodos também não podem ser visualizados pelas classes herdadas.
# protected
Torna o membro acessível às classes do mesmo pacote ou através de herança, seus membros herdados não são acessíveis a outras classes fora do pacote em que foram declarados.
# default(padrão)
A classe e/ou seus métodos serão acessíveis somente por classes do mesmo pacote, na sua declaração não é definido nenhum tipo de modificador.

## abstract
Esse modificador de acesso não é aplicado nas variáveis, apenas em classes e métodos. Uma classe abstrata não pode ser instanciada. Se houver alguma declaração de um método como abstract, a classe também deve ser marcada como abstract.
Abstrato = ideia de uma classe, não pode ser objeto de uma,
Exemplo: 
``` java
public abstract class FormaGeometrica{
	public abstract String nome(); //método de uma classe abstrata
	public abstract Double area();
}
```

## static
É usado para a criação de uma variável que poderá ser acessada por todas as instâncias de objetos dessa classe como uma variável comum, ou seja, a variável criada será a mesma em todas as instâncias e quando seu conteúdo é modificado numa das instâncias, a modificação ocorre em todas as demais. E nas declarações de métodos ajudam no acesso direto à classe, portanto, não é necessário instanciar um objeto para acessar o método.

## final
Quando é aplicado na classe, não permite estender, nos métodos impede que o mesmo seja sobrescrito(overriding) na subclasse, e nos valores de variáveis não pode ser alterado depois que já tenha atribuído um valor.
