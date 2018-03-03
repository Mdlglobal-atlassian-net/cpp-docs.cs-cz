---
title: "Eventtargetarray::eventtargetarray – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8c8ada61a18437ed159452355e8286bc9d190f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray – konstruktor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Po operacích tento konstruktor parametr `hr` označuje, zda přidělení pole byla úspěšná nebo neúspěšná. Následující tabulka uvádí možné hodnoty pro `hr`.  
  
 S_OK  
 Operace byla úspěšná.  
  
 E_OUTOFMEMORY  
 Nepodařilo se přidělit paměť pro pole.  
  
 S_FALSE  
 Parametr `items` je menší než nebo rovna nule.  
  
 `items`  
 Počet elementů pole přidělit.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy EventTargetArray.  
  
 EventTargetArray slouží k udržování pole obslužné rutiny událostí v objektu EventSource.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [EventTargetArray – třída](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)