---
title: AsyncStatusInternal – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 0eadd1e3a287feecd36b00b231b42c31218352c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214146"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Poznámky

Určuje mapování mezi interními výčty pro stav asynchronních operací a výčet `Windows::Foundation::AsyncStatus`.

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

**Hlavička:** Async. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
