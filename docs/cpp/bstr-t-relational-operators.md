---
title: _bstr_t – relační operátory
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: a4126eb7771e17db5fb813898d6fa4917f6983bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190310"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t – relační operátory

**Specifické pro společnost Microsoft**

Porovná dva objekty `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>Poznámky

Tyto operátory porovnávají dva objekty `_bstr_t` lexikograficky. Operátory vrátí hodnotu TRUE, pokud se podrží porovnávání, jinak vrátí FALSE.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_bstr_t – třída](../cpp/bstr-t-class.md)
