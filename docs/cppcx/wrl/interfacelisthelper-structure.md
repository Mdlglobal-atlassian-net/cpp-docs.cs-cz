---
title: InterfaceListHelper – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 1a7b4c19bbcdd4161e9078274f18f96a48f9e7d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213847"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper – struktura

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

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
Parametr šablony 0, který je povinný.

*Lince*<br/>
Parametr šablony 1, který je ve výchozím nastavení neurčen.

*T2*<br/>
Parametr šablony 2, který je ve výchozím nastavení neurčen. Třetí parametr šablony.

*Typu*<br/>
Parametr šablony 3, který je ve výchozím nastavení neurčen.

*T4*<br/>
Parametr šablony 4, který je ve výchozím nastavení neurčen.

*Výtisk*<br/>
Parametr šablony 5, který je ve výchozím nastavení neurčen.

*T6*<br/>
Parametr šablony 6, který je ve výchozím nastavení neurčen.

*T7*<br/>
Parametr šablony 7, který je ve výchozím nastavení neurčen.

*T8*<br/>
Parametr šablony 8, který není ve výchozím nastavení zadán.

*T9*<br/>
Parametr šablony 9, který není ve výchozím nastavení specifikován.

## <a name="remarks"></a>Poznámky

Vytvoří `InterfaceList` typ rekurzivním aplikováním zadaných argumentů parametrů šablony.

Šablona **InterfaceListHelper –** používá parametr šablony *T0* k definování prvního datového členu ve `InterfaceList` struktuře a pak rekurzivně aplikuje šablonu **InterfaceListHelper –** na všechny zbývající parametry šablony. **InterfaceListHelper –** se zastaví, když neexistují žádné zbývající parametry šablony.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`TypeT`|Synonymum pro typ InterfaceList –|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceListHelper`

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
