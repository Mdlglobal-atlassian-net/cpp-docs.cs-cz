---
title: "Boolstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::BoolStruct
dev_langs: C++
helpviewer_keywords: BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fdbaf9af73940ab342e915edb475f9f35027eaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Boolstruct::Member – datový člen](../windows/boolstruct-member-data-member.md)|Určuje, že [ComPtr](../windows/comptr-class.md) , nebo není, Správa doba života objektu rozhraní.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BoolStruct`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType operátor](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)