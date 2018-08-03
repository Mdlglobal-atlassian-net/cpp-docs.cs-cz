---
title: ComPtr::operator! = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a4c15946862a66c0d4d830f590230763ce3e6f9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461819"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= – operátor
Určuje, zda dva **ComPtr** objekty nejsou stejné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *a*  
 Odkaz na **ComPtr** objektu.  
  
 *b*  
 Odkaz na jiný **ComPtr** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 První operátor výnosy **true** Pokud objekt *a* není roven objektu *b*; v opačném případě **false**.  
  
 Druhý a třetí operátory yield **true** Pokud objekt *a* není roven **nullptr**; v opačném případě **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr – třída](../windows/comptr-class.md)