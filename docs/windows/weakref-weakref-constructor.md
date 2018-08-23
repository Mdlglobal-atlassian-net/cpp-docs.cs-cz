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
ms.openlocfilehash: d7c8bc81040ce8d4c1cea7497f9d1371fbb9d41f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611607"
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