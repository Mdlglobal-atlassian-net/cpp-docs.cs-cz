---
title: '&lt;ostream&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 02936fdfc990ea65a99b2875cf7f482eb2ce4ebe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429741"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; – definice TypeDef

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

Vytvoří typ z basic_ostream –, který se specializuje na **char** a `char_traits` specializované na **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ostream –](../standard-library/basic-ostream-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="wostream"></a>  wostream

Vytvoří typ z basic_ostream –, který se specializuje na **wchar_t** a `char_traits` specializované na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_ostream –](../standard-library/basic-ostream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="see-also"></a>Viz také:

[\<ostream >](../standard-library/ostream.md)<br/>
