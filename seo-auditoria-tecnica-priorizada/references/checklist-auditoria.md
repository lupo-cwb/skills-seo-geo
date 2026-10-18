# Checklist de auditoria técnica

Cada item traz **o que verificar**, **como verificar** e a **prioridade sugerida** (1 a 5) caso haja problema. Ajuste a prioridade ao contexto: um item de prioridade 3 pode virar 1 se afetar a principal fonte de receita.

Avalie cada item **por contexto** (blog, loja, institucional etc.) e, quando fizer sentido, **por template**.

---

## 1. Rastreio e acesso

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 1.1 | `robots.txt` acessível, retornando 200, sem bloquear seções importantes | Abrir o arquivo; testar URLs-chave de cada template contra as regras | 1 |
| 1.2 | Regras de robots com escopo correto (curingas, posição de parâmetros, `?` × `&`) | Testar a URL completa contra cada regra | 1 |
| 1.3 | Recursos de renderização (JS, CSS, imagens) não bloqueados | Listar recursos das páginas-chave e testar contra o robots | 2 |
| 1.4 | Sitemap declarado no `robots.txt` | Leitura direta | 4 |
| 1.5 | Robôs de busca e de IA não bloqueados por firewall, CDN ou proteção antibot | Inspeção de URL ao vivo e estatísticas de rastreio do painel do buscador; logs com robôs verificados por IP; sem logs, os relatórios de robôs dos planos gratuitos de CDN ou firewall, quando houver. Sem nenhuma dessas fontes, marque os robôs de IA como não verificados. Uma requisição só trocando o user agent não basta, porque firewalls costumam validar o robô pelo IP | 1 |
| 1.6 | Política para robôs de IA definida por categoria: **busca/citação** (bloquear reduz citações nas respostas), **treinamento** (bloquear não remove necessariamente das respostas com fonte) e **agentes e acessos acionados pelo usuário** (buscas em tempo real feitas quando o usuário pede; alguns operadores declaram que esses acessos podem não seguir o robots.txt, e o controle efetivo fica no firewall) | Revisar as regras por user agent no robots e no firewall e conferir se refletem uma decisão de negócio documentada | 1 se o bloqueio dos robôs de busca for não intencional; 3 se for política deliberada |
| 1.7 | Espaços infinitos controlados (filtros, ordenações, calendários, busca interna) | Rastreio: padrões de URL com explosão de combinações | 2 |
| 1.8 | Parâmetros de sessão ou rastreamento não geram URLs indexáveis | Rastreio e cobertura: URLs com parâmetros | 2 |
| 1.9 | Profundidade de clique das páginas importantes razoável a partir da home | Rastreio: distribuição de profundidade por template | 3 |
| 1.10 | Logs: robôs gastam rastreio nas páginas certas | Logs filtrados por robô verificado, agrupados por template | 3 |
| 1.11 | Tempo de resposta do servidor estável para robôs | Logs ou relatório de estatísticas de rastreio | 3 |
| 1.12 | Respostas de IA na própria página de resultados não confundidas com assistentes externos: elas dependem do robô principal de busca e das diretivas de snippet | Revisar se alguma regra pensada para IA afeta o robô principal | 1 se alguma regra afetar o robô principal; n/a se não |

## 2. Indexação

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 2.1 | Páginas importantes indexáveis (200, sem noindex, canonical para si mesmas) | Rastreio por template | 1 |
| 2.2 | Sem `noindex` indevido (meta tag ou cabeçalho HTTP) | Rastreio, incluindo cabeçalhos | 1 |
| 2.3 | Páginas sem valor com noindex ou fora do índice (busca interna, filtros sem demanda, obrigado, área logada) | Rastreio e cobertura | 3 |
| 2.4 | Proporção indexadas ÷ enviadas por sitemap saudável, com motivos de exclusão entendidos | Relatório de cobertura por sitemap | 2 |
| 2.5 | "Rastreada, mas não indexada" e "Descoberta, mas não indexada" investigadas por template | Cobertura: amostras por motivo | 2 |
| 2.6 | Soft 404 (página vazia ou de erro retornando 200) | Cobertura e rastreio: páginas com pouco conteúdo e status 200 | 2 |
| 2.7 | Homologação, preview e ambientes de teste bloqueados e fora do índice | Busca pelo domínio de homologação; robots e autenticação | 1 |

## 3. Sitemaps

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 3.1 | Sitemaps contêm só URLs canônicas, indexáveis e com 200 | Cruzar sitemap × rastreio | 2 |
| 3.2 | Todas as páginas importantes estão em algum sitemap | Cruzar páginas com impressão × sitemap | 3 |
| 3.3 | Sem sobreposição relevante entre sitemaps | Contar URLs duplicadas entre arquivos | 4 |
| 3.4 | Data de modificação reflete mudança real | Comparar com a data de atualização do conteúdo | 4 |
| 3.5 | Separação por tipo de página, que facilita o diagnóstico de cobertura | Estrutura do índice de sitemaps | 4 |
| 3.6 | Tamanho e formato válidos (limite de URLs e de bytes, compressão, codificação) | Validação do arquivo | 3 |

