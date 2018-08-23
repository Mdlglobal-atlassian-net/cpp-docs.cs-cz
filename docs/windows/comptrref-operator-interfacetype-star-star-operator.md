---
title: ComPtrRef::operator InterfaceType ** – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
dev_langs:
- C++
helpviewer_keywords:
- operator InterfaceType** operator
ms.assetid: b32e3240-a4f0-4998-a55f-d4e35dc9a15a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88b83e475ad2452d55b4696bc9b5f1b8bc75a169
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606656"
---
# <a name="comptrrefoperator-interfacetype-operator"></a>ComPtrRef::operator InterfaceType** – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
operator InterfaceType**();
```

## <a name="remarks"></a>Poznámky

Odstraní aktuální **comptrref –** objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována **comptrref –** objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ComPtrRef – třída](../windows/comptrref-class.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)