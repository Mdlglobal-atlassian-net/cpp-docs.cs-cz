---
title: '&lt;ostream&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 18f30a12a6f4d2b97cb5dca3ace98e6241d856a7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447169"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; definice typedef

|||
|-|-|
|[ostream](#ostream)|[wostream –](#wostream)|

## <a name="ostream"></a>ostream

Vytvoří typ z basic_ostream, který je specializovaný na **char** a `char_traits` specializovaný na **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wostream"></a>wostream –

Vytvoří typ z basic_ostream, který je specializovaný na **wchar_t** a `char_traits` specializovaný na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_ostream](../standard-library/basic-ostream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)
