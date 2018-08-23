---
title: Asyncbase::Cancel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbf216d672dd22e453f8c213f7a9f34f08a47273
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593134"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel – metoda

Zruší asynchronní operace.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   Cancel
)(void);
```

## <a name="return-value"></a>Návratová hodnota

Ve výchozím nastavení vždy vrátí hodnotu S_OK.

## <a name="remarks"></a>Poznámky

**Cancel()** je výchozí implementace `IAsyncInfo::Cancel`, a nemá žádné samotnou práci. Pokud chcete skutečně zrušit asynchronní operaci, přepsat `OnCancel()` čistě virtuální metody.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)