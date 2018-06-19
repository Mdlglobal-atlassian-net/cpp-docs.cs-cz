---
title: Mutex::Operator = – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8791d3c947206be399f475bb8c895b2b5e032133
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875484"
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