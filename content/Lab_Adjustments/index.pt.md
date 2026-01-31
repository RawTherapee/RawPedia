---
title: Lab Adjustments
contributors:
  - DigitalPix
  - DrSlony
tags:
  - 'Tool Description'
  - 'Exposure Tab'
---

![](Lab_color_space.png "Lab_color_space.png")
[Lab](https://en.wikipedia.org/wiki/Lab_color_space) (também chamado
CIELAB ou L\*a\*b) é um espaço de cores tridimensional projetado para
aproximar a visão humana, em oposição ao espaço de cores RGB que modela
a saída de dispositivos físicos em vez da percepção visual humana. Ele
mantém o tom (também chamado de claridade ou valor) separado da cor,
para que possas ajustar um sem alterar o outro.

- O componente L aproxima-se da percepção humana de claridade.
- O componente a define como é a cor verde/magenta.
- O componente b define como é a cor amarelo/azul.

## Claridade

Ao usar o controle deslizante Claridade na seção Lab, uma curva de tom é
aplicada ao canal L do espaço de cores Lab. Assim como o controle
deslizante de brilho na seção Exposição acima, o ponto preto e o ponto
branco não se movem.

## Contraste

O controle deslizante de contraste no Lab aumenta ou diminui o contraste
da foto, novamente aplicado ao canal L. Em termos de desenvolvedor: este
controle deslizante aplica uma curva de contraste centrada no nível
médio de claridade. As tonalidades acima da média são elevadas
(rebaixadas), enquanto as tonalidades abaixo da média são rebaixadas
(elevadas).

## Cromaticidade

O controle deslizante Cromaticidade de Lab aumenta ou diminui a
cromaticidade da imagem, aplicando uma curva de contraste aos canais a e
b do espaço Lab. Configurando este controle deslizante como -100 remove
todas as cores, tornando a imagem em preto e branco. O melhor caminho
para converter uma imagem para preto e branco é usando a ferramenta
dedicada e poderosa *Preto e Branco* na guia *Cor*.

## Tonificação P&B

A "*Tonificação P&B*" caixa de seleção foi descontinuada a partir da
versão 4.0.12 e foi substituída pela ferramenta *[Preto e
Branco](Preto_e_Branco.md)* localizada na guia *Cor*. Para
compatibilidade com versões anteriores, ao abrir perfis de processamento
em que "*Tonificação P&B*" foi usado, o controle deslizante
*Cromaticidade* será automaticamente definido como -100, fornecendo o
mesmo efeito.

## Evite Mudança de Cor

