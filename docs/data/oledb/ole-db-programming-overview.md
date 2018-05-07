---
title: Přehled programování v architektuře OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fdeca20ad97a09f9d5862fa43be680a2f907405f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-programming-overview"></a>Přehled programování v architektuře OLE DB
OLE DB je databáze založená na modelu COM, vysoce výkonné technologie. Poskytuje společné způsob, jak přistupovat k datům bez ohledu na formulář, ve kterém je uložený. V typické obchodní situaci je uložený obrovské množství informací mimo firemní databáze. Tyto informace naleznete v systémech souborů (například FAT nebo systému souborů NTFS), sekvenční indexované soubory, osobní databáze (například přístup), tabulky (například aplikace Excel), aplikace plánování projektu (například projekt) a e-mailu (jako je například Outlook). OLE DB umožňuje přístup k libovolného typu úložiště dat stejným způsobem, dokud úložiště dat obsahuje zprostředkovatele OLE DB.
  
 OLE DB umožňuje vyvíjet aplikace, které přístup různých datových zdrojů, ať už jsou databázového systému, nebo ne. OLE DB umožňuje univerzální přístup pomocí rozhraní modelu COM, které podporují funkci odpovídající databázového systému pro zdroj dat. COM snižuje zdvojení služeb a maximalizuje vzájemnou funkční spolupráci pouze mezi zdroje dat, ale také mezi jinými aplikacemi.  
  
## <a name="benefits-of-com"></a>Výhody modelu COM  
 Toto je, kde COM odeslán. OLE DB je sada rozhraní modelu COM. Podle přístup k datům prostřednictvím jednotné sady rozhraní, můžete uspořádat do matice spolupracující součástí databáze.  
  
 Podle specifikace modelu COM, technologie OLE DB definuje kolekci rozšiřitelný a udržovatelný rozhraní, které označují a zapouzdřují konzistentní, opakovaně použitelný dílčí funkce databázového systému. Tato rozhraní definují hranice databázového systému komponenty, například řádek kontejnery, procesory dotazu a koordinátory transakcí, které umožňují jednotný transakční přístup k informace o různých zdrojů.  
 
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Šablony OLE DB](../../data/oledb/ole-db-templates.md)