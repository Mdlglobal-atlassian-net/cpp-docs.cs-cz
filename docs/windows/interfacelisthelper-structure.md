---
title: Interfacelisthelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8d8b44f6b3732c19977e6839e96d4ab5013a112
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788406"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>Parametry

*T0*<br/>
Parametr šablony 0, což je povinné.

*T1*<br/>
Parametr šablony 1, která ve výchozím nastavení není zadán.

*T2*<br/>
Parametr šablony 2, která ve výchozím nastavení není zadán. Třetí parametr šablony.

*T3*<br/>
Parametr šablony 3, která ve výchozím nastavení není zadán.

*T4*<br/>
Parametr šablony 4, která ve výchozím nastavení není zadán.

*T5*<br/>
Parametr šablony 5, která ve výchozím nastavení není zadán.

*T6*<br/>
Parametr šablony 6, která ve výchozím nastavení není zadán.

*T7*<br/>
Parametr šablony 7, která ve výchozím nastavení není zadán.

*T8*<br/>
Parametr šablony 8, která ve výchozím nastavení není zadán.

*T9*<br/>
Parametr šablony 9, která ve výchozím nastavení není zadán.

## <a name="remarks"></a>Poznámky

Sestavení `InterfaceList` typ podle rekurzivně použití určené šablony parametr argumentů.

**Interfacelisthelper –** šablona používá parametr šablony *T0* k definování první datový člen v `InterfaceList` strukturu a rekurzivně se vztahuje  **Interfacelisthelper –** šablonu pro všechny zbývající parametry šablony. **Interfacelisthelper –** zastaví, když neexistují žádné zbývající parametry šablony.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`TypeT`|Synonymum pro typ interfacelist –.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceListHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)