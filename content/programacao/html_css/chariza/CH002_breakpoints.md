---
title: CH002 - Breakpoints
description: Settings - Pontos de interrupção e tamanho de tela.
---

## Introdução

Estamos utilizando [SASS](https://sass-lang.com){:target="_blank"} o que facilita muito na hora de codar.

Seguindo o ITCSS temos uma primeira camada que foi nomeada de _settings_ e aqui vamos guardar todas as variáveis que vão servir para configurar nosso framework.

O primeiro arquivo sera o de _breakpoints_.

Usei 3 frameworks de base para aprender como tratam esse tipo de assunto, o [Bootstrap](https://getbootstrap.com/docs/5.3/layout/breakpoints/){:target="_blank"}, [Tailwind](https://tailwindcss.com/docs/responsive-design){:target="_blank"} e [Bulma](https://bulma.io/documentation/overview/responsiveness/){:target="_blank"}.

## Mobile First

É verdade que estou mais acostumado com o Bulma mais escolhi me basear por ele por causa do conceito [_Mobile First_](https://desenvolvimentoparaweb.com/design/regras-web-design-responsivo/){:target="_blank"} que consiste em programar 
a partir do mobile para o desktop, modificando o layout somente quando a tela aumenta e não ao contrario.

Usei as medidas de responsividade as própria [documentação](https://bulma.io/documentation/overview/responsiveness/){:target='_blank'} do Bulma (já que são de um grande framework vão funcionar bem), as variáveis ficaram dessa forma :

> - mobile: até de 768px.
> - tablet: a partir 769px.
> - desktop: a partir 1024px.
> - widescreen: a partir 1216px.
> - fullhd: a partir 1408px.

Como a nossa referencia é o mobile as _media query's_ entram em ação conforme a tela vai se expandindo.

A sequânica da menor medida para a maior ficou assim : 

> Mobile - Tablet - Desktop - Widescreen - FullHD.

## Breakpoints

No site do DPW tem um artigos sobre [breakpoints](https://desenvolvimentoparaweb.com/css/css-breakpoints-maneira-correta/){:target='_blank'} e [media query](https://desenvolvimentoparaweb.com/css/media-queries/){:target='_blank'}.

Consideramos que tudo abaixo de 768px é mobile (celular ou tablet) e acima é desktop.

Logo o arquivo com a medidas os breakpoints ficou assim :

```sass
$mobile: 768px;
$tablet: 769px;
$desktop: 1024px;
$widescreen: 1216px;
$fullhd: 1408px;

// up
@mixin mobile {
    @media screen and (max-width: $mobile) {
        @content;
    }
}

@mixin tablet {
    @media screen and (min-width: $tablet) {
        @content;
    }
}

@mixin desktop {
    @media screen and (min-width: $desktop) {
        @content;
    }
}

@mixin wide {
    @media screen and (min-width: $widescreen) {
        @content;
    }
}

@mixin full {
    @media screen and (min-width: $fullhd) {
        @content;
    }
}

// between
@mixin tablet-only {
    @media screen and (min-width: $tablet) and (max-width: #{$desktop - 1}){
        @content;
    }
}

@mixin desktop-only {
    @media screen and (min-width: $desktop) and (max-width: #{$widescreen - 1}) {
        @content;
    }
}

@mixin wide-only {
    @media screen and (min-width: $widescreen) and (max-width: #{$fullhd - 1}) {
        @content;
    }
}

// below
@mixin desktop-down {
    @media screen and (max-width: $desktop) {
        @content;
    }
}

@mixin wide-down {
    @media screen and (max-width: $widescreen) {
        @content;
    }
}

@mixin full-down {
    @media screen and (max-width: $fullhd) {
        @content;
    }
}
```

