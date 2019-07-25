---
title: '&lt;IStream&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 864854fa2697a76c2f3476bcb050d5f5d084dc9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458752"
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream&gt; definice typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>iostream –

Typ `basic_iostream` specializovaný na **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="istream"></a>IStream

Typ `basic_istream` specializovaný na **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wiostream"></a>wiostream

Typ `basic_iostream` specializovaný na **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_iostream](../standard-library/basic-iostream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="wistream"></a>wistream

Typ `basic_istream` specializovaný na **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_istream](../standard-library/basic-istream-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)
