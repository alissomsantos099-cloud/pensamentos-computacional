# 🐛 Missão Tática: Caça aos Bugs
## Fase 1: Identificação (Algoritmo Imperfeito)

Conforme as diretrizes do Laboratório Prático da disciplina (Profa. Kadidja Valéria / Baseado em Santos, 2021), submetemos o módulo de validação do sistema PAI (Plataforma Acadêmica Inteligente) a uma auditoria de código.

Nesta etapa, focamos em localizar erros ocultos em uma versão inicial e imperfeita do algoritmo.

---

### 1. O Algoritmo Imperfeito
Abaixo está o trecho de código original em PHP. Ele foi projetado com falhas estruturais para o exercício de debugging:

```php
<?php
// 1. Array de dados (Simulando Banco)
$aluno = [
    'nome' => 'Daniel Lopes',
    'status' => 'Ativo',
    'media' => 15.5, // Nota impossível
    'faltas' => 2
] // <--- Faltando ponto e vírgula

// 2. Função de Recomendação
function gerarRecomendacao($dados) {
    
    // Verificando status com chave incorreta
    if ($dados['status_matricula'] !== 'Ativo') { 
        return "Matrícula Trancada.";
    }

    if ($dados['media'] >= 7) {
        return "Aprovado!";
    } else {
        return "Reprovado!";
    }
}

// 3. Execução
echo gerarRecomendacao($aluno);
?>
```

---

### 2. Mapeamento dos Erros Encontrados

Após a inspeção, mapeamos três categorias de bugs que impedem o funcionamento seguro do sistema em larga escala:

#### 🚨 A. Erro de Sintaxe
* **Local:** Linha 7 (fechamento do array `$aluno`).
* **Descrição:** Ausência do ponto e vírgula (`;`) obrigatório na sintaxe do PHP.
* **Impacto:** O interpretador PHP não consegue compilar o script, gerando um `Parse error: syntax error`. O sistema inteiro cai antes mesmo de rodar.

#### 🚨 B. Erro de Execução (Runtime Error)
* **Local:** Linha 13 (`if ($dados['status_matricula'] !== 'Ativo')`).
* **Descrição:** Tentativa de acessar uma chave de array (`status_matricula`) que não existe. A chave correta no banco de dados é apenas `status`.
* **Impacto:** Gera um *Warning* de `Undefined array key`. Dependendo da configuração do servidor web, isso pode expor a estrutura do código para o usuário final, caracterizando uma vulnerabilidade de segurança.

#### 🚨 C. Erro de Lógica
* **Local:** Linha 5 (`'media' => 15.5`) e Linha 17 (`if ($dados['media'] >= 7)`).
* **Descrição:** O algoritmo avalia se a média é maior que 7, mas não estabelece um teto (máximo 10) ou um piso (mínimo 0).
* **Impacto:** O sistema aceitaria dados corrompidos (como uma nota 15.5 ou -3), processando um aluno aprovado com base em um cálculo impossível na regra de negócio da faculdade.

---

### 3. Evidência do Erro (Log do Servidor)

*Abaixo está a captura de tela demonstrando o erro fatal no ambiente de testes (localhost/XAMPP):*

![Evidência do Erro no Localhost](./print_erro_xampp.png)
*(Nota: O erro de sintaxe impede a execução, validando a necessidade de refatoração imediata).*
