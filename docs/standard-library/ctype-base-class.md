---
title: ctype_base – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 83ef35f9fac438cfa217decf222abd365ff84269
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394179"
---
# <a name="ctypebase-class"></a>ctype_base – třída

Tato třída slouží jako základní třída pro omezující vlastnosti třídy šablony [ctype](../standard-library/ctype-class.md). Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.

## <a name="syntax"></a>Syntaxe

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>Poznámky

Definuje masku výčtu. Každý konstanta výčtu charakterizuje jiný způsob, jak klasifikaci znaků, jak jsou definovány pomocí funkcí s podobnými názvy deklarované v hlavičce \<ctype.h >. Konstanty jsou:

- **místo** (funkce [isspace](../standard-library/locale-functions.md#isspace))

- **Tisk** (funkce [isprint](../standard-library/locale-functions.md#isprint))

- **Stisknutím kláves CTRL +** (funkce [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **horní** (funkce [isupper](../standard-library/locale-functions.md#isupper))

- **nižší** (funkce [islower](../standard-library/locale-functions.md#islower))

- **číslice** (funkce [isdigit](../standard-library/locale-functions.md#isdigit))

- **punct** (funkce [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (funkce [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **systém Alpha** (funkce [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (funkce [isalnum](../standard-library/locale-functions.md#isalnum))

- **graf** (funkce [isgraph](../standard-library/locale-functions.md#isgraph))

Kombinace klasifikace podle ORing můžete charakterizují tyto konstanty. Zejména je vždy hodnotu true, který **alnum** == ( **alfa** &#124; **číslice** \) a **grafu** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
