# <p align="middle"> LABORATÓRIO CAMADA DE REDES</p>

<h2 align="left">1 - Introdução</h2>
<p align="justify">A Camada de Rede foca na interconexão de enlaces e redes distintas, e para resolver este problemas, são necessários dois personagens: Os protocolos de roteamento e os dispositivos de interconexão de enlaces (switchs ou roteadores)</p>

<h2 align="left">2 - Sistemas Autônomos</h2>
<p align="justify">Sistemas Autônomos (SA) são agrupamentos de roteadores administrados por um roteador central, geralmente o que está executando o protocolo BGP, conforme Figura 01, podemos observar um grupo de 3 (três) Sistemas Autônomos.</p>
<p align="justify">A Estrutura da Internet feita em Sistemas Autônomos dimimuita a quantidade de tabelas de roteamento replicadas, considerando que as informações inerentes as rotas interna a um SA reservam-se aos seus roteadores de borda.</P>
<p align="center"><img src="images/roteamento/01-as.png"  width="750" height="375" align="middle"/></p>
<h4 align="middle">Figura 01 - Sistemas Autônomos</h4>
<h2 align="left">3 - Roteamento Estático</h2>
<p align="justify">O roteamento dinâmico interconecta redes distintas, todavia, sua configuração é realizada pelo administrador do ambiente, devendo criar as rotas necessárias em cada roteador da rede, caso ocorra alguma queda do enlace os pacotes continuaram sendo encaminhados para o enlace descontinuada, somente depois da intervenção do administrador criando uma nova rota é que o problema será solucionado.</p>

<h2 align="left">4 - Roteamento Dinâmico</h2>
<p align="justify">O Roteamento Dinâmico as tabelas são criadas automáticamente pelo algoritmo de roteamento, sem intervenção do administrador do ambiente, devendo a este informar somente qual protocolo de roteamento deve-se utilizar. Os protocolos de roteamento dinâmicos utilizados na camada de rede são:</p>

* <b>RIP</b> – Utilizada como característica para escolha da rota o caminho mais curto, baseado na quantidade de saltos, é um protocolo interno ao Sistema Autônomo;<p>
* <b>OSPF</b> – Tem como caracterísitca para escolha da rota o estado do enlace, que nem sempre é o caminho mais curto é um protocolo interno ao Sistema Autônomo;<p>
* <b>BGP</b> -  Protocolo de Borda que Interconecta Sistemas Autônomos;<p>

<h2 align="left">5 - Laboratório Roteamento Dinâmico</h2>

<p align="justify">Iremos realizar a interconexão de duas redes distintas, Figura 2, usando um protocolo de roteamento dinâmico RIP, que utiliza o algoritmo de Vetor de Distância, ou seja, o melhor caminho é o que possui a menor quantidade de saltos</b></p>

<p align="center"><img src="images/roteamento/02-diagrama_rede.png"  width="600" height="391" align="middle"/></p>
<h4 align="middle">Figura 02 - Diagrama Rede</h4>

<h3 align="left">5.1 - Entendo a Arquitetura de um Roteador</h3>

<p align="justify">Um roteador é um compador com função específica de interconectar redes, seu hardware funciona de uma maneira um pouco difererente de um computador pessoal, um dos principais fabricantes do mercado é a CISCO, no qual nosso laboratório estará orientado, a Figura 03, apresenta a arquitetura dos componentes principais de um roteador. </p>
<p align="center"><img src="images/roteamento/03-roteador.png"  width="400" height="240" align="middle"/></p>
<h4 align="middle">Figura 03 - Componentes Roteador</h4>

