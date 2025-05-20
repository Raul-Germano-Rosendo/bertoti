# Loja de Produtos Católicos em Java

Este projeto simula uma loja de produtos católicos, algo parecido com o que eu, Raul Germano, Trabalho desde Novembro de 2024, com funcionalidades para:

- Adicionar produtos  
- Buscar produtos por nome  
- Buscar produtos por tipo  
- Listar todos os produtos disponíveis  

## Código-Fonte

```java
// Produto.java
public class Produto {
    private String nome;
    private String tipo; // ex: Terço, Livro, Imagem, Escapulário

    public Produto(String nome, String tipo) {
        this.nome = nome;
        this.tipo = tipo;
    }

    public String getNome() {
        return nome;
    }

    public String getTipo() {
        return tipo;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public void setTipo(String tipo) {
        this.tipo = tipo;
    }

    @Override
    public String toString() {
        return "Produto{" + "nome='" + nome + "', tipo='" + tipo + "'}";
    }
}
```

```java
// Loja.java
import java.util.List;
import java.util.LinkedList;

public class Loja {
    private List<Produto> produtos = new LinkedList<>();

    public void adicionarProduto(Produto produto) {
        produtos.add(produto);
    }

    public Produto buscarPorNome(String nome) {
        for (Produto p : produtos) {
            if (p.getNome().equalsIgnoreCase(nome)) {
                return p;
            }
        }
        return null;
    }

    public List<Produto> buscarPorTipo(String tipo) {
        List<Produto> encontrados = new LinkedList<>();
        for (Produto p : produtos) {
            if (p.getTipo().equalsIgnoreCase(tipo)) {
                encontrados.add(p);
            }
        }
        return encontrados;
    }

    public List<Produto> getProdutos() {
        return produtos;
    }
}
```

```java
// LojaTest.java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;
import java.util.List;

public class LojaTest {

    @Test
    public void testLojaProdutos() {
        Loja loja = new Loja();

        loja.adicionarProduto(new Produto("Terço de Madeira", "Terço"));
        loja.adicionarProduto(new Produto("Bíblia Sagrada", "Livro"));
        loja.adicionarProduto(new Produto("Imagem de Nossa Senhora", "Imagem"));

        assertEquals(3, loja.getProdutos().size());

        Produto p = loja.buscarPorNome("Bíblia Sagrada");
        assertNotNull(p);
        assertEquals("Livro", p.getTipo());

        List<Produto> terços = loja.buscarPorTipo("Terço");
        assertEquals(1, terços.size());
        assertEquals("Terço de Madeira", terços.get(0).getNome());
    }
}
```

---

## Como Executar

1. Clone este repositório.  
2. Compile os arquivos:
   ```bash
   javac Produto.java Loja.java LojaTest.java
   ```
3. Execute os testes com JUnit 5.
