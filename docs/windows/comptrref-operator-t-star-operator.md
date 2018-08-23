---
title: ComPtrRef::operator T * – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
dev_langs:
- C++
helpviewer_keywords:
- operator T* operator
ms.assetid: b4f83370-0ebc-4d56-87c6-1a8ea2d0079b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54c370029b4e6fc90d1f210164de7d7ecb22f3a5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595416"
---
# <a name="comptrrefoperator-t-operator"></a>ComPtrRef::operator T* – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
operator T*();
```

## <a name="remarks"></a>Poznámky

Vrátí hodnotu [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) datový člen aktuálního **comptrref –** objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ComPtrRef – třída](../windows/comptrref-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)