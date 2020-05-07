---
title: Výklad složitějších deklarací
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 13c81728f02963863b641348b58380da099b0013
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232862"
---
# <a name="interpreting-more-complex-declarators"></a>Výklad složitějších deklarací

Můžete uzavřít všechny deklarátory do závorek a určit tak konkrétní výklad "komplexní deklarátor". Komplexní deklarátor je identifikátor, který je kvalifikován více než jedním modifikátorem Array, pointer nebo Function. Můžete použít různé kombinace modifikátorů pole, ukazatele a funkce na jeden identifikátor. Obecně `typedef` lze použít pro zjednodušení deklarací. Viz [deklarace typedef](../c-language/typedef-declarations.md).

Při interpretaci složitých deklarátory, závorek a závorek (tj. modifikátory napravo od identifikátoru) mají přednost před hvězdičkami (tj. modifikátory nalevo od identifikátoru). Závorky a závorky mají stejnou prioritu a přiřadí se zleva doprava. Po úplném výkladu deklarátor je specifikátor typu použit jako poslední krok. Pomocí závorek můžete přepsat výchozí pořadí přidružení a vynutit konkrétní výklad. Nikdy nepoužívejte kulaté závorky, ale kolem názvu identifikátoru samotného. To může být špatně interpretováno jako seznam parametrů.

Jednoduchým způsobem, jak interpretovat složitou deklarátory, je přečíst si je z vnitřku, a to pomocí následujících čtyř kroků:

1. Začněte s identifikátorem a podívejte se přímo na pravé nebo hranaté závorky (pokud existují).

1. Tyto závorky nebo závorky vyhodnotí a vyhledejte hvězdičky.

1. Pokud narazíte na pravou závorku v libovolné fázi, vraťte se zpátky a použijte pravidla 1 a 2 na vše v závorkách.

1. Použijte specifikátor typu.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

V tomto příkladu jsou kroky očíslovány v pořadí a lze je interpretovat následujícím způsobem:

1. Identifikátor `var` je deklarovaný jako

1. ukazatel na

1. funkce, která vrací

1. ukazatel na

1. pole 10 prvků, které jsou

1. ukazatele na

1. `char`hodnota.

## <a name="examples"></a>Příklady

Následující příklady ilustrují další komplexní deklarace a ukazují, jak mohou kulaté závorky ovlivnit význam deklarace.

```
int *var[5]; /* Array of pointers to int values */
```

Modifikátor pole má vyšší prioritu než Modifikátor ukazatele, takže `var` je deklarován jako pole. Modifikátor ukazatele se vztahuje na typ prvků pole; Proto prvky pole jsou ukazatele na `int` hodnoty.

```
int (*var)[5]; /* Pointer to array of int values */
```

V této deklaraci `var`pro by kulaté závorky poskytovaly Modifikátor ukazatele s vyšší prioritou než modifikátor `var` pole a jsou deklarovány jako ukazatel na pole pěti `int` hodnot.

```
long *var( long, long ); /* Function returning pointer to long */
```

Modifikátory funkce mají také vyšší prioritu než modifikátory ukazatelů, takže tato deklarace pro `var` deklaraci `var` funkce vrací ukazatel na **dlouhou** hodnotu. Funkce je deklarována tak, aby jako argumenty převzala dvě **dlouhé** hodnoty.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Tento příklad je podobný předchozímu. Kulaté závorky poskytují Modifikátor ukazatele s vyšší prioritou než modifikátor funkce a `var` jsou deklarovány jako ukazatel na funkci, která vrací **dlouhou** hodnotu. Funkce znovu přebírá dva **dlouhé** argumenty.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Prvky pole nemohou být Functions, ale tato deklarace ukazuje, jak deklarovat pole ukazatelů na funkce namísto. V tomto příkladu `var` je deklarován jako pole pěti ukazatelů na funkce, které vracejí struktury se dvěma členy. Argumenty funkcí jsou deklarovány jako dvě struktury se stejným typem struktury, `both`. Všimněte si, že `*var[5]` jsou požadované kulaté závorky. Bez nich je deklarace neplatným pokusem o deklaraci pole funkcí, jak je znázorněno níže:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

Následující příkaz deklaruje pole ukazatelů.

```
unsigned int *(* const *name[5][10] ) ( void );
```

`name` Pole obsahuje 50 prvků uspořádaných v multidimenzionálním poli. Prvky jsou ukazatele na ukazatel, který je konstanta. Tento konstantní ukazatel odkazuje na funkci, která nemá žádné parametry a vrací ukazatel na typ bez znaménka.

V následujícím příkladu je funkce vracející ukazatel na pole tří hodnot typu **Double** .

```
double ( *var( double (*)[3] ) )[3];
```

V této deklaraci funkce vrací ukazatel na pole, protože funkce vracející pole jsou neplatné. Tady `var` je deklarovaný jako funkce, která vrací ukazatel na pole tří hodnot typu **Double** . Funkce `var` přijímá jeden argument. Argument, jako je vrácená hodnota, je ukazatel na pole tří hodnot typu **Double** . Typ argumentu je dán komplexním *deklarátorem abstract-*. Jsou vyžadovány závorky kolem hvězdičky v typu argumentu; bez nich by typ argumentu byl pole tří ukazatelů na **dvojitou** hodnotu. Diskuzi a příklady abstraktních deklarátory naleznete v tématu [abstract deklarátory](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Jak ukazuje výše uvedený příklad, ukazatel může ukazovat na jiný ukazatel a pole může obsahovat pole jako elementy. Zde `var` je pole s pěti prvky. Každý prvek je polem typu pět prvků ukazatelů na sjednocení se dvěma členy.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Tento příklad ukazuje, jak umístění závorek mění význam deklarace. V tomto příkladu `var` je pole s pěti prvky ukazatelů na pole na pět prvků ukazatelů na sjednocení. Příklady použití `typedef` pro zamezení složitých deklaracích naleznete v tématu [deklarace typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
