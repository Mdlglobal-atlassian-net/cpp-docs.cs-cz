---
title: alignment_of – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9af19f046cf6de44448e3fcddf97584f58adc9ae
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
