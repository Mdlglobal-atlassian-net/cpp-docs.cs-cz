---
title: "Pole členové stavu pole v přístupových objektech generovaných průvodcem | Microsoft Docs"
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
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 663b26d77138af60d13c3caf24960730a324131e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Datoví členové stavu pole v přístupových objektech generovaných průvodcem
Při použití průvodce příjemcem knihovny ATL technologie OLE DB pro vytvoření příjemce, Průvodce vytvoří datový člen v třídě uživatelského záznamu pro každé pole, které zadáte v mapě sloupců. Každý člen dat je typu `DWORD` a obsahuje hodnotu stavu odpovídající její příslušné pole.  
  
 Například pro člena dat *m_OwnerID*, Průvodce generuje člena další data pro stav pole (*dwOwnerIDStatus*) a další pro délka pole (*dwOwnerIDLength*). Také vytváří mapu sloupců s `COLUMN_ENTRY_LENGTH_STATUS` položky.  
  
 To je ukázáno v následujícím kódu:  
  
```  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
>  Pokud změníte třídu záznamu uživatele nebo napsat vlastní příjemce, data proměnné musí předcházet proměnné stavu a délka.  
  
 Můžete použít hodnoty stavu pro účely ladění. Pokud kód vygenerovaný průvodce příjemcem knihovny ATL technologie OLE DB generuje chyby kompilace, jako **DB_S_ERRORSOCCURRED** nebo **DB_E_ERRORSOCCURRED**, měli byste nejprve podívat na aktuální hodnoty pole stavu datové členy. Ty, které mají nenulové hodnoty odpovídají sloupcům problematické.  
  
 Hodnoty stavu můžete taky nastavit hodnotu NULL pro konkrétního pole. To vám pomůže v případech, ve kterých chcete odlišit hodnotu pole jako NULL spíše než nula. Je na vás rozhodnout, zda je platná hodnota nebo hodnota NULL a rozhodnout, jak vaše aplikace bude pracovat. OLE DB definuje **DBSTATUS_S_ISNULL** jako správný způsob zadání obecné hodnoty NULL. Pokud příjemce čte data a hodnota je null, pole stavu nastavená na **DBSTATUS_S_ISNULL**. Pokud příjemce chce nastavit hodnotu NULL, příjemce nastaví hodnotu stavu na **DBSTATUS_S_ISNULL** před voláním zprostředkovatele.  
  
 Dále otevřete Oledb.h a vyhledejte **DBSTATUSENUM**. Pak můžete porovnat číselnou hodnotu nenulové hodnoty stavu proti **DBSTATUSENUM** hodnot výčtu. Pokud název výčtu není dostatečná říct, co je nesprávný, naleznete v tématu "Status" v části "Vytvoření vazby dat hodnoty" [OLE DB – Příručka pro vývojáře](http://go.microsoft.com/fwlink/p/?linkid=121548). Toto téma obsahuje tabulky použité při získání nebo nastavení data hodnoty stavu. Informace o hodnotami délky naleznete v tématu "Délka" ve stejném oddílu.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Načítání stavu sloupce nebo délka  
 Je možné načíst stav sloupce nebo délka sloupce s proměnnou délkou (zkontrolujte **DBSTATUS_S_ISNULL**, například):  
  
-   Chcete-li získat délku, použijte `COLUMN_ENTRY_LENGTH` makro.  
  
-   Chcete-li získat stav, použijte `COLUMN_ENTRY_STATUS` makro.  
  
-   Chcete-li získat obojí, použijte `COLUMN_ENTRY_LENGTH_STATUS`, jak je uvedeno níže.  
  
```  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
 Při použití `CDynamicAccessor`, délku a stav svázána automaticky. Chcete-li načíst hodnoty délky a stavu, použijte `GetLength` a **GetStatus** členské funkce.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)