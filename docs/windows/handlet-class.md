---
title: "HandleT – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs: C++
helpviewer_keywords: HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff7261735149abb8db607c5fc0cd4aa837fdfd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handlet-class"></a>HandleT – třída
Představuje popisovač objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `HandleTraits`  
 Instance [handletraits –](../windows/handletraits-structure.md) stucture, která definuje běžné vlastnosti popisovač.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Traits`|Synonymum pro `HandleTraits`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::HandleT – konstruktor](../windows/handlet-handlet-constructor.md)|Inicializuje novou instanci třídy HandleT.|  
|[HandleT::~HandleT – destruktor](../windows/handlet-tilde-handlet-destructor.md)|Instance třídy HandleT deinitializes.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::Attach – metoda](../windows/handlet-attach-method.md)|Aktuální objekt HandleT přidruží Zadaný popisovač.|  
|[HandleT::Close – metoda](../windows/handlet-close-method.md)|Zavře aktuální objekt HandleT.|  
|[HandleT::Detach – metoda](../windows/handlet-detach-method.md)|Aktuální objekt HandleT z jeho základní popisovač zrušíte.|  
|[HandleT::Get – metoda](../windows/handlet-get-method.md)|Získá hodnotu základní popisovač.|  
|[HandleT::IsValid – metoda](../windows/handlet-isvalid-method.md)|Určuje, zda aktuální objekt HandleT představuje popisovač.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::InternalClose – metoda](../windows/handlet-internalclose-method.md)|Zavře aktuální objekt HandleT.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::operator= – operátor](../windows/handlet-operator-assign-operator.md)|Hodnota zadaného objektu HandleT přesune na aktuální objekt HandleT.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::handle_ – datový člen](../windows/handlet-handle-data-member.md)|Obsahuje obslužná rutina, která je reprezentována HandleT objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HandleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)