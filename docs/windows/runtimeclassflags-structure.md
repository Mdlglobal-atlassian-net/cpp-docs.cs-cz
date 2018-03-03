---
title: "Runtimeclassflags – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85eb42c537845d86ce8cf3b1f20db7e9eeffe76f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura
Obsahuje typu pro instanci [RuntimeClass](../windows/runtimeclass-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 A [RuntimeClassType – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[RuntimeClassFlags::value – konstanta](../windows/runtimeclassflags-value-constant.md)|Obsahuje [RuntimeClassType – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)