---
title: Deklarace pole
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313542"
---
# <a name="array-declarations"></a>Deklarace pole

"Deklarace pole" pojmenuje pole a určuje typ jeho elementů. Může také definovat počet prvků v poli. Proměnná s typem pole je považována za ukazatel na typ prvků pole.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *init-deklarátor-list*<sub>opt</sub> **;**

*init-deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor-list*  **,**  *init-deklarátor*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicializátor* deklarátor

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*Direct-deklarátor*:/\* A – funkce deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***[** opt *-Expression*<sub>opt</sub> **]**    

Protože je *konstantní výraz* volitelný, syntaxe má dva formuláře:

- První formulář definuje proměnnou pole. Argument *konstantního výrazu* v závorkách určuje počet prvků v poli. *Konstantní výraz*, pokud je přítomen, musí mít celočíselný typ a hodnotu větší než nula. Každý prvek má typ zadaný *specifikátorem typu*, který může být libovolný typ s výjimkou `void`. Prvek pole nemůže být typu funkce.

- Druhý formulář deklaruje proměnnou, která je definována jinde. Vynechá argument *konstantního výrazu* v závorkách, ale ne závorky. Tento formulář můžete použít pouze v případě, že jste již dříve inicializoval pole, deklarováno jako parametr nebo deklarovaného jako odkaz na pole explicitně definované jinde v programu.

V obou formulářích je *Přímá deklarátor* Pojmenovává proměnnou a může změnit typ proměnné. Hranaté závorky (**[]**) následující po *Direct-deklarátor* upraví deklarátor na typ pole.

Kvalifikátory typu mohou být uvedeny v deklaraci objektu typu pole, ale kvalifikátory se vztahují na prvky spíše než pole samotné.

Pole polí (multidimenzionální pole) můžete deklarovat pomocí pole deklarátor se seznamem konstantních výrazů v tomto formuláři v závorkách:

> *Type-specifikátor* *deklarátor* **[** *constant-expression* **]** **[** *konstantní výraz* **]** ...

Každý *konstantní výraz* v závorkách definuje počet prvků v dané dimenzi: dvojrozměrné pole mají dva výrazy v závorkách, trojrozměrné pole má tři a tak dále. První konstantní výraz můžete vynechat, pokud jste pole inicializoval, deklarujete jako parametr nebo jste ho deklarovali jako odkaz na pole explicitně definované jinde v programu.

Můžete definovat pole ukazatelů na různé typy objektů pomocí komplexního deklarátory, jak je popsáno v tématu [Interpretace složitějších deklarátory](../c-language/interpreting-more-complex-declarators.md).

Pole jsou uložena podle řádku. Například následující pole se skládá ze dvou řádků se třemi sloupci:

```C
char A[2][3];
```

Nejprve jsou uloženy tři sloupce prvního řádku a potom tři sloupce druhého řádku. To znamená, že se poslední dolní index mění rychleji.

Chcete-li odkazovat na jednotlivé prvky pole, použijte výraz dolního indexu, jak je popsáno v části [Příponové operátory](../c-language/postfix-operators.md).

## <a name="examples"></a>Příklady

Tyto příklady ilustrují deklarace pole:

```C
float matrix[10][15];
```

Dvojrozměrné pole s názvem `matrix` má 150 prvky, každý má typ **float** .

```C
struct {
    float x, y;
} complex[100];
```

Toto je deklarace pole struktur. Toto pole obsahuje 100 prvků; Každý prvek je struktura obsahující dva členy.

```C
extern char *name[];
```

Tento příkaz deklaruje typ a název pole ukazatelů na `char`. Skutečná definice se `name` vyskytuje jinde.

**Specifické pro Microsoft**

Typ celého čísla potřebného pro uložení maximální velikosti pole je velikost **size_t**. Definováno v hlavičkovém souboru STDDEF. H je **size_t** `unsigned int` s rozsahem 0x00000000 až 0x7CFFFFFF.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
