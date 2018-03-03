---
title: "Deferrableeventargs::invokeallfinished – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ca021d66c615bfec84b8f08df8474eeb20709e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished – metoda
Voláno k označení, že veškeré zpracování zpracování odložené události je kompletní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda by měly volat po volání zdroje událostí [invokeall –](../windows/eventsource-invokeall-method.md). Voláním této metody zabrání se dalšímu rozlišených položek přijetí a vynutí se tak, aby obslužná rutina dokončení spustit, pokud byly provedeny žádné rozlišených položek.  
  
 Příklad kódu, najdete v části [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll – metoda](../windows/eventsource-invokeall-method.md)