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

Deklarace typedef je deklarace s typedef jako třídou úložiště. Deklarátor se stala novým typem. Deklarace typedef můžete použít k vytvoření kratšího nebo více smysluplných názvů pro typy, které jsou již definovány v jazyce C nebo pro typy, které jste deklarovali. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.

Deklarace typedef je interpretována stejným způsobem jako deklarace proměnné nebo funkce, ale identifikátor namísto za předpokladu, že typ určený deklarací, se nazývá synonymum pro daný typ.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory init-deklarátor-list*<sub>opt</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace specifikátoru třídy úložiště – specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace specifikátoru typu – povolit specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru – specifikátory*<sub>opt</sub>

*specifikátor třídy úložiště*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**definic**

*specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**šekem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dostatečná**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**hmot**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dlouhou**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Plovák**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**klepat**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podpisy**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**celé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor struct nebo Union*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enum – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef – název*

*definice typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*

Všimněte si, že deklarace typedef nevytváří typy. Vytvoří synonyma pro existující typy nebo názvy pro typy, které mohou být zadány jiným způsobem. Pokud je název typedef použit jako specifikátor typu, může být kombinován s určitými specifikátory typu, ale ne jinými. Přijatelné modifikátory zahrnují **const** a `volatile`.

Názvy typedef sdílí obor názvů s běžnými identifikátory (Další informace najdete v tématu [Názvové prostory](../c-language/name-spaces.md) ). Program tedy může mít název typedef a identifikátor místního oboru se stejným názvem. Příklad:

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

Při deklarování identifikátoru místního oboru se stejným názvem jako typedef nebo při deklarování členu struktury nebo sjednocení ve stejném oboru nebo ve vnitřním oboru musí být určen specifikátor typu. Tento příklad znázorňuje toto omezení:

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

Názvy typedef lze použít ke zlepšení čitelnosti kódu. Všechny tři z následujících deklarací v `signal` určit přesně stejný typ, jako první bez použití jakýchkoli názvů typedef.

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>Příklady

Následující příklady ilustrují deklarace typedef:

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

Všimněte si `WHOLE` , že se teď dá použít v deklaraci proměnné `WHOLE i;` , `const WHOLE i;`jako je nebo. Deklarace `long WHOLE i;` by však byla neplatná.

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

Tento příkaz deklaruje `GROUP` jako typ struktury se třemi členy. Vzhledem k tomu, že `club`je zadána také značka struktury, lze v deklaracích`GROUP`použít buď název typedef (), nebo značku struktury. Je nutné použít klíčové slovo struct se značkou a nemůžete použít klíčové slovo struct s názvem typedef.

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

Typ `PG` je deklarován jako ukazatel na `GROUP` typ, který je definován jako typ struktury.

```C
typedef void DRAWF( int, int );
```

Tento příklad poskytuje typ `DRAWF` pro funkci, která nevrací žádnou hodnotu a přijímá dva argumenty typu int. To například znamená, že deklarace

```C
DRAWF box;
```

je ekvivalentem deklarace

```C
void box( int, int );
```

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
