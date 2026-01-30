---
title: The Floating Point Engine
contributors:
  - DigitalPix
  - DrSlony
tags:
  - 'General Information'
---

O RawTherapee 4 faz todos os cálculos em notação precisa de 32 bits de
[ponto flutuante](https://en.wikipedia.org/wiki/Floating_point)(em
contraste com os integrais de 16 bits, usado em muitos outros
conversores como o [dcraw](https://en.wikipedia.org/wiki/Dcraw) e também
no RawTherapee até a versão 3.0) para que nada seja arredondado e
perdido.

Conversores clássicos funcionam com números integrais de 16 bits. Um
canal de pixel tem valores variando de 0 a 65535 em 16 bits (para
aumentar a precisão dos conversores, usualmente se multiplica os valores
da câmera de 12 a 14 bits para preencher a faixa de 16 bits). Os números
não têm frações, portanto, por exemplo, não há valor entre 102 e 103. Em
contraste, os números de ponto flutuante armazenam um valor em um
intervalo muito mais amplo com uma precisão de significantes 6 a 7
dígitos. Isso ajuda especialmente nos realces, onde intervalos mais
altos podem ser recuperados. Permite que resultados intermediários na
cadeia de processamento excedam ou subtraiam temporariamente sem perder
informações. Os valores fracionários possíveis também ajudam a suavizar
as transições de cores para prevenir faixas coloridas. E não menos
importante, o ponto flutuante torna a vida mais fácil para os
desenvolvedores que não precisam se preocupar tanto com erros de
arredondamento ou recorte ao desenvolver algoritmos de imagem para o
RawTherapee.

A desvantagem é o espaço RAM que os números de ponto flutuante exigem,
que é exatamente o dobro dos integrais de 16 bits. Juntamente com a
crescente contagem de megapixels das câmeras digitais, um sistema
operacional de 32 bits pode facilmente ficar sem memória e causar falha
no RawTherapee. Portanto, um sistema operacional de 64 bits é altamente
recomendado para estabilidade. Se tiveres problemas para executar o RT
num sistema de 32 bits, tente o seguinte:

- Como regra geral, deves evitar ter pastas com muitas fotos raw, pois
  cada foto ocupa a memória quando exibida na guia Navegador de Arquivos
  do RawTherapee. Tente não ter mais de 100 fotos por pasta.
- O RawTherapee usa mais memória RAM enquanto estás usando a guia
  Navegador de Arquivos, portanto, evite abrir essa guia enquanto
  estiver processando as fotos.
- Use 4-Gigabyte Tuning no Windows. Veja "[4-Gigabyte Tuning: BCDEdit
  and
  Boot.ini](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)"
  para uma explicação do que é e descubra como fazer isso lendo o guia
  "[Como definir a opção de inicialização /3GB no Windows XP e
  Vista](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)".
- Feche outros programas enquanto trabalha no RawTherapee.
- Feche a guia do Editor de Imagem quando terminar de editar para
  liberar memória.
- Desligue o "início automático" na fila em lote. Somente adicione fotos
  à fila em lote quando terminar de editar todas e, em seguida,
  inicie-a. Use a fila em lote, não use o botão salvar imediato.
- Altere para um diretório com poucas ou nenhuma foto antes de iniciar a
  fila em lote.
- Podes liberar alguma memória excluindo (ou movendo para uma pasta
  diferente ou renomeando para algo como .unusedicc) todos os perfis
  .icc em perfis icc\entrada para as câmeras que não usas.
- Assegure-se de que o diretório de Quadro Escuro e o diretório Campo
  Plano em Preferências não apontem para pastas que contenham arquivos
  raw se não usares quadros escuros ou campos planos.
- As ferramentas mais intensivas em memória são [Mapeamento de
  Tom](Tone_Mapping/pt.md), [Contraste por Níveis de
  Detalhe](Contrast_by_Detail_Levels/pt.md) e [Reconstrução de
  Realce](Exposure/pt#Highlight_Reconstruction.md) usando
  "Propagação de Cor", então talvez seja necessário evitar usá-los se
  tua máquina e sistema operacional não forem padrão.

[Category:General](category:general)
