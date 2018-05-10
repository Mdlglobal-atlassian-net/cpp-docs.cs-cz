---
title: Deferrableeventargs::invokeallfinished – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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