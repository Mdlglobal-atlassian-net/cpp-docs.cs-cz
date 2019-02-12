---
title: Návratový typ
ms.date: 11/04/2016
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
ms.openlocfilehash: 3f781e59672764dc518f3c6fad61d4021720362a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148137"
---
# <a name="return-type"></a>Návratový typ

Návratový typ funkce se zavádí velikost a typ hodnoty vrácené funkcí a odpovídá specifikátoru typů ve níže uvedené syntaxe:

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*<sub>optimalizované</sub> *sekvence atributů*<sub>optimalizované</sub> *deklarátor* *seznam deklarací*  <sub>optimalizované</sub> *compound-statement*

/\* *sekvence atributů* je specifické pro Microsoft \*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*Specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Typ void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**plovoucí desetinnou čárkou**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podepsané**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaménka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Název TypeDef*

*Specifikátor typu* můžete zadat všechny základní struktura nebo sjednocení. Pokud není zadána *specifikátor typu*, návratový typ `int` se předpokládá, že.

Návratový typ zadaný v definici funkce musí odpovídat návratový typ v deklaracích funkce jinde v programu. Funkce vrací hodnotu při `return` je proveden příkaz, který obsahuje výraz. Výraz je vyhodnocen, převést na typ vrácené hodnoty, pokud potřebné a vrátilo do bodu, ve kterém byla volána funkce. Pokud funkce je deklarovaná s návratovým typem `void`, návratový příkaz, který obsahuje výraz vygeneruje upozornění a tento výraz není vyhodnocen.

Následující příklady znázorňují – návratové hodnoty funkce.

```C
typedef struct
{
    char name[20];
    int id;
    long class;
} STUDENT;

/* Return type is STUDENT: */

STUDENT sortstu( STUDENT a, STUDENT b )
{
    return ( (a.id < b.id) ? a : b );
}
```

Tento příklad definuje `STUDENT` typ s `typedef` prohlášení a definuje funkci `sortstu` mít `STUDENT` návratového typu. Funkce vybere a vrátí jeden z jejích argumentů dvě struktury. V následných voláních funkce, kompilátor kontroluje, ujistěte se, že typy argumentů jsou `STUDENT`.

> [!NOTE]
> By se zvýšila efektivita předáním ukazatele na strukturu, nikoli celou jejich strukturu.

```C
char *smallstr( char s1[], char s2[] )
{
    int i;

    i = 0;
    while ( s1[i] != '\0' && s2[i] != '\0' )
        i++;
    if ( s1[i] == '\0' )
        return ( s1 );
    else
        return ( s2 );
}
```

Tento příklad definuje funkci, která vrací ukazatel na pole znaků. Funkce přebírá dva znakových polí (řetězec) jako argumenty a vrací ukazatel na kratší dvou řetězců. Ukazatel na pole odkazuje na první prvky pole a jeho typ; Proto je návratový typ funkce na ukazatel na typ `char`.

Není nutné deklarovat funkce s `int` návratový typ před voláním, i když prototypy doporučují tak, aby správný typ kontroly pro argumenty a návratové hodnoty je povolená.

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
