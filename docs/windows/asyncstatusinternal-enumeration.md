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
ms.openlocfilehash: 4c7751929a55993876034bb3c1918b82193681fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016881"
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

`_Created`<br/>
Ekvivalent `::Windows::Foundation::AsyncStatus::Created`

`_Started`<br/>
Ekvivalent `::Windows::Foundation::AsyncStatus::Started`

`_Completed`<br/>
Ekvivalent `::Windows::Foundation::AsyncStatus::Completed`

`_Cancelled`<br/>
Ekvivalent `::Windows::Foundation::AsyncStatus::Cancelled`

`_Error`<br/>
Ekvivalent `::Windows::Foundation::AsyncStatus::Error`

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)