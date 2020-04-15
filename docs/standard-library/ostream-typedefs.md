---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373573"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

Vytvoří typ z basic_ostream, který se `char_traits` specializuje na **char** a specializuje se na **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_ostream](../standard-library/basic-ostream-class.md), specializované na prvky typu **char** s výchozími znakovými znaky.

## <a name="wostream"></a><a name="wostream"></a>wostream

Vytvoří typ z basic_ostream, který se `char_traits` specializuje na **wchar_t** a specializuje se na **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro [basic_ostream](../standard-library/basic-ostream-class.md)šablony třídy , který se specializuje na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="see-also"></a>Viz také

[\<ostream>](../standard-library/ostream.md)
