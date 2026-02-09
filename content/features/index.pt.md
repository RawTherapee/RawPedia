---
title: Features
contributors:
  - DigitalPix
  - DrSlony
tags:
  - 'General Information'
weight: 2
---

## Funcionalidades Gerais

- Todas as funcionalidades padrão que esperarias de um desenvolvedor raw
  e muito mais,
- Uma fila de processamento em lote para fazer ajustes na foto o mais
  rápido possível, deixando o trabalho da CPU na fila para mais tarde,
- Mecanismo do [Ponto
  flutuante](https://en.wikipedia.org/wiki/Floating_point) - o único
  desenvolvedor raw no mercado que faz todos os cálculos em notação
  precisa de ponto flutuante para que nada seja arredondado e perdido,
- Otimização de
  [SSE](https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions) para
  melhor desempenho em CPUs modernas,
- [Gerenciamento de cor](https://en.wikipedia.org/wiki/Color_management)
  usando o sistema de gerenciamento de cores
  [LittleCMS](https://en.wikipedia.org/wiki/LittleCMS) v2 para manuseio
  de cores mais preciso, proporcionando controle sobre o espaço de cores
  de trabalho e de saída,
- Suporte para leitura e mapeamento de tom de imagens HDR de ponto
  flutuante de 16 bits, 24 bits e 32 bits no formato DNG,
- Navegador de arquivos com marcação colorida, pesquisa (por texto
  correspondente ao nome do arquivo), filtragem de metadados (por tipo
  de arquivo, modelo de câmera, modelo de lente, parâmetros de foto),
- Suporte para perfis de cores DCP e
  [ICC](https://en.wikipedia.org/wiki/ICC_profile), para cores precisas
  ou para replicar a “aparência da câmera” para combinar imagens JPEG
  fora da câmera,
- Um painel de histórico para ver facilmente quais alterações fizeste e
  voltar para um ponto específico,
- Um painel de instantâneos para trabalhar com várias versões de
  alterações numa foto,
- Uma interface de usuário flexível, onde painéis e alguns elementos
  individuais podem ser adaptados ou ocultados,
- Divida facilmente fotos muito maiores do que a tela graças à
  amplificação da taxa de panoramização, eliminando a necessidade de
  movimentos numerosos e inquietos do mouse,
- Role os painéis de ferramentas usando a roda de rolagem do mouse sem
  se preocupar com o desajuste acidental de qualquer ferramenta ou
  segure a tecla Shift enquanto usa a roda de rolagem do mouse para
  manipular o ajustador por onde o cursor está passando,
- Maximize o espaço da tela clicando com o botão direito do mouse numa
  ferramenta para mantê-la visível enquanto recoloca automaticamente as
  outras,
- Uma visualização Antes\|Depois para comparar sua última alteração a
  qualquer anterior,
- Suporte para perfis de processamento PP3 ([arquivos
  sidecar](https://en.wikipedia.org/wiki/Sidecar_file)), inteiros e
  parciais,
- Mostrar vários canais na visualização: vermelho, verde, azul,
  luminosidade e uma máscara de foco,
- Mostrar vários canais no histograma: vermelho, verde, azul,luminância
  [CIELAB](https://en.wikipedia.org/wiki/Lab_color_space), cromaticidade
  e raw,
- Indicadores de [Recorte de
  cor](https://en.wikipedia.org/wiki/Clipping_(photography)) na
  visualização,
- Exportar Painel com Opções de Exportação Rápida,
- Atalhos de teclado para acelerar o trabalho,
- Suporte de linha de comando para automatizar o RawTherapee usando
  scripts ou chamá-lo de outros programas,
- Suporte para a maioria das câmeras,
- Suporta novos formatos raw simplesmente editando o arquivo
  [camconst.json](camconst.json) em um editor de texto,
- Feedback de áudio para informá-lo quando uma tarefa intensiva da CPU
  for concluída, por ex. quando a fila é processada,
- Preserve [IPTC](https://en.wikipedia.org/wiki/IPTC) e
  [XMP](https://en.wikipedia.org/wiki/Extensible_Metadata_Platform) de
  arquivos pré-marcados,
- Adapte o RawTherapee para usar o esquema de cores da interface do
  sistema e os widgets ou experimente os esquemas de cores
  personalizados fornecidos,
- Localização em quase 30 idiomas.

## Exposição e Funcionalidades de Cor

- A ferramenta Níveis Automáticos ajusta suas fotos para fornecer um bom
  ponto de partida,
- Vários métodos poderosos de recuperação e reconstrução de sombra e
  realce,
- Filtro de Vinheta pós-corte,
- Filtro Graduado (GND),
- Ferramenta de pipeta, que, quando ativada para uma curva específica,
  permite escolher um ponto na visualização da imagem e, em seguida,
  coloca um ponto de ajuste correspondente nessa curva,
- Duas curvas de tom RGB, cada uma com quatro métodos de controle, para
  controle sem precedentes de cores e exposição,
- Ajuste de curva de matiz, saturação e valor (HSV) e vermelho, verde e
  azul (RGB),
- Ajustes de abundância de Lab para controle separado de cores e
  luminância:
  - L\* curva para controlar claridade,
  - a\* curva para controlar a posição de uma cor entre vermelho/magenta
    e verde,
  - b\* curva para controlar a posição de uma cor entre amarelo e azul,
  - LH curva para controlar luminância como função de matiz,
  - CH curva para controlar cromaticidade como função de matiz,
  - HH curva para controlar matiz como função de matiz,
  - CC curva para controlar cromaticidade como função de cromaticidade,
  - LC curva para controlar luminância como função de cromaticidade,
  - CL curva para controlar cromaticidade como função de luminância.
- Evite a mudança de cor usando [correção
  Munsell](https://en.wikipedia.org/wiki/Munsell_color_system),
- Controle de Vibração,
- Preservação de tons de pele naturais,
- [Mapeamento de tom](https://en.wikipedia.org/wiki/Tone_mapping)
  baseado na [decomposição de preservação de
  borda](http://www.cs.huji.ac.il/~danix/epd/) para uma aparência
  natural,
- [Balanço de branco](https://en.wikipedia.org/wiki/White_balance) -
  automático, manual ou de uma ampla variedade de fontes predefinidas,
- Misturador de Canais,
- Conversão Preto e Branco,
- Vários métodos de tonalização de cor,
- Suporte para câmeras
  [monocromáticas](demosaicing/pt#monochrome_cameras)
- Adaptação do modelo de aparência de
  cor[CIECAM02](https://en.wikipedia.org/wiki/CIECAM02) ratificado pela
  Comissão Internacional de Iluminação (CIE) para manter cores precisas
  e, dado um conjunto de parâmetros iniciais de condição de
  visualização, converter a imagem de modo que ela fique com a mesma
  aparência sob as condições de visualização do alvo. O processamento de
  imagem usando o CIECAM02 é ativado por meio de vários métodos, usando
  curvas e controles deslizantes. Várias ferramentas são adaptadas para
  mudar automaticamente para o modo CIECAM02 quando em uso, incluindo
  [Mapeamento de Tom](tone_mapping/pt),
  [Nitidez](sharpening/pt),
  [Defringe](defringe/pt), etc.
- Gerenciamento de cor.

## Funcionalidades Detalhadas

- Vários métodos de nitidez:
  - [Máscara sem nitidez](https://en.wikipedia.org/wiki/Unsharp_mask)
    com um controle deslizante de limite único e poderoso para destacar
    detalhes, evitando halos,
  - [deconvolução
    RL](https://en.wikipedia.org/wiki/Richardson%E2%80%93Lucy_deconvolution)
    para desfazer desfocar,
  - [Bordas](https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en)
    verdadeira nitidez para melhorar as bordas,
  - Microconstraste para melhorar a textura,
  - Contraste por Níveis de Detalhe usando a decomposição wavelet em
    cinco níveis de detalhe.
- Redução de ruído baseada em wavelets muito potentes nos espaços de
  cores RGB e Lab,
- Redução do ruído por impulso para eliminar o ruído do tipo sal e
  pimenta,
- Ferramenta Defringe para eliminação de franjas roxas (ou outra cor).

## Funcionalidades de Transformação

- Correção de perspectiva,
- Suporte ao Perfil de Correção de Lentes Adobe para correção automática
  de distorção, vinheta e aberração cromática,
- Correção de distorção,
- Correção da aberração cromática pós-demosaica,
- Correção de vinheta pré-corte.

## Funcionalidades Raw Pré-Demosaicing

- Vários métodos de demosaicing para começar, espremendo o máximo de
  detalhes possível de sua foto raw:
  - AMaZE,
  - IGV e LMMSE para uso com redução de ruído para evitar padrões de
    labirinto,
  - EAHD,
  - HPHD,
  - VNG4,
  - DCB,
  - AHD,
  - Mono,
  - Rápida.
- Filtro ruído de linha,
- Ajuste de ponto branco e preto,
- Subtração de quadro escuro para eliminar algumas formas de ruído,
- Correção de campo plano para corrigir facilmente o efeito de vinheta,
  a coloração da lente e a poeira do sensor,
- Correção de aberração cromática manual e automática.

[Category:General](category:general)
