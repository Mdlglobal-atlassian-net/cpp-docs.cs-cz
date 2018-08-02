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
ms.openlocfilehash: c2ec20dca7bb0a37adae576a8b5a9adfad027b21
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465812"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** – operátor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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