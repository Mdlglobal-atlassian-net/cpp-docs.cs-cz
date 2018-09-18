---
title: Bitová pole jazyka C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c43823f996bfe931499aa7bd08ad5f9207f102bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090578"
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C

Kromě deklarátory členů struktury nebo sjednocení může být deklarátorem struktury také zadaný počet bitů, nazývaný "bitové pole." Jeho délka je nastavena od deklarátor pro název pole dvojtečkou. Bitové pole je interpretován jako s integrálním typem.

## <a name="syntax"></a>Syntaxe

*Struktura declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *deklarátor*<sub>optimalizované</sub> **:** *konstantního výrazu.*

*Konstantní výraz* Určuje šířku pole v bitech. *Specifikátor typu* pro `declarator` musí být `unsigned int`, **znaménkem**, nebo `int`a *konstantní výraz* musí být nezáporné celočíselná hodnota. Pokud je hodnota nula, deklarace nemá žádné `declarator`. Pole Bitová pole ukazatelů na bitová pole a funkce, která vrátí bitová pole nejsou povoleny. Volitelný `declarator` názvy bitové pole. Bitová pole lze deklarovat pouze v rámci struktury. Operátor address-of (**&**) nelze použít na komponenty bitového pole.

Nepojmenované bitové pole nemůže být odkazován, a jejich obsah v době běhu nepředvídatelné. Může se použít jako "fiktivní" pole, pro účely zarovnání. Nepojmenované bitové pole, jehož šířku je zadaný jako 0 zaručuje úložiště pro člena v následujících *struct-declaration-list* začíná `int` hranic.

Bitová pole musí být dostatečně dlouhá, aby obsahují bitový vzor. Například tyto dva příkazy nejsou platné:

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

Tento příklad definuje dvourozměrné pole struktury s názvem `screen`.

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

Pole obsahuje 2 000 prvků. Každý prvek je struktury jednotlivých, který obsahuje čtyři členy bitových polí: `icon`, `color`, `underline`, a `blink`. Velikost struktury je o dva bajty.

Bitová pole mají stejnou sémantiku jako typ celé číslo. To znamená, že bitové pole se používá ve výrazech stejným způsobem jako proměnnou stejné základní typ by použít, bez ohledu na to, kolik bitů v bitové pole.

**Specifické pro Microsoft**

Bitová pole, které jsou definované jako `int` je považován za podepsaný. Rozšíření standardu ANSI C společnosti Microsoft umožňuje `char` a **dlouhé** typy (obojí **podepsané** a `unsigned`) u bitových polí. Nepojmenované bitové pole se základním typem **dlouhé**, **krátký**, nebo `char` (**podepsané** nebo `unsigned`) vynutí zarovnání na hranici vhodné základního typu.

Bitová pole jsou přiděleny v rámci celé číslo z nejméně významné nejvýznamnější bit. V následujícím kódu

```
struct mybitfields
{
    unsigned short a : 4;
    unsigned short b : 5;
    unsigned short c : 7;
} test;

int main( void );
{
    test.a = 2;
    test.b = 31;
    test.c = 0;
}
```

bity by být uspořádány takto:

```
00000001 11110010
cccccccb bbbbaaaa
```

Jelikož procesory řady 8086 ukládají nižší bajt celočíselných hodnot před vyšší bajt, na celé číslo `0x01F2` výše by být uloženy ve fyzické paměti jako `0xF2` následovaný `0x01`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarace struktury](../c-language/structure-declarations.md)