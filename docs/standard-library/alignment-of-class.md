---
title: alignment_of – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d9ba59d7f1539f690d7b04c70139c263490368
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850688"
---
# <a name="alignmentof-class"></a>alignment_of – třída

Získá zarovnání zadaného typu. Tato struktura je implementována z hlediska [alignof](../cpp/alignof-and-alignas-cpp.md). Použití `alignof` přímo při jednoduše je potřeba zadat dotaz na hodnotu zarovnání. Alignment_of používejte, když potřebujete integrální konstanta, například při provádění odesílání značky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Typ dotazu obsahuje hodnotu zarovnání typu `Ty`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage – třída](../standard-library/aligned-storage-class.md)<br/>
