---
title: ComPtrRef::operator == – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 606059712e60ba181998155b55ae02ba8b27c4da
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463951"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *a*  
 Odkaz na objekt comptrref –.  
  
 *b*  
 Odkaz na jiný objekt comptrref – nebo ukazatel na anonymního typu (`void*`).  
  
## <a name="return-value"></a>Návratová hodnota  
 První operátor výnosy **true** Pokud objekt *a* rovná objektu *b*; v opačném případě **false**.  
  
 Druhý a třetí operátory yield **true** Pokud objekt *a* rovná **nullptr**; v opačném případě **false**.  
  
 Čtvrtý a pátý operátory yield **true** Pokud objekt *a* rovná objektu *b*; v opačném případě **false**.  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda dva objekty comptrref – jsou stejné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef – třída](../windows/comptrref-class.md)