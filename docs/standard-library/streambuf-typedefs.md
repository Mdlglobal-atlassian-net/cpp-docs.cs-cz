---
title: '&lt;streambuf&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376683"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedefs

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf řekl:](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

`basic_streambuf` Specializace, která používá **char** jako parametry šablony.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), specializované na prvky typu **char** s výchozími znakovými znaky.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf řekl:

`basic_streambuf` Specializace, která používá **wchar_t** jako parametry šablony.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro šablonu třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), specializované na prvky typu **wchar_t** s výchozími znakovými znaky.

## <a name="see-also"></a>Viz také

[\<streambuf>](../standard-library/streambuf.md)
