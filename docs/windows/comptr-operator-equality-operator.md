---
title: ComPtr::operator == – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e68566b5f8fa519a3cfcd5a406cc812edfaf8480
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648591"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== – operátor
Určuje, zda dva **ComPtr** objekty rovnají.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *a*  
 Odkaz na **ComPtr** objektu.  
  
 *b*  
 Odkaz na jiný **ComPtr** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 První operátor výnosy **true** Pokud objekt *a* rovná objektu *b*; v opačném případě **false**.  
  
 Druhý a třetí operátory yield **true** Pokud objekt *a* rovná **nullptr**; v opačném případě **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr – třída](../windows/comptr-class.md)