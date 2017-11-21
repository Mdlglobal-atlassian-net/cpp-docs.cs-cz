---
title: "Synclockt::synclockt – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs: C++
helpviewer_keywords: SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb7e1f9715f84a272e6bdb1029439f9310a65428
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT – konstruktor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Rvalue – odkaz na jiný objekt SyncLockT.  
  
 `sync`  
 Odkaz na jiný objekt SyncLockWithStatusT.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy SyncLockT – třída.  
  
 První konstruktor inicializuje aktuální objekt SyncLockT z jiného objektu SyncLockT určený parametrem `other`a pak zruší platnost druhý SyncLockT objekt. Druhý konstruktor je `protected`a inicializuje aktuální SyncLockT objekt, který má neplatný stav.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [SyncLockT – třída](../windows/synclockt-class.md)