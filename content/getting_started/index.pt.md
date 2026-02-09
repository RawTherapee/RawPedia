---
title: Getting Starded pt
contributors:
  - DigitalPix
  - DrSlony
---

## Bem Vindo

RawTherapee é um programa multiplataforma de processamento de imagem
raw, lançado sob a Licença Pública Geral GNU Versão 3. Foi originalmente
escrito por Gábor Horváth de Budapeste, e o desenvolvimento foi assumido
em 2010 por uma equipe de pessoas ao redor do mundo. Em vez de ser um
editor de gráficos de varredura como o Photoshop ou o GIMP ou um
programa de gerenciamento de ativos digitais como o digiKam, ele é
especificamente voltado para a pós-produção de fotos raw. E faz isso
muito bem - no mínimo, o RawTherapee é um dos mais poderosos programas
de processamento raw disponíveis.

## Instalando o RawTherapee

Os usuários podem simplesmente baixar um instalador RawTherapee de
<http://rawtherapee.com/downloads> ou do gerenciador de pacotes. No
entanto, também é possível compilar você mesmo, se desejar ou precisar.
A [página principal RawPédia](main_page#compiling) tem links
para instruções sobre como fazer isso.

Muitas versões estão disponíveis para download, e este parágrafo tentará
explicar a diferença entre elas para pessoas que não estão
familiarizadas com o funcionamento de um sistema de versões de liberação
contínua. Nós fazemos novas versões de "desenvolvimento" quase
diariamente, e uma ou duas vezes por ano lançamos uma nova versão
"estável", que é bem empacotada com todos os bugs importantes e
conhecidos corrigidos. Quaisquer bugs encontrados na versão "estável"
serão posteriormente corrigidos nas versões de desenvolvimento mais
recentes, e estas serão acumuladas até a próxima versão "estável" vários
meses depois, e assim por diante. Nestas versões de "desenvolvimento"
também é onde melhoramos as ferramentas existentes e adicionamos novas
ferramentas, embora seja necessário algum tempo para refiná-las e
garantir que elas funcionem bem. Por um lado, as versões de
"desenvolvimento" sempre têm o maior número de bugs corrigidos, mas, por
outro lado, as novas ferramentas nessas versões podem ser brutas e não
polidas e novos bugs aparecerão. Se você quiser experimentar novos
recursos, obtenha a versão mais recente do "desenvolvimento" - aproveite
todas as correções de bugs mais recentes e teste novas ferramentas e
relate problemas e ideias para nós, com o custo de descobrir novos bugs
. Para uso geral, recomendamos a versão mais recente "estável", que
oferece uma experiência geralmente mais polida.

## Iniciar RawTherapee

![](Rt_setm_fb.png "Rt_setm_fb.png") (atualmente aberto), Fila, Editor e
Preferências. 2- Pańéis usados para navegar pelos arquivos e pastas. 3-
Miniaturas da pasta atualmente aberta. 4- Filtros para limitar as
miniaturas para somente aquelas que correspondem a algum metadado ou
estado. 5- Zoom e informações de miniaturas. 6- Operações rápidas de
imagem. 7- Sub-guias do Navegador de Arquivos: Filtro (atualmente
aberto), Inspecionar (para ver uma pré-visualização JPEG integrada de
tamanho cheio), Edição em Lote (para aplicar algumas configurações a
todas aa imagens selecionadas) e Exportação Rápida (baixa qualidade e
ignora algumas ferramentas, mas salvando rápido - não use isso para
salvar normalmente!). 8- Clique com o botão direito do mouse no menu de
contexto (normalmente usarás isto para aplicar algum perfil de
processamento a todos os arquivos selecionados).\]\] Na primeira vez que
iniciares o RawTherapee, verás [guia Navegador de
Arquivo](The_File_Browser_Tab/pt.md), e poderá estar vazia.
Precisas apontar o RawTherapee para onde suas fotos raw estão
armazenadas. Use o navegador da árvore de diretórios à esquerda da guia
"Navegador de Arquivos" para navegar até o repositório de suas fotos raw
e clique duas vezes na pasta para abri-la. Em seguida, clique duas vezes
numa foto raw para começar a editá-la.

## Edite sua primeira imagem