*  <b>RAM</b> – Armazena as tabelas de roteamento e o arquivo de configuração temporário do roteador;<p>
* <b>NVRAM</b> – Armazena o arquivo de configuração que será utilizado na inicialização (startup config), não ocorre perca das informações armazenadas na NVRAM ao desligar o roteador;<p>
* <b>FLASH</b> - Armazena a imagem de inicialização do Sistema Operacional, possui a possibilidade armazenar várias imagens, retém seu conteúdo quando o roteador é desligado;<p>
* <b>ROM</b> -  Mantém instruções que definem o autoteste realizado na inicialização do roteador;<p>
* <b>Console</b> -  É uma interface de acesso direto ao roteador para sua manutenção e atualização de firmware em caso de percado de acesso externo;<p>
* <b>Interfaces</b> -  Conectam o roteador à rede para entrada e saída de pacotes, podem estar diretamenta conectadas na placa-mãe ou adicinadas através de módulos, em computadores pessoas são chamadas de placas de rede;<p>

<p align="center" ><img src="images/roteamento/aviso-importante.png"  width="300" height="130" align="middle"/></p>
<p align="justify">Todas as configurações realizadas em um roteador são salvas na RAM, portanto é um dado volátil, ocorrendo o desligamento inesperado a configuração feita é <b>PERDIDA</b>, daí a necessidade de salvar constante o que foi realizado na NVRAM através do comando: <i>copy running-config startup-config</i>.</p>

<h3 align="left">5.2 - Preparando o Ambiente para Realizar o Laboratório</h3>

<p align="justify">Iremos utilizar um software de simualação de rede desenvolvido e disponibilizado pela própria CISCO, chamado Packet Tracer, ele pode ser executado até mesmo em computadores antigos de 32 bits, para fazer o download cadastre-se no curso:</p>


