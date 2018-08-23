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
ms.openlocfilehash: 9ae4f50e6d2d614e444766babf8e55f5c9f83932
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609541"
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

*T*  
Typ modulu.

*zpětné volání*  
Volá se, když se uvolní objekt poslední instance modulu.

*object*  
*Objekt* a *metoda* v kombinaci se používají parametry. Když se uvolní objekt poslední instance v modulu odkazuje na poslední instance objektu.

*– Metoda*  
*Objekt* a *metoda* v kombinaci se používají parametry. Odkazuje na metodu poslední instance objektu poslední objekt instance v modulu se při uvolnění.

## <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)