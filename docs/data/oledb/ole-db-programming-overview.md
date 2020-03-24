---
title: Přehled programování v architektuře OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210065"
---
# <a name="ole-db-programming-overview"></a>Přehled programování v architektuře OLE DB

OLE DB je vysoce výkonná databázová technologie založená na modelu COM. Poskytuje běžný způsob, jak přistupovat k datům nezávisle na formuláři, ve kterém je uložená. V typické obchodní situaci se v podnikových databázích neukládají obrovské množství informací. Tyto informace najdete v systémech souborů (například FAT nebo NTFS), indexované sekvenční soubory, osobní databáze (například přístup), tabulky (například Excel), aplikace plánování projektu (například projekt) a e-maily (například Outlook). OLE DB umožňuje přístup k libovolnému druhu úložiště dat stejným způsobem, pokud úložiště dat má poskytovatele OLE DB.

OLE DB umožňuje vyvíjet aplikace s přístupem k různým zdrojům dat bez ohledu na to, zda jsou systémy DBMS. OLE DB zpřístupňuje univerzální přístup pomocí rozhraní COM, která podporují příslušné funkce DBMS pro daný zdroj dat. Model COM omezuje zbytečné duplikování služeb a maximalizuje interoperabilitu nejen mezi zdroji dat, ale také mezi jinými aplikacemi.

## <a name="benefits-of-com"></a>Výhody modelu COM

V takovém případě se v modelu COM nachází. OLE DB je sada rozhraní COM. Přístupem k datům prostřednictvím jednotné sady rozhraní můžete uspořádat databázi do matice spolupracujících komponent.

Na základě specifikace modelu COM OLE DB definuje rozšiřitelnou a udržovatelnou kolekci rozhraní, kterou součinitel a zapouzdření konzistentních a opakovaně použitelných částí DBMS funkcí. Tato rozhraní definují hranice součástí DBMS, jako jsou kontejnery řádků, procesory dotazů a koordinátory transakcí, které umožňují jednotný transakční přístup k různým zdrojům informací.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Šablony OLE DB](../../data/oledb/ole-db-templates.md)
