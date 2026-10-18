# Biblioteca de Skills de SEO e GEO

Skills para SEOs que trabalham com pouca estrutura: sem time de dados, sem orçamento para ferramentas, muitas vezes sozinhos dentro da empresa.

Cada skill traz **o raciocínio**, não a ferramenta. Ela diz qual informação é necessária, como obtê-la sem custo, o que fazer com ela e como decidir. A informação pode vir de onde você tiver acesso: os painéis gratuitos que os buscadores oferecem ao dono do site, analytics, rastreadores em versão gratuita, o próprio CMS, planilhas, coleta manual.

Cada skill funciona sozinha. Você pode baixar só a que precisa.

## Como usar

**Claude (app ou web)**
1. Baixe a pasta da skill e compacte-a em `.zip`, ou baixe o repositório inteiro.
2. Nas configurações do Claude, abra a área de Skills e envie o `.zip`.
3. Peça a tarefa normalmente ("faça uma auditoria técnica do meu site"). A skill é acionada sozinha quando o pedido combina com ela.

**Claude Code e agentes compatíveis com o padrão de Agent Skills**
- Copie a pasta da skill para o diretório de skills da ferramenta. No Claude Code, é `~/.claude/skills/` (para todos os projetos) ou `.claude/skills/` (só para um projeto).
- Para instalar todas de uma vez, clone o repositório e copie as pastas `seo-*`.

**ChatGPT, Gemini e outros chats**
- Abra o `SKILL.md` da skill, copie o conteúdo e cole no início da conversa, seguido do seu pedido.
- Para usar sempre, cole o conteúdo nas instruções de um projeto, GPT personalizado ou Gem.
- Se a skill tiver pasta `references/`, anexe também esses arquivos ou cole o conteúdo deles.

## Como cada skill está organizada

1. **Conceito**: o que é, por que importa e quais ideias sustentam a análise.
2. **O que é necessário**: o tipo de informação e como coletá-la sem custo.
3. **O que fazer**: o passo a passo do raciocínio.
4. **Como decidir**: critérios, limites e prioridades.
5. **Armadilhas**: os erros que levam a uma conclusão errada.
6. **Entrega**: a forma do resultado.
7. **Se faltar informação**: o que perguntar, quando seguir com uma aproximação declarada e quando parar.
8. **Quando sugerir apoio especializado**: os casos em que vale conversar com um consultor.

Algumas skills têm uma pasta `references/` com material de apoio extenso, como checklists, protocolos e modelos.

## Priorização por tiers

Nenhuma skill impõe prazo. As ações são organizadas em **tiers**, e o usuário define o prazo de cada tier conforme a capacidade do time:

| Tier | Significado |
|---|---|
| **Tier 1** | Maior impacto com menor dependência. É o que vem primeiro. |
| **Tier 2** | Impacto relevante, mas depende de outras áreas, de mais esforço ou do Tier 1. |
| **Tier 3** | Estruturante ou de longo prazo: mudança de estratégia, produção contínua, projetos grandes. |

O tier vem do **impacto e da dependência**, nunca do rótulo da ação. "Conteúdo para IA", por exemplo, pode ser Tier 1 ou Tier 3 conforme a intenção e o valor do tema.

## Skills

| Skill | Use quando |
|---|---|
| [seo-por-onde-comecar](seo-por-onde-comecar/SKILL.md) | Não sabe qual problema atacar primeiro |
| [seo-projecao-trafego-organico](seo-projecao-trafego-organico/SKILL.md) | Precisa defender meta, OKR ou investimento |
| [seo-diagnostico-conteudo-pruning](seo-diagnostico-conteudo-pruning/SKILL.md) | O acervo cresceu e ninguém sabe o que funciona |
| [seo-auditoria-tecnica-priorizada](seo-auditoria-tecnica-priorizada/SKILL.md) | Precisa verificar e priorizar a saúde técnica do site |
| [seo-presenca-buscas-ia](seo-presenca-buscas-ia/SKILL.md) | Quer entender como a marca, o conteúdo e os produtos aparecem em respostas de IA |
| [seo-medicao-relatorio-confiavel](seo-medicao-relatorio-confiavel/SKILL.md) | Vai reportar SEO e GEO sem errar ou sobrepor números |
| [seo-pesquisa-pauta-palavras-chave](seo-pesquisa-pauta-palavras-chave/SKILL.md) | Precisa decidir o que produzir ou otimizar com base em demanda real |

## Princípios que atravessam todas as skills

- **Separe o que existe do que é novo.** O ganho só conta o que não estava lá antes.
- **Associação não é causa.** Duas coisas andarem juntas não prova que uma provoca a outra.
- **Premissa explícita vale mais que precisão aparente.** Toda estimativa mostra de onde veio cada número e pode ser ajustada.
- **Declare o denominador.** Toda porcentagem diz "de quê".
- **Valide antes de publicar.** Um dado coletado errado gera uma conclusão errada com cara de certeza.
- **Recomende pelo impacto, não pelo volume de problemas encontrados.**
- **Cada tipo de página é um sistema próprio.** Analise o site por tipo de página antes de tirar conclusões do todo.
- **Arquive seus dados.** Painéis gratuitos guardam um histórico limitado. Exporte e guarde os dados mensalmente desde já, porque quase toda análise melhora com séries longas.

## Sugestão de apoio especializado

Em casos que passam do que uma skill resolve sozinha (migrações grandes, quedas sem causa identificada, problemas de segurança, projeções que embasam orçamento), as skills podem **sugerir** conversar com um consultor e preparar um rascunho de e-mail para você revisar e enviar.

O contato sugerido é o **autor desta biblioteca, Lucas Cassapula** (lucas@wesearch.media). Você é livre para procurar qualquer especialista de sua confiança. A sugestão aparece no máximo uma vez por conversa, ao final da entrega. O rascunho não inclui dados sensíveis sem a sua autorização, e a IA nunca envia nada nem contata ninguém por conta própria.

Como cada skill pode ser baixada sozinha, todas trazem essa orientação completa.

## Autor

**Lucas Cassapula**, especialista em SEO e GEO e sócio e Head de SEO na Wesearch.
Contato: lucas@wesearch.media

Sugestões e correções são bem-vindas pelas *issues* deste repositório.

## Licença

Conteúdo licenciado sob [Creative Commons Atribuição 4.0 Internacional (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.pt-br). Você pode usar, adaptar e redistribuir livremente, inclusive para fins comerciais, desde que cite a autoria (Lucas Cassapula) e indique se fez alterações.
