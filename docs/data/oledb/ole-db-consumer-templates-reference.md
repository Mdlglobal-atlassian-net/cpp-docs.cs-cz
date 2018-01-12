---
title: "Referenční dokumentace šablony příjemců OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs: C++
helpviewer_keywords: OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 681654f79f0cb3574b0893bb9f726bea78435e74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-consumer-templates-reference"></a>Referenční dokumentace k šablonám příjemců OLE DB
Šablony příjemce technologie OLE DB obsahovat následující třídy. Témata týkající se referenčního materiálu také obsahuje na [makra pro šablony příjemce technologie OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="session-classes"></a>Třídy relace  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 Připojení ke zdroji dat spravuje. Toto je užitečné třída pro vytvoření klienty, protože zapouzdřit nezbytných objektů (zdroj dat a relace) a některé úkoly, které musíte udělat při připojování ke zdroji dat.  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 OLE DB datový objekt, představující prostřednictvím poskytovatele připojení ke zdroji dat odpovídá. Jeden nebo více relace databáze, každý je znázorněn `CSession` objektu, můžete provést na jednoho připojení.  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 Odpovídá objektu enumerátor OLE DB, který načte sada řádků informací o zdrojích dat k dispozici.  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 Používá `CEnumerator` k přístupu k datům z enumerátor sady řádků. Tato sada řádků se skládá z zdroje dat a výčty viditelné z aktuální enumerátor.  
  
 [CSession](../../data/oledb/csession-class.md)  
 Představuje relaci přístup k jedné databáze. Jeden nebo více relací může být přidružené k jednotlivým `CDataSource` objektu.  
  
## <a name="accessor-classes"></a>Třídy přistupujícího objektu  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 Pro záznamy, které jsou staticky vázány na zdroj dat použít. Tato třída přistupující objekt použijte, když víte strukturu datového zdroje.  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 Základní třída pro všechny třídy přistupujícího objektu.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Vytvoření přistupujícího, která se dají vytvořit v době běhu na základě informací sloupec sady řádků. Tato třída slouží k načtení dat, pokud neznáte strukturu datového zdroje.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Přistupující objekt, můžete použít, pokud příkaz typy neznámé. Získá informace o parametru voláním `ICommandWithParameters` rozhraní, pokud zprostředkovatel podporuje rozhraní.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti podkladová struktura databáze.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída vyžaduje data z úložiště dat jako dat řetězců ANSI.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída vyžaduje data z úložiště dat jako data řetězce UNICODE.  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 Přistupující objekt s metody pro zpracování sloupce a parametry příkazu. S touto třídou můžete použít všechny typy dat, dokud zprostředkovatele můžete převést typ.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Můžete použít jako šablonu argumentu když nechcete, aby třídy pro podporu parametry nebo výstupní sloupce.  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 Podobně jako `CDynamicStringAccessor` s tím rozdílem, že tato třída převede všechna data z úložiště dat jako (s příznakem) data ve formátu XML.  
  
## <a name="rowset-classes"></a>Třídy sady řádků  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Zapouzdří sadu řádků a jeho přidružené přistupující objekty.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Umožňuje přístup k elementům sady řádků pomocí syntaxe pole.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Používá k načtení a manipulace s řádky v hromadné načtením více popisovačů řádků na základě jednoho volání.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Můžete použít jako šablonu argumentu Pokud příkaz nevrací sadu řádků.  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 Slouží k zadání omezení pro sady řádků schématu.  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 Použít k manipulaci, nastavit a načíst data sady řádků.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Vrátí `ISequentialStream` objektu místo sadu řádků; pak použijete **čtení** metoda pro načtení dat ve formátu XML. (SQL Server 2000 nemá formátování; tato funkce funguje pro SQL Server 2000 pouze.)  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 Poskytuje implementaci pro fiktivní `IRowsetNotify`, s prázdnou funkce pro `IRowsetNotify` metody `OnFieldChange`, `OnRowChange`, a `OnRowsetChange`.  
  
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Šablony technologie OLE DB poskytují sadu tříd, které odpovídají sady řádků schématu OLE DB.  
  
## <a name="command-classes"></a>Třídy příkazů  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Použít k nastavení a provést příkaz na základě parametrů OLE DB. Chcete-li otevřít jenom jednoduché sady řádků, použijte `CTable` místo.  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 Použít jako argument pro šablony `CCommand` šablony, když chcete, aby příkaz pro zpracování více sad výsledků dotazu.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Použít jako argument šablony pro šablony třídy, jako například `CCommand` a `CTable`, trvají argument Třída přistupujícího objektu. Použití `CNoAccessor` Pokud nechcete, aby třídy pro podporu parametry nebo výstupní sloupce.  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 Použít jako argument pro šablony `CCommand` šablony, když chcete, aby příkaz pro zpracování jedné sady řádků. `CNoMultipleResults`je výchozí hodnota pro argument šablony.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Použít jako argument šablony pro `CCommand` nebo `CTable` Pokud příkaz nebo tabulka, nevrátí sadu řádků.  
  
 [CTable](../../data/oledb/ctable-class.md)  
 Slouží k přístupu jednoduché sady řádků bez parametrů.  
  
## <a name="property-classes"></a>Vlastnost třídy  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 Sloužící k předávání pole ID vlastnost, pro které chce příjemce informace o vlastnosti. Vlastnosti patří do sady jednu vlastnost.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Umožňuje nastavit vlastnosti u zprostředkovatele.  
  
## <a name="bookmark-class"></a>BOOKMARK – třída  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Použít jako index pro přístup k datům v sadě řádků.  
  
## <a name="error-class"></a>Chyba – třída  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 Používá se k načtení informací o chybách OLE DB.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)   
 [Šablony OLE DB](../../data/oledb/ole-db-templates.md)