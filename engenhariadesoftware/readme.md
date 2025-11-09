
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
<h3>(6) Testes Automatizados</h3>

```Java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import java.util.ArrayList;
import java.util.List;

import static org.junit.jupiter.api.Assertions.*;

public class LivrariaTest {

    private Livraria livraria;

    @BeforeEach
    void setUp() {
        livraria = new Livraria();
        livraria.setLivros(new ArrayList<>());
        livraria.livrosEmprestados = new ArrayList<>();
        livraria.clientes = new ArrayList<>();
    }

    @Test
    void testSetAndGetLivros() {
        List<Livro> lista = new ArrayList<>();
        lista.add(new Livro());
        livraria.setLivros(lista);

        assertEquals(lista, livraria.getLivros());
        assertEquals(1, livraria.getLivros().size());
    }

    @Test
    void testAddLivro() {
        Livro livro = new Livro();
        livraria.addLivro(livro);

        assertEquals(1, livraria.getLivros().size());
        assertTrue(livraria.getLivros().contains(livro));
    }

    @Test
    void testEmprestarLivros() {
        // cria livros e pedido
        Livro livro1 = new Livro();
        Livro livro2 = new Livro();

        List<Livro> livrosDoPedido = new ArrayList<>();
        livrosDoPedido.add(livro1);
        livrosDoPedido.add(livro2);

        Pedido pedido = new Pedido();
        pedido.setLivros(livrosDoPedido);

        Cliente cliente = new Cliente("Ana", "11122233344");

        // executa empréstimo
        livraria.emprestarLivros(pedido, cliente);

        // verifica resultados
        assertEquals(2, livraria.livrosEmprestados.size());
        assertTrue(livraria.livrosEmprestados.contains(livro1));
        assertTrue(livraria.livrosEmprestados.contains(livro2));
        assertTrue(livraria.clientes.contains(cliente));
    }
}
```

```Java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import java.util.ArrayList;
import java.util.List;

import static org.junit.jupiter.api.Assertions.*;

public class PedidoTest {

    private Pedido pedido;

    @BeforeEach
    void setUp() {
        pedido = new Pedido();
    }

    @Test
    void testInicializacaoPadrao() {
        assertNotNull(pedido.getLivros());
        assertTrue(pedido.getLivros().isEmpty());
        assertNull(pedido.getPreçoTotal());
        assertNull(pedido.getId());
        assertNull(pedido.getData());
    }

    @Test
    void testSetAndGetPrecoTotal() {
        pedido.setPreçoTotal(59.90f);
        assertEquals(59.90f, pedido.getPreçoTotal());
    }

    @Test
    void testSetAndGetId() {
        pedido.setId("PED123");
        assertEquals("PED123", pedido.getId());
    }

    @Test
    void testSetAndGetData() {
        pedido.setData("09/11/2025");
        assertEquals("09/11/2025", pedido.getData());
    }

    @Test
    void testAddLivro() {
        Livro livro = new Livro();
        pedido.addLivro(livro);

        assertEquals(1, pedido.getLivros().size());
        assertTrue(pedido.getLivros().contains(livro));
    }

    @Test
    void testSetLivros() {
        List<Livro> lista = new ArrayList<>();
        lista.add(new Livro());
        lista.add(new Livro());

        pedido.setLivros(lista);

        assertEquals(2, pedido.getLivros().size());
        assertSame(lista, pedido.getLivros());
    }
}
```

```Java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import java.util.ArrayList;
import java.util.List;

import static org.junit.jupiter.api.Assertions.*;

public class ClienteTest {

    private Cliente cliente;

    @BeforeEach
    void setUp() {
        cliente = new Cliente("João", "12345678900");
    }

    @Test
    void testConstrutor() {
        assertEquals("João", cliente.getNome());
        assertEquals("12345678900", cliente.getCpf());
        assertNotNull(cliente.getPedidos());
        assertTrue(cliente.getPedidos().isEmpty());
    }

    @Test
    void testSettersAndGetters() {
        cliente.setNome("Maria");
        cliente.setCpf("98765432100");

        assertEquals("Maria", cliente.getNome());
        assertEquals("98765432100", cliente.getCpf());
    }

    @Test
    void testAddPedido() {
        Pedido pedidoMock = new Pedido(); // supondo que tenha construtor vazio
        cliente.addPedido(pedidoMock);

        assertEquals(1, cliente.getPedidos().size());
        assertTrue(cliente.getPedidos().contains(pedidoMock));
    }

    @Test
    void testSetPedidos() {
        List<Pedido> novaLista = new ArrayList<>();
        novaLista.add(new Pedido());
        novaLista.add(new Pedido());

        cliente.setPedidos(novaLista);

        assertEquals(2, cliente.getPedidos().size());
        assertSame(novaLista, cliente.getPedidos());
    }
}
```

```Java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.*;

public class LivroTest {

    private Livro livro;

    @BeforeEach
    void setUp() {
        livro = new Livro("O Hobbit", "Fantasia", 39.90);
    }

    @Test
    void testConstrutor() {
        assertEquals("O Hobbit", livro.getNome());
        assertEquals("Fantasia", livro.getGênero());
        assertEquals(39.90, livro.getPreço());
    }

    @Test
    void testSetAndGetNome() {
        livro.setNome("1984");
        assertEquals("1984", livro.getNome());
    }

    @Test
    void testSetAndGetGenero() {
        livro.setGênero("Ficção");
        assertEquals("Ficção", livro.getGênero());
    }

    @Test
    void testSetAndGetPreco() {
        livro.setPreço(45.50);
        assertEquals(45.50, livro.getPreço());
    }
}
```

<h2>(7) Diagramas de Classe UML</h2>

![Diagrama](https://github.com/JkDeltaz/bertoti/blob/main/engenhariadesoftware/Atividade%204%20-%20Eng%20de%20Software.jpg)
