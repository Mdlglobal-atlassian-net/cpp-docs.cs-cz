---
title: Implements::fillarraywithiid – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e020bd725d0c0f5c65ab1cfb38b45e2b8fbca62e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875718"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid – metoda
Vloží zadané parametrem aktuální šablony zeroth do elementu zadané pole ID rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Index počítaný od nuly určující počáteční elementu pole pro tuto operaci. Po dokončení této operace `index` se zvýší o 1.  
  
 `iids`  
 Pole typu IID.  
  
## <a name="remarks"></a>Poznámky  
 Interní pomocné funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Implements – struktura](../windows/implements-structure.md)