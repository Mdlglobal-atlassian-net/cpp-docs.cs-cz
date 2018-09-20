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
ms.openlocfilehash: 9a73608bd2faa8de2c5e23eff84290e7dd5fae11
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417186"
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

[Weakreference – třída](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)