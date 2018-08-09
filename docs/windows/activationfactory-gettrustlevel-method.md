---
title: Activationfactory::gettrustlevel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bddc5a453e1c3aac43fe58d105ccef863c67808
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652266"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel – metoda
Získá úroveň důvěryhodnosti objektu, který aktuální **activationfactory –** vytvoří instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
### <a name="parameters"></a>Parametry  
 *trustLvl*  
 Po dokončení této operace úroveň důvěryhodnosti modulu runtime třídy, která **activationfactory –** vytvoří instanci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě je vygenerován chybu kontrolní výraz a *trustLvl* je nastavena na `FullTrust`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ActivationFactory – třída](../windows/activationfactory-class.md)