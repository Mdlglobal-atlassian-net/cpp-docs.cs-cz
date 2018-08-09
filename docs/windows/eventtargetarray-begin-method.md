---
title: Eventtargetarray::begin – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs:
- C++
helpviewer_keywords:
- Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5dc081a24495fc8939f3069dc68bed4f75beaaf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642822"
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
ComPtr<IUnknown>* Begin();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Adresa první prvek v poli interní obslužných rutin událostí.  
  
## <a name="remarks"></a>Poznámky  
 Získá adresu prvního prvku v poli interní obslužných rutin událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Eventtargetarray – třída](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)