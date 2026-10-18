# Coleta e classificação de respostas de IA

## Protocolo de coleta manual

**Preparação**
1. Defina o **conjunto de prompts** (modelo abaixo) e o **conjunto competitivo** de marcas. Congele os dois antes de coletar.
2. Escolha as **plataformas**: os assistentes de IA mais usados pelo seu público e as respostas geradas na página de resultados do buscador principal.
3. Defina o **mercado**: país, idioma e, se o negócio for local, a cidade. Colete a partir desse mercado. Se estiver em outro lugar, registre a limitação.
4. Defina a **condição de sessão**: anônima, ou com conta com histórico, memória e instruções personalizadas desativados, com ou sem login. Use sempre a mesma condição em todas as coletas.

**Execução**
1. Abra uma sessão nova para cada bloco de prompts, sem histórico de conversa anterior.
2. Cole o prompt exatamente como está na planilha, sem ajustes.
3. Aguarde a resposta completa. Se houver painel de fontes, abra-o.
4. Salve o **texto bruto** da resposta e uma **captura de tela** com data e hora visíveis ou registradas no nome do arquivo.
5. Registre as marcas, URLs e produtos na planilha de respostas.
6. **Repita a coleta de forma recorrente, de preferência diária**, com o mesmo conjunto de prompts. Cada dia é uma repetição, e a consistência vem do acúmulo. Em uma análise pontual, sem monitoramento, rode cada prompt pelo menos três vezes em momentos diferentes.
7. Para as respostas geradas na página de resultados, faça a busca em janela anônima, no mercado definido, e registre se a resposta aparece, o texto e as fontes.

**Situações especiais**
- **Plataforma exige login para responder:** registre "com login" e mantenha essa condição nas próximas coletas.
- **Fontes não exibidas:** registre "sem fontes". A resposta entra nas análises de menção e sentimento e fica fora das de citação.
- **Carrossel de produtos:** cada item vira uma linha em `produtos`, com nome, marca, loja, preço e ordem.
- **Resposta recusada ou com erro:** registre e recolete uma vez. Se persistir, marque como inválida.
- **Mudança visível na plataforma** (novo modelo, nova interface) durante a coleta: anote a data. Comparações entre antes e depois exigem cautela.

**Arquivamento**
- Uma pasta por coleta (data), com as capturas, os textos brutos e a planilha.
- Nunca sobrescreva coletas anteriores: elas são a base da comparação ao longo do tempo.

## Modelo de planilha de prompts

| Coluna | Exemplo de preenchimento |
|---|---|
| id_prompt | P001 |
| prompt | Texto exato, como o usuário escreveria |
| tema | Tema macro definido antes da coleta |
| intencao | marca · descoberta · comparação · problema · compra · pós-compra |
| origem | consulta de busca · pergunta relacionada · atendimento · comunidade · avaliação |
| mercado_idioma | País e idioma |
| prioridade_negocio | alta · média · baixa |

### Regras para escrever prompts
- Escreva como o usuário fala, não como o marketing escreve.
- Varie o comprimento: curto, como numa busca, e longo, com contexto e restrições.
- Não induza a resposta: evite "por que [marca] é a melhor".
- Inclua restrições reais: orçamento, região, perfil, urgência.
- Mantenha versões equivalentes entre as marcas comparadas.

## Modelo de planilha de respostas

| Coluna | Descrição |
|---|---|
| id_prompt | Liga ao prompt |
| plataforma | Assistente ou resposta gerada na página de resultados |
| data | Data da coleta |
| repeticao | 1, 2, 3… |
| mercado | País, idioma e cidade, se aplicável |
| login | com login · sem login |
| sessao_limpa | sim/não |
| resposta_texto | Texto completo |
| marcas_mencionadas | Lista em ordem de aparição |
| urls_citadas | Lista em ordem |
| dominios_citados | Derivado das URLs |
| produtos | Lista de nome · marca do produto · vendedor · preço |
| sentimento_marca | positivo · neutro · negativo · misto · não mencionada |
| atributos | Lista de atributos associados à marca |
| trecho_sentimento | Frase que justifica a classificação |
| erro_factual | Descrição, se houver |
| elementos | lista · tabela · comparativo · carrossel · acompanhamento |

## Guia de classificação de sentimento

| Classe | Critério | Exemplo de estrutura |
|---|---|---|
| Positivo | A marca é recomendada ou descrita com atributos favoráveis | "[marca] se destaca por…" |
| Neutro | Citada de forma descritiva, sem juízo | "Opções incluem [marca], X e Y" |
| Negativo | Descrita com atributos desfavoráveis ou desaconselhada | "[marca] tem reclamações sobre…" |
| Misto | Atributos favoráveis e desfavoráveis na mesma resposta | "Bom preço, mas entrega lenta" |

Atributos comuns para padronizar: preço, custo-benefício, qualidade, variedade, entrega, atendimento, confiança, segurança, facilidade de uso, garantia, sustentabilidade.

Valide sempre uma amostra das classificações à mão antes de agregar, especialmente se a classificação for automatizada.

## Tipos de fonte para classificar domínios citados

- Site próprio
- Concorrente direto
- Varejista ou plataforma de revenda
- Fabricante ou marca de produto
- Mídia ou notícia
- Review ou comparador
- Fórum, comunidade ou rede social
- Vídeo
- Enciclopédia ou base de conhecimento
- Institucional, acadêmico ou governo
- Outro

## Métricas e fórmulas

| Métrica | Fórmula | Denominador |
|---|---|---|
| Taxa de menção | respostas com menção ÷ respostas válidas | Respostas (prompt × plataforma × repetição) do recorte |
| Taxa de citação | respostas com URL do site citada ÷ respostas com fontes | Só respostas que retornaram fontes |
| Participação de voz | menções da marca ÷ menções das marcas do conjunto competitivo | Menções do conjunto competitivo no recorte |
| Participação de citação | citações do domínio ÷ citações totais | Citações no recorte |
| Estabilidade | repetições (ou dias) com aparição ÷ repetições (ou dias) coletados | Repetições ou dias de coleta do mesmo prompt |
| Presença consistente | prompts com aparição na maioria das repetições ÷ prompts com repetições completas | Prompts com repetições completas: o mínimo de dias coletados no período (monitoramento) ou pelo menos três execuções (análise pontual), definido pelo usuário e declarado no método |
| Sentimento líquido | (positivas − negativas) ÷ respostas com menção | Respostas com menção |
| Presença de produto | respostas com produto seu ÷ respostas de prompts de compra e descoberta | Respostas de compra e descoberta |
| Presença como vendedor | respostas com sua loja indicada ÷ respostas com produto recomendado | Respostas com produto |
