---
title: WeakRef::operator&amp; operátor | Dokumentace Microsoftu
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
ms.openlocfilehash: 125ffe998e7c3f225f72e3fb47df4ef3525c37f9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649045"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; – operátor
Vrátí `ComPtrRef` objekt, který představuje aktuální **WeakRef** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&() throw()  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 A `ComPtrRef` objekt, který představuje aktuální **WeakRef** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Toto je interní pomocné operátor, který není určena k použití ve vašem kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)