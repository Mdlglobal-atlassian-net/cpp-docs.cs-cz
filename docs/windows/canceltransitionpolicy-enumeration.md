---
title: CancelTransitionPolicy – výčet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs:
- C++
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64f588e67066fed690271aa7d78fcbe726c67177
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)