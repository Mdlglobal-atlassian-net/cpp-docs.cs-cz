---
title: Isbaseofstrict::Value – konstanta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eaaf0b410861f28cd5b339f75a73c594b1bcba45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875803"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value – konstanta
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const bool value = __is_base_of(Base, Derived);  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje, zda jeden typ základní jiného.  
  
 `value` je `true` Pokud typ `Base` je základní třídou typu `Derived`, v opačném případě je `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** internal.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Isbaseofstrict – struktura](../windows/isbaseofstrict-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)