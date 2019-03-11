---
title: Správa paměti pomocí CStringT
ms.date: 11/04/2016
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: 189d15df17ac28528ebbcc41879871e3426f48fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748629"
---
# <a name="memory-management-with-cstringt"></a>Správa paměti pomocí CStringT

Třída [CStringT](../atl-mfc-shared/reference/cstringt-class.md) je třída šablony používá k manipulaci s řetězci proměnné délky znaků. Paměť k uložení těchto řetězců je přidělená a vydané prostřednictvím objektu string správce spojené s každou instanci `CStringT`. Knihovny MFC a ATL poskytují výchozí instancí `CStringT`, označované jako `CString`, `CStringA`, a `CStringW`, který manipulaci s řetězci znak různých typů. Tyto typy znaků jsou typu TCHAR, **char**, a `wchar_t`v uvedeném pořadí. Tyto typy výchozí řetězec použít Správce řetězec, který se přidělí paměť z haldy procesu (v ATL) nebo haldu CRT (v prostředí MFC). Pro typické aplikace stačí toto schéma přidělování paměti. Ale pro náročné kód pomocí řetězce (nebo vícevláknovém kódu), které správci výchozí paměti nemusí optimální. Toto téma popisuje, jak přepsat výchozí chování při správě paměti z `CStringT`, vytváření alokátorů speciálně optimalizovaná pro daný úkol.

- [Implementace vlastního správce řetězců (základní způsob)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Předcházení kolizi haldy](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementace vlastního správce řetězců (rozšířený způsob)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: Příklad z vlastního správce řetězců](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Viz také:

[Ukázka CustomString](../visual-cpp-samples.md)
