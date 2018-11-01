---
title: Anonymní typy třídy
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 9cd27fb40522a07ce4591b654ee8a6dda53b4f28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456404"
---
# <a name="anonymous-class-types"></a>Anonymní typy třídy

Třídy mohou být anonymní – to znamená, že mohou být deklarovány bez *identifikátor*. To je užitečné při nahrazení názvu třídy **typedef** název, viz následující příklad:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
>  Použití anonymních tříd uvedené v předchozím příkladu je užitečné pro zachování kompatibility se stávajícím kódem jazyka C. V kódu jazyka C, použití **typedef** ve spojení s anonymními strukturami převládá.

Anonymní třídy jsou také užitečné, pokud chcete odkazovat člena třídy, jako by nebyl obsažen v samostatné třídě (viz následující příklad):

```cpp
struct PTValue
{
    POINT ptLoc;
    union
    {
        int  iValue;
        long lValue;
    };
};

PTValue ptv;
```

V předchozím kódu `iValue` lze přistupovat pomocí operátoru výběru členů objektu (**.**) následujícím způsobem:

```cpp
int i = ptv.iValue;
```

Na anonymní třídy se vztahují jistá omezení. (Další informace o anonymních sjednoceních naleznete v tématu [sjednocení](../cpp/unions.md).) Anonymní třídy:

- Nemohou mít konstruktor ani destruktor.

- Nelze je předat jako argumenty funkcím (pokud není zrušena kontrola typu pomocí operátoru tři tečky).

- Nelze je vrátit jako návratové hodnoty funkcí.

## <a name="anonymous-structs"></a>Anonymní struktury

### <a name="microsoft-specific"></a>Specifické pro Microsoft

Rozšíření jazyka Microsoft C umožňuje deklarovat proměnnou struktury v jiné struktuře bez zadání názvu. Tyto vnořené struktury se nazývají anonymní struktury. Jazyk C++ nepovoluje anonymní struktury.

Ke členům anonymní struktury lze přistupovat, jako kdyby byly členy obsahující struktury.

```cpp
// anonymous_structures.c
#include <stdio.h>

struct phone
{
    int  areacode;
    long number;
};

struct person
{
    char   name[30];
    char   gender;
    int    age;
    int    weight;
    struct phone;    // Anonymous structure; no name needed
} Jim;

int main()
{
    Jim.number = 1234567;
    printf_s("%d\n", Jim.number);
}
//Output: 1234567
```

**Specifické pro END Microsoft**