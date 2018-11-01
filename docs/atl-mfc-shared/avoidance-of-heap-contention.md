---
title: Předcházení kolizi haldy
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: c28e5ba01cc2bb1e3cae19087a67cf97e6ac415f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536783"
---
# <a name="avoidance-of-heap-contention"></a>Předcházení kolizi haldy

Správci výchozí řetězec, k dispozici v rámci MFC a ATL jsou jednoduché obálky nad globální haldy. Tento globální haldy je zcela bezpečné pro vlákna, což znamená, že více vláken může přidělují a uvolňují paměť z něj současně bez poškození haldy. Jak zajistit bezpečný přístup z více vláken, halda má k serializaci přístup na sebe sama. To je obvykle provedeno pomocí kritický oddíl nebo podobné mechanismus zamykání. Pokaždé, když se dvě vlákna došlo k pokusu o přístup k haldě současně, jedno vlákno zablokována až do dokončení žádosti v jiném vlákně. Pro mnoho aplikací k této situaci dochází zřídka a vlivu na výkon mechanismus zamykání haldy je zanedbatelné. Ale pro aplikace, které často haldy přístup z více vláken může způsobit kolizi haldy zámku aplikace poběží pomaleji, než pokud byly jednovláknový (ještě na počítačích s více procesory).

Aplikace, které používají [CStringT](../atl-mfc-shared/reference/cstringt-class.md) jsou zvlášť náchylné k kolizi haldy protože operace `CStringT` objekty často vyžadují opětovné přidělení vyrovnávací paměti řetězce.

Jedním ze způsobů, abychom omezili kolizi haldy mezi vlákny je, aby každý podproces přidělit řetězce z místního vlákna, privátní haldy. Za předpokladu, kterým je přiřazen výraz řetězce allocator konkrétní vlákno se používají pouze v tomto vlákně, alokátoru nemusí být bezpečné pro vlákna.

## <a name="example"></a>Příklad

Následující příklad ukazuje postup vlákna, která se přidělí vlastní privátní haldy pro řetězce v daném vláknu není bezpečné pro vlákna:

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>Komentáře

Více vláken může být spuštěn pomocí stejný postup vlákno, ale protože každé vlákno má svůj vlastní haldy neexistuje žádné kolize mezi vlákny. Kromě toho skutečnost, že každá halda není bezpečná pro vlákno poskytuje měřitelné zvýšení výkonu i v případě, že je spuštěna pouze jedna kopie vlákna. To je výsledkem haldy pro ochranu před souběžný přístup bez použití propojené operace náročná.

Postup je složitější vlákno může být vhodné ukládat ukazatel na řetězec správce vlákna ve slotu (TLS) místní úložiště vláken. To umožňuje jiné funkce volané procedury vlákno k tomuto správci řetězec vlákna.

## <a name="see-also"></a>Viz také

[Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

