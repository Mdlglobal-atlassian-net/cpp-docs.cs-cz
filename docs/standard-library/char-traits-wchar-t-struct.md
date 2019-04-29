---
title: char_traits&lt;wchar_t&gt; – struktura
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: ef40a34b5aa874c8bdf48aeb7657ae3496160eec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379217"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; – struktura

Třída, která je specializací šablony struktury **char_traits\<CharType >** na prvek typu **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Poznámky

Specializace umožňuje využívat funkce knihovny, které pracují s objekty tohoto typu struktury **wchar_t**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řetězec >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[char_traits – struktura](../standard-library/char-traits-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
