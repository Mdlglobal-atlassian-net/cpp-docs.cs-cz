---
title: "Invokehelper::invokehelper – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs: C++
helpviewer_keywords: InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7016ce1c0a3e9c4a327f5db66903461e6748176
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper – konstruktor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit InvokeHelper(  
   TCallback callback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `callback`  
 Obslužné rutiny události.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy invokehelper –.  
  
 `TCallback` Parametr šablony určuje typ obslužné rutiny události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Invokehelper – struktura](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)