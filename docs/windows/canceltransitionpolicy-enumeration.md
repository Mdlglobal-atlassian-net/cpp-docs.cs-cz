---
title: "CancelTransitionPolicy – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs: C++
helpviewer_keywords: CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f21959daf740155a70787f7c35f8467d1fb2149
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy – výčet
Určuje, jak je asynchronní operace pokus o přechod do stavu terminálu z byla dokončena nebo chyba by měl chovat s ohledem na klient požádal zrušené stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`RemainCanceled`|Pokud asynchronní operace aktuálně zrušené stavu klient požádal, znamená to, že zůstane ve stavu zrušené oproti přechodu do Terminálové dokončit nebo chybový stav.|  
|`TransitionFromCanceled`|Pokud asynchronní operaci je momentálně ve stavu zrušené klient požádal, označuje stav měli přechod od zrušené stavu terminálu stavu dokončení nebo Chyba určeného hovoru, který využívá tento příznak.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)