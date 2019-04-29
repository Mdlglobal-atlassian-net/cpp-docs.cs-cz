---
title: AsyncStatusInternal – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: f12bf4aafc87e44a6e2fb15ba79de4a9744bea58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398781"
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

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)