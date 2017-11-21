---
title: "AsyncStatusInternal – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs: C++
helpviewer_keywords: AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f014cb2bdf1fa6077dd6922e40e0253b5297c29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje mapování mezi interní výčty pro stav asynchronní operace a **Windows::Foundation::AsyncStatus** výčtu.  
  
## <a name="members"></a>Členové  
 `_Created`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: vytvořen  
  
 `_Started`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: spustila  
  
 `_Completed`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: dokončena  
  
 `_Cancelled`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: zrušena  
  
 `_Error`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)