---
title: "Creatormap::factorycreator – datový člen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs: C++
helpviewer_keywords: factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e145bf91539274763c27650bd123120cafb184bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator – datový člen
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT (*factoryCreator)(  
   unsigned int* currentflags,  
   const CreatorMap* entry,  
   REFIID iidClassFactory,  
 IUnknown** factory);  
```  
  
## <a name="parameters"></a>Parametry  
 `currentflags`  
 Jeden z [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) výčty.  
  
 `entry`  
 Creatormap –.  
  
 `iidClassFactory`  
 Rozhraní ID objektu pro vytváření tříd.  
  
 `factory`  
 Po dokončení operace, adresu objektu pro vytváření tříd.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří objekt factory pro zadaný creatormap –.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Creatormap – struktura](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)