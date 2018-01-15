---
title: "Mutex::Operator = – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23526911a2d9e723455a7d846bdaafb2dbefd45a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mutexoperator-operator"></a>Mutex::operator= – operátor
Přiřadí (přesune) zadaný objekt Mutex do aktuální objekt Mutex objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Rvalue – odkaz na objekt Mutex.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální objekt Mutex.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu **přesunout sémantiku** části [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –
 
 ## <a name="see-also"></a>Viz také
 [Mutex – třída](../windows/mutex-class1.md)