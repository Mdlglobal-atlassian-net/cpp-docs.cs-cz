---
title: '&lt;streambuf &gt; definice typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688927"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf &gt; definice typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf –](#wstreambuf)|

## <a name="streambuf"></a>streambuf

Specializace `basic_streambuf`, která jako parametry šablony používá **char** .

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **char** s výchozími vlastnostmi znaků.

## <a name="wstreambuf"></a>wstreambuf –

Specializace `basic_streambuf`, která používá **wchar_t** jako parametry šablony.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro šablonu třídy [basic_streambuf](../standard-library/basic-streambuf-class.md)specializované pro prvky typu **wchar_t** s výchozími vlastnostmi znaků.

## <a name="see-also"></a>Viz také:

[\<streambuf >](../standard-library/streambuf.md)
