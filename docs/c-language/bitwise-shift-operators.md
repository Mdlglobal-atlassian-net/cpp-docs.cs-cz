---
title: Operátory bitového posunutí
ms.date: 10/18/2018
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
ms.openlocfilehash: acf31fbfbe534e3f7eba1492c5aaf173fcb8b31c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150412"
---
# <a name="bitwise-shift-operators"></a>Operátory bitového posunutí

Operátory posunutí posunutí prvního operandu vlevo (**&lt;&lt;**) nebo doprava (**>>**) počet pozic určuje druhého operandu.

## <a name="syntax"></a>Syntaxe

*shift-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression* **&lt;&lt;** *additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression* **>>** *additive-expression*

Oba operandy musí být integrální hodnoty. Tyto operátory provádějí obvyklé aritmetické převody Typ výsledku je typ levého operandu po převodu.

Pro leftward staffhubu uvolněných správných bitů nastavené na hodnotu 0. Pro rightward staffhubu jsou vyplněny uvolněných bitů vlevo na základě typu prvního operandu po převodu. Pokud je typ `unsigned`, jsou nastaveny na hodnotu 0. V opačném případě jsou vyplněny hodnotou kopie na bit znaménka. Pro operátory posunutí doleva bez přetečení, příkaz

```C
expr1 << expr2
```

je ekvivalentní k násobení hodnotou 2<sup>Výraz2</sup>. Pro operátory posunutí doprava

```C
expr1 >> expr2
```

je ekvivalentní k dělení 2<sup>Výraz2</sup> Pokud `expr1` je bez znaménka nebo má nezápornou hodnotu.

Výsledek operace posunutí není definován, pokud je druhý operand je záporný nebo pokud pravý operand je větší než nebo rovna šířce v bitech povýšeného operandu vlevo.

Protože převody provést podle přesun neposkytují operátory přetečení nebo podmínky podtečení, informace mohou být ztraceny, pokud výsledek operace posunutí nelze reprezentovat v typu prvního operandu po převodu.

```C
unsigned int x, y, z;

x = 0x00AA;
y = 0x5500;

z = ( x << 8 ) + ( y >> 8 );
```

V tomto příkladu `x` je posunuta doleva osm pozic a `y` je posunuté přímo osm pozic. Přidání posunuté hodnot, poskytuje 0xAA55 a přiřazená `z`.

Posunutí záporné hodnoty doprava dává polovinu původní hodnoty zaokrouhlené dolů. Například-253 (binární 11111111 00000011 posunutá) posunuta jeden bit doprava vytvoří-127 (binárně 11111111 10000001). Pozitivní 253 se posune doprava a vytvoří hodnotu + 126.

Posun doprava zachovává bit znaménka. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán.

## <a name="see-also"></a>Viz také:

[Operátory posunu vlevo a vpravo (>> a <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)
