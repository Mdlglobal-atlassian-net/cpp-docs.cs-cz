---
title: ComPtrRef::operator void ** – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbe9f077fd0d80a831d319660be26090ad5411f6
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463850"
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void\* \* – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Odstraní aktuální **comptrref –** objektu, přetypování ukazatel na rozhraní, která je reprezentována **comptrref –** objektu jako ukazatel na ukazatel- **void**a pak vrátí ukazatel přetypování.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Comptrref – třída](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)