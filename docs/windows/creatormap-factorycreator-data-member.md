---
title: Creatormap::factorycreator – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57f6e841326339f78d24fa8affea5e74ae5b8d74
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465380"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator – datový člen
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT (*factoryCreator)(  
   unsigned int* currentflags,  
   const CreatorMap* entry,  
   REFIID iidClassFactory,  
 IUnknown** factory);  
```  
  
## <a name="parameters"></a>Parametry  
 *currentflags*  
 Jeden z [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) enumerátory.  
  
 *entry*  
 Creatormap –.  
  
 *iidClassFactory*  
 ID rozhraní objekt pro vytváření tříd.  
  
 *objekt pro vytváření*  
 Po dokončení operace, adresa objektu pro vytváření tříd.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří objekt pro vytváření pro zadaný creatormap –.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Creatormap – struktura](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)