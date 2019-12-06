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
ms.openlocfilehash: fe9280f434dd6267b03764df2ee663c494f007d8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857031"
---
# <a name="return-type"></a>Návratový typ

Návratový typ funkce vytvoří velikost a typ hodnoty vrácené funkcí a odpovídá specifikátoru typu v následující syntaxi:

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*– atribut<sub>opt</sub> *-SEQ* *deklarátor* *deklarace-list*<sub></sub> <sub>opt –</sub> *složený* příkaz

atribut /\* *– SEQ* je specifický pro Microsoft \*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*třídy úložiště* -specifikátory *deklarace specifikátor-* <sub></sub> specifikátory<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *specifikátoru typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *kvalifikátoru typu* -deklarace

*specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**znak**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podepsané**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaménka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-Union-specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor enum*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-Name*

*Specifikátor typu* může specifikovat jakýkoli typ základní, struktury nebo sjednocení. Pokud nezahrnete *specifikátor typu*, předpokládá se návratový typ `int`.

Návratový typ zadaný v definici funkce musí odpovídat návratový typ v deklaracích funkce jinde v programu. Funkce vrací hodnotu, když je proveden příkaz `return` obsahující výraz. Výraz je vyhodnocen, převeden na typ návratové hodnoty v případě potřeby a vrácen do bodu, ve kterém byla funkce volána. Pokud je funkce deklarována s návratovým typem `void`, příkaz return obsahující výraz vygeneruje upozornění a výraz není vyhodnocen.

Následující příklady znázorňují návratové hodnoty funkcí.

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

Tento příklad definuje typ `STUDENT` s deklarací `typedef` a definuje `sortstu` funkce pro `STUDENT` návratový typ. Funkce vybere a vrátí jeden z jeho dvou argumentů struktury. V následných voláních funkce kompilátor kontroluje, zda jsou typy argumentů `STUDENT`.

> [!NOTE]
> Efektivita by se vylepšila předáním ukazatelů do struktury, nikoli celé struktury.

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

Tento příklad definuje funkci, která vrací ukazatel na pole znaků. Funkce přebírá dvě znaková pole (řetězce) jako argumenty a vrací ukazatel na kratší z obou řetězců. Ukazatel na pole odkazuje na první z prvků pole a má jeho typ; Proto návratový typ funkce je ukazatel na typ `char`.

Není nutné deklarovat funkce s `int` návratový typ předtím, než je zavoláte, i když jsou doporučeny prototypy, aby byla povolena správná kontrola typu pro argumenty a návratové hodnoty.

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