## 4. Canonicalização e duplicidade

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 4.1 | Um host canônico (com ou sem www, https) com os demais redirecionando em 301 | Requisitar as variações de host e protocolo | 1 |
| 4.2 | Canonical, sitemap, links internos e hreflang apontam para o mesmo host e formato de URL | Rastreio | 1 |
| 4.3 | Canonicals autorreferentes nas páginas indexáveis | Rastreio por template | 2 |
| 4.4 | Canonical não aponta para URL redirecionada, com erro ou noindex | Rastreio: status do destino do canonical | 2 |
| 4.5 | Barra final, maiúsculas e parâmetros consolidados | Rastreio: variações da mesma URL | 3 |
| 4.6 | Variações de produto (cor, tamanho) com estratégia definida de canonical ou indexação | Revisão por template de produto | 2 |
| 4.7 | Paginação com URLs próprias, rastreáveis e sem canonical para a página 1 | Rastreio de listagens | 3 |
| 4.8 | Conteúdo duplicado ou quase duplicado entre páginas | Rastreio: similaridade de conteúdo e títulos | 3 |

## 5. Redirecionamentos e status

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 5.1 | Sem cadeias nem loops de redirecionamento | Rastreio | 2 |
| 5.2 | Redirecionamentos permanentes (301 ou 308) onde a mudança é definitiva | Rastreio | 3 |
| 5.3 | Links internos apontam direto para o destino final, não para redirecionamento | Rastreio: links internos com 3xx | 3 |
| 5.4 | Links internos sem 404 ou 5xx | Rastreio | 2 |
| 5.5 | Páginas removidas com links externos redirecionadas para o equivalente real (mesmo tema e intenção); sem equivalente, 404 ou 410 | Cruzar 404 × links externos | 2 |
| 5.6 | Página 404 real (status 404) e útil para o usuário | Requisitar URL inexistente | 3 |
| 5.7 | Erros 5xx monitorados | Logs e relatórios de rastreio | 1 |

## 6. Arquitetura e linkagem interna

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 6.1 | Hierarquia clara (home > categoria > subcategoria > item) refletida em links e URLs | Rastreio e revisão da navegação | 3 |
| 6.2 | Páginas órfãs (sem links internos) | Cruzar sitemap e impressões × rastreio | 2 |
| 6.3 | Páginas estratégicas recebem links internos proporcionais à importância | Rastreio: links recebidos por página | 3 |
| 6.4 | Links de navegação em HTML rastreável (`<a href>`), não só em JavaScript | HTML cru | 2 |
| 6.5 | Breadcrumbs presentes e coerentes com a hierarquia | Revisão por template | 4 |
| 6.6 | Conteúdo informacional linka para páginas de negócio | Links no corpo do conteúdo | 3 |
| 6.7 | Texto âncora descritivo | Rastreio: âncoras internas | 4 |
| 6.8 | URLs legíveis, estáveis e sem parâmetros desnecessários | Revisão de padrões | 4 |
| 6.9 | Links internos sem `nofollow` desnecessário | Rastreio: links internos com nofollow | 3 |

## 7. On-page por template

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 7.1 | Título único, descritivo e com o termo principal, sem duplicação por template | Rastreio: títulos duplicados, vazios ou longos | 3 |
| 7.2 | Meta description presente e única nas páginas importantes | Rastreio | 4 |
| 7.3 | Um H1 claro, coerente com o título | Rastreio | 4 |
| 7.4 | Estrutura de headings lógica | Rastreio e amostra | 5 |
| 7.5 | Conteúdo principal suficiente nas páginas de listagem e produto (não só grade de itens) | Amostra por template | 3 |
| 7.6 | Imagens com texto alternativo, nomes descritivos, formatos modernos e dimensões definidas | Rastreio de imagens | 4 |
| 7.7 | Idioma declarado no HTML | HTML | 4 |
| 7.8 | Diretivas de snippet (`nosnippet`, `max-snippet`, `data-nosnippet`) aplicadas só onde é intencional, porque limitam o que aparece no resultado e nas respostas geradas na SERP | Rastreio: meta robots e atributos | 2 |

## 8. Renderização e JavaScript

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 8.1 | Conteúdo principal presente no HTML cru ou renderizado de forma confiável | Comparar código-fonte × DOM renderizado | 2 |
| 8.2 | Título, canonical, robots e dados estruturados no HTML cru e não alterados por JS de forma conflitante | Comparar cru × renderizado | 2 |
| 8.3 | Links internos descobertos sem interação (sem depender de clique ou rolagem infinita) | DOM renderizado sem interação | 2 |
| 8.4 | Conteúdo carregado por rolagem infinita tem paginação acessível | Revisão de listagens | 3 |
| 8.5 | Robôs de IA (que em geral não executam JavaScript) recebem o conteúdo no HTML | HTML cru das páginas-chave | 2 |

