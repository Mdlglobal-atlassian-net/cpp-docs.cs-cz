---
title: Reference šablony příjemce technologie OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a4a96ca189c8363d4aaf8df17e00b2419715086
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337950"
---
# <a name="ole-db-consumer-templates-reference"></a>Referenční dokumentace k šablonám příjemců OLE DB
Šablony příjemce technologie OLE DB obsahují následující třídy. Referenční materiál také obsahuje témata o [makra pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="session-classes"></a>Třídy relace  
 [Cdataconnection –](../../data/oledb/cdataconnection-class.md)  
 Spravuje připojení ke zdroji dat. To je užitečné třída pro vytvoření klientů, protože zapouzdřuje nezbytných objektů (zdroj dat a relace) a některé činnosti, které je třeba provést při připojování ke zdroji dat.  
  
 [CDataSource –](../../data/oledb/cdatasource-class.md)  
 Zdrojový objekt OLE DB data, představující připojení prostřednictvím poskytovatele ke zdroji dat odpovídá. Jeden nebo více relace databáze, každý je znázorněn `CSession` objektu, může proběhnout na jedno připojení.  
  
 [CEnumerator –](../../data/oledb/cenumerator-class.md)  
 Objekt enumerátoru OLE DB, který načte informace o sadách řádků o dostupných zdrojích dat odpovídá.  
  
 [Cenumeratoraccessor –](../../data/oledb/cenumeratoraccessor-class.md)  
 Používá `CEnumerator` pro přístup k datům z enumerátor sady řádků. Tato sada řádků se skládá z zdroje dat a enumerátory viditelné z aktuálního výčtu.  
  
 [CSession –](../../data/oledb/csession-class.md)  
 Představuje relaci izolovanou databázi přístup. Jeden nebo více relací může být přidružená k každý `CDataSource` objektu.  
  
## <a name="accessor-classes"></a>Přístupový objekt třídy  
 [CAccessor –](../../data/oledb/caccessor-class.md)  
 Používá se pro záznamy, které jsou staticky svázán se zdrojem dat. Pokud znáte struktury zdroje dat, použijte tuto třídu přistupujícího objektu.  
  
 [CAccessorBase –](../../data/oledb/caccessorbase-class.md)  
 Základní třída pro všechny třídy přistupujícího objektu.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Přístupový objekt, který lze v době běhu na základě informací o sloupec sady řádků. Tato třída slouží k načtení dat, pokud si nejste jisti strukturu datového zdroje.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Přístupový objekt, který slouží k tomu příkaz typy neznámé. Získá informace o parametrech voláním `ICommandWithParameters` rozhraní, pokud zprostředkovatel rozhraní podporuje.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Umožňuje přístup ke zdroji dat, když nemají žádné informace o základní strukturu vaší databáze.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída vyžádá data z úložiště dat jako data řetězce ANSI.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída vyžádá data z úložiště dat jako řetězce data ve formátu UNICODE.  
  
 [CManualAccessor –](../../data/oledb/cmanualaccessor-class.md)  
 Přístupové metody pro zpracování sloupců a parametry příkazu. Pomocí této třídy můžete použít všechny datové typy jako poskytovatel můžete převést typ.  
  
 [Cnoaccessor –](../../data/oledb/cnoaccessor-class.md)  
 Můžete použít jako argument šablony když nechcete, aby třídu tak, aby podporovala parametry nebo výstupní sloupce.  
  
 [CXMLAccessor –](../../data/oledb/cxmlaccessor-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída převede všechna data z úložiště dat jako ve formátu XML (označené) data.  
  
## <a name="rowset-classes"></a>Třídy sady řádků  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Zapouzdřuje sadu řádků a jejich přidružené přístupových objektů.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Používá pro přístup k prvkům sady řádků pomocí syntaxe pole.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Umožňuje načtení a manipulace s řádky hromadně načtením více popisovačů řádků pomocí jediného volání.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Můžete použít jako argument šablony v případě, že příkaz nevrací sadu řádků.  
  
 [cRestrictions –](../../data/oledb/crestrictions-class.md)  
 Slouží k určení omezení pro sad řádků schématu.  
  
 [CRowset –](../../data/oledb/crowset-class.md)  
 Používá k manipulaci s, nastavení a načtení dat sady řádků.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Vrátí `ISequentialStream` objektu místo sady řádků; potom použijete `Read` metodu pro načtení dat ve formátu XML. (SQL Server 2000 nemá formátování, mějte na paměti, že tato funkce funguje se serverem SQL Server 2000 jenom)  
  
 [IRowsetNotifyImpl –](../../data/oledb/irowsetnotifyimpl-class.md)  
 Poskytuje implementaci pro fiktivní `IRowsetNotify`, s prázdné funkce pro `IRowsetNotify` metody `OnFieldChange`, `OnRowChange`, a `OnRowsetChange`.  
  
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Šablony technologie OLE DB poskytují sadu tříd, které odpovídají sad řádků schématu technologie OLE DB.  
  
## <a name="command-classes"></a>Třídy příkazů  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Použít k nastavení a provedení příkazu založeného na parametru OLE DB. Chcete-li otevřít pouze jednoduché sady řádků, použijte `CTable` místo.  
  
 [CMultipleResults –](../../data/oledb/cmultipleresults-class.md)  
 Použít jako argument šablony pro `CCommand` šablony, pokud chcete, aby příkaz pro zpracování více sad výsledků dotazu.  
  
 [Cnoaccessor –](../../data/oledb/cnoaccessor-class.md)  
 Použít jako argument šablony pro šablony třídy, jako například `CCommand` a `CTable`, které přijímají argument třídy přístupový objekt. Použití `CNoAccessor` Pokud nechcete, aby třídu tak, aby podporovala parametry nebo výstupní sloupce.  
  
 [Cnomultipleresults –](../../data/oledb/cnomultipleresults-class.md)  
 Použít jako argument šablony pro `CCommand` šablony, pokud chcete, aby příkaz pro zpracování jedné sady řádků. `CNoMultipleResults` je výchozí hodnota pro argument šablony.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Použít jako argument šablony pro `CCommand` nebo `CTable` Pokud příkazu nebo tabulky nevrací sadu řádků.  
  
 [CTable –](../../data/oledb/ctable-class.md)  
 Používá pro přístup k jednoduché sady řádků bez parametrů.  
  
## <a name="property-classes"></a>Vlastnosti třídy  
 [Cdbpropidset –](../../data/oledb/cdbpropidset-class.md)  
 Sloužící k předávání pole ID vlastnost, pro které chce příjemce informace o vlastnosti. Vlastnosti patří do sady jednu vlastnost.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Slouží k nastavení vlastností ve zprostředkovateli.  
  
## <a name="bookmark-class"></a>Třídy (záložky)  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Používá jako index pro přístup k datům v sadě řádků.  
  
## <a name="error-class"></a>Třída chyb  
 [Cdberrorinfo –](../../data/oledb/cdberrorinfo-class.md)  
 Umožňuje načíst informace o chybě technologie OLE DB.  
  
## <a name="see-also"></a>Viz také  
 [Reference šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)   
 [Šablony OLE DB](../../data/oledb/ole-db-templates.md)