[Introduction to Packet Tracer](https://www.microsoft.com/pt-BR/download/details.aspx?id=45520)

<p align="justify">É um curso gratuíto de 10 horas, que não tem obrigatoriedade de sua realização, mas já disponibiliza conteúdo e a o download da ferramenta. O mais importante é que você pode até achar o arquivo de instalação do Packet Tracer na internert, todavia para liberar todas as funcionalidades da ferramenta é necessário um login criado no cadastro deste curso, vou disponiblizar a seguir o arquivo para download direto que salvei no google drive:</p>

[Packet Tracer - 32 bits](https://drive.google.com/open?id=10PJHweyAjtvTW5J4JWVAGVdsNSeJKk9f)

[Packet Tracer - 64 bits](https://drive.google.com/open?id=1v3oJeTjKZX5XFH3iwGnDYITVQ1u1FQG_)

[Packet Tracer - Linux](https://drive.google.com/open?id=10dGsuiEm2PqPYw1F5qqx2Pkdquy4sOBQ)

<p align="justify">Após o download faça a instalação do aplicativo que é muito simples, realize o login no mesmo, é o usuário que você cadastrou para ter acesso ao curso, e faça o download do arquivo do laboratório disponiblizado abaixo:</p>

[Laboratório - Roteamento Dinâmico RIP](https://drive.google.com/open?id=1H6cVuwK_GAYC0BXm2RTWAelJVvFJ1O6D)

Menu Options => Preferences
 
<h3 align="left">5.3 - Execução do Laboratório</h3>
<p align="justify">Ao abrir o arquivo baixado no link acima, o Packet Tracer será aberto com duas telas, uma com o wizard que apresentará seus acerto no final e a outra com o diagrama de rede no qual você irá configurar, Figura4. </p>
<p align="center"><img src="images/roteamento/04-lab-packettracer.png"  width="900" height="448" align="middle"/></p>
<h4 align="middle">Figura 04 - Laboratório Packet Tracer</h4>

<p align="justify">Objetivo do Laboratório:</p>
*  Congigurar o endereçamento IP em todos os dispositivos do ambiente;<p>
* Configurar o Roteamento Dinâmico RIP no <b>Router1</b> e <b>Router2</b> para que o <b>PC0</b> possa se comunicar com o <b>PC1</b>;<p>

<h3 align="left">5.4 - Configuração do PC0</h3>
<p align="justify">Seguiremos uma dinâmica no laboratório de configuração por dispositivo, acessa o dispositivo realiza todas as configurações inclusive de roteamento, se for o caso, e passa a fazer a configuração do seguinte, lembrado que o diagrama e endereçamento é o igual o apresentado na Figura 02.</p>

<p align="justify">O ambiente de rede apresentado não possui nenhuma configuração, somente foi acrescentado um módulo para disponibilizar uma comunicação serial entre os roteadores, acessem o <b>PC0</b> dando dois cliques em cima de uma imagem, onde será apresentado a imagem conforme Figura 05, com suas guias de configuração.</p>
<p align="center"><img src="images/roteamento/05-config-pc.png"  width="600" height="526" align="middle"/></p>
<h4 align="middle">Figura 05 - Configuração PC</h4>

<p align="justify">Acesse a guia <b>config</b> no menu <b>Settings</b> e atribuia o endereço do Gateway do PC0 que é a interface Gigabitethernet 0/0 com IP 192.168.0.1, Figura 06:</p>
<p align="center"><img src="images/roteamento/06-pc-gateway.png"  width="600" height="526" align="middle"/></p>
<h4 align="middle">Figura 06 - Configuração PC - Gateway</h4>

<p align="justify">No menu Interface => FastEthernet0 atribua o endereço conforme diagrama de redes, Figura 07: </p>
<p align="center"><img src="images/roteamento/07-pc0-endereco.png"  width="600" height="526" align="middle"/></p>
<h4 align="middle">Figura 07 - Configuração PC - Endereço IP</h4>

<h3 align="left">5.5 - Configuração do Router1</h3>
<p align="justify">A configuração de um Router da CISCO é completamente diferente de qualquer sistema operacional de computadores pessoais ou roteadores domésticos, ele possui um Sistema Operacional própio chamado Internetwork Operating System (IOS) presente também em Switchs da cisco, o importante de suas configurações é enteder a localização quanto aos prompts. Outro as pectos a se considerar é que a administração deste sistema operacional é realizada utilizando linhas de comandos através da Command Lina Interface-CLI, a tabela abaixo apresenta os principais prompts utilizados no IOS:</p>
<p align="center"><img src="images/roteamento/tabela-prompt-v2.png"  width="600" height="174" align="middle"/></p>


<p align="justify">Para configurar o <b>Router1</b> clique duas vezes em cima de sua imagem, será aberto uma tela com as guias de configurações físicas, lógicas e CLI, Figura 8:</p>

<p align="center"><img src="images/roteamento/08-config-router.png"  width="600" height="526" align="middle"/></p>
<h4 align="middle">Figura 08 - Configuração Router</h4>

<p align="justify">Toda a administração do roteador será feita na guia <b>CLI</b>, no qual será disponibilizado o prompt de administração, Figura 9, o <b>CLI</b> estará bloqueado para ter acesso digite <b>enter</b>, onde será liberado o <b>prompt modo usuário</b> (>).</p>

<p align="center"><img src="images/roteamento/09-config-router-cli.png"  width="600" height="526" align="middle"/></p>
<h4 align="middle">Figura 09 - Configuração Router - CLI</h4>

<p align="center" ><img src="images/roteamento/aviso-importante.png"  width="300" height="130" align="middle"/></p>
<p align="justify">Por questões de padronização deixei o texto referente ao Prompt do IOS em negrito, caracterizando que não deve ser digitado na CLI</p>

<p align="justify" >Ao acessar a <b>CLI</b> pela primeira vez o prompt liberado é o <b>modo usuário</b>, todavia neste prompt só podemos realizar consultas, para administrar e configurar o router, deve-se acessar o prompt <b>modo priviletiado</b> digitando o comando: enable</p>
<p align="justify"><b>Router></b>  enable</p><p align="justify">Para realizar configuração no router devemos acessar o prompt no <b>Modo de Configuração Global</b> digitando: configure terminal ou conf t</p><p align="justify"><b>Router#</b> configure terminal</p><p align="justify">Para atribuir o endereço ip a uma interface deve-se acessar seu prompt de acordo a porta da interface conforme apresentado, em nosso laboratório iremos acessar a interface GibabitEthernet 0/0 que conecta o Router1 ao PC0</p><p align="justify"><b>Router(config)#</b> interface gigabitethernet 0/0</p>

<p align="justify">Deve-se atribuir o endereço conforme apresentado</p><p align="justify"><b>Router(config-if)#</b> ip address 192.168.0.1 255.255.255.0</p>
<p align="justify"><b>Obs.: </b>Caso digite qualquer comando errado, como o endereço da interface, por exemplo: ip address 192.168.0.10 255.255.255.0, basta repetir o comando com a palavra <b>no</b> no começo: <b>no</b> ip address 192.168.0.10 255.255.255.0, e digitar o comando correto.

<p align="justify">Toda interface por padrão vem desligada, após atribuir o endereçamento deve-se digitar o comando: no shutdown ou no shut</p><p align="justify"><b>Router(config-if)#</b> no shutdown</p><p align="justify">Saia do prompt da interface com o comando: exit</p><p align="justify"><b>Router(config-if)#</b> exit</p>

<p align="justify">Acesse o prompt da interface serial 0/3/0</p><p align="justify"><b>Router(config)#</b> interface serial 0/3/0</p>

<p align="justify">Atribua o IP conforme especificado na Figura 2</p><p align="justify"><b>Router(config-if)#</b> ip address 192.168.10.1 255.255.255.0</p>

<p align="justify">Ative a interface</p><p align="justify"><b>Router(config-if)#</b> no shutdown</p><p align="justify">Saia do Prompt</p><p align="justify"><b>Router(config-if)#</b> exit</p>

<p align="justify">Neste ponto será configurado o protocolo de Roteamento RIP, que é um protocolo dinâmico que constroi sua tabela de roteamento baseada no estado do enlace, para acessar o prompt de roteamento digite o comando: router rip</p><p align="justify"><b>Router(config)#</b> router rip</p>

<p align="justify">Deve-se informar todas as redes que estão diretamente conectada no roteador, eles possam anunciá-las</p><p align="justify"><b>Router(config-router)#</b> network 192.168.0.0</p><p align="justify"><b>Router(config-router)#</b> network 192.168.10.0</p>

<p align="justify">Para reduzir a quantidade de anúncios de rede e atividades de processamento do router, deve-se informar quais são as <b>interfaces passivas</b> que não necessitaram anunciar redes, geralmente são interfaces que não estão conectadas a roteadores, como a GigaBitEthernet 0/0.</p><p align="justify"><b>Router(config-router)#</b> passive-interface giGabitethernet 0/0</p>

<p align="justify"><b>Obs.: </b>Caso faça algum parâmetro errado no prompt de roteamento, basta apagar toda a configuração de roteamento digitando no prompt de configuracão global: no router rip</p>

<p align="justify">Saia do prompt de roteamento</p><p align="justify"><b>Router(config-router)#</b>  end</p>
<p align="justify">Todas as configurações realizadas anteriormentes estão sendo salvas de maneira automática no arquivo <b>running-config</b> na RAM, em caso de desligamento inesperado tudo o que foi digitado seria perdido, para que a configuração seja salva copie o arquivo running-config para o arquivo <b>startup-config</b> na NVRAM.</p><p align="justify"><b>Router#</b> copy running-config startup-config</p>

<p align="justify">É pedido uma confirmação da cópia, basta digitar enter</p>Destination filename [startup-config]?<p> Building configuration...[OK]<p>

<h3 align="left">5.6 - Configuração do Router1</h3>
<p align="justify">A configuração do Router2 é similitar ao Router1, a única diferença são os parâmetros de configuração, portanto não irei repetir as explicações, somente repassar o comando, com excessão quando irei usar o <b>clock rate</b></p> 


<p align="justify"><b>Router></b>  enable</p><p align="justify"><b>Router#</b> configure terminal</p><p align="justify"><b>Router(config)#</b> interface serial 0/3/0</p>

<p align="justify"><b>Router(config-if)#</b> ip address 192.168.10.2 255.255.255.0</p>
<p align="justify">O <b>clock rate</b> define a taxa de bits transmitida na interface serial que opera no modo de Equipamento de Comunicação de Dados-DCE, caso este parâmetro não seja configurado não ocorrerá comunicação entre os roteadores.</p>
<p align="justify"><b>Router(config-if)#</b> clock rate 56000</p>
<p align="justify"><b>Router(config-if)#</b> no shutdown</p><p align="justify"><b>Router(config-if)#</b> exit</p>

<p align="justify"><b>Router(config)#</b> interface GigabitEthernet 0/0</p>

<p align="justify"><b>Router(config-if)#</b> ip address 192.168.20.1 255.255.255.0</p>

<p align="justify"><b>Router(config-if)#</b> no shutdown</p><p align="justify"><b>Router(config-if)#</b> exit</p>

<p align="justify"><b>Router(config)#</b> router rip</p>

<p align="justify"><b>Router(config-router)#</b> network 192.168.10.0</p><p align="justify"><b>Router(config-router)#</b> network 192.168.20.0</p>

<p align="justify"><b>Router(config-router)#</b> passive-interface GigabitEthernet 0/0</p>

<p align="justify"><b>Router(config-router)#</b>  end</p>
<p align="justify"><b>Router#</b> copy running-config startup-config</p>

Destination filename [startup-config]?<p> Building configuration...[OK]<p>

<h3 align="left">5.7 - Configuração do PC1</h3>

<p align="justify">A configuração do PC1 é similar ao PC0, necessitando somente usar o gateway conforme o diagrama de rede <b>192.168.20.1</b> e o endereço ip do computador <b>192.168.20.10</b>.

<p align="justify"><b>Obs.:</b> Em caso de dúvida volte no tópico 5.4, para ver como acessar a área de configuração do PC</p>
<h3 align="left">5.8 - Analisando se a Configuração está Correta</h3>

<p align="justify">Para verificar se a configuração está correta acesse novamente o PC0 dando dois cliques na imagem, será aberto a caixa de configuração, Figura 05, selecione a guia <b>Desktop</b> e <b>Prompt de Comando</b> dentro do terminal aberto digite o comando: ping 192.168.20.10, se a configuração estiver correta não ocorrerá perca de nenhum pacote</p>

<p align="justify">A analise dos resultados de toda a configuração é feita clicando no botão <b>Check Results</b>, Figura 10</p>

<p align="center"><img src="images/roteamento/10-checkresults.png"  width="521" height="316" align="middle"/></p>
<h4 align="middle">Figura 10 - Check Results</h4>

<p align="justify">No qual será aberto uma caixa de diálogo com três guias de relatórios: Feedback Geral, Itens Corretos e Teste de Conectividades, conforme imagens abaixo:</p>

<p align="center"><img src="images/roteamento/feedback-geral.png"  width="700" height="340" align="middle"/></p>

<p align="center"><img src="images/roteamento/itens-corretos.png"  width="700" height="540" align="middle"/></p>

<p align="center"><img src="images/roteamento/teste-conectividade.png"  width="700" height="196" align="middle"/></p>

<h3 align="left">5.9 - Comandos Importantes</h3>

<p align="justify">Alguns comandos importantes serão apresentados a seguir, todos eles devem ser executados no prompt privilegiado:</p>

*  <b>show running-config</b> – Apresenta o arquivo de configuração do router que está executando na RAM;<p>
* <b>show startup-config</b> – Apresenta o arquivo de configuração que está salvo na NVRAM e que será carregado na inicialização do router;<p>
* <b>show ip route</b> - Exibe as todas as tabelas de roteamentos montatas pelo router;

