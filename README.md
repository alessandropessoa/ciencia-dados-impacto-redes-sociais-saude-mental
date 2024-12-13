# ciencia-dados-impacto-redes-sociais-saude-mental
Projeto aplicado do disciplina Aprendizado de Máquina para Saúde do curso de pós graduação strictu sensu (mestrado) em Ciência da Computação. 


Pasta dos datasets: <a href="https://drive.google.com/drive/folders/1Wii-Y_hYjB8jCbJWy3HAvgT7iHDaZxyQ?usp=drive_link">Datasets gerados</a>

Código COLAB:  <a href="https://colab.research.google.com/drive/1M1Ywpn6wJGW8Lq-7XdpK0ucxcSsfW85_?usp=sharing">Codigo</a>

Introdução

As redes sociais têm se consolidado como um elemento central na vida cotidiana dos brasileiros, influenciando desde as interações interpessoais até o consumo de informações e entretenimento. Segundo levantamento da Comscore, o tempo dedicado às redes sociais no Brasil cresceu 31% entre janeiro de 2020 e o final de 2023, alcançando impressionantes 356 bilhões de minutos. Em dezembro de 2023, cada usuário passou, em média, 46 horas conectados a essas plataformas, superando o tempo investido em sites de entretenimento, varejo e serviços financeiros online [1].
Esse comportamento, embora represente um avanço tecnológico e social, também levanta preocupações sobre seu impacto na saúde mental dos indivíduos. Estudos têm associado o uso excessivo de redes sociais a problemas como ansiedade, depressão e dificuldade para dormir, especialmente quando esse consumo não é direcionado por um propósito específico [2]. A necessidade de compreender as nuances dessa relação motivou este estudo, que busca investigar possíveis correlações entre o tempo gasto nas mídias sociais e a saúde mental, utilizando abordagens baseadas em machine learning para identificar grupos de risco.
O presente trabalho enfrentou diversos desafios, desde a coleta e qualidade dos dados até questões éticas relacionadas à privacidade e ao uso responsável das informações pessoais. Para isso, foi conduzida uma pesquisa piloto intitulada “Pesquisa Impacto das redes sociais na saúde mental”, realizada com 57 participantes recrutados via WhatsApp entre os dias 16 e 18 de novembro de 2024. Apesar de seu caráter exploratório, essa pesquisa permitiu consolidar regras de negócio e compreender melhor as variáveis relevantes para o estudo. È importante ressaltar que a  pesquisa teve um caráter piloto, servindo como importante vetor de consolidação do entendimento das regras de negócio, não tendo sido submetida a CEP (comissão de ética de pesquisa) devido a morosidade do processo que tornaria inexequível para o tempo.
Ao propor soluções que combinam ciência de dados e preocupações éticas, este trabalho busca não apenas compreender os efeitos das redes sociais na saúde mental, mas também contribuir para um uso mais saudável dessas plataformas, promovendo o bem-estar emocional de seus usuários.

Formalização matemática

Após encerrar o período de coleta da pesquisa realizada via Whatsapp do autor  por intermédio do google forms, foi obtida uma amostra aleatória simples de 57 pessoas de diversas idades e estados brasileiro, sendo mais da metade de cidades do estado Rio de Janeiro. Neste sentido essa é uma amostra mínima representativa de uma população de tamanho 2000 pessoas, cujo  os parâmetros são: nível de confiança de 95%, margem de erro de 15%, proporção amostral de  50%. O calculo foi uma estimativa feita levando em conta o desconhecimento do numero exato do tamanho populacional da rede social coletada (população infinita ), em outras palavras a estimativa da população foi feita a partir do numero da amostra conforme Figura 01.







			      Figura 01 - Calculadora de tamanho de amostra 

https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/distribuicaoNomalSkew.png
 
		
			Fonte: Calculator.io (2024). Disponível em: https://www.calculator.io/pt/calculadora-de-tamanho-da-amostra/?utm_source=chatgpt.com. Acesso em: 10 dez. 2024.

Foi necessário saber o tamanho máximo da população que poderia ser utilizados para uma margem de erro mínima tendo uma amostra de 57 pessoas, para se obter máxima robustez na geração de dados sintéticos a partir das CTGAN’s, que construiu uma população baseado nos dados tabulares da amostra da pesquisa, preservando as características estatísticas e relacionais do dados reais.

Os dados faltantes foram preprocessados antes de servirem de insumo para o modelo CTGAN, e as colunas que possuíam dados faltantes foram substituídas pela mediana no caso de dados quantitativo e pela moda no caso de dados qualitativos  preservando as características de distribuição estatística, observando o teorema central do limite, visando mitigar a potencialização de assimetrias nestas colunas, conforme.
	
		Figura 2 - Medidas de posição: média aritmética, moda e mediana 

Fonte: Lecursos (2024). Disponível em: https://lecursos.com/pt-br/articles/medidas-de-posicao-media-aritmetica-moda-e-mediana. Acesso em: 10 dez. 2024. 

A modelagem foi estruturada em três etapas principais, cada uma utilizando técnicas específicas para atender aos objetivos da pesquisa:
    1. Clusterização com K-Means e DBScan: Esses modelos foram aplicados para identificar possíveis agrupamentos nos dados, permitindo compreender padrões subjacentes e comportamentos semelhantes entre os respondentes.
    2. Redução de Dimensionalidade com PCA: O método de Análise de Componentes Principais (PCA) foi utilizado para avaliar a relevância de cada variável (feature) e determinar o número mínimo de variáveis que explicassem, no mínimo, 80% da variabilidade dos dados. Essa abordagem ajudou a simplificar o conjunto de dados, mantendo a maior parte da informação relevante.
    3. Modelagem com Regressão Logística: Por fim, a regressão logística foi empregada para explorar o impacto das redes sociais na saúde mental. A variável resposta utilizada como alvo foi derivada da pergunta da pesquisa: "Qual o impacto que você acredita que as redes sociais causam em você?" (escalonada de 1, muito negativo, a 5, muito positivo). Essa variável permitiu modelar a relação entre as características dos participantes e suas percepções sobre os impactos das redes sociais.
Com essa abordagem, foi possível combinar técnicas de aprendizado de máquina e estatística para analisar, reduzir e interpretar os dados, alinhando os métodos aos objetivos da pesquisa.








Referências:

1 .O GLOBO. Brasil é o terceiro país que mais consome redes sociais. O Globo, Rio de Janeiro, 24 mar. 2023. Disponível em: https://oglobo.globo.com/economia/tecnologia/noticia/2023/03/brasil-e-o-terceiro-pais-que-mais-consome-redes-sociais.ghtml. Acesso em: 08 dez. 2024.

2.SOUZA, Karlla; CUNHA, Mônica Ximenes Carneiro da. Impactos do uso das redes sociais virtuais na saúde mental dos adolescentes: uma revisão sistemática da literatura. Revista Eletrônica do Instituto Federal de Educação, Ciência e Tecnologia de Alagoas, v. 3, n. 3, p. 1-15, 2023. DOI: https://doi.org/10.37444/issn-2594-5343.v3i3.156. Disponível em: https://doi.org/10.37444/issn-2594-5343.v3i3.156. Acesso em: 10 dez. 2024.

