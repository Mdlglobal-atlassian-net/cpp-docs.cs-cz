---
title: "Přehled programování v architektuře OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f3d97dda514b3cdb0773adb3d7830e611bca3d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Šablony technologie OLE DB](../../data/oledb/ole-db-templates.md)