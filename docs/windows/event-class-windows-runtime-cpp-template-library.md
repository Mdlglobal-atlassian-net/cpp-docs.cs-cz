---
title: Event – třída (knihovna šablon C++ prostředí Windows Runtime) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c07d58f244bf2e7e6c9329196bae7b5bb323ce12
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644161"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event – třída (knihovna šablon C++ prostředí Windows Runtime)
Představuje událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Event::Event Konstruktor (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Inicializuje novou instanci třídy **události** třídy.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Event::operator= – operátor](../windows/event-operator-assign-operator.md)|Přiřadí zadaný **události** odkaz na aktuální **události** instance.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HandleT`  
  
 `Event`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)