---
title: forward_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 04d526e7778dc219a8d9a49db40751b4418cc82d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434252"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag – struktura

Třída, která poskytuje návratový typ pro **iterator_category** funkce, která představuje iterátor předání.

## <a name="syntax"></a>Syntaxe

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Kategorie značky tříd se používají při kompilaci značky pro algoritmus výběru. Funkce šablony musí zjistit, co nejspecifičtější kategorie svůj argument iterátoru je tak, aby v době kompilace může použít co nejúčinnější algoritmus. Pro každý iterátor typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musí být definovány nejspecifičtější značky kategorii, která popisuje chování iterátoru.

Typ je stejný jako **iterátoru** \< **Iter**> **:: iterator_category** při **Iter** popisuje objekt, který může sloužit jako iterátor předání.

## <a name="example"></a>Příklad

Zobrazit [iterator_traits –](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad, jak používat **iterator_tag**s.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[input_iterator_tag – struktura](../standard-library/input-iterator-tag-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
