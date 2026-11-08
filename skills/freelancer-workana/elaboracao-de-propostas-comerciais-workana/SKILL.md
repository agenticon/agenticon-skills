---
name: elaboracao-de-propostas-comerciais-workana
description: "Elabora propostas comerciais a partir da URL de um projeto publicado na Workana: lê as informações do projeto pela URL, escreve a proposta e gera um arquivo PDF ao final. Use sempre que pedirem proposta, orçamento ou resposta a projeto com um link da Workana, e quando pedirem o PDF da proposta, mesmo sem dizer o nome do método. Não serve para negociar fora da plataforma nem para executar o serviço."
---

# Elaboração de Propostas Comerciais na Workana

## Quando usar
- Quando o pedido trouxer o texto de um projeto publicado na Workana (junto com a URL de referência) e pedir proposta, orçamento ou resposta comercial.
- Quando o pedido pedir o PDF da proposta.
- Quando for preciso revisar uma proposta já escrita para um projeto da Workana.
Não use esta skill para negociar valores ou condições fora da plataforma, nem para executar o serviço contratado.
## Passo a passo
1. **Confirme a entrada.** A entrada principal é o texto do projeto colado pelo humano (título, descrição, orçamento, prazo e, se houver, dados do contratante). Peça também a URL do projeto na Workana (domínio [workana.com](http://workana.com) com caminho de projeto), que serve como referência para citar no PDF e no nome do arquivo. O porquê: as páginas de projetos na Workana exigem login para exibir os dados completos, de modo que a proposta depende do texto colado pelo usuário.
2. **Obtenha os dados do projeto.** Use o texto colado como fonte dos dados. Só tente ler a URL com firecrawl_scrape se o texto não vier; se a leitura trouxer só a página de login, pare e peça ao humano para colar o texto do projeto, sem inventar dados. Se faltar orçamento ou prazo no texto, escreva a proposta assim mesmo, marcando esses campos como "a confirmar", e liste-os nas lacunas. O porquê: a proposta precisa refletir o que o cliente de fato publicou, sem suposições.
3. **Verifique a aderência e o histórico.** Compare o projeto com as competências que você entrega. Se o projeto estiver fora do nicho ou o contratante tiver histórico ruim, informe o motivo e recomende não enviar, ou enviar com escopo mais protegido. O porquê: enviar menos propostas, mas mais direcionadas, converte melhor.
4. **Diagnostique a necessidade.** Identifique a dor principal, o resultado esperado e as dúvidas em aberto. Liste de duas a três perguntas que ajudariam a fechar o escopo. O porquê: mostrar leitura atenta do projeto pesa mais que qualquer afirmação genérica.
5. **Consulte a base apenas para completar lacunas.** Use a base aprovada da Agenticon para padrões de escopo, prazo e precificação que o projeto não cobre. Cite título e data de aprovação. Se a base contradisser uma diretriz deste guia, siga a diretriz.
6. **Escreva a proposta.** Use esta ordem:
	- Entendimento do problema, em uma ou duas frases na linguagem do cliente.
	- Solução proposta, com as etapas principais.
	- Escopo e entregáveis, sem itens ambíguos.
	- Prazo e forma de acompanhamento.
	- Valor, com o que está incluído.
	- Próximo passo concreto, como responder às dúvidas.
	O porquê: o cliente decide mais rápido quando entende o que recebe e o que acontece depois.
7. **Revise contra as regras da plataforma.** Confirme que a proposta:
	- não contém e-mail, telefone, links externos, perfis em redes sociais ou qualquer forma de contato fora da plataforma;
	- não menciona taxas ou comissões da plataforma;
	- não oferece trabalho gratuito;
	- não sugere pagamento fora da plataforma;
	- mantém linguagem profissional e focada no escopo.
	O porquê: propostas que descumprem essas regras podem ser removidas e prejudicar a conta. Vale também para o PDF.
8. **Gere o PDF ao final.** Só depois de revisada a proposta, monte um documento com título do projeto, URL de origem, data e texto da proposta. Dê ao arquivo o nome proposta-[identificador-do-projeto].pdf, usando o identificador extraído da URL. Se não houver ferramenta disponível para criar arquivos PDF no ambiente, não invente um arquivo: entregue o texto final formatado para exportação e registre a lacuna. O porquê: o arquivo precisa existir de fato e não pode ser simulado.
9. **Faça a checagem final.** Confirme que o texto está claro e objetivo, que os dados do projeto estão corretos, que as fontes de dados de mercado estão citadas e que os fatos foram separados das estimativas.
## Formato da entrega
- Arquivo PDF da proposta com o nome definido no passo 8, ou o texto formatado para exportação, se o PDF não puder ser gerado.
- Resumo dos dados lidos do projeto: título, orçamento, prazo e URL.
- Lista curta com os pontos fortes da abordagem.
- Lacunas: informações do projeto que faltaram e, se for o caso, o motivo de o PDF não ter sido gerado.
## Exemplo
Pedido: "Faça a proposta em PDF para este projeto da Workana (link: [https://www.workana.com/job/exemplo-de-projeto](https://www.workana.com/job/exemplo-de-projeto)):
Título: Atendimento automatizado no site
Descrição: Precisamos integrar um bot de atendimento no nosso site institucional.
Orçamento: R$ 1.500
Prazo: 2 semanas"
Entrega esperada: arquivo proposta-exemplo-de-projeto.pdf, com a proposta completa, e resumo: "Projeto de atendimento automatizado no site, orçamento e prazo obtidos do texto informado. Pontos fortes: escopo em etapas, entregáveis claros e próximo passo definido. Lacunas: volume mensal de atendimentos não informado no projeto."
## Critérios de qualidade
- O texto colado pelo humano foi usado como fonte primária dos dados, e a URL foi usada como referência no PDF e no nome do arquivo.
- Se faltaram orçamento ou prazo, foram marcados como "a confirmar" na proposta e registrados nas lacunas.
- A proposta mostra que o escopo foi lido com atenção.
- Cada entregável é concreto e verificável.
- Nenhuma regra da plataforma foi descumprida, nem no texto nem no PDF.
- O PDF existe de fato, ou a lacuna está declarada.
- Dados de mercado têm fonte, e estimativas são identificadas como estimativas.
