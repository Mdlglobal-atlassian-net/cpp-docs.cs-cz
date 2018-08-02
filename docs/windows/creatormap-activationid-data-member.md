---
title: Creatormap::activationid – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70a331bbbf34a623b02e9d8bc9aa0b80fbee2216
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467128"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId – datový člen
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## <a name="parameters"></a>Parametry  
 *identifikátor CLSID*  
 Identifikátor rozhraní.  
  
 *getRuntimeName*  
 Funkce, která načte název modulu runtime Windows objektu.  
  
## <a name="remarks"></a>Poznámky  
 Představuje ID objektu, který je identifikován classic ID třídy modelu COM nebo název modulu runtime Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Creatormap – struktura](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)