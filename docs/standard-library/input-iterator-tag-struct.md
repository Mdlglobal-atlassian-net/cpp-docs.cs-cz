---
title: input_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 5478a8f9fa6013202a1ea8dd838eedb80b9c367e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159246"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor vstupu.

## <a name="syntax"></a>Syntaxe

input_iterator_tag – struktura {};

## <a name="remarks"></a>Poznámky

Kategorie značky tříd se používají při kompilaci značky pro algoritmus výběru. Funkce šablony musí najít nejspecifičtější kategorie svůj argument iterátoru tak, aby ho používat co nejúčinnější algoritmus v době kompilace. Pro každý iterátor typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musí být definovány nejspecifičtější značky kategorii, která popisuje chování iterátoru.

Typ je stejný jako **iterátoru** \< **Iter**> **:: iterator_category** při `Iter` popisuje objekt, který může sloužit jako vstupní iterátor.

## <a name="example"></a>Příklad

Zobrazit [iterator_traits –](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad, jak používat `iterator_tag`s.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
