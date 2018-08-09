---
title: Weakref::weakref – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e7b7d35fd8cae44c3f374a81cae572e4c9ee4f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011156"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef – konstruktor
Inicializuje novou instanci třídy **WeakRef** třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *ptr*  
 Ukazatel, odkaz nebo odkaz rvalue na existující objekt, který inicializuje aktuální **WeakRef** objektu.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje prázdnou **WeakRef** objektu. Druhý konstruktor inicializuje **WeakRef** z ukazatele na objekt `IWeakReference` rozhraní. Třetí konstruktor inicializuje **WeakRef** z odkazu na objekt `ComPtr<IWeakReference>` objektu. Čtvrtý a pátý konstruktor inicializuje **WeakRef** objektu z jiného **WeakRef** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [WeakRef – třída](../windows/weakref-class.md)