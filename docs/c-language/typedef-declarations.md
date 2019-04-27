---
title: Typedef – deklarace
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: b4bf7bc82cdf792e5a23f6d5533cc4d800fe4252
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346103"
---
# <a name="typedef-declarations"></a>Typedef – deklarace

Deklarace typedef je deklarace pomocí direktivy typedef jako třídy úložiště. Deklarátor stane nového typu. TypeDef – deklarace můžete použít k vytvoření kratších nebo výstižnějších názvů pro typy, které jsou již definovány pomocí jazyka C nebo pro typy, které je deklarován. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.

Deklarace typedef je interpretován stejným způsobem jako proměnnou nebo deklarace funkce, ale tento identifikátor, ne za předpokladu, že zadaný typ deklarací, je synonymum pro typ.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace init-declarator-list*<sub>optimalizované</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace Storage-class-specifier*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu specifikátory deklarace*<sub>optimalizované</sub>

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Definice TypeDef**

*Specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Typ void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**plovoucí desetinnou čárkou**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podepsané**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaménka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Název TypeDef*

*Název typedef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

Všimněte si, že deklarace typedef nevytváří žádné typy. Vytvoří synonyma pro existující typy nebo názvy pro typy, které by mohl být specifikován jinými způsoby. Pokud název typedef slouží jako specifikátoru typu, dá se kombinovat s určitým specifikátory typu, ale ne pro jiné. Zahrnout přijatelné modifikátory **const** a `volatile`.

Názvy typu TypeDef sdílí obor názvů s běžnými identifikátory (viz [obory názvů](../c-language/name-spaces.md) Další informace). Program tedy může mít název typedef a identifikátor místního oboru se stejným názvem. Příklad:

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

Při deklarování identifikátoru místního oboru se stejným názvem jako typedef nebo při deklarování členu struktury nebo sjednocení ve stejném oboru nebo ve vnitřním oboru musí být určen specifikátor typu. Tento příklad znázorňuje tato omezení:

```C
typedef char FlagType;
const FlagType x;
```

Pro opětovné použití názvu `FlagType` pro identifikátor, člen struktury nebo člen sjednocení musí být určen typ:

```C
const int FlagType;  /* Type specifier required */
```

Nestačí říct

```C
const FlagType;      /* Incomplete specification */
```

protože `FlagType` se považuje za část typu, nikoli identifikátor, který je znovu deklarován. Tato deklarace je neplatnou jako

```C
int;  /* Illegal declaration */
```

Pomocí typedef je možné deklarovat jakýkoli typ, včetně ukazatele, funkce a typů polí. Je možné deklarovat název typedef pro ukazatel na typ struktury nebo sjednocení před definováním typu struktury nebo sjednocení, pokud má definice stejnou viditelnost jako deklarace.

Názvy typu TypeDef je možné pro lepší čitelnost kódu. Všechny tři následující deklarace `signal` zadejte přesně stejného typu, nejprve bez provedení užívání žádné názvy typu typedef.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Příklady

Následující příklady znázorňují TypeDef – deklarace:

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Všimněte si, že `WHOLE` by se teď dá v deklaraci proměnné, jako `WHOLE i;` nebo `const WHOLE i;`. Však deklarace `long WHOLE i;` by byla neplatná.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Tento příkaz deklaruje `GROUP` jako typ struktury pomocí tří členů. Od značku struktury `club`, je také zadán, název typedef (`GROUP`) nebo značku struktury lze použít v deklaracích. Je nutné použít klíčové slovo struct se značkou a struct – klíčové slovo nelze použít s názvem typedef.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Typ `PG` je deklarována jako ukazatel `GROUP` typ, který zase je definována jako typ struktury.

```C
typedef void DRAWF( int, int );
```

Tento příklad poskytuje typ `DRAWF` pro funkci nevracející žádnou hodnotu a přijímající dva celočíselné argumenty. To znamená, například, že deklarace

```C
DRAWF box;
```

je ekvivalentem deklarace

```C
void box( int, int );
```

## <a name="see-also"></a>Viz také:

[Deklarace a typy](../c-language/declarations-and-types.md)
