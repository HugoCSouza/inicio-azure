# Apresentação de configurações iniciais em Azure para trabalhar com Machine Learning

## Criação do Azure Machine Learning

Ao se registrar dentro da plataforma da Azure, iremos inicialmente criar um modelo de ML para configuração. Na primeira etapa dentro do Menu Lateral, iremos Clicar em Criar um Recurso > IA + Machine Learning > Azure Machine Learning.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/c1a988ac-5a9f-4cd5-b67a-c64617fc48e8)

Ao clicar em criar, esse menu de configuração será apresentado.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/0989c290-ee43-4e74-b6b8-dccac0bc9b23)

As configurações básicas que devem ser preenchidas são:
- Assinatura (A assinatura que está vinculada a sua conta)
- Grupo de recursos (Todo recurso deve fazer parte de um grupo de recursos)
- Nome
- Região
A conta de armazenamento, cofre de chaves e Application Insights podem ou não estar preenchidos automaticamente. Caso não esteja, clique em criar logo abaixo.

Se tratando de uma configuração básica, pode-se clicar em examinar + criar. Caso tudo esteja preenchido corretamente e validado pela Azure, como na imagem abaixo, clique em criar.

![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/685d969c-edb3-4580-beb2-a9c5098a1743)

Ao clicar em criar, o recurso irá começar a ser iniciado, pode demorar alguns minutos. Ao iniciar a tela abaixo será exibida, aguarde até ser iniciado.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/6e175e20-7f05-4b21-b61a-d4003f70d681)
Quando finalizada a criação, a tela que aparecerá está abaixo. Clique em ir ao recurso.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/bc418b42-70d9-4650-971a-705add9c6225)

Ao entrar, você deveria ir ao Azure Studio para configurar sua aplicação clicando em Iniciar o Studio
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/cd9260c5-9dac-443d-9141-dcf5ebbd68cf)

## Azure Studio
Iniciando o Azure Studio você terá várias opções de Machine Learning para realizar. No nosso caso, como primeiro caso de aprendizado, iremos clicar em **"ML Automatizado"** no menu lateral.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/15df3ec0-053b-4086-b860-02b30651aced)

Essa opção fará com que, definida as operações iniciais, o Azure irá treinar modelos conforme as configurações. Dentro da aba ML Automatizado, selecione a opção **"Novo trabalho de ML Automatizado"**
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/7851123c-e256-4ba1-94d5-82fa1b0c6e7f)

Dentro das configurações, iremos definir algumas configurações padrões como manda a [documentação oficial da Microsoft](https://microsoftlearning.github.io/AI-900-AIFundamentals.pt-BR/Instructions/02-module-02.html) que são:

    Selecionar tipo de tarefa: regressão
    Selecionar conjunto de dados: crie um novo conjunto de dados com as seguintes configurações:
    Tipo de dados:
        Nome: bike-rentals
        Descrição: dados históricos de aluguel de bicicletas
        Tipo: tabular
    Fonte de dados:
        Selecione De arquivos da Web
    URL da Web:
        URL da Web: https://aka.ms/bike-rentals
        Ignorar validação de dados: não selecionar
    Configurações:
        Formato de arquivo: delimitado
        Delimitador: vírgula
        Codificação: UTF-8
        Cabeçalhos de coluna: somente o primeiro arquivo tem cabeçalhos
        Ignorar linhas: Nenhum
        O conjunto de dados contém dados multilinhas: não selecione
    Esquema:
        incluir todas as colunas que não sejam Caminho
        Examinar os tipos detectados automaticamente

![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/abf388e3-61e7-4c86-bbd8-66d92ae9cf71)

Após seguir o passo-a-passo da documentação do item 2.2 tipo de tarefa e dados, será apresentado essa tela, clique em criar (Levará alguns segundos).
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/7ac05548-bae1-43a2-a619-6ddabc1a4bfc)

