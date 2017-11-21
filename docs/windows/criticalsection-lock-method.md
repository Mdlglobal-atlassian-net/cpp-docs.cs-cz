---
title: "Criticalsection::Lock – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs: C++
helpviewer_keywords: Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4df91ea9030ca4917f246bc05be1ba059673680e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock – metoda
Čeká na vlastnictví objektu zadaného kritická sekce. Funkce vrátí hodnotu, pokud volající vlákno je uděleno vlastnictví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cs`  
 Objekt zadaného uživatelem kritická sekce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Zámek objekt, který lze použít k odemknutí aktuální kritická sekce.  
  
## <a name="remarks"></a>Poznámky  
 První **zámku** funkce ovlivňuje aktuální objekt kritická sekce. Druhý **zámku** funkce ovlivňuje kritická sekce zadaného uživatelem.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [CriticalSection – třída](../windows/criticalsection-class.md)