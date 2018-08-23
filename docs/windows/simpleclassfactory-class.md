---
title: Simpleclassfactory – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: deb100cfcbb8d2af14501b8b5cf90569a90c2d4d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600488"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory – třída

Poskytuje základní mechanismus pro vytvoření základní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*základ*  
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytovat konstruktor default.

Následující příklad kódu ukazuje, jak používat **simpleclassfactory –** s [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance – metoda](../windows/simpleclassfactory-createinstance-method.md)|Vytvoří instanci zadaného rozhraní.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)