
<h3>Atividade 1 - Engenharia de Software</h3>

O texto I fala que programação e ciência da computação estão mais ligadas a escrever código e teoria, enquanto engenharia de software busca aplicar métodos rigorosos para construir sistemas reais e confiáveis. Ele também destaca que, com a crescente importância do software no dia a dia, é necessário adotar práticas mais sérias e estruturadas, semelhantes às de outras engenharias.

O texto II fala que engenharia de software envolve não só escrever código, mas também cuidar de todo o processo para mantê-lo útil e sustentável ao longo do tempo. Ele destaca três princípios essenciais: tempo e mudança (como o código deve se adaptar), escala e crescimento (como a organização evolui) e custos e trade-offs (como tomar decisões equilibradas)

<h3>Tradeoffs:</h3>

<h4>Velocidade de desenvolvimento vs. Qualidade do código</h4>
- Se a equipe prioriza entregar rápido, pode escrever código menos limpo e com menos testes. Isso acelera no curto prazo, mas pode gerar dívida técnica e aumentar custos futuros de manutenção.

<h4>Performance vs. Legibilidade</h4>
- Às vezes, otimizar ao máximo o código (por exemplo, usando estruturas complexas ou truques de baixo nível) torna o programa mais rápido, mas também mais difícil de entender e manter.

<h4>Customização vs. Padronização</h4>
- Oferecer várias opções e flexibilidade (ex.: permitir que cada cliente configure o sistema de forma diferente) aumenta a satisfação do usuário, mas dificulta manutenção e aumenta a complexidade.

<h2>Diagramas de Classe UML</h2>

![Diagrama](https://github.com/JkDeltaz/bertoti/blob/main/engenhariadesoftware/Atividade%204%20-%20Eng%20de%20Software.jpg)

<h2>Códigos em Java</h2>

```Java
public class Main {
    public static void main(String[] args) {

        Livraria livraria = new Livraria();

        Cliente cliente = new Cliente("Lilia", "181015112006");
        Livro livro01 = new Livro("Fahrenheit 451", "Distopia", 16.90);
        Livro livro02 = new Livro("Harry Potter", "Fantasia", 20.00);
        Livro livro03 = new Livro("2001", "Espacial", 32.89);

        Pedido pedido = new Pedido();
        pedido.addLivro(livro01);
        pedido.addLivro(livro03);

        cliente.addPedido(pedido);
        livraria.emprestarLivros(pedido, cliente);
    }
}
```

```Java
import java.util.List;

public class Livraria {

    List<Livro> livros;
    List<Livro> livrosEmprestados;
    List<Cliente> clientes;

    public List<Livro> getLivros() {
        return livros;
    }

    public void setLivros(List<Livro> livros) {
        this.livros = livros;
    }

    public void addLivro(Livro livro){
        livros.add(livro);
    }

    public void emprestarLivros(Pedido pedido, Cliente cliente){
        for (Livro livro:pedido.getLivros()) {
            livrosEmprestados.add(livro);
        }
        clientes.add(cliente);
    }
}
```

```Java
import java.util.ArrayList;
import java.util.List;

public class Pedido {

    List<Livro> livros =  new ArrayList<Livro>();
    Float preçoTotal;
    String id;
    String data;

    public List<Livro> getLivros() {
        return livros;
    }

    public void setLivros(List<Livro> livros) {
        this.livros = livros;
    }

    public void addLivro(Livro livro) {
        livros.add(livro);
    }

    public Float getPreçoTotal() {
        return preçoTotal;
    }

    public void setPreçoTotal(Float preçoTotal) {
        this.preçoTotal = preçoTotal;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getData() {
        return data;
    }

    public void setData(String data) {
        this.data = data;
    }
}
```

```Java
import java.util.ArrayList;
import java.util.List;

public class Cliente {

    String nome;
    String cpf;
    List<Pedido> pedidos = new ArrayList<Pedido>();

    public Cliente(String nome, String cpf) {
        this.nome = nome;
        this.cpf = cpf;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getCpf() {
        return cpf;
    }

    public void setCpf(String cpf) {
        this.cpf = cpf;
    }

    public List<Pedido> getPedidos() {
        return pedidos;
    }

    public void setPedidos(List<Pedido> pedidos) {
        this.pedidos = pedidos;
    }

    public void addPedido(Pedido pedido) {pedidos.add(pedido);}

}
```

```Java
public class Livro {

    String nome;
    String gênero;
    Double preço;

    public String getNome() {
        return nome;
    }

    public Livro(String nome, String gênero, Double preço) {
        this.nome = nome;
        this.gênero = gênero;
        this.preço = preço;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getGênero() {
        return gênero;
    }

    public void setGênero(String gênero) {
        this.gênero = gênero;
    }

    public Double getPreço() {
        return preço;
    }

    public void setPreço(Double preço) {
        this.preço = preço;
    }
}
```