Após finalizar, caso clique no nome dado ao tipo de dados ("bike-rentals") será aberto uma janela dentro da pagina de demonstrando como seu dataset se encontra. Prosseguindo a configuração, em configuração de tarefas, seguiremos os seguinte valores:

    Tipo de tarefa: regressão
    Conjunto de dados: bike-rentals
    Coluna de destino: aluguéis (inteiro) ou rentals (integer)
    Definições de configuração adicionais:
        Métrica primária: erro quadrático médio da raiz normalizada ou NormalizedRootSquaredError
        Explicar o melhor modelo: não selecionado
        Usar todos os modelos com suporte: Não selecionado. Você restringirá o trabalho para experimentar apenas alguns algoritmos específicos.
        Modelos permitidos: selecione apenas RandomForest e LightGBM. O ideal seria tentar usar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
    Limites: expanda esta seção
        Avaliações máximas: 3
        Máximo de avaliações simultâneas: 3
        Máximo de nós: 3
        Limite de pontuação da métrica: 0,85 (de modo que se um modelo atingir uma pontuação de métrica de raiz do erro quadrático médio normalizada de até 0,085, o trabalho será encerrado.)
        Tempo limite: 15
        Tempo limite de iteração: 15
        Habilitar encerramento antecipado: selecionado
    Validação e teste:
        Tipo de validação: divisão de validação de treinamento
        Percentual de dados de validação: 10
        Conjunto de dados de teste: nenhum
    Computação:
        Selecionar tipo de computação: sem servidor
        Tipo de máquina virtual: CPU
        Camada da máquina virtual: dedicada
        Tamanho da máquina virtual: Standard_DS3_V2
        Número de instâncias: 1


Após todas as configurações feitas, essa aba de verificação final será apresentada. Confira se todas as configurações estão conforme o desejado e clique em "*Envie o trabalho de treinamento*". 
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/6917a254-7fb4-4493-b61a-119c6238de27)

Ao enviar, ele primeiro apresenta a primeira imagem informando que seu trabalho foi enviado mas ainda não inicializado. Após alguns minutos, o trabalho automaticamente se iniciará conforme a segunda imagem, mudando o seu status para *Em execução*. Até que o modelo finalize, pode demorar alguns minutos (em média, 15 minutos de execução, a partir da mudança de status).
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/10d587cc-37e1-47b5-b07e-5a932d13c079)
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/0afc023b-f469-4f15-bbfc-8988c635beda)

Ao terminar o modelo, o status do treinamento mudará para concluido e as informações estarão diponíveis dentro do modelo. Na aba *"Melhor resumo de modelo"*, as informações do melhor modelo configurado, quais as métricas deste melhor modelo.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/5c1170cb-9cbe-4f2c-81bd-1206e87b982d)

## Implantação do modelo

Na página do modelo, clique na opção *"Modelo de registro"*. Será aberto uma aba igual a imagem abaixo. Preencha com as informações de nome e descrição apenas e registre seu modelo.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/5a2e98bf-f450-4049-8309-e5db0aef3de3)

Agora na aba lateral, dentro da guia Ativos, clique em modelos, e clique no modelo que você acabou de registrar.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/7f7f4d04-b559-4deb-99f2-d3009c5f3214)

Clique no nome abaixo do item *"Criado por trabalho"*. Ao abrir a janela, você terá acesso as informações do modelo criado como métricas, logs de saida, logs de treinamento, entre outros. O nome na parte superior estará um nome diferente pois é o nome do melhor modelo dentro dos parametros que você passou para o azure. Estes nomes são criados pelo próprio Azure para diferenciar os modelos de IA entre si.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/b9d87566-3e28-48c8-a345-02bbdec66ef2)

## Teste do modelo
Para testar a saída do modelo e verificar se ela se encontra fáctivel com os dados compartilhados, iremos realizar testes. No menu lateral do Azure, clique em *"Pontos de extremidade"* dentro da aba "Ativos". Clique em Criar, caso não esteja criado seu ponto de extremidade, e avançe até implantar o modelo. A implantação se iniciará conforme a imagem abaixo. Isso poderá levar alguns minutos. Após concluido, clique na aba testar.
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/786bb78e-02a9-481c-8b62-1ee985d37ada)

Dentro dessa aba, será apresentada essa interface. No item *"Input"*, já é apresentado um arquivos JSON de como deve ser a estrutura do arquivos para testes. Foi usado os seguinte parâmetros para teste:
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/59845144-29ab-4539-8309-7526b8092e9d)
```
 {
   "input_data": { 
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
```
Se tratando de um modelo de machine learning, cada modelo apresentará um valor. Nesta instância, o resultado do modelo foi:
![image](https://github.com/HugoCSouza/inicio-azure/assets/150296370/16bfd565-b408-4dea-aeb1-781cf04209cc)

### **Obs: É importante excluir os modelos caso sejam apenas para aprendizado pois cada recurso no Azure pode ser cobrado financeiramente a depende da sua assinatura.**

#### Este repositório foi feito com objetivo de demonstrar a configuração básica de uma ferramenta de machine learning dentro do Azure, além de servir como base de avaliação dentro do bootcamp " Microsoft Azure AI Fundamentals" ministrado pela DIO. Qualquer sugestão, pode solicitar um pull request ou entrar em contato comigo via [linkedin](https://www.linkedin.com/in/hugo-cs-souza/)
























