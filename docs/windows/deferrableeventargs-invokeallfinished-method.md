---
title: Deferrableeventargs::invokeallfinished – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 23d521b8373969abdd739b6e4f48eb334284664d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605170"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished – metoda
Volá se, že je veškeré zpracování zpracování odložené události dokončení.
  
## <a name="syntax"></a>Syntaxe
  
```cpp
void InvokeAllFinished()  
```
  
## <a name="remarks"></a>Poznámky
 Byste měli volat tuto metodu po volání zdroje události [invokeall –](../windows/eventsource-invokeall-method.md). Voláním této metody zabrání se dalšímu odložení změněny a vynutí obslužné rutiny dokončení spustit, když se nevytvořily žádné odložení.
  
 Příklad kódu naleznete v tématu [deferrableeventargs – třída](../windows/deferrableeventargs-class.md).
  
## <a name="requirements"></a>Požadavky
 **Záhlaví:** event.h
  
 **Namespace:** Microsoft::WRL
  
## <a name="see-also"></a>Viz také
 [DeferrableEventArgs – třída](../windows/deferrableeventargs-class.md)  
 [EventSource::InvokeAll – metoda](../windows/eventsource-invokeall-method.md)