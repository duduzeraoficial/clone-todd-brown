# Clone Digital Todd Brown

## 1. Descrição do Projeto

Este projeto é uma implementação completa do desafio "Clone Digital do Todd Brown". Trata-se de um sistema de IA que analisa, avalia e otimiza briefings de VSL (Video Sales Letter) com base nos princípios e frameworks do Método E5 de Todd Brown.

O sistema recebe um briefing bruto, processa-o através de uma cadeia de 6 LLMs especializados e retorna uma análise estratégica detalhada em formato JSON. A análise inclui:
* Uma avaliação de aprovação baseada nos critérios de Todd Brown.
* Uma análise crítica da Big Marketing Idea (BMI) com 5 pontos de melhoria.
* Uma pontuação quantitativa (0-10) para cada bloco da VSL (Lead, História, Mecanismo e Oferta).
* Um diagnóstico completo dos pontos fracos com prescrições acionáveis.
* Um novo `briefing_vsl_v2` otimizado e pronto para execução.

## 2. Demonstração em Vídeo

Uma demonstração completa do sistema em funcionamento, desde o upload do briefing até a análise do resultado final, pode ser encontrada no vídeo abaixo:

https://www.loom.com/share/c873f84233484b6e954f2780e4bbec44?sid=7366dd25-007f-4fc0-bb4c-040f02f62881

## 3. Tecnologias Utilizadas

* **Orquestração de Workflow:** n8n
* **Interface (Front-end):** Lovable
* **Motor de Inteligência (LLMs):** Gemini & Claude (via OpenRouter)
* **Linguagem de Documentação:** Markdown

## 4. Como Testar o Sistema

Existem duas formas de testar o sistema. A primeira opção é a mais recomendada, pois demonstra a experiência completa do produto.

### Opção 1: Testar a Aplicação Completa (Recomendado)

Esta opção permite-lhe interagir com a interface do utilizador final e ver o fluxo completo em ação.

1.  **Aceda à Aplicação:** Abra o seguinte link no seu browser:
    [https://clone-todd-brown.lovable.app/](https://clone-todd-brown.lovable.app/)

2.  **Faça o Login:** Utilize as seguintes credenciais de demonstração:
    * **Login:** `admin`
    * **Senha:** `admin123`

3.  **Faça o Upload do Briefing:** Na interface, clique para selecionar um ficheiro e escolha o documento de teste `brief_vsl_playboy_coffe.docx`, que pode encontrar na pasta `/input-de-teste` deste repositório.

4.  **Aguarde a Análise:** Uma tela de carregamento será exibida. O processo de análise leva aproximadamente 3 minutos para ser concluído.

5.  **Veja o Resultado:** O JSON completo com a análise estratégica será exibido diretamente na tela.

> **Nota de Segurança:** As credenciais fornecidas são exclusivamente para fins de avaliação deste desafio e não dão acesso a sistemas ou dados sensíveis.

### Opção 2: Testar o Workflow Diretamente no n8n

Esta opção é ideal para desenvolvedores que desejam inspecionar a lógica do backend diretamente.

1.  **Faça o Download do Workflow:** Descarregue o ficheiro `todd-brown-clone-workflow.json` da pasta `/sistema`.

2.  **Importe no n8n:** Na sua instância n8n, importe o ficheiro JSON para criar o workflow completo.

3.  **Configure as Chaves de API:** Adicione a sua chave de API do OpenRouter nos nós de LLM correspondentes para permitir a comunicação com os modelos de linguagem.

4.  **Execute o Teste no Trigger:**
    * Encontre o primeiro nó do workflow (o trigger, que pode ser do tipo "On form submission" ou similar).
    * Utilize a funcionalidade de teste do próprio nó para fazer o upload de um ficheiro. Selecione o documento de teste `brief_vsl_playboy_coffe.docx`.
    * Clique em "Execute Node" ou na opção equivalente para iniciar a execução de teste.

5.  **Verifique a Saída:** Após a conclusão, o resultado JSON final estará disponível na saída do último nó do workflow.

## 5. Estrutura do Repositório

O repositório está organizado da seguinte forma para garantir clareza e fácil navegação:

```
/
|-- README.md (Este ficheiro)
|
|-- /ativos/
|   |-- base-conhecimento-todd-brown.pdf (A pesquisa completa sobre a metodologia)
|   |-- base-conhecimento-estruturada.md (Versão processada para engenharia de prompt)
|
|-- /documentacao/
|   |-- 01-documentacao-concepcao.md (Arquitetura e plano do projeto)
|   |-- 02-construcao-base-conhecimento.md (Processo de criação da base de conhecimento)
|   |-- 03-documentacao-metricas.md (Como as métricas são calculadas e apresentadas)
|   |-- 04-documentacao-validacao-qualidade.md (Metodologia de validação do sistema)
|   |-- 05-analise-de-custo-e-viabilidade.md (Análise de ROI e custo operacional)
|   |-- diagrama.md (Diagrama de fluxo do sistema em Mermaid)
|
|-- /input-de-teste/
|   |-- brief_vsl_playboy_coffe.docx (Ficheiro de teste usado no desafio)
|
|-- /output/
|   |-- analise-playboy-coffee.json (O resultado JSON da análise do briefing de teste)
|
|-- /prompts/
|   |-- prompt-01-a-06.md (Documentação detalhada de cada um dos 6 prompts utilizados)
|
|-- /sistema/
|   |-- todd-brown-clone-workflow.json (O workflow exportado do n8n)
```
