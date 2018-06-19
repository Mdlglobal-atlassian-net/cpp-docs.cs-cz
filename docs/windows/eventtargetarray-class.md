---
title: EventTargetArray – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4461004a1681d9095449c51fb9cb3973d5017693
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881306"
---
# <a name="eventtargetarray-class"></a>EventTargetArray – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Poznámky  
 Představuje pole obslužné rutiny událostí.  
  
 Obslužné rutiny událostí, které jsou přidružené [EventSource](../windows/eventsource-class.md) objekt jsou uložené v chráněného člena EventTargetArray data.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray – konstruktor](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializuje novou instanci třídy EventTargetArray.|  
|[EventTargetArray::~EventTargetArray – destruktor](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Deinitializes aktuální EventTargetArray – třída.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[EventTargetArray::AddTail – metoda](../windows/eventtargetarray-addtail-method.md)|Přidá zadanou událost obslužné rutiny na konec interní pole obslužné rutiny událostí.|  
|[EventTargetArray::Begin – metoda](../windows/eventtargetarray-begin-method.md)|Získá adresu první prvek v poli interní obslužných rutin událostí.|  
|[EventTargetArray::End – metoda](../windows/eventtargetarray-end-method.md)|Získá adresu posledním prvkem v poli interní obslužných rutin událostí.|  
|[EventTargetArray::Length – metoda](../windows/eventtargetarray-length-method.md)|Získá aktuální počet prvků v poli interní obslužných rutin událostí.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `EventTargetArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)