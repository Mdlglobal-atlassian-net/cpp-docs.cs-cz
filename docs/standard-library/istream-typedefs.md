---
title: '&lt;IStream&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: bea06c9799783feafaff1f68f4019463e452a4f2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958852"
---
# <a name="ltistreamgt-typedefs"></a>&lt;IStream&gt; – definice TypeDef

||||
|-|-|-|
|[iostream –](#iostream)|[IStream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream –

Typ `basic_iostream` specializované na **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_iostream –](../standard-library/basic-iostream-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="istream"></a>  IStream

Typ `basic_istream` specializované na **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_istream](../standard-library/basic-istream-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="wiostream"></a>  wiostream

Typ `basic_iostream` specializované na **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_iostream –](../standard-library/basic-iostream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="wistream"></a>  wistream

Typ `basic_istream` specializované na **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_istream](../standard-library/basic-istream-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="see-also"></a>Viz také:

[\<IStream >](../standard-library/istream.md)<br/>
