---
title: Comptrref::comptrref – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef, constructor
ms.assetid: ce2d2533-fef6-4b2d-b088-6f3db01df5a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24844588a18f269ee6f3a19286e6755b11b1c6bf
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463629"
---
# <a name="comptrrefcomptrref-constructor"></a>ComPtrRef::ComPtrRef – konstruktor
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ComPtrRef(  
   _In_opt_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *ptr*  
 Zadaná hodnota jiného **comptrref –** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy **comptrref –** třídy z zadaný ukazatel na jiný **comptrref –** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Comptrref – třída](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)