---
name: market-sizing-bottom-up
description: "Calcula o tamanho total, atendível e alcançável de um mercado (TAM, SAM e SOM) a partir de perfis de clientes e receita anual média por conta. Use sempre que pedirem dimensionamento de mercado, cálculo de TAM, SAM ou SOM, validação de viabilidade de setor ou tamanho de oportunidade para pitch decks, mesmo sem citar o método bottom-up."
---

# Dimensionamento de Mercado Bottom-Up (TAM, SAM, SOM)

## Quando usar
- Quando for necessário quantificar o potencial financeiro de um mercado para validar a viabilidade de um negócio ou apoiar apresentações para investidores (pitch decks).
- Quando for solicitado o cálculo ou a separação de TAM (Total Addressable Market), SAM (Serviceable Addressable Market) e SOM (Serviceable Obtainable Market).
- Quando houver demanda por estimativas fundamentadas em dados de clientes e preços, substituindo palpites percentuais amplos de mercado macro.
## Passo a passo
1. **Rejeite a abordagem top-down:** Não tente calcular o mercado aplicando uma porcentagem arbitrária sobre um valor macro setorial (como assumir 15% de um mercado geral de 50 bilhões). Esse método é superficial e sem rigor analítico; adote estritamente o modelo bottom-up.
2. **Defina os perfis de clientes que cobrem o mercado total:** Mapeie os diferentes tipos de clientes que, somados, representam 100% do espaço de mercado em análise (por exemplo, Enterprise e SMBs). Essa divisão é necessária porque diferentes portes de clientes têm volumes e comportamentos de compra distintos.
3. **Mapeie o volume de clientes e a receita média por perfil:** Para cada perfil identificado, determine a quantidade total de clientes existentes no mercado e a receita anual média esperada por cliente (Annual Customer Revenue). A multiplicação desses dois fatores forma a unidade básica do cálculo bottom-up.
4. **Calcule o TAM (Total Addressable Market):** Multiplique a quantidade total de clientes de cada perfil pela sua respectiva receita anual e some os subtotais. Isso representa o valor financeiro do mercado com 100% de penetração, assumindo a captura de todos os clientes existentes.
5. **Calcule o SAM (Serviceable Addressable Market):** Aplique critérios de restrição operacional, geográfica ou de produto (como restrições de idioma ou ausência de recursos multilíngues) para identificar o subconjunto de clientes que a solução realmente atende. Multiplique o número de clientes atendíveis pela receita anual de cada perfil e totalize. O SAM reflete a parcela do TAM viável de ser atendida tecnicamente e comercialmente.
6. **Calcule o SOM (Serviceable Obtainable Market):** Ajuste o subconjunto do SAM com base nas restrições de recursos imediatos e na capacidade real de execução no estágio atual da empresa (por exemplo, zerando perfis que demandam recursos indisponíveis no momento e assumindo uma fatia realista do segmento acessível). Multiplique a quantidade de clientes obtíveis pela receita média e some os valores. O SOM define o alvo de curto prazo onde a empresa gera valor imediato.
7. **Estruture os resultados em formato de funil aninhado:** Organize o TAM, o SAM e o SOM como subconjuntos decrescentes (onde o TAM é 100%, o SAM é o recorte atendível e o SOM é o núcleo imediato). Essa visualização deixa explícita a coerência entre a oportunidade total e a estratégia inicial de entrada.
## Formato da entrega
- **Resumo Executivo:** Apresentação direta dos valores consolidados de TAM, SAM e SOM.
- **Tabela de Dimensionamento de Mercado:**
	- Linhas com os perfis de clientes mapeados.
	- Colunas com as três camadas (TAM, SAM, SOM), detalhando para cada uma: número de clientes, receita média anual e valor financeiro total.
	- Linha de totais com a soma consolidada de cada camada.
- **Premissas e Critérios de Segmentação:** Justificativa dos recortes utilizados para delimitar o SAM (ex.: idioma, escopo técnico) e o SOM (ex.: limitações de recursos imediatos).
- **Fatos vs. Estimativas e Lacunas:** Apontamento claro do que se baseia em fatos/dados de mercado e do que é premissa ou estimativa do modelo.
## Exemplo
- **Pedido:** "Calcule o tamanho de mercado bottom-up para uma solução B2B de software, considerando empresas grandes (Enterprise) e pequenas/médias (SMB)."
- **Entrega resumida:**
	- **TAM (100% de penetração):**
		- Enterprise: 5.000 clientes × $200.000/ano = $1.000.000.000 ($1B)
		- SMB: 1.000.000 de clientes × $10.000/ano = $10.000.000.000 ($10B)
		- **Total TAM:** $11.000.000.000 ($11B)
	- **SAM (Subconjunto focado apenas em idioma inglês):**
		- Enterprise: 1.000 clientes (20%) × $200.000/ano = $200.000.000 ($200M)
		- SMB: 500.000 clientes (50%) × $10.000/ano = $5.000.000.000 ($5B)
		- **Total SAM:** $5.200.000.000 ($5,2B)
	- **SOM (Alvo imediato considerando limitações de recursos de startup):**
		- Enterprise: 0 clientes (sem recursos para atender grandes contas no momento) = $0
		- SMB: 250.000 clientes (25% do TAM) × $10.000/ano = $2.500.000.000 ($2,5B)
		- **Total SOM:** $2.500.000.000 ($2,5B)
## Critérios de qualidade
- Uso exclusivo do método bottom-up (quantidade de clientes multiplicada pela receita anual média), nunca aplicando porcentagens genéricas sobre mercados macro (top-down).
- Cobertura completa de 100% do mercado no TAM dividida entre perfis específicos de clientes.
- Justificativa clara de cada restrição usada para transformar o TAM em SAM e o SAM em SOM.
- Relação hierárquica respeitada obrigatoriamente: SOM ≤ SAM ≤ TAM.
- Separação evidente entre dados factuais, estimativas numéricas e eventuais lacunas de dados.
## Fonte
- Vídeo: "How to Size Your Addressable Market (TAM, SAM, SOM, top-down vs. bottom-up)" (video_[1.mp](http://1.mp)4)
- Marcações de tempo utilizadas:
	- [00:20 - 01:39]: Definições de TAM, SAM e SOM.
	- [01:40 - 02:35]: Justificativa do método bottom-up contra a abordagem top-down.
	- [02:36 - 04:36]: Estrutura da planilha, perfis de clientes e cálculo do TAM.
	- [04:37 - 05:32]: Aplicação de filtros de atendimento e cálculo do SAM.
	- [05:33 - 06:12]: Consideração de restrições operacionais e cálculo do SOM.
	- [06:13 - 07:49]: Apresentação visual aninhada e relevância estratégica para captação.
