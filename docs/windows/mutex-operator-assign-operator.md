---
title: Mutex::Operator = – operátor | Dokumentace Microsoftu
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
ms.openlocfilehash: 9ce42a1e14e3de77b8ac10c67a8f15b6ee3f080f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019953"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= – operátor
Přiřadí (přesun) zadaný **Mutex** objektů na aktuální **Mutex** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odkaz rvalue na **Mutex** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální **Mutex** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu **přesunutí sémantiky** část [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –
 
 ## <a name="see-also"></a>Viz také
 [Mutex – třída](../windows/mutex-class1.md)