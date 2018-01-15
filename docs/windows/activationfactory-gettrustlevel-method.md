---
title: "Activationfactory::gettrustlevel – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs: C++
helpviewer_keywords: GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48db1632c50726073372e314a338cdca543c29e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel – metoda
Získá objekt, který vytvoří instanci aktuální ActivationFactory úroveň důvěryhodnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### <a name="parameters"></a>Parametry  
 `trustLvl`  
 Když tato operace dokončí, úroveň důvěryhodnosti třídy runtime, která vytvoří instanci ActivationFactory.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak, jsou vydávány chybu kontrolní výraz a `trustLvl` je nastaven na FullTrust.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ActivationFactory – třída](../windows/activationfactory-class.md)