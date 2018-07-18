---
title: '&lt;streambuf –&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 81c7cd875c6083ee77701116f6b1179760373ec0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953989"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf –&gt; – definice TypeDef

|||
|-|-|
|[streambuf –](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf –

Specializace `basic_streambuf` , která používá **char** jako parametry šablony.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **char** s výchozí vlastností.

## <a name="wstreambuf"></a>  wstreambuf

Specializace `basic_streambuf` , která používá **wchar_t** jako parametry šablony.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **wchar_t** s výchozí vlastností.

## <a name="see-also"></a>Viz také:

[\<streambuf – >](../standard-library/streambuf.md)<br/>
