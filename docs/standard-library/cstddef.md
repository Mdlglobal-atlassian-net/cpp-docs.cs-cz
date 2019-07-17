---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244448"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Obsahuje hlavičku standardní knihovny C \<stddef.h > a přidá názvy přidružené k `std` oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v hlavičce standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<cstddef – > obsahuje typ **bajtů** a neobsahuje typ **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Namespace a makra

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>Parametry

*ptrdiff_t*\
Implementaci definované podepsané celočíselný typ, který může obsahovat rozdíl dvou dolní indexy v objektu array.

*size_t*\
Typ unsigned integer definovanou implementací, který je dostatečně velký, aby se tak, aby obsahovala velikost v bajtech libovolného objektu.

*max_align_t*\
Typ POD jehož požadavek na zarovnání je minimálně stejně velká jako u každé skalárního typu a jejichž požadavek na zarovnání je podporovaná v každé kontextu.

*nullptr_t*\
Synonymum pro typ **nullptr** výrazu. I když **nullptr** adresu nelze přijmout, adresu jiného *nullptr_t* objekt, který je l-hodnoty. je možné provést.

## <a name="byte-class"></a>bajty třídy

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
