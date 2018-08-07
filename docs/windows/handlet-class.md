---
title: Handlet – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87a8718971a2da008b03dca1e9653d8454115adb
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570594"
---
# <a name="handlet-class"></a>HandleT – třída
Reprezentuje popisovač objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
### <a name="parameters"></a>Parametry  
 *Handletraits –*  
 Instance [handletraits –](../windows/handletraits-structure.md) stucture, který definuje běžné vlastnosti popisovač.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Traits`|Synonymum pro `HandleTraits`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::HandleT – konstruktor](../windows/handlet-handlet-constructor.md)|Inicializuje novou instanci třídy **HandleT** třídy.|  
|[HandleT::~HandleT – destruktor](../windows/handlet-tilde-handlet-destructor.md)|Uvolní instanci **HandleT** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::Attach – metoda](../windows/handlet-attach-method.md)|Přidruží Zadaný popisovač s aktuálním **HandleT** objektu.|  
|[HandleT::Close – metoda](../windows/handlet-close-method.md)|Zavře aktuální **HandleT** objektu.|  
|[HandleT::Detach – metoda](../windows/handlet-detach-method.md)|Zruší přidružení aktuální **HandleT** objekt z jeho základní popisovač.|  
|[HandleT::Get – metoda](../windows/handlet-get-method.md)|Načte hodnotu podkladového popisovače.|  
|[HandleT::IsValid – metoda](../windows/handlet-isvalid-method.md)|Určuje, zda aktuální **HandleT** objekt představuje popisovač.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::InternalClose – metoda](../windows/handlet-internalclose-method.md)|Zavře aktuální **HandleT** objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::operator= – operátor](../windows/handlet-operator-assign-operator.md)|Přesune hodnotu zadaného **handlet –** objektů na aktuální **HandleT** objektu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[HandleT::handle_ – datový člen](../windows/handlet-handle-data-member.md)|Obsahuje popisovač, která je reprezentována **HandleT** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HandleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)