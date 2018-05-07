---
title: Architektura šablon zprostředkovatele OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 099f6e3ce4a84baa156dd26d9bff62be8a4936da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-provider-template-architecture"></a>Architektura šablon zprostředkovatele OLE DB
## <a name="data-sources-and-sessions"></a>Zdroje dat a relace  
 Architektura zprostředkovatele OLE DB obsahuje objekt zdroje dat a jednu nebo více relací. Objekt zdroje dat je počáteční objekt, který musí vytvořit instanci každé zprostředkovatele. Když se aplikace příjemce potřebuje data, společně vytvoří objekt zdroje dat zahájíte zprostředkovatele. Objekt zdroje dat vytvoří objekt relace (pomocí **IDBCreateSession** rozhraní) prostřednictvím který příjemce připojí k objektu zdroje dat. Programátoři rozhraní ODBC můžete představit jako ekvivalentní objekt zdroje dat **HENV** a objekt relace jako ekvivalent **HDBC**.  
  
 ![Architektura zprostředkovatele](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 Šablony technologie OLE DB implementovat objekt zdroje dat, společně s zdrojové soubory generované průvodcem zprostředkovatele OLE DB. Relace je objekt, který odpovídá OLE DB **TSession**.  
  
## <a name="mandatory-and-optional-interfaces"></a>Povinné a nepovinné rozhraní  
 Šablony zprostředkovatele technologie OLE DB poskytují předem definované implementace pro všechny požadované rozhraní. Povinné a nepovinné rozhraní jsou definovány OLE DB pro několik typů objektů:  
  
-   [Zdroj dat](../../data/oledb/data-source-object-interfaces.md)  
  
-   [Relace](../../data/oledb/session-object-interfaces.md)  
  
-   [Sady řádků](../../data/oledb/rowset-object-interfaces.md)  
  
-   [příkaz](../../data/oledb/command-object-interfaces.md)  
  
-   [Transakce](../../data/oledb/transaction-object-interfaces.md)  
  
 Všimněte si, že šablony zprostředkovatele technologie OLE DB neimplementují řádek a úložiště objektů.  
  
 Následující tabulka uvádí a povinné rozhraní pro objekty výše uvedené podle požadavků [OLE DB 2.6 dokumentaci k sadě SDK](https://msdn.microsoft.com/en-us/library/ms722784.aspx).  
  
|Součást|Rozhraní|Komentář|  
|---------------|---------------|-------------|  
|[Zdroj dat](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[povinné] **IDBCreateSession**<br /><br /> [povinné] **IDBInitialize**<br /><br /> [povinné] `IDBProperties`<br /><br /> [povinné] `IPersist`<br /><br /> [Nepovinné] **IConnectionPointContainer**<br /><br /> [Nepovinné] **IDBAsynchStatus**<br /><br /> [Nepovinné] **IDBDataSourceAdmin**<br /><br /> [Nepovinné] **Rozhraní IDBInfo**<br /><br /> [Nepovinné] `IPersistFile`<br /><br /> [Nepovinné] **ISupportErrorInfo**|Připojení z příjemce k poskytovateli. Objekt se používá k určení vlastností připojení, jako je například název zdroje dat, ID a heslo uživatele. Objekt můžete použít také ke správě zdroje dat (vytvářet, aktualizovat, odstranit, tabulky a tak dále).|  
|[Relace](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[povinné] **IGetdataaSource**<br /><br /> [povinné] `IOpenRowset`<br /><br /> [povinné] **ISessionProperties**<br /><br /> [Nepovinné] **IAlterIndex**<br /><br /> [Nepovinné] **IAlterTable**<br /><br /> [Nepovinné] **IBindResource**<br /><br /> [Nepovinné] **ICreateRow**<br /><br /> [Nepovinné] **IDBCreateCommand**<br /><br /> [Nepovinné] **IDBSchemaRowset**<br /><br /> [Nepovinné] **IIndexDefinition**<br /><br /> [Nepovinné] **ISupportErrorInfo**<br /><br /> [Nepovinné] **ITableCreation**<br /><br /> [Nepovinné] **ITableDefinition**<br /><br /> [Nepovinné] **ITableDefinitionWithConstraints**<br /><br /> [Nepovinné] **ITransaction**<br /><br /> [Nepovinné] **ITransactionJoin**<br /><br /> [Nepovinné] **ITransactionLocal**<br /><br /> [Nepovinné] **ITransactionObject**|Objekt relace představuje jednu konverzaci mezi příjemce a zprostředkovatele. To trochu podobné ODBC **HSTMT** v, že může být velký počet souběžných relací aktivní.<br /><br /> Objekt relace je primární odkaz získat funkce technologie OLE DB. Chcete-li získat příkaz, transakce nebo objektu sady řádků, projít objektu session.|  
|[Sada řádků](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[povinné] `IAccessor`<br /><br /> [povinné] `IColumnsInfo`<br /><br /> [povinné] **IConvertType**<br /><br /> [povinné] `IRowset`<br /><br /> [povinné] `IRowsetInfo`<br /><br /> [Nepovinné] **IChapteredRowset**<br /><br /> [Nepovinné] **IColumnsInfo2**<br /><br /> [Nepovinné] **IColumnsRowset**<br /><br /> [Nepovinné] **IConnectionPointContainer**<br /><br /> [Nepovinné] **IDBAsynchStatus**<br /><br /> [Nepovinné] **IGetRow**<br /><br /> [Nepovinné] `IRowsetChange`<br /><br /> [Nepovinné] **IRowsetChapterMember**<br /><br /> [Nepovinné] **IRowsetCurrentIndex**<br /><br /> [Nepovinné] **IRowsetFind**<br /><br /> [Nepovinné] **IRowsetIdentity**<br /><br /> [Nepovinné] **IRowsetIndex**<br /><br /> [Nepovinné] `IRowsetLocate`<br /><br /> [Nepovinné] **IRowsetRefresh**<br /><br /> [Nepovinné] `IRowsetScroll`<br /><br /> [Nepovinné] `IRowsetUpdate`<br /><br /> [Nepovinné] **IRowsetView**<br /><br /> [Nepovinné] **ISupportErrorInfo**<br /><br /> [Nepovinné] **IRowsetBookmark**|Objekt sady řádků představuje data ze zdroje dat. Objekt je zodpovědný za vazby dat a všechny základní operace (aktualizace, načtení, přesun a dalších) na data. Vždy máte objektu sady řádků obsahovat a manipulovat s daty.|  
|[Příkaz](../../data/oledb/command-object-interfaces.md) ([CCommand](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409))|[povinné] `IAccessor`<br /><br /> [povinné] `IColumnsInfo`<br /><br /> [povinné] `ICommand`<br /><br /> [povinné] **ICommandProperties**<br /><br /> [povinné] `ICommandText`<br /><br /> [povinné] **IConvertType**<br /><br /> [Nepovinné] **IColumnsRowset**<br /><br /> [Nepovinné] **ICommandPersist**<br /><br /> [Nepovinné] **ICommandPrepare**<br /><br /> [Nepovinné] `ICommandWithParameters`<br /><br /> [Nepovinné] **ISupportErrorInfo**<br /><br /> [Nepovinné] **ICommandStream**|Objekt příkazu zpracovává operace s daty, jako jsou dotazy. Ho může zpracovávat parametrizované nebo jiné parametry příkazy.<br /><br /> Objekt příkazu je také zodpovědná za zpracování vazby pro parametry a výstupní sloupce. Vazba je struktura, která obsahuje informace o tom, jak mají být načtena sloupec, v sadě řádků. Obsahuje informace, jako je pořadí, datový typ, délku a stav.|  
|[Transakce](../../data/oledb/transaction-object-interfaces.md) (volitelné)|[povinné] **IConnectionPointContainer**<br /><br /> [povinné] **ITransaction**<br /><br /> [Nepovinné] **ISupportErrorInfo**|Transakční objekt definuje atomické jednotky práce na zdroj dat a určuje, jak tyto jednotky vztahují k sobě navzájem. Tento objekt není přímo podporována šablony zprostředkovatele technologie OLE DB (to znamená, že vytvoříte vlastní objekt).|  
  
 Další informace naleznete v následujících tématech:  
  
-   [Mapy vlastností](../../data/oledb/property-maps.md)  
  
-   [Uživatelský záznam](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB – rozhraní](https://msdn.microsoft.com/en-us/library/ms709709.aspx)