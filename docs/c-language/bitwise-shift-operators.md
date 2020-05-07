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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326024"
---
# <a name="bitwise-shift-operators"></a>Operátory bitového posunutí

Operátory posunutí posunou první operand vlevo (**&lt;**) nebo Right (**>>**) podle počtu pozic, které určuje druhý operand.

## <a name="syntax"></a>Syntaxe

*SHIFT-Expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového výrazu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového* výrazu *SHIFT-Expression* ** &lt; **<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz doplňkového* výrazu *SHIFT-Expression* **>>**

Oba operandy musí být integrální hodnoty. Tyto operátory provádějí obvyklé aritmetické převody; Typ výsledku je typ levého operandu po převodu.

Pro Leftward Shift jsou uvolněné pravá bity nastavené na 0. Pro rightward Shift se uvolněné levé bity vyplní na základě typu prvního operandu po převodu. Pokud je `unsigned`typ, je nastaven na hodnotu 0. V opačném případě jsou vyplněny kopiemi bit znaménka. U operátorů posunutí doleva bez přetečení příkazu

```C
expr1 << expr2
```

je ekvivalentem násobení podle 2<sup>Výraz2</sup>. Pro operátory pravého posunutí

```C
expr1 >> expr2
```

je ekvivalentem dělení 2<sup>Výraz2</sup> , pokud `expr1` je nepodepsaná nebo má nezápornou hodnotu.

Výsledek operace posunutí není definován, pokud je druhý operand záporný, nebo pokud je pravý operand větší než nebo roven šířce v bitech s povýšenou hodnotou levého operandu.

Vzhledem k tomu, že převody prováděné operátory Shift neposkytují podmínky přetečení nebo podtečení, mohou být informace ztraceny, pokud výsledek operace posunutí nelze reprezentovat v typu prvního operandu po převodu.

```C
unsigned int x, y, z;

x = 0x00AA;
y = 0x5500;

z = ( x << 8 ) + ( y >> 8 );
```

V tomto příkladu `x` se posune vlevo o osm pozic a `y` posune se o osm pozic doprava. Posunuté hodnoty jsou přidány, dávají 0xAA55 a přiřazeny `z`.

Posunutí záporné hodnoty k pravému výsledku vrátí polovinu původní hodnoty a zaokrouhlí dolů. Například-253 (binární 11111111 00000011) posunutí vpravo o jeden bit vytvoří-127 (binární 11111111 10000001). Kladné 253 posune doprava k výrobě + 126.

Posun doprava zachovává bit znaménka. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán.

## <a name="see-also"></a>Viz také

[Operátory posunu vlevo a vpravo (>> a <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)
