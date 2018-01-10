---
title: "Runtimeclass::getweakreference – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetWeakReference
dev_langs: C++
helpviewer_keywords: GetWeakReference method
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba87fe5097f9aff52b54770c1d438be2be425259
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassgetweakreference-method"></a>RuntimeClass::GetWeakReference – metoda
Získá ukazatel na objekt slabé odkaz pro aktuální objekt RuntimeClass.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetWeakReference  
)(_Deref_out_ IWeakReference **weakReference);  
```  
  
#### <a name="parameters"></a>Parametry  
 `weakReference`  
 Když tato operace dokončí, ukazatel na slabé referenční objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)