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
ms.openlocfilehash: 6206a167c8b7292db21b9466975d057fc36cbe2f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604931"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags – struktura
Obsahuje typ pro instanci [RuntimeClass](../windows/runtimeclass-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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