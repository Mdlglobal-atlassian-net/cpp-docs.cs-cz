---
title: ComPtrRef::operator! = – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d5a6e7389215452177add30b587004c312aeae1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= – operátor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator!=(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `a`  
 Odkaz na objekt ComPtrRef.  
  
 `b`  
 Odkaz na jiný objekt ComPtrRef nebo ukazatel na anonymní objekt (`void*`).  
  
## <a name="return-value"></a>Návratová hodnota  
 První operátor jsou `true` Pokud objekt `a` není roven objektu `b`, jinak hodnota `false`.  
  
 Yield – operátory druhý a třetí `true` Pokud objekt `a` se nerovná `nullptr`, jinak hodnota `false`.  
  
 Yield – operátory čtvrté a páté `true` Pokud objekt `a` není roven objektu `b`, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda dva objekty ComPtrRef nejsou stejné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef – třída](../windows/comptrref-class.md)