## 9. Dados estruturados

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 9.1 | Tipos adequados ao template (organização, produto, oferta, avaliação, artigo, breadcrumb, FAQ, local). A marcação ajuda a máquina a entender a página, mas não garante resultado enriquecido; alguns tipos, como FAQ, hoje têm exibição restrita | Extração de dados estruturados por template | 4 |
| 9.2 | Marcação válida e sem erros | Validador de dados estruturados | 3 |
| 9.3 | Marcação coerente com o conteúdo visível (preço, disponibilidade, avaliações) | Comparar marcação × página | 3 |
| 9.4 | Entidade da organização consistente (nome, logo, perfis oficiais) | Home e páginas institucionais | 4 |

## 10. Performance e experiência

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 10.1 | Métricas de experiência de campo (carregamento, interatividade, estabilidade visual) dentro dos limites recomendados, por template | Dados de experiência real, por URL ou grupo | 3 |
| 10.2 | Template com pior resultado identificado e causa provável | Agrupar por template; testes de laboratório para diagnóstico | 3 |
| 10.3 | Imagens e recursos pesados otimizados; carregamento adiado do que está fora da tela | Testes de laboratório | 4 |
| 10.4 | Cobertura dos dados de campo declarada (nem toda URL tem dado) | Contar URLs com dado | n/a |

## 11. Mobile

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 11.1 | Conteúdo, links e dados estruturados equivalentes entre mobile e desktop | Comparar as duas versões | 2 |
| 11.2 | Layout responsivo, sem elementos fora da tela e com áreas de toque adequadas | Revisão em viewport mobile | 3 |
| 11.3 | Intersticiais e pop-ups não bloqueiam o conteúdo principal | Revisão em mobile | 3 |

## 12. Internacionalização (se aplicável)

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 12.1 | Hreflang com retorno recíproco, códigos válidos e x-default | Rastreio de hreflang | 2 |
| 12.2 | Hreflang aponta para URLs canônicas e indexáveis | Rastreio | 2 |
| 12.3 | Sem redirecionamento automático por IP que impeça robôs de ver outras versões | Requisitar de diferentes origens | 2 |

## 13. Segurança e protocolo

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 13.1 | HTTPS em todo o site, com HTTP redirecionando | Requisitar versão HTTP | 2 (1 se as versões HTTP e HTTPS estiverem indexadas em duplicidade ou houver alerta de segurança no navegador) |
| 13.2 | Sem conteúdo misto (recursos HTTP em páginas HTTPS) | Rastreio de recursos | 4 |
| 13.3 | Certificado válido em todos os hosts e subdomínios públicos | Verificação de certificado | 1 |
| 13.4 | Sem sinais de invasão, spam injetado ou páginas desconhecidas indexadas | Busca pelo domínio; relatórios de segurança do buscador | 1 |
| 13.5 | Sem ações manuais (penalidades) aplicadas pelo buscador | Seção de ações manuais do painel do buscador | 1 |

## 14. Local (se aplicável)

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 14.1 | Páginas de unidade ou localidade com conteúdo próprio (não só troca de nome da cidade) | Amostra de páginas locais | 3 |
| 14.2 | Nome, endereço e telefone consistentes entre site, perfis locais e diretórios | Comparação | 3 |
| 14.3 | Dados estruturados de negócio local nas páginas de unidade | Extração | 4 |

## 15. E-commerce e produtos (se aplicável)

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 15.1 | Dados de produto (nome, preço, disponibilidade, avaliações, identificadores) completos e no HTML cru | Amostra de páginas de produto: código-fonte e dados estruturados | 2 |
| 15.2 | Feed de produtos enviado às listagens gratuitas do buscador, sem reprovações relevantes | Painel do buscador e central de produtos gratuita | 2 |
| 15.3 | Preço e disponibilidade coerentes entre página, dados estruturados e feed | Comparar as três fontes numa amostra | 2 |
| 15.4 | Produtos esgotados ou descontinuados com tratamento definido (manter com aviso, redirecionar para equivalente real ou 404/410) | Amostra e regra do CMS | 3 |

## 16. Pós-deploy e migração

| # | Item | Como verificar | Prioridade |
|---|---|---|---|
| 16.1 | Host canônico configurado resolve e responde | DNS e requisição | 1 |
| 16.2 | Robots, canonical e sitemap no host definitivo e coerentes entre si | Leitura direta | 1 |
| 16.3 | Produção indexável; homologação e preview bloqueados | Testar os dois ambientes | 1 |
| 16.4 | Mapa de redirecionamentos de URL antiga → equivalente real nova, em um salto, sem envio em massa para a home | Testar amostra do mapa | 1 |
| 16.5 | Títulos, canonicals e dados estruturados preservados nos novos templates | Comparar antes × depois | 2 |
| 16.6 | Cobertura e desempenho monitorados no período seguinte, com janela definida pelo usuário | Relatórios do buscador | 2 |
