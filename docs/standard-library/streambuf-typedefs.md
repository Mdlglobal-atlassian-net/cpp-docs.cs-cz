---
title: '&lt;streambuf –&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 505739861771a05dd39741f432579a6e9b2d0c26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412381"
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

[\<streambuf>](../standard-library/streambuf.md)<br/>
