---
title: bidirectional_iterator_tag – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 108397f6c3c3c088839230f2b48b505300149345
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844390"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag – struktura

Třídu, která poskytuje návratový typ pro **iterator_category –** funkce, která představuje iterator obousměrné.

## <a name="syntax"></a>Syntaxe

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Třídy značky kategorie se používají jako zkompilovat značky pro výběr algoritmů. Funkce šablony musí najít nejvíce určitou kategorii její argument iterator tak, aby v době kompilace může použít algoritmus maximální efektivitou. Pro každý iterator typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category –** musí být definován jako nejvíce značky kategorii, která popisuje iteraci chování.

Typ je stejný jako **iterator** \< **Iter**>:: **iterator_category –** při **Iter** popisuje objekt, který můžete sloužit jako iterator obousměrné.

## <a name="example"></a>Příklad

V tématu [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad použití `bidirectional_iterator_tag`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[forward_iterator_tag – struktura](../standard-library/forward-iterator-tag-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
