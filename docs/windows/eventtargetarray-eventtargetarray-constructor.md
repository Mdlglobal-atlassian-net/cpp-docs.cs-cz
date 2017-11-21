---
title: "Eventtargetarray::eventtargetarray – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6dbe316310e04172c659460c08137edd2a401df6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)