---
title: Výklad složitějších deklarací
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 13c81728f02963863b641348b58380da099b0013
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148241"
---
# <a name="interpreting-more-complex-declarators"></a>Výklad složitějších deklarací

Je uzavřít žádné deklarátoru v závorkách určují konkrétní interpretaci "složitých deklarátorů." Složitých deklarátorů je identifikátor kvalifikován pomocí více než jednoho pole, ukazatel nebo modifikátor funkce. Můžete použít různé kombinace pole, ukazatel a modifikátorů funkce do jednoho identifikátoru. Obecně `typedef` slouží ke zjednodušení deklarace. Zobrazit [deklarace Typedef](../c-language/typedef-declarations.md).

V výklad složitých deklarátorů, kulaté a složené závorky (tj. modifikátorů napravo od identifikátoru) přednost hvězdičky (tj. modifikátorů nalevo od identifikátoru). A složené závorky mají stejnou prioritu a jsou asociativní zleva doprava. Po deklarátor má plně interpretovat, specifikátor typu použít jako poslední krok. Pomocí závorek můžete přepsat výchozí přidružení pořadí a vynutit konkrétní interpretaci. Nikdy nepoužívejte však závorky kolem název identifikátoru samostatně. To může být špatně interpretována jako seznam parametrů.

Jednoduchý způsob interpretace složitých deklarátorů je číst "zevnitř," pomocí následujících čtyřech krocích:

1. Začněte s identifikátorem a podívejte se přímo na pravé straně pro závorek nebo složených závorek (pokud existuje).

1. Interpretace těchto hranaté závorky nebo závorek a podívejte se na levé straně pro hvězdičky z obou stran.

1. Pokud narazíte na pravou závorkou v jakékoli fázi, přejděte zpět a použití pravidel 1 a 2 pro všechno, co v závorkách.

1. Použití specifikátoru typu.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

Kroky v tomto příkladu jsou číslována v pořadí a může být interpretován takto:

1. Identifikátor `var` je deklarován jako

1. Ukazatel na

1. funkce vracející

1. Ukazatel na

1. pole 10 prvků, které jsou

1. ukazatele na

1. `char` hodnoty.

## <a name="examples"></a>Příklady

Následující příklady ilustrují jiné komplexní deklarace a zobrazit vliv význam deklaraci závorky.

```
int *var[5]; /* Array of pointers to int values */
```

Modifikátor pole má vyšší prioritu než modifikátor ukazatele, takže `var` je deklarováno jako pole. Modifikátor ukazatele se vztahuje na typ prvků pole; proto prvky pole jsou ukazatele na `int` hodnoty.

```
int (*var)[5]; /* Pointer to array of int values */
```

V této deklaraci pro `var`, závorky poskytovaly modifikátor ukazatele vyšší prioritu než modifikátor pole a `var` je deklarováno jako ukazatel na pole pěti `int` hodnoty.

```
long *var( long, long ); /* Function returning pointer to long */
```

Modifikátorů funkce také mají vyšší prioritu než modifikátorů ukazatelů, takže tato deklarace pro `var` deklaruje `var` jako funkce vrací ukazatel na **dlouhé** hodnotu. Funkce je deklarována berou dva **dlouhé** hodnoty jako argumenty.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Tento příklad je podobný předchozímu. Závorky poskytovaly modifikátor ukazatele vyšší prioritu než modifikátor funkce a `var` je deklarováno jako ukazatel na funkci, která se vrátí **dlouhé** hodnotu. Znovu funkci má dva **dlouhé** argumenty.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Prvky pole nemůžou být funkce, ale tato deklarace ukazuje, jak se místo toho deklarovat pole ukazatelů na funkce. V tomto příkladu `var` je deklarováno jako pole pět ukazatelů na funkce, které se dvěma členy struktury vrácení. Argumenty, které mají tyto funkce jsou deklarovány jako dvě struktury se stejným typem struktura `both`. Všimněte si, že závorky kolem `*var[5]` jsou povinné. Bez nich je deklarace k neplatnému pokusu deklarovat celou řadu funkcí, jak je znázorněno níže:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

Následující příkaz deklaruje pole ukazatelů.

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name` Pole nemá 50 prvky uspořádané do multidimenzionálního pole. Prvky jsou ukazatele na ukazatel, který je konstanta. Tento konstantní ukazatel odkazuje na funkci, která nemá žádné parametry a vrací ukazatel na typ bez znaménka.

Tento další příklad je funkce vrací ukazatel na pole tří **double** hodnoty.

```
double ( *var( double (*)[3] ) )[3];
```

V této deklaraci funkce vrací ukazatel na pole, od funkce vracející pole jsou neplatná. Tady `var` je deklarováno jako funkci, která vrací ukazatel na pole tří **double** hodnoty. Funkce `var` přijímá jeden argument. Argument, jako je návratová hodnota je ukazatel na pole tří **double** hodnoty. Typ argumentu je dán komplexní *abstraktní deklarátor*. Závorky kolem hvězdičky v argumentu typu jsou povinné; bez nich, typ argumentu bude pole tří ukazatelů na **double** hodnoty. Příklady abstraktní deklarátory a diskusi najdete v tématu [abstraktní Deklarátory](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Jak ukazuje příklad výše, ukazatel může odkazovat na jiný ukazatel a pole může obsahovat pole jako prvky. Tady `var` je pět prvků pole. Každý prvek je pět elementu pole ukazatelů na ukazatele na sjednocení se dvěma členy.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Tento příklad ukazuje, jak se změní umístění závorky význam deklarace. V tomto příkladu `var` je pět elementu pole ukazatelů na pět elementu pole ukazatelů na sjednocení. Příklady použití `typedef` vyhnout komplexní prohlášení, najdete v článku [deklarace Typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Viz také:

[Deklarace a typy](../c-language/declarations-and-types.md)
