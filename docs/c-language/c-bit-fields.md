---
title: Bitová pole jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: 62c982fa078182cb1902b6770f0a3713ca4ff7a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326492"
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C

Kromě deklarátory pro členy struktury nebo sjednocení může mít deklarátor struktury také zadaný počet bitů nazývaný "bitové pole". Jeho délka je nastavená na deklarátor pro název pole dvojtečkou. Bitové pole je interpretováno jako integrální typ.

## <a name="syntax"></a>Syntaxe

*Struktura – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ – specifikátor* *deklarátor*<sub>opt</sub> **:** *konstantní výraz*

*Konstantní výraz* určuje šířku pole v bitech. *Specifikátor typu* `declarator` pro musí být `unsigned int`, **signed int**nebo `int`a *konstantní výraz* musí být nezáporná celočíselná hodnota. Pokud je hodnota nula, deklarace nemá žádný `declarator`. Pole bitových polí, ukazatelů na bitová pole a funkce vracející bitová pole nejsou povoleny. Volitelné `declarator` názvy bitového pole. Bitová pole lze deklarovat pouze jako součást struktury. Operátor address-of (**&**) nelze použít na komponenty bitového pole.

Nepojmenovaná bitová pole nemohou být odkazována a jejich obsah v době běhu je nepředvídatelné. Je možné je použít jako "fiktivní" pole pro účely zarovnání. Nepojmenované bitové pole, jehož šířka je zadána jako 0, zaručuje, že úložiště pro člena, který následuje, v *seznamu struct-Declaration-list* začíná na `int` hranici.

Bitová pole musí být také dostatečně dlouhá, aby obsahovala bitový vzorek. Například tyto dva příkazy nejsou platné:

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

Tento příklad definuje dvojrozměrné pole struktur s názvem `screen`.

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

Pole obsahuje 2 000 prvků. Každý prvek je jednotlivá struktura obsahující čtyři členy bitových polí `icon`:, `color`, `underline`a. `blink` Velikost každé struktury je dva bajty.

Bitová pole mají stejnou sémantiku jako typ Integer. To znamená, že bitové pole se používá ve výrazech přesně stejným způsobem jako proměnná stejného základního typu, a to bez ohledu na to, kolik bitů se v bitovém poli používá.

**Specifické pro Microsoft**

Bitová pole definovaná `int` jako jsou považována za podepsaná. Rozšíření společnosti `char` Microsoft pro standard ANSI C povoluje a **dlouhé** typy ( **podepsaná** i `unsigned`) pro bitová pole. Nepojmenovaná bitová pole se základním typem **Long**, **short**nebo `char` (**podepsaná** nebo `unsigned`) vynuťte zarovnání na hranici odpovídající základnímu typu.

Bitová pole jsou přidělována v rámci celého čísla z nejméně významných bitů. V následujícím kódu

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

bity budou uspořádány takto:

```
00000001 11110010
cccccccb bbbbaaaa
```

Vzhledem k tomu, že řada procesorů 8086 ukládá nízké bajty celočíselných hodnot před horním bajtem, bude celé číslo `0x01F2` výše uloženo ve `0xF2` fyzické paměti `0x01`jako následováno.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarace struktury](../c-language/structure-declarations.md)
