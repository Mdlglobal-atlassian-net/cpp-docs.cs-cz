---
title: Referenční dokumentace k šablonám příjemců OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 52fe3df7e872c257aa8802f84c548ad57d21be27
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447404"
---
# <a name="ole-db-consumer-templates-reference"></a>Referenční dokumentace k šablonám příjemců OLE DB

Šablony příjemce OLE DB obsahují následující třídy. Referenční materiál obsahuje také témata o [makrech pro OLE DB šablon zákazníků](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Třídy relací

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Spravuje připojení ke zdroji dat. Tato třída je užitečnou třídou pro vytváření klientů, protože zapouzdřuje nezbytné objekty (zdroj dat a relace) a některé práce, které je třeba provést při připojování ke zdroji dat.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Odpovídá objektu zdroje dat OLE DB, který představuje připojení prostřednictvím poskytovatele ke zdroji dat. Jedna nebo více relací databáze, z nichž každý představuje `CSession` objekt, mohou probíhat na jednom připojení.

[CEnumerator –](../../data/oledb/cenumerator-class.md)<br/>
Odpovídá objektu výčtu OLE DB, který načítá informace o sadě řádků dostupných zdrojů dat.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Používá se `CEnumerator` pro přístup k datům ze sady řádků výčtu. Tato sada řádků se skládá ze zdrojů dat a enumerátorů viditelných z aktuálního enumerátoru.

[CSession](../../data/oledb/csession-class.md)<br/>
Představuje jednu relaci přístupu k databázi. K jednotlivým objektům `CDataSource` může být přidružena jedna nebo více relací.

## <a name="accessor-classes"></a>Přístupové třídy

[CAccessor –](../../data/oledb/caccessor-class.md)<br/>
Používá se pro záznamy, které jsou staticky svázané se zdrojem dat. Tuto třídu přístupového objektu použijte, když znáte strukturu zdroje dat.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Základní třída pro všechny přístupové třídy.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Přistupující objekt, který lze vytvořit v době běhu, na základě informací o sloupci sady řádků. Tuto třídu použijte k načtení dat, pokud neznáte strukturu zdroje dat.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Přistupující objekt, který lze použít, pokud jsou typy příkazů neznámé. Získává informace o parametrech voláním rozhraní `ICommandWithParameters`, pokud poskytovatel rozhraní podporuje.

[CDynamicStringAccessor –](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti o podkladové struktuře databáze.

[CDynamicStringAccessorA –](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Podobně jako u `CDynamicStringAccessor` s tím rozdílem, že tato třída požaduje data, ke kterým se přistupovalo z úložiště dat jako data řetězce ANSI

[CDynamicStringAccessorW –](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Podobně jako u `CDynamicStringAccessor` s tím rozdílem, že tato třída požaduje data, ke kterým se dostanete z úložiště dat jako data řetězce UNICODE.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Přistupující objekt s metodami pro zpracování parametrů sloupce a příkazu. S touto třídou můžete použít libovolný datový typ, pokud poskytovatel může typ převést.

[CNoAccessor –](../../data/oledb/cnoaccessor-class.md)<br/>
Dá se použít jako argument šablony, když nechcete, aby třída podporovala parametry nebo výstupní sloupce.

[CXMLAccessor –](../../data/oledb/cxmlaccessor-class.md)<br/>
Podobně jako u `CDynamicStringAccessor` s tím rozdílem, že tato třída převede všechna data, která jsou k dispozici z úložiště dat jako data ve formátu XML (tagované).

## <a name="rowset-classes"></a>Třídy sady řádků

[CAccessorRowset –](../../data/oledb/caccessorrowset-class.md)<br/>
Zapouzdřuje sadu řádků a její přidružené přistupující objekty.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Slouží k přístupu k prvkům sady řádků pomocí syntaxe pole.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Slouží k načtení a manipulaci s řádky hromadně díky načtení více popisovačů řádků s jedním voláním.

[CNoRowset –](../../data/oledb/cnorowset-class.md)<br/>
Dá se použít jako argument šablony, pokud příkaz nevrátí sadu řádků.

[CRestrictions –](../../data/oledb/crestrictions-class.md)<br/>
Slouží k zadání omezení pro sady řádků schématu.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Slouží k manipulaci, nastavování a načítání dat sady řádků.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Vrátí objekt `ISequentialStream`, nikoli sadu řádků; pak použijte metodu `Read` k načtení dat ve formátu XML. (SQL Server 2000 toto formátování. Všimněte si, že tato funkce funguje pouze s SQL Server 2000.)

[IRowsetNotifyImpl –](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Poskytuje fiktivní implementaci pro `IRowsetNotify`s prázdnými funkcemi pro `IRowsetNotify` metody `OnFieldChange`, `OnRowChange`a `OnRowsetChange`.

[Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Šablony OLE DB poskytují sadu tříd, které odpovídají OLE DB schémat sady řádků schématu.

## <a name="command-classes"></a>Třídy příkazů

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Slouží k nastavení a spuštění příkazu OLE DB založeného na parametru. Chcete-li otevřít pouze jednoduchou sadu řádků, použijte místo toho `CTable`.

[CMultipleResults –](../../data/oledb/cmultipleresults-class.md)<br/>
Slouží jako argument šablony pro šablonu `CCommand`, pokud chcete, aby příkaz zpracovával více sad výsledků.

[CNoAccessor –](../../data/oledb/cnoaccessor-class.md)<br/>
Slouží jako argument šablony pro třídy šablon, jako je například `CCommand` a `CTable`, které přebírají přistupující argument třídy. Použijte `CNoAccessor`, pokud nechcete, aby třída podporovala parametry nebo výstupní sloupce.

[CNoMultipleResults –](../../data/oledb/cnomultipleresults-class.md)<br/>
Slouží jako argument šablony pro šablonu `CCommand`, pokud chcete, aby příkaz zpracovával jednu sadu řádků. `CNoMultipleResults` je výchozí hodnota argumentu šablony.

[CNoRowset –](../../data/oledb/cnorowset-class.md)<br/>
Slouží jako argument šablony pro `CCommand` nebo `CTable`, pokud příkaz nebo tabulka nevrací sadu řádků.

[CTable](../../data/oledb/ctable-class.md)<br/>
Používá se pro přístup k jednoduché sadě řádků bez parametrů.

## <a name="property-classes"></a>Třídy vlastností

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Slouží k předání pole ID vlastností, pro které chce příjemce získat informace o vlastnostech. Vlastnosti patří do jedné sady vlastností.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Slouží k nastavení vlastností u zprostředkovatele.

## <a name="bookmark-class"></a>Bookmark – třída

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Používá se jako index pro přístup k datům v sadě řádků.

## <a name="error-class"></a>Error – třída

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Slouží k načtení informací o chybě OLE DB.

## <a name="see-also"></a>Viz také

[Referenční dokumentace k šablonám zprostředkovatelů OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Šablony OLE DB](../../data/oledb/ole-db-templates.md)