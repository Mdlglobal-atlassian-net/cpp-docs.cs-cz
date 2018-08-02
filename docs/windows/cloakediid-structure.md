---
title: Cloakediid – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
dev_langs:
- C++
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e0155006987165f5b192aac73bb31991081a231
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461220"
---
# <a name="cloakediid-structure"></a>CloakedIid – struktura
Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Rozhraní, který je skrytý (skryté).  
  
## <a name="remarks"></a>Poznámky  
 Následuje příklad `CloakedIid` se používá: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)