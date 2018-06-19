---
title: Cloakediid – struktura | Microsoft Docs
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
ms.openlocfilehash: 57ad76b48b92519eaeed089dfb14817c38273588
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856157"
---
# <a name="cloakediid-structure"></a>CloakedIid – struktura
Šablon RuntimeClass, implementuje a chaininterfaces – označuje, že zadané rozhraní není dostupný v seznamu IID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Rozhraní, které je skrytý (skryté).  
  
## <a name="remarks"></a>Poznámky  
 Následuje příklad použití cloakediid –: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)