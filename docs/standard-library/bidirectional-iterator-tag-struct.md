---
title: bidirectional_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: bab2664fcb552a72baa032d719cf6b0141ffe525
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456626"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkci, která představuje obousměrný iterátor.

## <a name="syntax"></a>Syntaxe

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Třídy značek kategorie jsou používány jako kompilovat Tagy pro výběr algoritmu. Funkce šablony musí najít nejvíce konkrétní kategorie argumentu iterátoru, aby mohla používat nejúčinnější algoritmus v době kompilace. Pro `Iterator`každý iterátor typu `iterator_traits` < >:: iterator_category musí být definován jako nejvíce specifická značka kategorie, která popisuje chování iterátoru.  `Iterator`

Typ je stejný jako **iterátor** \< **ITER**>:: **iterator_category** , pokud `Iter` popisuje objekt, který může sloužit jako obousměrný iterátor.

## <a name="example"></a>Příklad

Příklad [](../standard-library/random-access-iterator-tag-struct.md) použití `bidirectional_iterator_tag`naleznete v tématu random_access_iterator_tag.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[forward_iterator_tag – struktura](../standard-library/forward-iterator-tag-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
