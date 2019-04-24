---
title: Třídy ATL kolekcí a výčtů
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1ab9a160b01ea278d162a515e5121054bf398f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252322"
---
# <a name="atl-collection-and-enumerator-classes"></a>Třídy ATL kolekcí a výčtů

Knihovna ATL poskytuje následující třídy, aby vám pomohly implementovat kolekce a výčty.

|Třída|Popis|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|Implementace rozhraní kolekce|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v kontejneru kompatibilní knihovny C++ Standard)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v poli)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementace objektu enumerátor (používá `IEnumOnSTLImpl`)|
|[Ccomenum –](../atl/reference/ccomenum-class.md)|Implementace objektu enumerátor (používá `CComEnumImpl`)|
|[_Copy](../atl/atl-copy-policy-classes.md)|Třídy zásady kopírování|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Třídy zásady kopírování|
|[CAdapt](../atl/reference/cadapt-class.md)|Třída adaptéru (skryje **operátor &** povolení `CComPtr`, `CComQIPtr`, a `CComBSTR` k uložení do kontejnery standardní knihovny C++)|

## <a name="see-also"></a>Viz také:

[Kolekce a výčty](../atl/atl-collections-and-enumerators.md)
