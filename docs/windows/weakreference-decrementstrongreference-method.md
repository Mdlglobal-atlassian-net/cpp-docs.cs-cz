---
title: Weakreference::decrementstrongreference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3620a4b82aabb0058773f68938f545119f90791
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605595"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
ULONG DecrementStrongReference();
```

## <a name="remarks"></a>Poznámky

Sníží počet silné referenční aktuálního **WeakReference** objektu.

Když počet odkazů silné klesne na nulu, silného odkazu se nastaví na **nullptr**.

## <a name="return-value"></a>Návratová hodnota

Počet odkazů sníží silné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Weakreference – třída](../windows/weakreference-class1.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)