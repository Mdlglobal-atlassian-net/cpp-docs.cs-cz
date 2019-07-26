---
title: input_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 47e0d08f79cfa41c414ac4fcd570ce8fdfbd0b35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455319"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkci, která představuje vstupní iterátor.

## <a name="syntax"></a>Syntaxe

struktura input_iterator_tag {};

## <a name="remarks"></a>Poznámky

Třídy značek kategorie jsou používány jako kompilovat Tagy pro výběr algoritmu. Funkce šablony musí najít nejvíce specifickou kategorii argumentu iterátoru tak, aby mohla používat nejúčinnější algoritmus v době kompilace. Pro `Iterator`každý iterátor typu,  `iterator_traits` <  ::iterator_category> musí být definován jako nejvíce specifická značka kategorie, která popisuje chování iterátoru. `Iterator`

Typ je stejný jako **iterátor** \< **ITER**>  **:: iterator_category** , pokud `Iter` popisuje objekt, který může sloužit jako vstupní iterátor.

## <a name="example"></a>Příklad

Příklad [](../standard-library/iterator-traits-struct.md) použití `iterator_tag`s najdete v tématu iterator_traits nebo [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
