---
title: "Synclockwithstatust::getStatus – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs: C++
helpviewer_keywords: GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd9fe5d9c572b48904bff820466e5665291f6808
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek operace čekání na objekt, který je založen na třídě SyncLockWithStatusT například [Mutex](../windows/mutex-class1.md) nebo [Semaphore](../windows/semaphore-class.md). Nula (0) označuje, že operace čekání vrátil stav signalizovaného; jinak jiný stav došlo k chybě, například uplynulý čas vypršení platnosti.  
  
## <a name="remarks"></a>Poznámky  
 Načte stav Čekání aktuálního objektu SyncLockWithStatusT.  
  
 Načte hodnotu základní funkce GetStatus() [status_ –](../windows/synclockwithstatust-status-data-member.md) – datový člen. Pokud objekt podle SyncLockWithStatusT – třída provádí operace uzamčení, objekt nejprve čeká objekt k dispozici. Výsledek této operace čekání je uložený v `status_` – datový člen. Možné hodnoty `status_` – datový člen jsou vrácené hodnoty operace čekání. Další informace najdete v tématu vrácené hodnoty **WaitForSingleObjectEx()** funkce v knihovně MSDN.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)