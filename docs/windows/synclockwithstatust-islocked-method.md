---
title: "Synclockwithstatust::islocked – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs: C++
helpviewer_keywords: IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e31f0931a53e8bdd977e82fcef56f1bacc45f76b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda je aktuální objekt SyncLockWithStatusT vlastní prostředek; To znamená, je objekt SyncLockWithStatusT *uzamčení*.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud objekt SyncLockWithStatusT je uzamčení, jinak hodnota **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)