---
title: Runtimeclassflags – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05166be14680b14d704095f5f1c9375bd97da7d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892023"
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