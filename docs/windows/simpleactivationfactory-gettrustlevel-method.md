---
title: Simpleactivationfactory::gettrustlevel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22fa30a3662897b171245da194573ec17da2f64e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645185"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel – metoda
Získá instanci třídy určené úroveň důvěryhodnosti `Base` parametr šablony třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
### <a name="parameters"></a>Parametry  
 *trustLvl*  
 Když tato operace dokončí, úroveň důvěryhodnosti objektu aktuální třídy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)