---
title: Weakreference::setunknown – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6adf747fd7612c2bcaa0964f91ecb585bbfbef0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018049"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void SetUnknown(  
   _In_ IUnknown* unk  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *UNK*  
 Ukazatel `IUnknown` rozhraní objektu.  
  
## <a name="remarks"></a>Poznámky  
 Nastaví silný odkaz aktuální **WeakReference** objektu na zadané rozhraní ukazatel.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také
 [Weakreference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)