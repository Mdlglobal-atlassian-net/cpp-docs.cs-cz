---
title: ComPtrRefBase::operator IUnknown ** – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4a176cedd0860251fd81dedb74deecf5f2c7e31
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648675"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
operator IUnknown**() const;  
```  
  
## <a name="remarks"></a>Poznámky  
 Přetypování aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) na ukazatel na ukazatel – datový člen `IUnknown` rozhraní.  
  
 Je vygenerován chybu, pokud aktuální **comptrrefbase –** není odvozen od `IUnknown`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Comptrrefbase – třída](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)