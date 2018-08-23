---
title: Modulebase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6d60e5114d189ddede87899bb55fba25a296c57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601468"
---
# <a name="modulebase-class"></a>ModuleBase – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Poznámky

Představuje základní třídu [modulu](../windows/module-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[ModuleBase::ModuleBase – konstruktor](../windows/modulebase-modulebase-constructor.md)|Inicializuje novou instanci `Module` třídy.|
|[ModuleBase::~ModuleBase – destruktor](../windows/modulebase-tilde-modulebase-destructor.md)|Zruší inicializaci aktuální instance `Module` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ModuleBase::DecrementObjectCount – metoda](../windows/modulebase-decrementobjectcount-method.md)|Při implementaci, sníží počet objektů sledování modulu.|
|[ModuleBase::IncrementObjectCount – metoda](../windows/modulebase-incrementobjectcount-method.md)|Při implementaci, zvýší počet objektů, které jsou sledovány v rámci modulu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ModuleBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)