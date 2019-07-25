---
title: forward_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 687e39ce752bc0d4d289421887570dea6870f8f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457127"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag – struktura

Třída, která poskytuje návratový typ pro funkci **iterator_category** , která představuje dopředný iterátor.

## <a name="syntax"></a>Syntaxe

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Třídy značek kategorie jsou používány jako kompilovat Tagy pro výběr algoritmu. Funkce šablony potřebuje zjistit, co je nejvíce specifická kategorie argumentu iterátoru, aby mohla používat nejúčinnější algoritmus v době kompilace. Pro `Iterator`každý iterátor typu,  `iterator_traits` <  ::iterator_category> musí být definován jako nejvíce specifická značka kategorie, která popisuje chování iterátoru. `Iterator`

Typ je stejný jako **iterátor** \< **ITER**>  **:: iterator_category** , pokud **ITERA** popisuje objekt, který může sloužit jako dopředný iterátor.

## <a name="example"></a>Příklad

Příklad použití **iterator_tag**s naleznete v tématu [iterator_traits](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) .

## <a name="requirements"></a>Požadavky

**Hlavička:** \<iterátor >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[input_iterator_tag – struktura](../standard-library/input-iterator-tag-struct.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
