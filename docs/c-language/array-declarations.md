---
title: Deklarace pole
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147773"
---
# <a name="array-declarations"></a>Deklarace pole

"Pole deklarace" názvů poli a určuje typu jeho elementů. Můžete také definovat počet prvků v poli. Proměnná typu pole je považován za ukazatel na typ prvků pole.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *init-declarator-list*<sub>optimalizované</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=** *inicializátor*

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*přímé declarator*: /\* deklarátorem funkce \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **[** *konstantní výraz*<sub>optimalizované</sub> **]** 

Protože *konstantního výrazu* je volitelný, má dvě různými formami syntaxe:

- První formulář definuje proměnnou pole. *Konstantní výraz* argument v hranatých závorkách určuje počet prvků v poli. *Konstantní výraz*, pokud jsou k dispozici, musí mít celočíselný typ a hodnotu větší než nula. Každý prvek má typ daný *specifikátor typu*, což může být libovolný typ s výjimkou `void`. K elementu pole nemůže být typ funkce.

- Druhý typ deklaruje proměnnou, která je definována jinde. Vynechá *konstantní výraz* argument v závorkách, ale ne závorky. Tento formulář můžete použít jenom v případě, že jste dříve inicializovat pole deklarovaný jako parametr, nebo ji deklarovali jako odkaz na pole explicitně definovány jinde v programu.

V obou formách *direct-declarator* názvy proměnných a může změnit typ proměnné. Hranaté závorky (**[] č.**) následující *direct-declarator* upravit deklarátor na typ array.

Kvalifikátory typu se může objevit v deklaraci objektu typu pole, ale v kvalifikátorech použít pro prvky spíše než pole samotného.

Pomocí následujících deklarátor pole se seznamem konstantní výrazy v závorkách v tomto formuláři je možné deklarovat pole polí (pole "multidimenzionální"):

> *Specifikátor typu* *deklarátor* **[** *konstantní výraz* **]** **[** *konstantní výraz* **]** ...

Každý *konstantní výraz* v závorkách definuje počet prvků v dané dimenzi: dvojrozměrné pole mají dvě výrazy v závorkách, mají tři trojrozměrného pole a tak dále. Máte-li inicializovat pole deklarovaný jako parametr, nebo ji deklarovali jako odkaz na pole explicitně definovány jinde, můžete vynechat první konstantní výraz v programu.

Můžete definovat pole ukazatelů na různé typy objektů pomocí složitých deklarátorů, jak je popsáno v [interpretace složitých Deklarátorů](../c-language/interpreting-more-complex-declarators.md).

Pole jsou uložena po řádku. Například následující pole je tvořen dvěma řádky se třemi sloupci:

```C
char A[2][3];
```

Tři sloupce na prvním řádku se ukládají nejprve, za nímž následuje tři sloupce ve druhém řádku. To znamená, že se poslední dolní index mění nejrychleji.

K odkazování na jednotlivý prvek pole, použijte výraz dolního indexu, jak je popsáno v [Příponové operátory](../c-language/postfix-operators.md).

## <a name="examples"></a>Příklady

Tyto příklady ilustrují deklarace pole:

```C
float matrix[10][15];
```

Dvourozměrné pole s názvem `matrix` má 150 prvky, každý s **float** typu.

```C
struct {
    float x, y;
} complex[100];
```

Toto je deklaraci pole struktur. Toto pole má 100 prvků. Každý prvek je struktura obsahující dva členy.

```C
extern char *name[];
```

Tento příkaz deklaruje typ a název pole ukazatelů na `char`. Skutečnou definici `name` dochází jinde.

**Microsoft Specific**

Typ celého čísla potřebných k uložení maximální velikost pole je velikost **size_t**. Definovaný v souboru hlaviček STDDEF. H, **size_t** je `unsigned int` s rozsahem 0x00000000 k 0x7CFFFFFF.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
