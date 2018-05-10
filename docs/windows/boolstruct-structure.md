---
title: Boolstruct – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af2827d85a1df647dca2c02c5c6ee5a12a416d51
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="boolstruct-structure"></a>BoolStruct – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct BoolStruct;  
```  
  
## <a name="remarks"></a>Poznámky  
 Boolstruct – struktura definuje, zda je ComPtr správou doba života objektu rozhraní. Boolstruct – se používá interně pomocí [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operátor.  
  
## <a name="members"></a>Členové  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[BoolStruct::Member – datový člen](../windows/boolstruct-member-data-member.md)|Určuje, že [ComPtr](../windows/comptr-class.md) , nebo není, Správa doba života objektu rozhraní.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BoolStruct`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType – operátor](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)