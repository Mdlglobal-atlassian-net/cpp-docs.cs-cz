---
title: '&lt;ostream&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856504"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; definice typedef

|||
|-|-|
|[ostream](#ostream)|[wostream –](#wostream)|

## <a name="ostream"></a>ostream

Vytvoří typ z basic_ostream, který je specializovaný na **char** a `char_traits` specializované na **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ostream](../standard-library/basic-ostream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wostream"></a>wostream –

Vytvoří typ z basic_ostream specializovaného na **wchar_t** a `char_traits` specializované na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_ostream](../standard-library/basic-ostream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také

[\<ostream >](../standard-library/ostream.md)
