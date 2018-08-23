---
title: Runtimeclassbaset – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b0bae186a0c4d4e9a6c7eec8553c296428b3a59
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597188"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parametry

*RuntimeClassTypeT*  
Pole, která určuje jeden nebo více příznaků [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) enumerátory.

## <a name="remarks"></a>Poznámky

Poskytuje pomocné metody pro `QueryInterface` operace a získat ID rozhraní.

## <a name="members"></a>Členové

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassBaseT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Referenční dokumentace (knihovna Windows Runtime)](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)