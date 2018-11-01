---
title: output_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: cb2a59d2c81e6d7cc80de2714ba86476c5fa837f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659303"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor výstupu.

## <a name="syntax"></a>Syntaxe

output_iterator_tag – struktura {};

## <a name="remarks"></a>Poznámky

Kategorie značky tříd se používají při kompilaci značky pro algoritmus výběru. Funkce šablony musí najít nejspecifičtější kategorie svůj argument iterátoru tak, aby ho používat co nejúčinnější algoritmus v době kompilace. Pro každý iterátor typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musí být definovány nejspecifičtější značky kategorii, která popisuje chování iterátoru.

Typ je stejný jako **iterátoru** \< **Iter**> **:: iterator_category** při `Iter` popisuje objekt, který může sloužit jako výstupní iterátor.

Toto klíčové slovo není parametrizované u `value_type` nebo `difference_type` iterátoru, stejně jako u jiných iterátoru značky, protože buď není nutné výstupní iterátory `value_type` nebo `difference_type`.

## <a name="example"></a>Příklad

Zobrazit [iterator_traits –](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad, jak používat `iterator_tag`s.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
