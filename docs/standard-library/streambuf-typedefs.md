---
title: '&lt;streambuf&gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 178b489d92a4ed7340084490329fdf8fa16c2aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449591"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; definice typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>streambuf

Specializace `basic_streambuf` , která jako parametry šablony používá **char** .

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wstreambuf"></a>wstreambuf –

Specializace `basic_streambuf` , která používá **wchar_t** jako parametry šablony.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro třídu šablony [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také:

[\<streambuf>](../standard-library/streambuf.md)
