---
title: ctype_base – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 4fac75d90c4e40a22e8ceae974c3f49c3d50a1d3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688197"
---
# <a name="ctype_base-class"></a>ctype_base – třída

Třída slouží jako základní třída pro omezující vlastnosti třídy template [CType](../standard-library/ctype-class.md). Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.

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

Definuje masku výčtu. Každá konstanta výčtu charakterizuje jiný způsob klasifikace znaků, jak jsou definovány funkcemi s podobnými názvy deklarovanými v hlavičce \<ctype. h >. Konstanty jsou:

- **Space** (funkce- [Space](../standard-library/locale-functions.md#isspace))

- **Tisk** (funkce- [Print](../standard-library/locale-functions.md#isprint))

- **TAB** (Function [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **Upper** (funkce – [horní](../standard-library/locale-functions.md#isupper))

- **Lower** (funkce je [levnější](../standard-library/locale-functions.md#islower))

- **číslice** (funkce- [číslice](../standard-library/locale-functions.md#isdigit))

- **punct** (Function [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (Function [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alfa** (Function- [alfa](../standard-library/locale-functions.md#isalpha))

- **alnum** (Function [isalnum](../standard-library/locale-functions.md#isalnum))

- **Graph** (Function [graf](../standard-library/locale-functions.md#isgraph))

Můžete charakterizovat kombinaci klasifikací tím, že ORing tyto konstanty. Konkrétně je vždy true, že **alnum** = = ( **alfa** &#124; **číslice** \) a **Graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
