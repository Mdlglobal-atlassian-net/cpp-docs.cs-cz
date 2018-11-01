---
title: bidirectional_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: c8296ddf30c0e2a3d34e69cbf079c0477e0e8b7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661510"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje obousměrný iterátor.

## <a name="syntax"></a>Syntaxe

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Kategorie značky tříd se používají při kompilaci značky pro algoritmus výběru. Funkce šablony musí najít největší určitou kategorii svého argumentu iterátoru, tak, aby ho používat co nejúčinnější algoritmus v době kompilace. Pro každý iterátor typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category** musí být definovány nejspecifičtější značky kategorii, která popisuje chování iterátoru.

Typ je stejný jako **iterátoru** \< **Iter**>:: **iterator_category** při `Iter` popisuje objekt, který může sloužit jako obousměrné iterátor.

## <a name="example"></a>Příklad

Zobrazit [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad, jak používat `bidirectional_iterator_tag`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[forward_iterator_tag – struktura](../standard-library/forward-iterator-tag-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
