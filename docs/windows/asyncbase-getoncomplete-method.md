---
title: Asyncbase::getoncomplete – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffe517b75df4e1cdd8172279c12256db940f0980
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647034"
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete – metoda
Adresa aktuálního obslužné rutiny události dokončení zkopíruje do zadané proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
### <a name="parameters"></a>Parametry  
 *completeHandler*  
 Umístění, kde je uložen adresu aktuální obslužné rutiny události dokončení.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)