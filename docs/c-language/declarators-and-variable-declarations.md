---
title: Deklarátor a deklarace proměnné
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234518"
---
# <a name="declarators-and-variable-declarations"></a>Deklarátor a deklarace proměnné

Zbytek této části popisuje formulář a význam deklarací pro typy proměnných shrnuté v tomto seznamu. Konkrétně tyto části vysvětlují, jak deklarovat následující:

|Typ proměnné|Popis|
|----------------------|-----------------|
|[Jednoduché proměnné](../c-language/simple-variable-declarations.md)|Proměnné s jednou hodnotou s typem integrálu nebo s plovoucí desetinnou čárkou|
|[Pole](../c-language/array-declarations.md)|Proměnné složené z kolekce elementů se stejným typem|
|[Ukazatele](../c-language/pointer-declarations.md)|Proměnné, které odkazují na jiné proměnné a obsahují umístění proměnných (ve formě adres) místo hodnot|
|[Proměnné výčtu](../c-language/c-enumeration-declarations.md)|Jednoduché proměnné s celočíselným typem, které uchovávají jednu hodnotu ze sady pojmenovaných celočíselných konstant.|
|[Struktury](../c-language/structure-declarations.md)|Proměnné složené z kolekce hodnot, které mohou mít různé typy|
|[Sjednocení](../c-language/union-declarations.md)|Proměnné složené z několika hodnot různých typů, které zabírají stejný prostor úložiště|

Deklarátor je část deklarace, která určuje název, který se má do programu začlenit. Může obsahovat modifikátory, jako je <strong>\*</strong> například (ukazatel na) a jakékoli klíčové slovo konvence volání společnosti Microsoft.

**Specifické pro Microsoft**

V deklarátor

```C
__declspec(thread) char *var;
```

`char`je specifikátor typu `__declspec(thread)` a `*` jsou modifikátory a `var` je název identifikátoru.

**Specifické pro konec Microsoftu**

Deklarátory použijete k deklaraci polí hodnot, ukazatelů na hodnoty a funkcí, které vracejí hodnoty zadaného typu. Deklarátory se zobrazí v deklaracích Array a pointer popsaných dále v této části.

## <a name="syntax"></a>Syntaxe

*deklarátor*:<br/>
&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*přímý – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *deklarátor*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***[** opt *-Expression*<sub>opt</sub> **]**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct – deklarátor*  **(**  *parametr-Type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(** souhlas se*seznamem identifikátorů*<sub>opt</sub> **)**    

*ukazatel*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*kvalifikátor typu – seznam –*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Type-kvalifikátor – ukazatel na seznam*<sub>výslovných</sub> *pointer*

*typ – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kvalifikátor typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kvalifikátor typu – kvalifikátor typu seznamu*

> [!NOTE]
> Podívejte se na syntaxi pro *deklaraci* v tématu [Přehled deklarací](../c-language/overview-of-declarations.md) nebo [Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md) pro syntaxi, která odkazuje na *deklarátor*.

Když se deklarátor skládá z neupraveného identifikátoru, deklarovaná položka má základní typ. Pokud se zobrazí hvězdička (<strong>\*</strong>) nalevo od identifikátoru, je typ změněn na typ ukazatele. Je-li identifikátor následován závorkami (**[]**), je typ změněn na typ pole. Pokud je identifikátor následován závorkami, je typ změněn na typ funkce. Další informace o interpretaci přednosti v deklaracích naleznete v tématu [Interpretace složitějších deklarátory](../c-language/interpreting-more-complex-declarators.md).

Každý deklarátor deklaruje alespoň jeden identifikátor. Deklarátor musí zahrnovat specifikátor typu, aby bylo možné dokončit deklaraci. Specifikátor typu poskytuje typ prvků typu pole, typ objektu adresované typem ukazatele nebo návratový typ funkce.

Deklarace [polí](../c-language/array-declarations.md) a [ukazatelů](../c-language/pointer-declarations.md) jsou podrobněji popsány dále v této části. Následující příklady ilustrují několik jednoduchých forem deklarátory:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Specifické pro Microsoft**

Kompilátor jazyka Microsoft C neomezuje počet deklarátory, které mohou upravovat typ aritmetické, struktury nebo sjednocení. Počet je omezen pouze dostupnou pamětí.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
