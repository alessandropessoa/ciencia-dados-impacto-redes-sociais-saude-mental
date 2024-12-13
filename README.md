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

![Texto Alternativo](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/formulaTamanhoAmostral.png)
 
		
			Fonte: Calculator.io (2024). Disponível em: https://www.calculator.io/pt/calculadora-de-tamanho-da-amostra/?utm_source=chatgpt.com. Acesso em: 10 dez. 2024.

Foi necessário saber o tamanho máximo da população que poderia ser utilizados para uma margem de erro mínima tendo uma amostra de 57 pessoas, para se obter máxima robustez na geração de dados sintéticos a partir das CTGAN’s, que construiu uma população baseado nos dados tabulares da amostra da pesquisa, preservando as características estatísticas e relacionais do dados reais.

Os dados faltantes foram preprocessados antes de servirem de insumo para o modelo CTGAN, e as colunas que possuíam dados faltantes foram substituídas pela mediana no caso de dados quantitativo e pela moda no caso de dados qualitativos  preservando as características de distribuição estatística, observando o teorema central do limite, visando mitigar a potencialização de assimetrias nestas colunas, conforme Figura 02.
	
		Figura 2 - Medidas de posição: média aritmética, moda e mediana 
![Texto Alternativo](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/distribuicaoNomalSkew.png)

Fonte: Lecursos (2024). Disponível em: https://lecursos.com/pt-br/articles/medidas-de-posicao-media-aritmetica-moda-e-mediana. Acesso em: 10 dez. 2024. 

A modelagem foi estruturada em três etapas principais, cada uma utilizando técnicas específicas para atender aos objetivos da pesquisa:
    1. Clusterização com K-Means e DBScan: Esses modelos foram aplicados para identificar possíveis agrupamentos nos dados, permitindo compreender padrões subjacentes e comportamentos semelhantes entre os respondentes.
    2. Redução de Dimensionalidade com PCA: O método de Análise de Componentes Principais (PCA) foi utilizado para avaliar a relevância de cada variável (feature) e determinar o número mínimo de variáveis que explicassem, no mínimo, 80% da variabilidade dos dados. Essa abordagem ajudou a simplificar o conjunto de dados, mantendo a maior parte da informação relevante.
    3. Modelagem com Regressão Logística: Por fim, a regressão logística foi empregada para explorar o impacto das redes sociais na saúde mental. A variável resposta utilizada como alvo foi derivada da pergunta da pesquisa: "Qual o impacto que você acredita que as redes sociais causam em você?" (escalonada de 1, muito negativo, a 5, muito positivo). Essa variável permitiu modelar a relação entre as características dos participantes e suas percepções sobre os impactos das redes sociais.
Com essa abordagem, foi possível combinar técnicas de aprendizado de máquina e estatística para analisar, reduzir e interpretar os dados, alinhando os métodos aos objetivos da pesquisa.

