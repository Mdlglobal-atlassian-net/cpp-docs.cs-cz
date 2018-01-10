---
title: "Asweak – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::AsWeak
dev_langs: C++
helpviewer_keywords: AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2bc994c502a806fcca0ead9a5c73aa6f8b5dd02e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asweak-function"></a>AsWeak – funkce
Načte slabé odkaz na zadané instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename T  
>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Ukazatel na typ parametru `p`.  
  
 `p`  
 Instance typu.  
  
 `pWeak`  
 Když tato operace dokončí, ukazatel na slabé odkaz na parametr `p`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je tato operace úspěšná. v opačném chybu HRESULT, která určuje příčinu selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)