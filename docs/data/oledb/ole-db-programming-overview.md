---
title: Přehled programování v architektuře OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: d19e98d7c5743207dba224214b0d9a0e9f308e81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608917"
---
# <a name="ole-db-programming-overview"></a>Přehled programování v architektuře OLE DB

OLE DB je založená na modelu COM, vysoce výkonné databázové technologie. Poskytuje běžný způsob, jak získat přístup k datům nezávislý formuláře, ve kterém jsou uložená. V typickém podnikovém situaci obrovské množství informací nejsou uložená v podnikových databází. Tyto informace je nalezené v systémech souborů (například FAT nebo systému souborů NTFS), sekvenční indexovat soubory, osobní databází (jako je například přístup), tabulky (například aplikace Excel), aplikace plánování projektu (například projekt) a e-mailu (jako je například Outlook). OLE DB umožňuje získat přístup k jakýkoli druh úložiště dat stejným způsobem jako úložiště dat obsahuje zprostředkovatele OLE DB.

OLE DB umožňuje vyvíjet aplikace s přístupem k různorodých zdrojů, ať už jsou to DBMS, nebo ne. OLE DB umožňuje univerzální přístup pomocí rozhraní modelu COM, které podporují správnou funkčnost DBMS pro daný zdroj dat. COM snižuje zdvojení služeb a maximalizuje vzájemnou funkční spolupráci pouze mezi zdroji dat, ale také mezi jinými aplikacemi.

## <a name="benefits-of-com"></a>Výhody modelu COM

To přichází modelu COM. OLE DB je sada COM rozhraní. Tak přístup k datům prostřednictvím sady jednotné rozhraní, můžete uspořádat do matice spolupracujících součástí databáze.

Podle specifikace modelu COM, OLE DB definuje rozšiřitelné a udržuje kolekci rozhraní, která faktor a zapouzdření konzistentní vzhledem k aplikacím, opakovatelně použitelných částí funkcí DBMS. Tato rozhraní definují hranice DBMS komponent, jako jsou kontejnery řádek, procesory dotazu a koordinátory transakcí, které umožňují jednotné transakční přístup k rozličnými zdroji informací.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Šablony OLE DB](../../data/oledb/ole-db-templates.md)