Adapta as cores da imagem na gamut do espaço de cores de trabalho e
aplica-se [correção
Munsell](https://en.wikipedia.org/wiki/Munsell_color_system) para manter
a pureza da cor.

## Restringir o LC para Vermelho e Tons de Pele

Quando ativado, restringe os efeitos da curva *Claridade de acordo com
Cromaticidade* (*LC*), para que possas tornar a cor da pele mais clara
(aumentando a claridade da cor da pele) sem afetar a roupa ou o plano de
fundo do modelo.

## Proteção Vermelho e Tons de Pele

Quando ativado, os efeitos do controle deslizante da Cromaticidade e da
curva CC não serão aplicados às cores da pele, para que possas aumentar
a cromaticidade de tua foto sem fazer com que a cor da pele pareça super
saturada.

## Curvas

Ajustes Lab fornece uma riqueza de curvas para alterar a aparência da
imagem. Abaixo estão as explicações ilustradas de cada curva.

### Curva L

![](Lab_L_BA.jpg "Lab_L_BA.jpg") A curva L permite controlar a claridade
de saída com base na claridade de entrada, L=f(L). O histograma na curva
L reflete a claridade antes dos ajustes Lab. Esta curva permite que
controles a claridade sem afetar a cor.

Uma curva em forma de S aplicada ao canal L aumenta o contraste da
imagem. Ao mesmo tempo, isto leva a uma aparência perceptivamente
dessaturada. Ajustes da cromaticidade podem ser usados para compensar
este efeito.  

### Curvas "a" e "b"

As curvas "a" e "b" permitem controlar os canais de saída "a" e "b"
baseado nos canais de entrada "a" e "b" respectivamente,, a=f(a) e
b=f(b).

Conforme indicado pelas barras coloridas, a curva "a" permite alternar
as cores entre verde e magenta, e a curva "b" para alternar entre azul e
amarelo. Isto pode ser usado para aplicar efeitos de tonalidade de
cores.  

#### Tonificação de Cor em Preto e Branco

A tonificação de cor de uma imagem em preto-e-branco pode ser feita
usando um de dois métodos: o método recomendado e mais intuitivo é a
ferramenta [Tonificação de
Cor](Color_Toning/pt#Black_and_White.md) junto com a ferramenta
Preto e Branco. O outro método, menos poderoso, é usar as curvas a\* e
b\* da ferramenta Ajustes L\*a\*b\* quando a imagem é desaturada. A
razão pela qual ainda descrevemos como fazer isso sem usar as
ferramentas Preto e Branco e Tonificação de Cor é que estas ferramentas
são adições relativamente novas ao RawTherapee, e talvez estejas usando
uma versão mais antiga que não possui estas ferramentas, ou então
estejas curioso sobre quais são suas opções.

Leia sobre tonificação de cor de uma imagem em preto e branco da maneira
recomendada na página da ferramenta [Tonificação de
Cor](Color_Toning/pt#Black_and_White.md); esta seção descreve
como fazer isso usando as curvas a\* e b\*.

Primeiro precisas transformar a imagem em preto e branco. Faça isto
usando qualquer um dos métodos disponíveis: usando a ferramenta Preto e
Branco ou diminuindo a saturação na ferramenta Exposição, ou diminuindo
a cromaticidade na ferramenta Ajustes L\*a\*b\*. Cada ferramenta levará
a um efeito diferente, pois elas funcionam de maneiras diferentes e em
diferentes espaços de cor. É só uma questão de gosto. Quando a imagem é
reduzida para a escala de cinza, podes dar um tom à imagem usando as
curvas a\* e b\*. Para copiar apenas a tonificação de cor de uma imagem
para outra, copie o perfil de processamento atual para a área de
transferência ![Image:Gtk-copy.png](Gtk-copy.png "Image:Gtk-copy.png"),
em seguida, cole-o parcialmente ou clicando com o botão direito do mouse
numa foto no *Navegador de Arquivo* e selecionando "*Operações de Perfil
de Processamento \> Colar parcial*", ou da guia *Editor de Imagem* por
Ctrl+clicando em "*Colar o perfil da área de transferência*"
[image:Gtk-paste.png](image:gtk-paste.png) para colar apenas
a seção *Ajustes L\*a\*b\** do perfil. Observe que outros ajustes nas
seções *Ajustes L\*a\*b\** também serão colados. Como alternativa, as
curvas a\* e b\* podem ser copiadas e coladas individualmente. Esse é
outro motivo para usar o método recomendado, porque é mais fácil, mais
preciso, copiar e colar das ferramentas Tonificação de Cor e Preto e
Branco.  

### Curva LH

![](Lab_LH_BA.jpg "Lab_LH_BA.jpg") A curva LH (claridade de acordo com
matiz) permite modificar a claridade com base no matiz. Para clarear as
cores do matiz específico, mova o ponto desejado na curva LH para cima e
para escurecer para baixo.  

### Curva CH

![](Lab_CH_BA1.jpg "Lab_CH_BA1.jpg") A curva CH (cromaticidade de acordo
com matiz) permite controlar a cromaticidade da saída baseada no matiz
de entrada, C=f(H). Usando-a podes facilmente impulsionar ou abafar
somente um intervalo selecionado de cores.  

### Curva HH

![](Lab_HH_BA.jpg "Lab_HH_BA.jpg") A curva HH (matiz de acordo com
matiz) permite alterar o matiz para um matiz especificado. Por exemplo,
pode-se mudar os vermelhos para ficarem mais alaranjados movendo o ponto
vermelho para cima até que a linha horizontal grossa que aparece quando
o ponto está sendo arrastado se torne a cor que desejas. O RawTherapee
possui duas curvas HH, uma nas ferramentas Lab na guia Expoição e uma na
ferramenta HSV na guia Cor. A curva de HH nas ferramentas Lab tem um
alcance mais restrito comparado com a curva HH no equalizador HSV, para
permitir ajustes mais finos. O intervalo está entre a cor anterior e a
seguinte, por exemplo, verde pode ser alterado dentro do intervalo de
amarelo e azul (como podes ver na curva na imagem acima). Isto é útil,
por exemplo, para afinar a aparência do tom da pele, removendo uma
aparência esverdeada pálida, mudando os vermelhos e amarelos um pouco
para magenta.  

### Curva CC

A curva CC (cromaticidade de acordo com cromaticidade) permite controlar
a cromaticidade da saída baseada na cromaticidade da entrada, C=f(C). O
histograma na curva CC reflete a cromaticidade antes do ajuste. Isto
permite que ajustes separadamente a cromaticidade de pixels de baixa e
alta saturação, para que possas impkusionar a saturação onde necessário,
sem causar zonas saturadas para cortar.

Image:Lab_CC_BA1.jpg\|Impulsionar a baixa cromaticidade, abafar a alta
cromaticidade. Image:Lab_CC_BA2.jpg\|Abafar a baixa cromaticidade.
Image:Lab_CC_BA3.jpg\|Abafar a baixa cromaticidade.

Podes usar o botão Mostrar/Ocultar histograma de cromaticidade
![Image:HistChro.png](HistChro.png "Image:HistChro.png") além do
histograma para ajudá-lo a ver os efeitos dos seus ajustes da curva CC
no histograma e para ajudá-lo a encontrar o valor máximo antes de
começares a recortar as cores.

Image:Lab_CC_hist_neutral.png\|Histograma de cromaticidade suave com
curva CC neutra. Image:Lab_CC_hist_clipped.png\|Histograma de
cromaticidade cravado com curva CC muito forte.

As capturas de tela mostram como o histograma de cromaticidade se parece
com a imagem intocada e o que acontece quando aumentas demais a
cromaticidade (podes fazer isto usando o controle deslizante
Cromaticidade ou, como na captura de tela, deslizando o ponto superior
direito da curva CC para a esquerda. Segurar a tecla Shift enquanto
deslizas o ponto irá ajudá-lo a manter o ponto no topo).

Para encontrar o máximo impulso de cromaticidade que podes aplicar sem
causar picos desagradáveis, que aparecerão como repentinas regiões
planas de cor na imagem, semelhante à posterização, tudo o que precisas
fazer é clicar em Mostrar/Ocultar histograma de cromaticidade se não
tiver feito isso e, em seguida, lentamente, impulsione a cromaticidade
até perceberes que o histograma começa a cravar. A curva não precisa ser
linear, claro.

### Curva LC

A curva LC (claridade de acordo com cromaticidade) permite controlar a
claridade de saída baseada na cromaticidade de entrada, L=f(C). Podes
usá-la em retratos para clarear o tom da pele

Image:Lab LC BA1.jpg\|Clarear zonas de baixa cromaticidade. Image:Lab LC
BA2.jpg\|Clarear tons de pele.

A ação da curva LC é modulada pela caixa de seleção *Restringir LC para
vermelho e tons de pele*. Assim, a curva LC fornece um controle de
imagem complexo, alterando a claridade baseada na cromaticidade da
imagem e também visando um intervalo especificado de matizes. Com esta
opção ativada, somente a claridade de tons vermelhos e de cor de pele
são afetados, por exemplo, permitindo que faças a cor da pele mais justa
e esconda rugas e manchas enquanto preserva a cor das roupas do modelo e
do fundo. Quando está desativada, a curva LC atua em outras cores
também.

A coloração da barra no eixo horizontal da curva LC muda para refletir
quais cores a curva se aplica, conforme escolhido pelo estado da caixa
de seleção Restringir LC para vermelho e tons de pele.

### Curva CL

A curva CL (cromaticidade de acordo com claridade) permite controlar a
cromaticidade da saída baseada na claridade da entrada, C = f (L). Ela
permite que controles separadamente a cromaticidade das regiões da
imagem com base em sua claridade, assim podes, por exemplo, diminuir a
cromaticidade das sombras se elas tiverem ruidos ou para fins
artísticos, ou aumentar a cromaticidade de tons escuros e médios sem
afetar o brilho do céu.

Image:Lab CL BA1.jpg\|Aumentar a cromaticidade das áreas de luz sem
saturar as sombras. Image:Lab CL BA2.jpg\|A cromaticidade dos tons
escuros e médios aumentou sem saturar o céu.
