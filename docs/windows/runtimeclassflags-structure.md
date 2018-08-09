---
title: Runtimeclassflags – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 823244b54513e4f6b2901bc29984604f65eb9a11
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018033"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura
Obsahuje typ pro instanci [RuntimeClass](../windows/runtimeclass-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
### <a name="parameters"></a>Parametry  
 *příznaky*  
 A [runtimeclasstype – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[RuntimeClassFlags::value – konstanta](../windows/runtimeclassflags-value-constant.md)|Obsahuje [runtimeclasstype – výčet](../windows/runtimeclasstype-enumeration.md) hodnotu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)