---
title: Runtimeclass::getiids – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 91d0a082a422657f6716e16c8b53ab33e0313d82
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020132"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids – metoda
Získává pole, která může obsahovat rozhraní implementované aktuální ID **RuntimeClass** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Parametry  
 *iidCount*  
 Pokud tato operace dokončí, celkový počet prvků v poli *IID*.  
  
 *IID*  
 Když tato operace dokončí, ukazatel na pole ID rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)