Gráficos da Pesquisa
![Image 25](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/idade_barras.png)
![Image 26](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/genero_piza.png)
![Image 27](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/tempo%20medio%20nas%20redes%20sociais%20horas%20por%20dia.png)
![Image 1](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Distribui%C3%A7%C3%A3o%20Geogr%C3%A1fica%20dos%20Participantes%20por%20Cidade%20de%20Resid%C3%AAncia_barras.png) 
![Image 2](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Distribui%C3%A7%C3%A3o%20da%20Dificuldade%20de%20Concentra%C3%A7%C3%A3o%20entre%20os%20Participantes%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Pouca%20Dificuldade%2C%205%20%3D%20Muita%20Dificuldade).png)
![Image 3](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Distribui%C3%A7%C3%A3o%20da%20Facilidade%20de%20Distra%C3%A7%C3%A3o%20entre%20os%20Participantes%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205.png)
![Image 4](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20com%20que%20os%20Participantes%20Buscam%20Valida%C3%A7%C3%A3o%20por%20Meio%20de%20'Curtidas'%20nas%20M%C3%ADdias%20Sociais%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Nenhum%2C%205%20%3D%20Muito).png)
![Image 5](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20com%20que%20os%20Participantes%20Relatam%20Sentir-se%20Deprimidos%20em%20uma%20Escala%20de%20Likert%20de%200%20a%205%20(0%20%3D%20Nunca%20%2C%205%20%3D%20Sempre).png)
![Image 6](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20com%20que%20os%20Participantes%20Relatam%20Utilizar%20Redes%20Sociais%20Sem%20Um%20Proposito%20Especifico%2C%20em%20uma%20Escala%20de%20Likert%20de%200%20a%205%20%20(0%20%3D%20Nunca%20%2C%205%20%3D%20Sempre).png)
![Image 7](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20de%20Compara%C3%A7%C3%A3o%20com%20Pessoas%20de%20Sucesso%20por%20Meio%20das%20Redes%20Sociais%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20%20(1%20%3D%20Pouco%20%2C%205%20%3D%20Muito).png)
![Image 8](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20de%20Distra%C3%A7%C3%A3o%20com%20Redes%20Sociais%20durante%20Atividades%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Pouco%2C%205%20%3D%20Muito).png)
![Image 9](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Frequ%C3%AAncia%20de%20Uso%20de%20Plataformas%20de%20M%C3%ADdia%20Social%20pelos%20Participantes.png)
![Image 10](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Identidade%20de%20G%C3%AAnero%20dos%20Participantes%20da%20Pesquisa.png)
![Image 11](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Impacto%20Psicol%C3%B3gico%20de%20Receber%20Poucos%20'Likes'%20nas%20Postagens%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Mal%20%2C%205%20%3D%20Bem).png)
![Image 12](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Impacto%20Psicol%C3%B3gico%20de%20Receber%20Poucos%20'Likes'%20nas%20Postagens%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Mal%2C%205%20%3D%20Bem).png)
![Image 13](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Percep%C3%A7%C3%A3o%20dos%20Participantes%20sobre%20o%20Impacto%20das%20Redes%20Sociais%20em%20uma%20Escala%20de%20Likert%20de%201%20a%205%20(1%20%3D%20Muito%20Negativo%2C%205%20%3D%20Muito%20Positivo).png)
![Image 14](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Preval%C3%AAncia%20de%20Diagn%C3%B3sticos%20de%20Condi%C3%A7%C3%B5es%20de%20Sa%C3%BAde%20Mental%20entre%20os%20Participantes.png)
![Image 15](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20%20dos%20Participantes%20que%20Acreditam%20Passar%20Mais%20Tempo%20Nas%20Redes%20Sociais%20dp%20Gostariam.png)
![Image 16](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20da%20Percep%C3%A7%C3%A3o%20dos%20Participantes%20sobre%20o%20Impacto%20do%20Uso%20das%20Redes%20Sociais%20no%20Humor%20(Positivo%20vs.%20Negativo).png)
![Image 17](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20da%20Renda%20Mensal%20Bruta%20dos%20Participantes%20em%20Rela%C3%A7%C3%A3o%20ao%20Custo%20de%20Vida.png)
![Image 18](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20das%20Rea%C3%A7%C3%B5es%20dos%20Participantes%20a%20Coment%C3%A1rios%20Negativos%20ou%20Cr%C3%ADticas%20em%20Suas%20Postagens.png)
![Image 19](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20Empregados%20e%20Desempregados%20na%20Pesquisa.png)
![Image 20](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20Relatando%20Diferentes%20N%C3%ADveis%20de%20Dificuldade%20para%20Dormir.png)
![Image 21](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20em%20Rela%C3%A7%C3%A3o%20a%20Pratica%20de%20Esporte.png)
![Image 22](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20por%20Religi%C3%A3o%20Declarada.png)
![Image 23](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20que%20Declararam%20Possuir%20Religi%C3%A3o.png)
![Image 24](https://github.com/alessandropessoa/ciencia-dados-impacto-redes-sociais-saude-mental/blob/main/Propor%C3%A7%C3%A3o%20de%20Participantes%20que%20Relataram%20Sentimentos%20de%20Inveja%20ou%20Inferioridade%20ao%20se%20Compararem%20com%20Outras%20Pessoas%20nas%20Redes%20Sociais.png)


Referências:

1 .O GLOBO. Brasil é o terceiro país que mais consome redes sociais. O Globo, Rio de Janeiro, 24 mar. 2023. Disponível em: https://oglobo.globo.com/economia/tecnologia/noticia/2023/03/brasil-e-o-terceiro-pais-que-mais-consome-redes-sociais.ghtml. Acesso em: 08 dez. 2024.

2.SOUZA, Karlla; CUNHA, Mônica Ximenes Carneiro da. Impactos do uso das redes sociais virtuais na saúde mental dos adolescentes: uma revisão sistemática da literatura. Revista Eletrônica do Instituto Federal de Educação, Ciência e Tecnologia de Alagoas, v. 3, n. 3, p. 1-15, 2023. DOI: https://doi.org/10.37444/issn-2594-5343.v3i3.156. Disponível em: https://doi.org/10.37444/issn-2594-5343.v3i3.156. Acesso em: 10 dez. 2024.

