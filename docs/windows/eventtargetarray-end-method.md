---
title: Eventtargetarray::end – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17f79830cf50d83058ee2f2665b94f86a53acd78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428977"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
ComPtr<IUnknown>* End();
```

## <a name="return-value"></a>Návratová hodnota

Adresa poslední prvek v poli interní obslužných rutin událostí.

## <a name="remarks"></a>Poznámky

Získá adresu poslední prvek v poli interní obslužných rutin událostí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[EventTargetArray – třída](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)