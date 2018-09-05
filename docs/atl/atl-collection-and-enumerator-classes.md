---
title: Třídy ATL kolekcí a výčtů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ff5fec4749e08826bab5572149c6cd24a204f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765070"
---
# <a name="atl-collection-and-enumerator-classes"></a>Třídy ATL kolekcí a výčtů

Knihovna ATL poskytuje následující třídy, aby vám pomohly implementovat kolekce a výčty.

|Třída|Popis|
|-----------|-----------------|
|[Icollectiononstlimpl –](../atl/reference/icollectiononstlimpl-class.md)|Implementace rozhraní kolekce|
|[Ienumonstlimpl –](../atl/reference/ienumonstlimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v kontejneru kompatibilní knihovny C++ Standard)|
|[Ccomenumimpl –](../atl/reference/ccomenumimpl-class.md)|Enumerátor implementace rozhraní (předpokládá data uložená v poli)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementace objektu enumerátor (používá `IEnumOnSTLImpl`)|
|[Ccomenum –](../atl/reference/ccomenum-class.md)|Implementace objektu enumerátor (používá `CComEnumImpl`)|
|[_Kopírovat](../atl/atl-copy-policy-classes.md)|Třídy zásady kopírování|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|Třídy zásady kopírování|
|[CAdapt](../atl/reference/cadapt-class.md)|Třída adaptéru (skryje **operátor &** povolení `CComPtr`, `CComQIPtr`, a `CComBSTR` k uložení do kontejnery standardní knihovny C++)|

## <a name="see-also"></a>Viz také

[Kolekce a výčty](../atl/atl-collections-and-enumerators.md)

