---
title: Comptrref::releaseandgetaddressof – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 273c8aaded45e04f1564d434c1a4f4a6920c3883
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647798"
---
# <a name="comptrrefreleaseandgetaddressof-method"></a>ComPtrRef::ReleaseAndGetAddressOf – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
InterfaceType** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní, která je reprezentována pomocí odstraněným **comptrref –** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Odstraní aktuální **comptrref –** objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována **comptrref –** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Comptrref – třída](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)