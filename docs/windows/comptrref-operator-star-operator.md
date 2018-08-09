---
title: ComPtrRef::operator * operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator* operator
ms.assetid: 0287ca7a-4ce1-47f7-bab6-714fca3e04bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 229a5a61bfe28280f7bffcd92f9d9cebffa2415b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647157"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator* Operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
InterfaceType* operator *();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní reprezentované aktuální **comptrref –** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Načte ukazatel na rozhraní reprezentované aktuální **comptrref –** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Comptrref – třída](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)