### **Prompt 6: Compiladora Final de Análise de VSL**

#### **1. Objetivo**

Este prompt funciona como a **Unidade de Montagem e Validação Sintática** do sistema. A sua única e exclusiva missão é atuar como uma "compiladora" de alta precisão, recebendo os outputs JSON modulares dos cinco LLMs anteriores e montando-os num único objeto JSON mestre.

O seu valor estratégico não está na inteligência ou na análise, mas sim na **fiabilidade e na disciplina**. Ele garante que o output final enviado ao front-end seja sempre perfeitamente estruturado, sintaticamente válido e 100% fiel aos dados gerados pelas análises anteriores, atuando como o "quality gate" final da arquitetura do sistema.

#### **2. Prompt Completo**

# Prompt para LLM 6: Compiladora Final

```markdown  
# PROMPT: LLM 6 - Compiladora Final de Análise de VSL

## Sua Missão  
Você é a **Compiladora Final**. Sua única função é executar uma tarefa de montagem de alta precisão: compilar os outputs JSON das 5 LLMs anteriores em um único objeto JSON mestre, seguindo a estrutura exata que o front-end espera.

**Regras Absolutas:**  
- Não analise, não interprete, não modifique conteúdo  
- Apenas compile e estruture  
- Mantenha 100% de fidelidade aos dados originais  
- Garanta JSON sintaticamente perfeito

## INPUT QUE VOCÊ RECEBERÁ

Você receberá 5 blocos de JSON, cada um proveniente de uma LLM anterior:

1. **LLM 1** - Análise Clone Todd Brown  
2. **LLM 2** - Análise Big Idea  
3. **LLM 3** - Avaliação Quantitativa  
4. **LLM 4** - Pontos de Melhoria do Briefing  
5. **LLM 5** - Resumo VSL Ajustada

## ESTRUTURA DO OUTPUT FINAL

Você DEVE gerar um JSON com esta estrutura exata:

```json  
{  
  "analise_clone_todd_brown": {},  
  "analise_big_idea": {},  
  "avaliacao_quantitativa_blocos": {},  
  "pontos_de_melhoria_briefing": {},  
  "resumo_vsl_ajustada": {}  
}  
```

## INSTRUÇÕES DE COMPILAÇÃO

### Etapa 1: Mapeamento da LLM 1  
- **Origem:** Objeto `llm_1_analise_todd_brown` do JSON da LLM 1  
- **Destino:** Campo `analise_clone_todd_brown`  
- **Ação:** Copie TODO o conteúdo interno do objeto de origem para o destino

### Etapa 2: Mapeamento da LLM 2  
- **Origem:** Objeto `llm_2_analise_big_idea` do JSON da LLM 2  
- **Destino:** Campo `analise_big_idea`  
- **Ação:** Copie TODO o conteúdo interno do objeto de origem para o destino

### Etapa 3: Mapeamento da LLM 3  
- **Origem:** Objeto `llm_3_avaliacao_quantitativa` do JSON da LLM 3  
- **Destino:** Campo `avaliacao_quantitativa_blocos`  
- **Ação:** Copie TODO o conteúdo interno do objeto de origem para o destino

### Etapa 4: Mapeamento da LLM 4  
- **Origem:** Objetos de blocos (lead, historia, mecanismo, oferta, prova) do JSON da LLM 4  
- **Destino:** Campo `pontos_de_melhoria_briefing`  
- **Ação:** Copie TODOS os objetos dos blocos para o destino

### Etapa 5: Mapeamento da LLM 5  
- **Origem:** Objeto `briefing_vsl_v2` do JSON da LLM 5  
- **Destino:** Campo `resumo_vsl_ajustada`  
- **Ação:** Copie TODO o conteúdo interno do objeto de origem para o destino

## CHECKLIST DE VALIDAÇÃO

Antes de entregar o JSON final, você DEVE verificar:

✅ Todas as 5 chaves principais estão presentes  
✅ Cada chave contém o conteúdo correto da LLM correspondente  
✅ Não há vírgulas faltando ou sobrando  
✅ Todas as chaves `{` e colchetes `[` estão fechados corretamente  
✅ O JSON é sintaticamente válido (pode ser parseado sem erros)  
✅ Nenhum conteúdo foi modificado, apenas reorganizado

## FORMATO DE ENTREGA

Entregue APENAS o JSON final compilado, sem explicações adicionais.

Comece sua resposta com:  
```json  
{  
  "analise_clone_todd_brown": {  
```

E termine com:  
```  
}  
```

## EXEMPLO DE EXECUÇÃO

**Input (simplificado):**  
```json  
// LLM 1  
{"llm_1_analise_todd_brown": {"elemento": "valor1"}}

// LLM 2  
{"llm_2_analise_big_idea": {"elemento": "valor2"}}

// ... etc  
```

**Output esperado:**  
```json  
{  
  "analise_clone_todd_brown": {"elemento": "valor1"},  
  "analise_big_idea": {"elemento": "valor2"},  
  "avaliacao_quantitativa_blocos": {...},  
  "pontos_de_melhoria_briefing": {...},  
  "resumo_vsl_ajustada": {...}  
}  
```

## INÍCIO DA TAREFA

Agora você receberá os 5 outputs JSON. Execute a compilação seguindo as instruções acima.

**Aguardando os 5 JSONs de entrada...**  
```

## Como Usar Este Prompt

1. **Copie o prompt acima**  
2. **Cole em uma nova conversa com a LLM 6**  
3. **Em seguida, forneça os 5 JSONs** das LLMs anteriores (pode ser em mensagens separadas ou tudo de uma vez)  
4. **A LLM retornará apenas o JSON compilado final**

## Variação: Prompt Mais Conciso

Se preferir uma versão mais enxuta:

```markdown  
# LLM 6: Compiladora Final

Compile os 5 JSONs das LLMs anteriores em um único JSON com esta estrutura:

```json  
{  
  "analise_clone_todd_brown": {},      // ← LLM 1: objeto llm_1_analise_todd_brown  
  "analise_big_idea": {},              // ← LLM 2: objeto llm_2_analise_big_idea  
  "avaliacao_quantitativa_blocos": {}, // ← LLM 3: objeto llm_3_avaliacao_quantitativa  
  "pontos_de_melhoria_briefing": {},   // ← LLM 4: todos os blocos  
  "resumo_vsl_ajustada": {}            // ← LLM 5: objeto briefing_vsl_v2  
}  
```

**Regras:**  
- Copie o conteúdo interno de cada objeto origem para o destino correspondente  
- Não modifique conteúdo, apenas reorganize  
- Garanta JSON sintaticamente válido  
- Retorne APENAS o JSON final, sem explicações

**Forneça os 5 JSONs agora:**  
```

#### **3. Contexto de Input**

Este prompt recebe como input os **cinco outputs JSON** gerados individualmente pelos LLMs 1 a 5. É crucial notar que ele **não recebe o briefing original**, reforçando a sua função como um montador puro, desprovido de qualquer contexto analítico.

#### **4. Formato de Saída Esperado**

A saída é um único objeto JSON mestre, perfeitamente formatado e sintaticamente válido, que consolida todas as análises anteriores numa estrutura coesa, pronta para ser enviada ao front-end.

JSON

{  
  "analise_clone_todd_brown": {  
    "aprovado_por_todd_brown": true,  
    "justificativa_aprovacao": "O briefing seria aprovado porque demonstra uma compreensão profunda dos princípios E5 para um mercado sofisticado (Nível 4). Ele identifica corretamente o avatar como Problem-Aware (Nível 2) e, crucialmente, baseia toda a estratégia em um Mecanismo Único (UM) forte e diferenciado ('Playboy Coffee Trick'), que é obrigatório para este nível de saturação. A abordagem não é uma venda direta, mas uma campanha educacional projetada para mudar crenças, o que está perfeitamente alinhado com a metodologia.",  
    "framework_correto": true,  
    "justificativa_framework": "O framework de comunicação está correto pois segue a jornada de mudança de crenças de Todd Brown. A estrutura da VSL agita o problema (medos do avatar), invalida soluções antigas (falhas das pílulas azuis), revela a 'verdadeira causa' do problema (os MUPs: 'Testosterona Morta' e 'Óxido Nítrico Bloqueado') e apresenta o UM como a única solução lógica para essa causa, em vez de apenas listar benefícios."  
  },  
  "analise_big_idea": {  
    "big_idea_extraida": "O ritual secreto de Hugh Hefner, revelado por arquivos vazados, que devolve a virilidade de um homem de 20 anos aos 70, expondo a conspiração da indústria farmacêutica.",  
    "pontos_de_melhoria": [  
      {  
        "ponto": "Intensificar o Inimigo Comum",  
        "melhoria": "Em vez de culpar a 'Big Pharma' de forma abstrata, a BMI deve focar na 'arma' do inimigo: '...liberta você da armadilha química das pílulas azuis, projetada pela Big Pharma para garantir um cliente dependente para o resto da vida.'",  
        "justificativa_todd_brown": "Uma BMI forte precisa de um vilão tangível. Personificar o inimigo em um objeto que o cliente já usa (a pílula) torna a ameaça pessoal e imediata, aumentando a motivação para a mudança."  
      },  
      {  
        "ponto": "Aumentar as Apostas (Stakes)",  
        "melhoria": "Elevar a aposta da disfunção erétil de um 'problema de performance' para um 'sinal de alerta precoce de um evento cardíaco fatal'. Ex: 'O que Hugh Hefner sabia sobre o sinal de alerta #1 para ataques cardíacos...'",  
        "justificativa_todd_brown": "As melhores BMIs conectam o problema imediato a um medo universal e maior. O medo da morte é um motivador muito mais poderoso do que o medo da má performance."  
      },  
      {  
        "ponto": "Injetar Especificidade e Visualização",  
        "melhoria": "Substituir promessas abstratas como 'virilidade' por resultados concretos. Ex: 'O ritual de 90 segundos que Hugh Hefner usava para ter o tipo de ereção aos 80 anos que a maioria dos homens perde aos 40.'",  
        "justificativa_todd_brown": "Especificidade gera credibilidade e cria imagens mentais poderosas. O cérebro do cliente consegue 'ver' o resultado, o que o torna mais real e desejável."  
      },  
      {  
        "ponto": "Fortalecer o Ângulo Contraintuitivo",  
        "melhoria": "Criar um paradoxo desafiando um hábito diário. Ex: 'Por que a sua xícara de café matinal pode estar secretamente destruindo sua testosterona... a menos que você a combine com o 'sal vermelho' secreto de Hefner.'",  
        "justificativa_todd_brown": "Desafiar uma crença comum é a forma mais rápida de quebrar o padrão e capturar a atenção. Isso força o prospecto a reavaliar o que sabe e o abre para uma nova solução."  
      },  
      {  
        "ponto": "Amplificar a Urgência",  
        "melhoria": "Adicionar um gatilho temporal específico e crível à narrativa. Ex: 'Os arquivos médicos de Hefner, selados por um acordo de 25 anos, acabaram de expirar. Advogados da indústria já entraram com uma liminar para enterrá-los novamente.'",  
        "justificativa_todd_brown": "Uma BMI de elite responde 'Por que AGORA?'. Uma ameaça iminente e com prazo definido cria um Medo de Perder (FOMO) que transforma curiosidade em ação imediata."  
      }  
    ]  
  },  
  "avaliacao_quantitativa_blocos": {  
    "lead": {  
      "nota": 9.5,  
      "motivo": "A nota é alta porque o Lead cria uma curiosidade irresistível ao introduzir o gancho da Big Idea (o 'ritual secreto de Hefner') de forma misteriosa. Ele combina múltiplos elementos de elite (celebridade, segredo, conspiração), cumprindo seu único trabalho de prender a atenção. Não é 10 apenas porque a urgência poderia ser mais explícita no gancho inicial."  
    },  
    "historia": {  
      "nota": 8.5,  
      "motivo": "A nota é forte porque a História dá uma origem crível e única à Big Idea, usando o 'filho do urologista' para construir autoridade. A narrativa transita bem ao agitar o problema e revelar a 'verdadeira causa' (os MUPs). Não é 10 pois falta um arco emocional mais forte para o 'expert'."  
    },  
    "mecanismo": {  
      "nota": 10,  
      "motivo": "A nota é máxima porque o Mecanismo ('Playboy Coffee Trick') é a execução técnica perfeita da promessa da Big Idea. Ele responde de forma lógica e satisfatória à curiosidade criada pelo Lead, explicando o 'COMO' o segredo funciona e resolvendo diretamente os problemas revelados na História."  
    },  
    "oferta": {  
      "nota": 3,  
      "motivo": "A nota é baixa porque a Oferta falha em seu trabalho. Após uma construção narrativa poderosa, a oferta é apenas 'um produto e um preço', sem bônus estratégicos, uma garantia de inversão de risco forte ou um 'value stack'. Há uma quebra de coesão, pois a força da Big Idea não é refletida na força da Oferta."  
    }  
  },  
  "pontos_de_melhoria_briefing": {  
    "lead": {  
      "principal_erro": "Urgência vaga e implícita, sem um prazo específico.",  
      "melhoria_sugerida": "Adicionar um gatilho temporal crível e específico. Exemplo: 'Advogados da indústria farmacêutica entraram com uma liminar para remover este vídeo. Temos 72 horas antes que a ordem judicial seja cumprida.'"  
    },  
    "historia": {  
      "principal_erro": "O expert (o filho do urologista) não tem uma motivação pessoal ou um catalisador emocional forte.",  
      "melhoria_sugerida": "Adicionar um arco emocional: o expert decidiu revelar o segredo após uma tragédia pessoal (ex: um familiar quase morrer por causa das pílulas azuis), tornando sua missão pessoal e urgente."  
    },  
    "mecanismo": {  
      "principal_erro": "A ponte de credibilidade entre a história do 'ritual' simples (Café + Sal) e o produto final complexo (cápsulas com múltiplos ingredientes) é fraca.",  
      "melhoria_sugerida": "Explicar explicitamente que a fórmula moderna é uma versão cientificamente otimizada e potencializada do ritual original, justificando por que não pode ser replicada em casa."  
    },  
    "oferta": {  
      "principal_erro": "Ausência de um Framework de Oferta SIN (Superior, Irresistível, No-brainer) completo.",  
      "melhoria_sugerida": "Construir uma oferta completa com 3-5 bônus estratégicos que resolvem objeções, um 'value stack' claro para criar contraste de valor, e uma garantia de inversão de risco poderosa."  
    },  
    "prova": {  
      "principal_erro": "A prova social (depoimentos de 'homens comuns') está concentrada apenas no final da VSL.",  
      "melhoria_sugerida": "Distribuir 'micro-depoimentos' ao longo de toda a VSL, imediatamente após cada afirmação importante, para neutralizar o ceticismo em tempo real."  
    }  
  },  
  "resumo_vsl_ajustada": {  
    "novo_briefing_blocos": {  
      "lead_ajustado": "O novo Lead deve combinar três ganchos: 1) Uma estatística chocante sobre os riscos cardíacos das pílulas azuis. 2) A conspiração da Big Pharma para esconder essa informação. 3) A revelação do 'ritual secreto de Hefner' como a solução segura. Tudo isso com um gatilho de urgência específico, como um prazo de 72 horas.",  
      "historia_ajustada": "A nova História deve incluir um catalisador emocional para o expert. Sua missão de revelar o segredo não é apenas profissional, mas pessoal, desencadeada por uma tragédia familiar ligada aos perigos das soluções farmacêuticas. A narrativa também deve integrar 'micro-depoimentos' em pontos-chave.",  
      "mecanismo_ajustado": "O novo Mecanismo deve incluir uma seção clara de 'Ponte de Credibilidade'. Deve explicar que o ritual original de Hefner era a base, mas a fórmula moderna é a versão cientificamente otimizada, com extratos purificados e cofatores sinérgicos que potencializam o efeito e não podem ser replicados em casa.",  
      "oferta_ajustada_sin": {  
        "produto_principal": "Fornecimento de 6 Meses do 'Playboy Coffee Ritual'.",  
        "bonus_1": "Bônus Estratégico 1: 'O Guia da Dieta da Virilidade' (para resolver a objeção 'e se meu estilo de vida estiver atrapalhando?').",  
        "bonus_2": "Bônus Estratégico 2: 'O Protocolo Mental Anti-Ansiedade de Performance' (para resolver a objeção 'e se o problema for psicológico?').",  
        "bonus_3": "Bônus Estratégico 3: Acesso Vitalício à Comunidade 'A Nova Confraria' (para resolver a objeção 'terei suporte?').",  
        "garantia": "Garantia de Inversão de Risco Total: 'Teste por 90 dias. Se não funcionar, devolvemos 100% do seu dinheiro e você fica com todos os bônus.'",  
        "value_stack": "Apresentar o valor total de todos os componentes (produto + bônus) para criar um contraste massivo com o preço final da oferta.",  
        "escassez": "Justificar a escassez com a dificuldade de obter o 'Alaea Red Salt' autêntico do Havaí."  
      }  
    }  
  }  
}

#### **5. Análise Estratégica do Prompt**

A decisão de dedicar um LLM inteiro a uma tarefa aparentemente simples de compilação é um pilar fundamental da robustez da arquitetura do sistema.

* **Princípio do Operário Especializado (Separação de Responsabilidades):** Em vez de sobrecarregar o LLM 5 (Arquiteta de Roteiro) com a tarefa adicional de montar o JSON final, esta responsabilidade é delegada a um nó especializado. Isso segue o princípio de engenharia de software da "Separação de Responsabilidades", onde cada componente tem uma única e bem definida função. O LLM 5 foca-se em gerar conteúdo de alta qualidade; o LLM 6 foca-se em garantir a integridade estrutural.  
* **Redução Drástica do Risco de Erro Sintático:** Pedir a um LLM para gerar um JSON grande e complexo de uma só vez aumenta exponencialmente o risco de erros de sintaxe (vírgulas em falta, chaves não fechadas). Ao dividir o trabalho em JSONs mais pequenos e usar um compilador final com instruções simples, a probabilidade de um erro fatal no output final é minimizada. O "Checklist de Validação" no prompt reforça ainda mais esta função.  
* **Baixo Custo Computacional e Alta Fiabilidade:** A tarefa deste prompt é deterministicamente simples. Não requer raciocínio complexo, apenas mapeamento de dados. Isso significa que pode ser executado por um modelo de LLM mais rápido e barato, com uma taxa de sucesso próxima de 100%. Ele funciona como um passo de "build" fiável no final da "linha de montagem" de IA.  
* **Facilidade de Depuração e Manutenção:** Se o JSON final estiver malformado, a equipa de desenvolvimento sabe que o ponto de falha está quase certamente neste nó, em vez de ter de investigar os cinco prompts analíticos anteriores. Isso acelera drasticamente a depuração e a manutenção do workflow.

