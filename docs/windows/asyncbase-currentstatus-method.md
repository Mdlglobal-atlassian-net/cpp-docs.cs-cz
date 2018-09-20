---
title: Asyncbase::currentStatus – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 792f9f6c6d76097459498c43068f46d86b2e2349
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401482"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus – metoda

Načte stav aktuální asynchronní operace.

## <a name="syntax"></a>Syntaxe

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Umístění, kde tato operace uloží aktuální stav.

## <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro vlákno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)<br/>
[AsyncStatusInternal – výčet](../windows/asyncstatusinternal-enumeration.md)