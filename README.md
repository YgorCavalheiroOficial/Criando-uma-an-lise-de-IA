# Criando-uma-an-lise-de-IA
Criando uma análise de IA(Bootcamo_DIO)

# Pontos de extremidade e análise de dados - IA treinada do Microsoft Azure

  Primeiramente eu realizei a criação da área de trabalho na subscrição do Azure, para
que fosse possível utilizar os serviços do estúdio Azure Machine Learning. Após segui o
seguinte passo a passo:

No estúdio (Azure Machine Learning Studio) criei meu novo projeto e realizei as seguintes configurações:

Configurações básicas :

Nome do trabalho : mslearn-bike-automl

Novo nome do experimento : mslearn-bike-rental

Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas

Marcadores : nenhum


Tipo de tarefa e dados :

  Selecionei o tipo de tarefa : Regressão
  
  Selecionei o conjunto de dados;
  
  Criei um novo conjunto de dados com as seguintes configurações;


Tipo de dados :

  Nome : aluguel de bicicletas
  
  Descrição : dados históricos de aluguel de bicicletas
  
  Tipo : Tabular

  
Fonte de dados :

  Selecionei Dos arquivos da web
  
  URL da Web :
  
    URL da Web :https://aka.ms/bike-rentals
    
    Ignorar validação de dados : não selecionar
    
  Configurações :
  
    Formato de arquivo : Delimitado
    
    Delimitador : Vírgula
    
    Codificação : UTF-8
    
    Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos
    
    Pular linhas : Nenhum
    
    O conjunto de dados contém dados multilinhas : não selecione
    
  Esquema :
  
    Inclui todas as colunas exceto Caminho
    
    Revisei os tipos detectados automaticamente


Após a criação do conjunto de dados, selecionei o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações de tarefa :


  Tipo de tarefa : Regressão
  
  Conjunto de dados : aluguel de bicicletas
  
  Coluna de destino : Aluguéis (inteiro)
  
  
Configurações adicionais :

  Métrica primária : raiz do erro quadrático médio normalizado
  
  Explique o melhor modelo : Não selecionado
  
  Usar todos os modelos suportados : Desmarcado.
  
  Modelos permitidos : Selecionei apenas RandomForest e LightGBM.
  
  -Limites
  
  Máximo de testes : 3
  
  Máximo de testes simultâneos : 3
  
  Máximo de nós : 3
  
  Limite de pontuação da métrica : 0,085
  
  Tempo limite : 15
  
  Tempo limite de iteração : 15
  
  Habilitar rescisão antecipada : selecionado
  
- Validação e teste :
    
  Tipo de validação : divisão de validação de trem

  Porcentagem de dados de validação : 10
  
  Conjunto de dados de teste : Nenhum

- Calcular :
  
  Selecione o tipo de computação : sem servidor
  
  Tipo de máquina virtual : CPU
  
  Camada de máquina virtual : Dedicada
  
  Tamanho da máquina virtual : Standard_DS3_V2*
  
  Número de instâncias : 1


Em seguida dei início ao treinamento da máquina.


## Implantei e testei o modelo


Na guia Modelo do melhor modelo treinado pelo seu trabalho automatizado de machine learning, selecionei Implantar e usei a opção de serviço Web para implantar o modelo com as seguintes configurações:


  Nome : prever-aluguéis
  
  Descrição : Prever aluguel de bicicletas
  
  Tipo de computação : Instância de Contêiner do Azure
  
  Habilitar autenticação : selecionado
  
  
  ## Teste do serviço implantado


No estúdio Azure Machine Learning, no menu esquerdo, selecionei "Pontos de Extremidade"(Endpoint) e abri o ponto final em tempo real.


Na página do endpoint em tempo real de previsão de aluguel, acessei a guia Teste .


No painel Dados de entrada para testar o endpoint, substitui o modelo JSON pelos seguintes dados de entrada:


## Configuração dos pontos de extremidade:

     {
         "Inputs": { 
     
         "data": [
     
           {
             "day": 1,
             "mnth": 1,   
             "year": 2022,
             "season": 2,
             "holiday": 0,
             "weekday": 1,
             "workingday": 1,
             "weathersit": 2, 
             "temp": 0.3, 
             "atemp": 0.3,
             "hum": 0.3,
             "windspeed": 0.3 
           }
         ]    
       },   
       "GlobalParameters": 1.0
     }

