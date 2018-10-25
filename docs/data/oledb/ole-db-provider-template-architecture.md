---
title: Architektura šablon zprostředkovatele OLE DB | Dokumentace Microsoftu
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
ms.openlocfilehash: 650bf76f5e179e46b334d29d435d64701822013d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054550"
---
# <a name="ole-db-provider-template-architecture"></a>Architektura šablon zprostředkovatele OLE DB

## <a name="data-sources-and-sessions"></a>Zdroje dat a relace

Architektura zprostředkovatele OLE DB zahrnuje objekt zdroje dat a jednu nebo více relací. Objekt zdroje dat je počáteční objekt, který musí vytvořit instanci každý zprostředkovatele. Když aplikace příjemce vyžaduje data, společně vytvoří objekt zdroje dat spustit zprostředkovatele. Objekt zdroje dat vytvoří objekt relace (pomocí `IDBCreateSession` rozhraní) přes který uživatel připojí k objektu zdroje dat. Programátoři rozhraní ODBC si můžete představit jako ekvivalentní objekt zdroje dat `HENV` a objekt relace jako ekvivalentní `HDBC`.

![Architektura zprostředkovatele](../../data/oledb/media/vc4twb1.gif "vc4twb1")

Šablony technologie OLE DB spolu s zdrojové soubory vytvořené průvodcem zprostředkovatele OLE DB, implementovat objekt zdroje dat. Relace je objekt, který odpovídá OLE DB `TSession`.

## <a name="mandatory-and-optional-interfaces"></a>Povinné a nepovinné rozhraní

Šablony zprostředkovatele OLE DB poskytují předpřipravenou implementace pro všechna požadovaná rozhraní. Povinné a volitelné rozhraní jsou definovány OLE DB pro několik typů objektů:

- [Zdroj dat](../../data/oledb/data-source-object-interfaces.md)

- [Relace](../../data/oledb/session-object-interfaces.md)

- [Sady řádků](../../data/oledb/rowset-object-interfaces.md)

- [Příkaz](../../data/oledb/command-object-interfaces.md)

- [Transakce](../../data/oledb/transaction-object-interfaces.md)

Všimněte si, že šablony zprostředkovatele OLE DB neimplementují řádek a úložiště objektů.

Následující tabulka obsahuje seznam povinných a volitelných rozhraní pro objekty uvedené výše, podle [2.6 SDK dokumentace technologie OLE DB](/previous-versions/windows/desktop/ms722784).

