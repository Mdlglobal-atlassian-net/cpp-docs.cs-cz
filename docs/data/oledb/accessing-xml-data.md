---
title: Přístup k datům XML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d7db1d790ca9caeea6bd9c7853139f59ffa0ab6c
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808716"
---
# <a name="accessing-xml-data"></a>Přístup k datům XML

Existují dvě samostatné metody načítání dat XML ze zdroje dat: jeden používá [CStreamRowset](../../data/oledb/cstreamrowset-class.md) a jiné účely [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Funkce|CStreamRowset –|CXMLAccessor –|  
|-------------------|-------------------|------------------|  
|Přenesené množství dat.|Načte data ze všech sloupců a řádků najednou.|Načte data ze všech sloupců, ale pouze jeden řádek v čase. Je nutné přejít řádky pomocí metod, jako například `MoveNext`.|  
|Formátování řetězce|SQL Server formáty řetězec XML a odešle ji příjemci.|Načte sada řádků data v nativním formátu (počet požadavků, které zprostředkovatel odeslat ho jako řetězce Unicode) a poté sestaví řetězec uchovávající data ve formátu XML.|  
|Kontrola nad formátováním|Máte určitou úroveň kontroly nad formátování řetězce XML tak, že nastavíte některé vlastnosti specifické pro SQL Server 2000.|Nemáte žádnou kontrolu nad formátem vygenerovaný řetězec XML.|  
  
Zatímco `CStreamRowset` poskytuje další celkové efektivní způsob načítání dat ve formátu XML, je podporován pouze serverem SQL Server 2000.  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>Načítání dat XML pomocí CStreamRowset  

Zadáte [CStreamRowset](../../data/oledb/cstreamrowset-class.md) jako typ sady řádků ve vašich `CCommand` nebo `CTable` deklarace. Můžete ji použijete s vlastním přístupový objekt nebo přístupovou metodu, například:  
  
```cpp  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
-nebo-  
  
```cpp  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
Obvykle při volání `CCommand::Open` (například určení `CRowset` jako `TRowset` třídy), získá `IRowset` ukazatel. `ICommand::Execute` Vrátí `IRowset` ukazatel, který je uložený v `m_spRowset` člena `CRowset` objektu. Metody jako `MoveFirst`, `MoveNext`, a `GetData` k načtení dat použít tento ukazatel.  
  
Naopak pokud voláte `CCommand::Open` (ale zadat `CStreamRowset` jako `TRowset` třídy), `ICommand::Execute` vrátí `ISequentialStream` ukazatel, který je uložený v `m_spStream` datový člen třídy [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Pak použijete `Read` metodu pro načtení dat (řetězce Unicode) ve formátu XML. Příklad:  
  
```cpp  
myCmd.m_spStream->Read()  
```  
  
SQL Server 2000 provede formátování, XML a vrátí všechny sloupce a všechny řádky v sadě řádků jako jeden řetězec XML.  
  
Příklad použití `Read` metody, naleznete v části "Přidání podpory XML příjemci" v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
> Podpora XML pomocí `CStreamRowset` pracuje pouze se SQL Server 2000 a vyžaduje, abyste měli zprostředkovatele OLE DB Provider pro SQL Server 2000 (instalovanou se MDAC).  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Načítání dat XML pomocí CXMLAccessor  

[CXMLAccessor –](../../data/oledb/cxmlaccessor-class.md) umožňuje přístup k datům ze zdroje dat jako řetězce dat při nemají žádné informace o schématu datové úložiště. `CXMLAccessor` funguje jako `CDynamicStringAccessorW` s tím rozdílem, že předchozí převede všechna data z úložiště dat jako ve formátu XML (označené) data. Názvy značek XML shodovat s názvy sloupců v úložišti dat co nejpřesněji.  
  
Použití `CXMLAccessor` stejně jako jiná třída přístupový objekt, předejte ji jako parametr šablony `CCommand` nebo `CTable`:  
  
```cpp  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
Použití [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) pro načtení dat z jednoho řádku tabulky v čase a vyhledání řádků pomocí metod, jako `MoveNext`, například:  
  
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
  
Můžete použít [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) načíst informace o sloupci (datový typ) jako řetězec ve formátu XML data.  
  
## <a name="see-also"></a>Viz také  

[Použití přístupových objektů](../../data/oledb/using-accessors.md)