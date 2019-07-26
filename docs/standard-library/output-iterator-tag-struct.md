---
title: output_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 942e2214f42f97e262d4daf7836e8b6ced0e0ab2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453020"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkci, která představuje výstupní iterátor.

## <a name="syntax"></a>Syntaxe

struktura output_iterator_tag {};

## <a name="remarks"></a>Poznámky

Třídy značek kategorie jsou používány jako kompilovat Tagy pro výběr algoritmu. Funkce šablony musí najít nejvíce specifickou kategorii argumentu iterátoru tak, aby mohla používat nejúčinnější algoritmus v době kompilace. Pro `Iterator`každý iterátor typu,  `iterator_traits` <  ::iterator_category> musí být definován jako nejvíce specifická značka kategorie, která popisuje chování iterátoru. `Iterator`

Typ je stejný jako **iterátor** \< **ITER**>  **:: iterator_category** , pokud `Iter` popisuje objekt, který může sloužit jako výstupní iterátor.

Tato značka `value_type` není Parametrizovaná na nebo `difference_type` pro iterátor, stejně jako u ostatních značek iterátoru, protože výstupní iterátory nemají buď `value_type` ani `difference_type`.

## <a name="example"></a>Příklad

Příklad [](../standard-library/iterator-traits-struct.md) použití `iterator_tag`s najdete v tématu iterator_traits nebo [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
