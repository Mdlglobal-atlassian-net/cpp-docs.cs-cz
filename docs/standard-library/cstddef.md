---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 87d268977ee46112fedce517e66a9e68071863db
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457563"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Obsahuje hlavičku \<standardní knihovny jazyka C STDDEF. h > a přidává k `std` oboru názvů přidružené názvy. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v záhlaví standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<cstddef > zahrnuje typ **Byte** a nezahrnuje typ **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Obor názvů a makra

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
Typ celého čísla se znaménkem definovaný pro implementaci, který může obsahovat rozdíl dvou dolních indexů v objektu Array.

*size_t*\
Uživatelsky definovaný typ unsigned integer, který je dostatečně velký, aby obsahoval velikost v bajtech libovolného objektu.

*max_align_t*\
Typ POD, jehož požadavek na zarovnání je nejméně stejně skvělý jako u každého skalárního typu a jehož požadavek na zarovnání je podporován v každém kontextu.

*nullptr_t*\
Synonymum pro typ výrazu **nullptr** . I když adresu **nullptr** nelze vzít, adresa jiného objektu *nullptr_t* , která je l-hodnotou, může být provedena.

## <a name="byte-class"></a>Byte – třída

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

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