|Součást|Rozhraní|Komentář|
|---------------|---------------|-------------|
|[Zdroj dat](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[povinné] `IDBCreateSession`<br /><br /> [povinné] `IDBInitialize`<br /><br /> [povinné] `IDBProperties`<br /><br /> [povinné] `IPersist`<br /><br /> [volitelné] `IConnectionPointContainer`<br /><br /> [volitelné] `IDBAsynchStatus`<br /><br /> [volitelné] `IDBDataSourceAdmin`<br /><br /> [volitelné] `IDBInfo`<br /><br /> [volitelné] `IPersistFile`<br /><br /> [volitelné] `ISupportErrorInfo`|Připojení od uživatele ke zprostředkovateli. Objekt se používá k určení vlastností na připojení, jako je například název zdroje ID, heslo a dat uživatele. Objekt je také možné spravovat zdroje dat (vytvořit, aktualizovat, odstranit, tabulky a tak dále).|
|[Relace](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[povinné] `IGetDataSource`<br /><br /> [povinné] `IOpenRowset`<br /><br /> [povinné] `ISessionProperties`<br /><br /> [volitelné] `IAlterIndex`<br /><br /> [volitelné] `IAlterTable`<br /><br /> [volitelné] `IBindResource`<br /><br /> [volitelné] `ICreateRow`<br /><br /> [volitelné] `IDBCreateCommand`<br /><br /> [volitelné] `IDBSchemaRowset`<br /><br /> [volitelné] `IIndexDefinition`<br /><br /> [volitelné] `ISupportErrorInfo`<br /><br /> [volitelné] `ITableCreation`<br /><br /> [volitelné] `ITableDefinition`<br /><br /> [volitelné] `ITableDefinitionWithConstraints`<br /><br /> [volitelné] `ITransaction`<br /><br /> [volitelné] `ITransactionJoin`<br /><br /> [volitelné] `ITransactionLocal`<br /><br /> [volitelné] `ITransactionObject`|Objekt relace představuje jeden konverzaci mezi spotřebitele a zprostředkovatele. Je poněkud podobný rozhraní ODBC `HSTMT` v tom, že může existovat mnoho souběžných relací aktivní.<br /><br /> Objekt relace je primární propojení, chcete-li získat funkce technologie OLE DB. Pokud chcete získat k příkazu, transakce nebo objektu sady řádků, projít objekt relace.|
|[Sada řádků](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[povinné] `IAccessor`<br /><br /> [povinné] `IColumnsInfo`<br /><br /> [povinné] `IConvertType`<br /><br /> [povinné] `IRowset`<br /><br /> [povinné] `IRowsetInfo`<br /><br /> [volitelné] `IChapteredRowset`<br /><br /> [volitelné] `IColumnsInfo2`<br /><br /> [volitelné] `IColumnsRowset`<br /><br /> [volitelné] `IConnectionPointContainer`<br /><br /> [volitelné] `IDBAsynchStatus`<br /><br /> [volitelné] `IGetRow`<br /><br /> [volitelné] `IRowsetChange`<br /><br /> [volitelné] `IRowsetChapterMember`<br /><br /> [volitelné] `IRowsetCurrentIndex`<br /><br /> [volitelné] `IRowsetFind`<br /><br /> [volitelné] `IRowsetIdentity`<br /><br /> [volitelné] `IRowsetIndex`<br /><br /> [volitelné] `IRowsetLocate`<br /><br /> [volitelné] `IRowsetRefresh`<br /><br /> [volitelné] `IRowsetScroll`<br /><br /> [volitelné] `IRowsetUpdate`<br /><br /> [volitelné] `IRowsetView`<br /><br /> [volitelné] `ISupportErrorInfo`<br /><br /> [volitelné] `IRowsetBookmark`|Objektu sady řádků představuje data z datového zdroje. Objekt je zodpovědná za vazby dat a všechny základní operace (aktualizace, načítání, přesouvání a jiné) s daty. Vždy máte objektu sady řádků obsahovala a manipulaci s daty.|
|[Příkaz](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|[povinné] `IAccessor`<br /><br /> [povinné] `IColumnsInfo`<br /><br /> [povinné] `ICommand`<br /><br /> [povinné] `ICommandProperties`<br /><br /> [povinné] `ICommandText`<br /><br /> [povinné] `IConvertType`<br /><br /> [volitelné] `IColumnsRowset`<br /><br /> [volitelné] `ICommandPersist`<br /><br /> [volitelné] `ICommandPrepare`<br /><br /> [volitelné] `ICommandWithParameters`<br /><br /> [volitelné] `ISupportErrorInfo`<br /><br /> [volitelné] `ICommandStream`|Objekt příkazu zpracovává operace s daty, jako jsou dotazy. Dokáže zpracovat parametrizované nebo parametrizované příkazy.<br /><br /> Objekt příkazu je také zodpovědná za zpracování vazby pro parametry a výstupní sloupce. Vazba je struktura, která obsahuje informace o tom, jak by mělo být získáno sloupec, v sadě řádků. Obsahuje informace, jako je pořadí, datový typ, délku a stav.|
|[Transakce](../../data/oledb/transaction-object-interfaces.md) (volitelné)|[povinné] `IConnectionPointContainer`<br /><br /> [povinné] `ITransaction`<br /><br /> [volitelné] `ISupportErrorInfo`|Objekt transakce definuje atomickou jednotku práce na zdroji dat a určuje, jak tyto jednotky práce vzájemně souvisí. Tento objekt není přímo podporován šablonami zprostředkovatele OLE DB (to znamená, že vytvoříte vlastní objekt).|

Další informace naleznete v následujících tématech:

- [Mapy vlastností](../../data/oledb/property-maps.md)

- [Uživatelský záznam](../../data/oledb/user-record.md)

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Rozhraní OLE DB](/previous-versions/windows/desktop/ms709709)