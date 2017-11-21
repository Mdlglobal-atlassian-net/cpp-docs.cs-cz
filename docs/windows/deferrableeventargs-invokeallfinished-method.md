---
title: "Deferrableeventargs::invokeallfinished – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: acae8467ceeaaafea6668d4fbf6b5e2f4884b373
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [EventSource::invokeall – metoda](../windows/eventsource-invokeall-method.md)