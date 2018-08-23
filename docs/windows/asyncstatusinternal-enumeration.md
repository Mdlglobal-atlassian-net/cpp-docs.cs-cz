---
title: Asyncstatusinternal – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b389e5b137ef3cdb94ffbb1fc381ebe2e5813963
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603967"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Poznámky

Určuje mapování mezi interní výčty pro stav asynchronní operace a `Windows::Foundation::AsyncStatus` výčtu.

## <a name="members"></a>Členové

`_Created`  
Ekvivalent `::Windows::Foundation::AsyncStatus::Created`

`_Started`  
Ekvivalent `::Windows::Foundation::AsyncStatus::Started`

`_Completed`  
Ekvivalent `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`  
Ekvivalent `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`  
Ekvivalent `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)