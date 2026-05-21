# 📋 Representação 1: Lista (Ordem e Sequência)
> Foco Principal: Passos e ordem cronológica.

No contexto do **Portal Acadêmico Integrado (PAI)**, utilizamos a estrutura de dados em **Lista** para representar o fluxo sequencial e ordenado de ações quando uma nota é lançada no sistema. 

A informação bruta (a nota) passa por um processo linear (pipeline) até se tornar conhecimento estruturado (uma recomendação inteligente) para o aluno.

### Fluxo Linear: Ciclo de Vida da Nota no Sistema PAI

1. **Autenticação:** O sistema valida o token JWT do `Usuario` (Professor) para garantir que ele tem permissão de edição.
2. **Seleção de Entidade:** O `Professor` acessa a interface da `Disciplina` vinculada ao seu perfil.
3. **Entrada de Dados (Input):** O `Professor` seleciona o `Aluno` na lista de chamadas e insere o valor numérico da avaliação (ex: 8.5).
4. **Validação de Regra de Negócio:** O sistema checa se a nota está no intervalo permitido (0 a 10) para evitar erros de lógica.
5. **Persistência de Dados:** A nota é gravada no banco de dados e vinculada ao ID do `Aluno` e ao ID da `Disciplina`.
6. **Acionamento de Gatilho (Trigger):** O módulo acadêmico notifica o microsserviço `MotorIA` de que há uma nova alteração no histórico do aluno.
7. **Processamento (Abstração):** O `MotorIA` consome o novo histórico e recalcula a média geral do `Aluno`.
8. **Análise de Padrões:** O `MotorIA` cruza o novo desempenho com os requisitos para formatura e com o banco de conteúdos sugeridos.
9. **Geração de Insight:** Uma recomendação personalizada (ex: "Sugestão de leitura complementar") é gerada e associada ao perfil do `Aluno`.
10. **Saída de Dados (Output):** O sistema dispara uma notificação *push* ou e-mail alertando o `Aluno` de que uma nova nota e recomendação estão disponíveis no portal.

---
**Justificativa de Uso:** Conforme a literatura da disciplina, a representação em Lista foi escolhida aqui pois a ordem dos fatores altera o produto. O `MotorIA` (passo 7) não pode atuar antes que a validação de regra de negócio (passo 4) esteja concluída.
