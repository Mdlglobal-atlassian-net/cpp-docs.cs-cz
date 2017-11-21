---
title: "Implements::fillarraywithiid – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs: C++
helpviewer_keywords: FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a53a7eb9a05e1f4583c49b42fa10efdf1ee815ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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