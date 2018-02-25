---
title: "Přístup k datům XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c25e5019ebe930cec1dc5cf7c547e9bc03a3ffa8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="accessing-xml-data"></a>Přístup k datům XML
Existují dvě samostatné metody načítání dat XML ze zdroje dat: jeden používá [CStreamRowset](../../data/oledb/cstreamrowset-class.md) a jiné účely [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Funkce|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|Velikost přenášených dat|Načte data ze všech sloupců a řádků najednou.|Načte data ze všech sloupců, ale pouze jeden řádek v čase. Je nutné přejít řádky pomocí metody, jako `MoveNext`.|  
|Formátování řetězce|SQL Server formátuje řetězec XML a odešle ho k příjemce.|Načte data pro sadu řádků v nativním formátu (počet požadavků, které zprostředkovatel odeslat jako řetězců v kódu Unicode) a potom vytvoří řetězec obsahující data ve formátu XML.|  
|Kontrola nad formátováním|Máte nějaké úroveň kontroly nad formátování řetězec XML nastavením některé vlastnosti specifické pro službu SQL Server 2000.|Nemáte žádnou kontrolu nad formátem generované řetězec XML.|  
  
 Při `CStreamRowset` poskytuje další celkově efektivnější způsob načítání dat ve formátu XML, je podporován pouze serverem SQL Server 2000.  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>Načítání dat XML pomocí CStreamRowset  
 Zadáte [CStreamRowset](../../data/oledb/cstreamrowset-class.md) jako typ sady řádků ve vaší `CCommand` nebo `CTable` deklarace. Můžete ho s vlastními přistupujícího objektu nebo žádný přistupující objekt, například:  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 -nebo-  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 Obvykle při volání `CCommand::Open` (určení, například `CRowset` jako `TRowset` třída), získá `IRowset` ukazatel. `ICommand::Execute` Vrátí `IRowset` ukazatele, který je uložen v `m_spRowset` členem `CRowset` objektu. Metody, jako `MoveFirst`, `MoveNext`, a `GetData` používají tento ukazatel načíst data.  
  
 Naopak při volání `CCommand::Open` (ale zadat `CStreamRowset` jako `TRowset` třída), `ICommand::Execute` vrátí `ISequentialStream` ukazatele, který je uložen v `m_spStream` dat členem [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Pak použijete `Read` metoda pro načtení dat (Unicode string) ve formátu XML. Příklad:  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 provádí formátování XML a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.  
  
 Pro příklad použití `Read` metodu, najdete v části "Přidání podpory XML příjemci" v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
>  Podpora XML pomocí `CStreamRowset` pracuje pouze se SQL Server 2000 a vyžaduje, abyste měli zprostředkovatele OLE DB pro SQL Server 2000 (instalovanou se MDAC).  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Načítání dat XML pomocí CXMLAccessor  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) umožňuje přístup k datům ze zdroje dat jako řetězce data při nemají žádné informace o úložišti dat. schématu. `CXMLAccessor` funguje jako `CDynamicStringAccessorW` s tím rozdílem, že první převede všechna data z úložiště dat jako (s příznakem) data ve formátu XML. Názvy značek XML shodovat s názvy sloupců úložiště dat co nejblíže.  
  
 Použití `CXMLAccessor` stejně jako jakoukoli jinou přístupovou třídu, předání jako parametru šablony k `CCommand` nebo `CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 Použití [GetXMLRowData –](../../data/oledb/cxmlaccessor-getxmlrowdata.md) a načtení dat z jednoho řádku tabulky najednou, přejděte řádky pomocí metody, jako `MoveNext`, například:  
  
```  
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
  
 Můžete použít [GetXMLColumnData –](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) načíst informace o sloupci (datový typ) jako data na řetězec ve formátu XML.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)