---
title: Module::Create – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444694"
---
# <a name="modulecreate-method"></a>Module::Create – metoda

Vytvoří instanci modulu.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()  
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ modulu.

*zpětné volání*<br/>
Volá se, když se uvolní objekt poslední instance modulu.

*object*<br/>
*Objekt* a *metoda* v kombinaci se používají parametry. Když se uvolní objekt poslední instance v modulu odkazuje na poslední instance objektu.

*– Metoda*<br/>
*Objekt* a *metoda* v kombinaci se používají parametry. Odkazuje na metodu poslední instance objektu poslední objekt instance v modulu se při uvolnění.

## <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)