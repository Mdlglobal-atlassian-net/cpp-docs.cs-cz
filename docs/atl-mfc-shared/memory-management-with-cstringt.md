---
title: Správa paměti pomocí CStringt
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: af042c80b9e3e0de872261f89255a26728b218cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440503"
---
# <a name="memory-management-with-cstringt"></a>Správa paměti pomocí CStringt

Třída [CStringT](../atl-mfc-shared/reference/cstringt-class.md) je třída šablony používaná k manipulaci s řetězci znaků s proměnlivou délkou. Paměť pro uložení těchto řetězců je přidělena a uvolněna prostřednictvím objektu Správce řetězce přidruženého k jednotlivým instancím `CStringT`. MFC a ATL poskytují výchozí instance `CStringT`, nazývané `CString`, `CStringA`a `CStringW`, které pracují s řetězci různých typů znaků. Tyto typy znaků jsou typu TCHAR, **char**a `wchar_t`v uvedeném pořadí. Tyto výchozí řetězcové typy používají správce řetězců, který přiděluje paměť z haldy procesu (v knihovně ATL) nebo z haldy CRT (v MFC). Pro typické aplikace je toto schéma přidělování paměti dostatečné. Nicméně pro kód, který poskytuje náročné použití řetězců (neboli vícevláknového kódu), nemusí výchozí správci paměti fungovat optimálně. Toto téma popisuje, jak potlačit výchozí chování při správě paměti `CStringT`a vytváření přidělování speciálně optimalizovaných pro daný úkol.

- [Implementace vlastního správce řetězců (základní způsob)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Předcházení kolizi haldy](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implementace vlastního správce řetězců (rozšířený způsob)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: Příklad vlastního správce řetězců](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Viz také

[Ukázka CustomString](../overview/visual-cpp-samples.md)
