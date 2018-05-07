---
title: Šablony příjemce technologie OLE DB (C++) | Microsoft Docs
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
ms.openlocfilehash: 39264ed7485e67377963316730689645c73f185f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-consumer-templates-c"></a>OLE DB – šablony příjemce (C++)
Šablony příjemce technologie OLE DB podporují specifikaci verzi 2.6 OLE DB. (Šablony příjemce technologie OLE DB jsou testovány proti 2.6 technologie OLE DB, ale nepodporují každé rozhraní ve specifikaci.) Šablony příjemce minimalizovat kód, který musí zapsat implementace příjemce technologie OLE DB. Šablony poskytují:  
  
-   Snadný přístup k funkcím technologie OLE DB a snadnou integraci s použitím knihovny ATL a MFC.  
  
-   Jednoduchý vazební model pro parametry databáze a sloupce.  
  
-   Nativní datové typy C/C++ pro programování technologie OLE DB.  
  
 Pokud chcete používat šablony technologie OLE DB, měli seznámit pomocí šablon C++, COM a rozhraní OLE DB. Pokud nejste obeznámeni s OLE DB, přečtěte si téma [referenční příručka programátora technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms718124.aspx).  
  
 Šablony technologie OLE DB podporují existující model objektu OLE DB místo přidání nového objektu modelu. Horní vrstva tříd v šablony příjemce technologie OLE DB paralelní součásti definované ve specifikaci OLE DB. Návrh šablony příjemce technologie OLE DB zahrnuje pokročilé funkce, jako je například několik přístupových objektů pro sadu řádků. Použití šablon a vícenásobná dědičnost díky knihovny malé a flexibilní.  
  
## <a name="how-ole-db-consumers-access-data"></a>Jak příjemce technologie OLE DB přistupovat k datům  
 Příjemci používají několik druhů objektů, které jsou popsány v následujících tématech:  
  
-   [Zdroje dat a relace](../../data/oledb/data-sources-and-sessions.md)  
  
-   [Přístupové objekty a sady řádků](../../data/oledb/accessors-and-rowsets.md)  
  
-   [Příkazy a tabulky](../../data/oledb/commands-and-tables.md)  
  
-   [Uživatelské záznamy](../../data/oledb/user-records.md)  
  
 Předtím, než příjemce nebude nic, nejprve vyberte zprostředkovatele OLE DB, který je vhodný pro typ databáze, kterou potřebujete pro přístup k (například SQL, Oracle, rozhraní ODBC a MSDS). K tomu obvykle použijte čítač (viz [CEnumerator](../../data/oledb/cenumerator-class.md) jak je uvedeno v [zdroje dat a relace](../../data/oledb/data-sources-and-sessions.md)).  
  
 [Objekt zdroje dat](../../data/oledb/data-sources-and-sessions.md) poskytuje informace o připojení, která je požadovaná pro připojení ke zdroji dat, který jste vybrali. Objekt zdroje dat obsahuje také informace o ověřování (například přihlašovací jména a hesla), který se používá k udělení oprávnění k přístupu ke zdroji dat uživatelům. Objekt zdroje dat vytvoří připojení k databázi a poté vytvoří jeden nebo více objektů relace. Každý [objektu session](../../data/oledb/data-sources-and-sessions.md) spravuje vlastní interakce s databází (to znamená, dotazování a načítání dat) a provede tyto transakce nezávisle na jiné existující relací.  
  
 Relace vytvoří objekty sady řádků a příkaz. [Objekt příkazu](../../data/oledb/commands-and-tables.md) umožňuje uživatelům interakci s databází, například pomocí příkazů SQL. [Objektu sady řádků](../../data/oledb/accessors-and-rowsets.md) je sada dat, který můžete přejít a ve kterém můžete [aktualizaci, odstranění a vložení řádků](../../data/oledb/updating-rowsets.md).  
  
 Příjemce technologie OLE DB váže sloupců v tabulkách databáze s lokálními proměnnými; k tomu použije [přistupujícího objektu](../../data/oledb/accessors-and-rowsets.md), který obsahuje mapu způsob uložení dat v rámci příjemce. Mapy obsahuje sadu vazeb mezi sloupců tabulky a místní vyrovnávací paměti (proměnné) v aplikaci příjemce.  
  
 Jednou z důležité koncepce při práci s příjemci je, že deklarujete dvě třídy v příjemce: [třídy příkazu (nebo tabulky)](../../data/oledb/commands-and-tables.md) a [třída uživatelského záznamu](../../data/oledb/user-records.md). Sada řádků přistupujete prostřednictvím třídu příkazu (nebo tabulky), která dědí z třídy sady řádků i třídu přistupujícího objektu. Třída záznamu uživatele obsahuje mapu vazby sady řádků se popisuje výš.  
  
 Další informace naleznete v následujících tématech:  
  
-   [Vytvoření příjemce OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)  
  
-   [Běžné OLE DB scénáře (příklady)](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přístup k datům](../data-access-in-cpp.md)   
 [Dokumentaci k sadě SDK OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [Referenční příručka programátora prostředí OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx)