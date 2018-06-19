---
title: HStringReference::Operator = – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73ec71526d340aafb16ddf2af274dce7ad0e9cbd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875536"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= – operátor
Hodnota jiného objektu HStringReference přesune na aktuální objekt HStringReference.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Existující objekt HStringReference.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota existující `other` objektu se zkopíruje do aktuální objekt HStringReference a potom `other` zničena objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HStringReference – třída](../windows/hstringreference-class.md)