Depois de abrir uma foto raw para edição, notarás que a visualização não
é a mesma que o JPEG fora da câmera. O artigo "[Eek! Minha Foto Raw
Photo Parece Deiferente do JPEG da
Câmera](The_Image_Editor_Tab/pt#Eek.21_My_Raw_Photo_Looks_Different_than_the_Camera_JPEG.md)"
explica porque.

A Edição é feita na guia [Editor de
Imagem](The_Image_Editor_Tab/pt.md). É aqui que trabalhas com o
RawTherapee para criar obras de arte impressionantes - ou talvez apenas
aplique os primeiros socorros aos seus instantâneos.
![](Rt_setm_editor.png "Rt_setm_editor.png") Reserve um momento para
olhar em volta desta guia principal do Editor. Observe que existem guias
nessa guia - à direita da tela, na parte superior. Essas guias e os
controles são a caixa de ferramentas. Provavelmente tens a primeira guia
aberta e, se passares o mouse sobre ela, verás que é chamada de guia
Exposição. Abaixo das abas estão as ferramentas que a aba escolhida
contém - Exposição, Sombras/Realces, Mapeamento de Tom, etc. Se clicares
num deles, ele se expandirá para que possas ver seu conteúdo. Clique
novamente e ele entrará em colapso. Clique com o botão direito do mouse
num e ele se expandirá, enquanto todos os outros entrarão em colapso -
um atalho que economiza tempo. À esquerda da etiqueta de cada ferramenta
há um botão de energia
![<File:ExpanderEnabled.png>](ExpanderEnabled.png "File:ExpanderEnabled.png")
que permite que ligues ou desligues, ou em alguns casos, em vez de um
botão de energia, há um expansor triangular. Leia o [seção Ferramentas
dos Comentários Gerais Sobre Alguns Widgets da Caixa de
Ferramentas](General_Comments_About_Some_Toolbox_Widgets/pt#Tools.md)
artigo para uma explicação detalhada. Navegue pelas guias e painéis até
ter dominado totalmente tudo o que está disponível.

Antes de começares a trabalhar numa imagem, aqui estão alguns conselhos
importantes - *Não entre em pânico!* 'Você não corre o risco de destruir
nenhuma de suas imagens premiadas se cometer um erro. RawTherapee tem
alguns recursos que ajudam a proteger suas imagens:

- RawTherapee faz edição não-destrutiva de seus arquivos raw. Isso
  significa que RawTherapee nunca alterará o seu arquivo raw. Todas as
  alterações são armazenadas em arquivos secundários. Podes descobrir
  mais sobre eles no artigo [Arquivos Sidecar - Processamento de
  Perfis](Sidecar_Files_-_Processing_Profiles/pt.md).
- Ao usar o Editor de Imagem, você verá o painel à
  esquerda[Histórico](the_image_editor_tab/pt#history). Este
  painel mostra uma pilha de histórico de todas as alterações feitas na
  sua imagem. Para voltar a qualquer etapa (inclusive quando a imagem
  foi carregada pela primeira vez), basta clicar na linha relevante no
  painel Histórico.
- No painel Histórico, você verá um painel
  [Instantâneos](the_image_editor_tab/pt#snapshots). Podes
  pular isso por enquanto, mas você achará útil quando ganhar
  experiência com RawTherapee. Este painel armazena o estado de todas as
  ferramentas como "instantâneo". Isso permite que facilmente, por
  exemplo, ajustes tua foto para um visual agradável e colorido e tire
  um instantâneo, em seguida, ajuste-a novamente num lindo visual em
  preto-e-branco e tire outro instantâneo e então compare os dois
  clicando em qualquer instantâneo. (Nota: O RawTherapee não salva
  instantâneos no arquivo PP3, mas fará isso no futuro. Se tiveres três
  snapshots que desejes reter, será necessário clicar neles e salvar um
  arquivo PP3 sempre com um nome exclusivo).
- Como podes esperar, o Control-z irá desfazer a alteração anterior.
  (OK, não é ciência de foguetes, mas ainda é útil!)

### Noções Básicas

1.  Comece clicando na
    ![<File:Colour.png>](Colour.png "File:Colour.png") guia Cor e
    expandindo a ferramenta [Balanço de
    Branco](White_Balance/pt.md) clicando com o botão direito
    nela. O RawTherapee iniciará com o balanço de branco usado pela sua
    câmera. A maioria dos ajustes de balanço de branco envolve mover os
    controles deslizantes Temperatura e Tonalidade ou usar
    ![<File:Gtk-color-picker.png>](Gtk-color-picker.png "File:Gtk-color-picker.png")
    Selecionador Local de Balanço de Branco num caminho incolor (cinza
    neutro). Ajustar a gosto.
2.  Em seguida, corrija a exposição indo na guia Exposição
    ![<File:Exposure.png>](Exposure.png "File:Exposure.png"), expandindo
    a ferramenta [Exposição](exposure/pt) e ajustando-a a
    gosto. Por enquanto, basta usar os controles deslizantes Compensação
    de Exposição e Saturação.
3.  Se tua imagem tiver ruido, mude para a guia Detalhes
    ![<File:Detail.png>](Detail.png "File:Detail.png"), zoom para 100%
    usando o botão
    ![<File:Gtk-zoom-100.png>](Gtk-zoom-100.png "File:Gtk-zoom-100.png")
    ou usando a tecla de atalho de teclado "z", porque os efeitos das
    ferramentas nesta guia só são visíveis na visualização ampliada para
    100% (e na imagem salva), e habilite a ferramenta [Redução de
    Ruído](Noise_Reduction/pt.md) clicando no botão de energia
    ![<File:ExpanderEnabled.png>](ExpanderEnabled.png "File:ExpanderEnabled.png")
    deixando as configurações em seus valores padrão por enquanto.
    RawTherapee removeu automaticamente o ruído de cor (crominância). O
    ruído de luminância é removido
    [manualmente](noise_reduction/pt#usage), embora sais por
    hora, o ruído de luminância gerlamente empresta um visual agradável,
    granulado e semelhante a um filme. Como regra geral, ao usar a
    redução de ruído, não use nitidez. Diminua o zoom para ver a imagem
    inteira usando o botão
    ![<File:Gtk-zoom-fit.png>](Gtk-zoom-fit.png "File:Gtk-zoom-fit.png")
    ou usando a tecla de atalho de teclado "f".
4.  Agora decidiste que queres consertar a
    [geometria](lens/geometry/pt) e composição de tua foto.
    - Primeiro faça o nível do horizonte, ou corrija as coisas que devem
      ser verticais, como lâmpadas de rua ou bordas de construções. Para
      fazer isso facilmente, pressione a tecla "s" no teclado (o mesmo
      que clicar no botão
      ![<File:Straighten.png>](Straighten.png "File:Straighten.png")), e
      clique e arraste uma linha ao longo do horizonte ou ao longo da
      borda de um prédio sobre a visualização. Sua imagem irá girar de
      acordo e você será automaticamente levado para a guia
      Transformar![<File:Transform.png>](Transform.png "File:Transform.png").
    - Para cortar a foto, pressione a tecla de atalho "c" no teclado (ou
      use o botão ![<File:Crop.png>](Crop.png "File:Crop.png")) e clique
      e arraste um recorte sobre a visualização; você notará que a
      ferramenta [Cortar](crop/pt) fica automaticamente
      ativada. Não há necessidade de "aplicar" um corte - ele tem efeito
      no momento em que o desenhas. Podes querer definir Cortar "tipo de
      guia" para "nenhum" se for um problema.
    - Finalmente,podes querer diminuir a foto, porque quem quer enviar
      um JPEG de 10MB para sua rede social. Ativar oa
      feramenta[Redimensionar](resize/pt) e deixe-a nas
      configurações padrão. Observe que o efeito de redimensionamento é
      aplicado apenas à imagem salva, não à visualização.
5.  Tens tudo pronto, vamos [salvar](saving/pt) isso
    imediatamente. Clique no
    ![<File:Gtk-save-large.png>](Gtk-save-large.png "File:Gtk-save-large.png")
    botão Salvar a Imagem Atual ou use o atalho de teclado Ctrl+s. Salve
    como um arquivo JPG, qualidade em "92", subamostragem em
    "balanceado". Estas são boas configurações completas. Escolha uma
    pasta onde desejas salvar, e após alguns segundos seu arquivo estará
    pronto na pasta que você selecionou. Se fechares o RawTherapee, as
    configurações usadas serão armazenadas num [arquivo sidecar
    PP3](Sidecar_Files_-_Processing_Profiles/pt.md) ao lado do
    arquivo raw, para que possas reabrir a foto raw no futuro e manter
    as configurações de ferramenta usadas.

Agora que fizestes o ajuste básico de fotos e estás familiarizado com as
etapas, recapitule-as com detalhes mais avançados.

### Avançado

Leia sobre cada ferramenta no RawPedia antes de usá-la, para obter uma
compreensão do que ela faz. Os artigos explicam como as ferramentas
funcionam no RawTherapee, enquanto os conceitos gerais não específicos
do RawTherapee são deixados para o usuário encontrar na Wikipedia ou em
outro lugar.

Não deixe de ver os [Atalhos de
Teclado](Keyboard_Shortcuts/pt.md).

A ordem das ferramentas dentro do encadeamento do motor do RawTherapee é
codificada, então, desse ponto de vista, não importa quando habilitas ou
desabilitas uma ferramenta. No entanto, algumas ferramentas podem ter um
grande impacto em outras ferramentas, por ex. a alteração da exposição
pode requerer que reajustes a tonalidade das cores, e algumas
ferramentas podem requerer bastante energia da CPU para calcular a
visualização, fazendo atualizações da visualização a partir de então,
por isso, sugerimos que você se atenha a essa ordem geral de operações:

1.  Comece certificando-se de que o ambiente do RawTherapee está
    configurado corretamente, ou seja:
    - Certifique-se de que o RawTherapee esteja usando o perfil de cores
      do seu monitor se usares um fluxo de trabalho com gerenciamento de
      cores. Verificar Preferências\> Gerenciamento de Cor. Também podes
      precisar carregar as curvas de calibração apropriadas na sua placa
      gráfica se tiveres criado o perfil de cores do monitor sobre elas,
      embora a maneira como fazes isso esteja fora do escopo do
      RawTherapee.
    - Certifique-se de que a ferramenta Gerenciamento de Cor esteja
      configurada corretamente. Normalmente, os padrões são os melhores.
      Leia os artigos [Gerenciamento de
      Cor](Color_Management/pt.md) e [Adicionar Gerenciamento de
      Cor](Color_Management_addon/pt.md). Se, em vez de usares a
      matriz de cores ou os perfis DCP ou ICC fornecidos com o
      RawTherapee, decidires usar um externo como, por exemplo, um DCP
      próprio ou da Adobe, carregue-o primeiro, caso contrário, talvez
      seja necessário reajustar algumas das ferramentas de cores. Sempre
      use um perfil de saída - na maioria dos casos, o padrão, RT_sRGB.
      Se achas que estás sendo inteligente selecionando "Sem Saída ICM:
      sRGB", estás enganado.
2.  Se quiseres usar uma imagem [Campo Plano](flat_field/pt)
    e/ou [Quadro Escuro](dark_frame/pt), faça isso agora,
    para evitar ajuste.
3.  Agora defina o correto [Balanço de
    Branco](White_Balance/pt.md). Podes corrigir a exposição
    primeiro se a imagem estiver muito escura (ou muito clara) para ver
    as alterações no balanço de branco.
4.  Primeiro. ajuste a [Exposição](exposure/pt), usando os
    controles deslizantes Compensação de Exposição e Preto para obter a
    imagem no estádio certo. Uma vez no estádio certo, continue usando
    as duas curvas de tom. Não deixe de ler a [seção Curva de
    Tom](Exposure/pt#Tone_Curves.md) no artigo de Exposição para
    saber porque existem duas e como usá-las melhor - elas são
    ferramentas muito poderosas!
5.  Na seção Noções Básicas acima, sugerimos que você use o controle
    deslizante [Saturação](exposure/pt#saturation) (na
    ferramenta Exposição). Agora que aprendeste o básico e estás
    explorando técnicas mais avançadas, sugerimos que não uses mais o
    controle deslizante Saturação e, em vez disso, use o mais poderoso
    [curva CC](lab_adjustments/pt#cc_curve) na ferramenta
    [Ajustes L\*a\*b\*](lab_adjustments/pt), como um controle
    mais refinado.
6.  A ordem do resto fica confusa. Algumas ferramentas influenciarão
    inevitavelmente outras pessoas. Continue com a ferramenta [Ajustes
    L\*a\*b\*](Lab_Adjustments/pt.md) e depois o resto das
    ferramentas na guia Exposição.
7.  Então use a ferramenta [Wavelet](wavelet/pt) na guia
    Wavelet ![<File:wavelet.png>](wavelet.png "File:wavelet.png").
8.  Em seguida, use as ferramentas na guia Cor
    ![<File:Colour.png>](Colour.png "File:Colour.png"). A ferramenta
    [Tonificação de Cor](color_toning/pt) especificamente é
    muito sensível a alterações de exposição, então deixe-a por último.
9.  Em seguida, aplique zoom em 100% e use as ferramentas na guia
    Detalhes ![<File:Detail.png>](Detail.png "File:Detail.png").
    Geralmente, não use nitidez se estiver usando redução de ruído.
10. Finalmente, reduza o zoom novamente e use as ferramentas na guia
    Transformar
    ![<File:Transform.png>](Transform.png "File:Transform.png"). A razão
    pela qual ficaram para o final é que elas podem deixar a imagem
    parecer embaçada, porque para que a visualização seja responsiva, o
    RawTherapee usa aquela mesma imagem de visualização em baixa
    resolução que você vê - para mostrar o que as ferramentas fazem, e
    quandoê giras ou altera a geometria de uma imagem pequena, há uma
    suavização clara. Isso não é um problema quando se salva, a partir
    desse ponto, o RawTherapee faz seu processamento na imagem em
    tamanho cheio, que é lenta, mas de alta qualidade.
11. Salvar, diretamente quando desejas salvar uma única foto ou via
    [Fila em Lote](the_batch_queue/pt) quando desejas
    processar muitas fotos.

Podes editar metadados na guia Metadados
![<File:Meta.png>](Meta.png "File:Meta.png") a qualquer momento. Para
que as alterações feitas na guia Metadados entrem em vigor na imagem
salva, certifique-se de que "Preferências\> Processamento de Imagens\>
Copiar Exif/IPTC/XMP inalterado para o arquivo de saída" esteja
desmarcado. Se estiver marcado, as alterações feitas na guia Metadados
serão ignoradas na imagem salva.
