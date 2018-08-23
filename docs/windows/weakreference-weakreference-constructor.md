---
title: Weakreference::weakreference – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d506bc99d584222de55de56c9efbe40f9c71434a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593490"
---
# <a name="weakreferenceweakreference-constructor"></a>WeakReference::WeakReference – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
WeakReference();
```

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy [weakreference – třída](../windows/weakreference-class1.md).

Silný odkaz ukazatel pro **WeakReference** objekt je inicializován na **nullptr**, a počet silného odkazu je inicializován na hodnotu 1.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)