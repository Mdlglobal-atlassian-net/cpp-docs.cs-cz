---
title: Šablony příjemce technologie OLE DB (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b22f97401900a24ae864174872027b18509dfe0c
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082420"
---
# <a name="ole-db-consumer-templates-c"></a>OLE DB – šablony příjemce (C++)

Šablony příjemce technologie OLE DB podporují specifikaci verze 2.6 OLE DB. (Šablony příjemce technologie OLE DB je testován vůči 2.6 technologie OLE DB, ale nepodporují každé rozhraní ve specifikaci). Šablony příjemce minimalizovat množství kódu, který musíte napsat k implementaci příjemce technologie OLE DB. Šablony poskytují:  
  
- Snadný přístup k funkcím technologie OLE DB a snadnou integraci s použitím knihovny ATL a MFC.  
  
- Model jednoduché vazby pro parametry a sloupce databáze.  
  
- Nativní datových typů jazyka C/C++ pro programování technologie OLE DB.  
  
Použití šablony technologie OLE DB, byste měli vědět, jak šablon jazyka C++, COM a rozhraní OLE DB. Pokud nejste obeznámeni s OLE DB, přečtěte si téma [OLE DB referenční informace pro programátory](/previous-versions/windows/desktop/ms718124).  
  
Šablony technologie OLE DB podporovat existující objektový model OLE DB místo přidání nového objektu modelu. Horní vrstva tříd v šablony příjemce technologie OLE DB paralelní součásti definovaných ve specifikaci OLE DB. Návrh šablony příjemce technologie OLE DB zahrnuje pokročilé funkce, jako je několik přístupových objektů pro sadu řádků. Použití šablon a vícenásobná dědičnost činí knihovnu malé a flexibilní.  
  
## <a name="how-ole-db-consumers-access-data"></a>Jak příjemce technologie OLE DB přistupovat k datům  

Zákazníci používají několik typů objektů, které jsou popsány v následujících tématech:  
  
- [Zdroje dat a relace](../../data/oledb/data-sources-and-sessions.md)  
  
- [Přístupové objekty a sady řádků](../../data/oledb/accessors-and-rowsets.md)  
  
- [Příkazy a tabulky](../../data/oledb/commands-and-tables.md)  
  
- [Uživatelské záznamy](../../data/oledb/user-records.md)  
  
Předtím, než uživatel provede cokoli, nejprve vyberte zprostředkovatele OLE DB, která je vhodná pro typ databáze, kterou je potřeba přístup (například SQL, Oracle, ODBC a MSDS). K tomuto účelu použijete obvykle enumerátor (viz [CEnumerator](../../data/oledb/cenumerator-class.md) jak je uvedeno v [zdroje dat a relace](../../data/oledb/data-sources-and-sessions.md)).  
  
[Objektu zdroje dat](../../data/oledb/data-sources-and-sessions.md) poskytuje informace o připojení, která je potřebná pro připojení ke zdroji dat, který jste vybrali. Objekt zdroje dat obsahuje také informace o ověřování (například přihlašovací jména a hesla), který se používá k udělení oprávnění pro přístup ke zdroji dat uživatelům. Objekt zdroje dat vytvoří připojení k databázi a potom vytvoří jeden nebo více relací objektů. Každý [objektu relace](../../data/oledb/data-sources-and-sessions.md) spravuje svou vlastní interakce s databází (to znamená, dotazování a načítání dat) a provádí tyto transakce nezávisle na jiných existující relace.  
  
Relace vytváří objekty příkazu a sady řádků. [Objekt příkazu](../../data/oledb/commands-and-tables.md) umožňuje uživatelům interakci s databází, například pomocí příkazů SQL. [Objektu sady řádků](../../data/oledb/accessors-and-rowsets.md) je sada dat, který můžete procházet a ve kterém můžete [aktualizovat, odstranit a vložit řádky](../../data/oledb/updating-rowsets.md).  
  
Příjemce technologie OLE DB váže sloupců v tabulkách databáze s lokálními proměnnými; k tomuto účelu se používá [přistupující objekt](../../data/oledb/accessors-and-rowsets.md), která obsahuje mapu způsob uložení dat v rámci příjemce. Na mapě se skládá z sadu vazeb mezi sloupce tabulky a místní vyrovnávací paměti (proměnné) v aplikaci příjemce.  
  
Jeden důležitý koncept při práci se zákazníky, je deklarovat dvě třídy do příjemce: [příkazu (nebo tabulky) třídy](../../data/oledb/commands-and-tables.md) a [třídy uživatelského záznamu](../../data/oledb/user-records.md). Máte přístup k dané sadě řádků prostřednictvím příkazu (nebo tabulky) třídy, která dědí z třídy sady řádků i třídu přistupujícího objektu. Třída záznamu uživatele obsahuje mapu vazby sady řádků popsaných výše.  
  
Další informace naleznete v následujících tématech:  
  
- [Vytvoření příjemce OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)  
  
- [Běžné technologie OLE DB scénáře (příklady)](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## <a name="see-also"></a>Viz také  

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přístup k datům](../data-access-in-cpp.md)<br/>
[Dokumentace k sadě SDK technologie OLE DB](/previous-versions/windows/desktop/ms722784)   
[Referenční informace pro OLE DB programátory](/previous-versions/windows/desktop/ms713643)