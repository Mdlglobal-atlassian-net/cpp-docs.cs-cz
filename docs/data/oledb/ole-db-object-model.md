---
title: "OLE DB – Model objektů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b91198d4280a271c775b7be79ecab3da7271fb57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-object-model"></a>OLE DB – model objektů
OLE DB objektový model obsahuje následující objekty nebo součásti. První čtyři objekty nebo součásti (zdrojů dat, relace, příkazy a sady řádků) umožňují připojení ke zdroji dat a jeho zobrazení. Rest, počínaje přístupové objekty, se vztahují k práci s daty, jakmile se zobrazí.  
  
## <a name="data-sources"></a>Zdroje dat  
 Objekty zdroje dat umožňují připojení ke zdroji dat, jako je soubor nebo databázového systému. Objekt zdroje dat vytváří a spravuje připojení a obsahuje informace o oprávnění a ověřování (například přihlašovací jméno a heslo). Objekt zdroje dat můžete vytvořit jeden nebo více relací.  
  
## <a name="sessions"></a>Relace  
 Relace spravuje specifickou interakci se zdrojem dat pro dotazování a načíst data. Každá relace je jediné transakce. Transakce je nedělitelná jednotka práce definována ACID testem. Definici ACID, najdete v části [transakce](#vcconoledbcomponents_transactions).  
  
 Relace provádět důležité úkoly, jako je například otevírání sady řádků a vrací objekt zdroje dat, která ji vytvořila. Relace můžete se taky vrátit metadata nebo informací o zdroji dat (například informace o tabulce).  
  
 Relaci můžete vytvořit jeden nebo více příkazů.  
  
## <a name="commands"></a>Příkazy  
 Příkazy provedou text příkazu, například příkazu jazyka SQL. Pokud příkaz text určuje sadu řádků, jako je například SQL **vyberte** příkaz, příkaz vytvoří sadu řádků.  
  
 Příkaz je jednoduše kontejner pro text příkazu, který obsahuje řetězec (například příkazu jazyka SQL) předaná od příjemce na objekt zdroje dat pro provedení základní úložiště dat poskytovatele. Příkaz text je obvykle SQL **vyberte** – příkaz (v takovém případě, protože SQL **vyberte** určuje sadu řádků, příkaz automaticky vytvoří sadu řádků).  
  
## <a name="rowsets"></a>Sady řádků  
 Sady řádků vystavit data v tabulkovém formátu. Index je zvláštní případ sady řádků. Sady řádků můžete vytvořit z relace nebo příkaz.  
  
### <a name="schema-rowsets"></a>Sady řádků schématu  
 Schémata obsahují metadata (strukturální informace) o databázi. Sady řádků schématu jsou sady řádků, které obsahují informace o schématu. Někteří poskytovatelé OLE DB pro databázového systému podporují objektu sady řádků schématu. Další informace o sad řádků schématu najdete v tématu [získávání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) a [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
### <a name="view-objects"></a>Objekty zobrazení  
 Objekt zobrazení definuje podmnožinu řádků a sloupců ze sady řádků. Obsahuje žádná data. Objekty zobrazení nelze kombinovat data z více sad řádků.  
  
## <a name="accessors"></a>Přístupové objekty  
 Pouze technologie OLE DB používá koncepci přístupových objektů. Přistupující objekt popisuje způsob uložení dat v příjemce. Obsahuje sadu vazby (nazývané mapa sloupce) mezi poli sady řádků (sloupce) a datových členů je deklarovat příjemce.  
  
##  <a name="vcconoledbcomponents_transactions"></a>Transakce  
 Transakce objekty se používají při potvrzování nebo přerušování vnořených transakcí na než nejnižší úroveň. Transakce je nedělitelná jednotka práce definována ACID testem. Zkratka ACID:  
  
-   Nedělitelnost: nelze rozdělit na menší jednotky práce.  
  
-   Concurrency: více než jednu transakci může dojít v čase.  
  
-   Izolace: jednu transakci omezené znalosti o změny provedené jiným uživatelem.  
  
-   Odolnost: transakce provádí trvalé změny.  
  
## <a name="enumerators"></a>Výčty  
 Výčty vyhledat dostupné zdroje dat a další výčty. Příjemci, kteří nejsou přizpůsobení pro určitý zdroj dat používá čítače pro vyhledání zdroje dat použít.  
  
 Kořenový enumerátor, který se dodává v sadě Microsoft Data Access SDK, prochází registru hledá zdroje dat a další výčty. Další výčty překračují registru nebo vyhledávání způsobem specifický pro zprostředkovatele.  
  
## <a name="errors"></a>Chyby  
 Každé rozhraní libovolného objektu OLE DB může způsobit chyby. Chyby obsahují další informace o chybě, včetně objekt volitelné vlastní chyby. Tyto informace jsou obsaženy v HRESULT.  
  
## <a name="notifications"></a>Oznámení  
 Oznámení se používají skupiny spolupracující příjemcům sdílení sady řádků (kde sdílení znamená, že uživatelé se předpokládá, že pracují v rámci stejné transakci). Oznámení povolení spolupracující příjemcům sdílení sady řádků informováni o akcích na sadě řádků provádí svým spolupracovníkům.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)