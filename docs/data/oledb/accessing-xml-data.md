---
title: Přístup k datům XML
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: be4225003211449a98d3fbe5fd686b9b8058a651
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212274"
---
# <a name="accessing-xml-data"></a>Přístup k datům XML

Existují dvě samostatné metody načítání dat XML ze zdroje dat: jeden používá [CStreamRowset](../../data/oledb/cstreamrowset-class.md) a druhý používá [CXMLAccessor –](../../data/oledb/cxmlaccessor-class.md).

|Funkce|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Množství přenesených dat|Načte data ze všech sloupců a řádků najednou.|Načte data ze všech sloupců, ale vždy pouze v jednom řádku. Řádky je nutné procházet pomocí metod, jako je `MoveNext`.|
|Formátování řetězce|SQL Server formátuje řetězec XML a odesílá ho příjemci.|Načte data sady řádků v nativním formátu (požadavky, které poskytovatel odešle jako řetězce Unicode) a poté sestaví řetězec obsahující data ve formátu XML.|
|Řízení formátování|Máte určitou úroveň kontroly nad tím, jak je řetězec XML naformátován, nastavením některých vlastností specifických pro SQL Server 2000.|Nemáte žádnou kontrolu nad formátem generovaného řetězce XML.|

I když `CStreamRowset` poskytuje obecnější způsob načítání dat ve formátu XML, je podporován pouze SQL Server 2000.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Načítání dat XML pomocí CStreamRowset

[Určete jako](../../data/oledb/cstreamrowset-class.md) typ sady řádků v deklaraci `CCommand` nebo `CTable`. Můžete ji použít s vlastním přístupovým objektem nebo bez přístupového objektu, například:

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-nebo-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Obvykle při volání `CCommand::Open` (určení, například `CRowset` jako třída `TRowset`), získá `IRowset` ukazatel. `ICommand::Execute` vrátí ukazatel `IRowset`, který je uložen v `m_spRowset` členu objektu `CRowset`. Metody jako `MoveFirst`, `MoveNext`a `GetData` používají tento ukazatel k načtení dat.

Naopak při volání `CCommand::Open` (ale určení `CStreamRowset` jako třídy `TRowset`) `ICommand::Execute` vrátí ukazatel `ISequentialStream`, který je uložen v datovém členovi `m_spStream` pro [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Pak použijte metodu `Read` k načtení dat (řetězce Unicode) ve formátu XML. Příklad:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 provede formátování XML a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.

Příklad použití metody `Read` naleznete v tématu **Přidání podpory XML příjemci** v tématu [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).

> [!NOTE]
> Podpora XML pomocí `CStreamRowset` pracuje pouze s SQL Server 2000 a vyžaduje, abyste poskytovatele OLE DB pro SQL Server 2000 (nainstalovaný s MDAC).

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Načítání dat XML pomocí CXMLAccessor –

[CXMLAccessor –](../../data/oledb/cxmlaccessor-class.md) umožňuje přístup k datům ze zdroje dat jako řetězcová data, pokud neznáte žádné znalosti schématu úložiště dat. `CXMLAccessor` funguje jako `CDynamicStringAccessorW` s tím rozdílem, že předchozí převádí všechna data, která jsou dostupná z úložiště dat, jako data ve formátu XML (označená). Názvy značek XML odpovídají názvům sloupců úložiště dat co nejvíce.

Použijte `CXMLAccessor` jako jakoukoli jinou třídu přístupového objektu a předejte ji jako parametr šablony pro `CCommand` nebo `CTable`:

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Pomocí [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) můžete načítat data z tabulky po jednotlivých řádcích a procházet řádky pomocí metod, jako je například `MoveNext`.

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

Pomocí [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) můžete načíst informace o sloupci (datový typ) jako data řetězce ve formátu XML.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
