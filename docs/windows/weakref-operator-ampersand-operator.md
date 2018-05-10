---
title: WeakRef::operator&amp; operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c8221b405618b1879f4e4c865115a227eb09857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; – operátor
Vrátí objekt ComPtrRef, který představuje aktuální objekt WeakRef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 ComPtrRef objekt, který představuje aktuální objekt WeakRef.  
  
## <a name="remarks"></a>Poznámky  
 Toto je interní pomocná operátor, který není určen pro použití v kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)