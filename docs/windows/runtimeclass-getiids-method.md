---
title: Runtimeclass::getiids – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c309c97b9c9ce057ca67ab4b5d729c61d803ea5a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids – metoda
Získá pole, které může obsahovat ID implementované aktuální objekt RuntimeClass rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iidCount`  
 Když tato operace dokončí, celkový počet prvků v poli `iids`.  
  
 `iids`  
 Když tato operace dokončí, ukazatel na pole ID rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)