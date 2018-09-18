---
title: Pole Datoví členové stavu v přístupových objektech generovaných průvodcem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e289e2f40326142894894dad1bfe34c801889bb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066853"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Datoví členové stavu pole v přístupových objektech generovaných průvodcem

Při použití průvodce příjemcem ATL OLE DB vytvořte příjemce, Průvodce vytvoří datový člen ve třídě uživatel záznam pro každé pole, které jste zadali v mapě sloupců. Každý datový člen je typu `DWORD` a obsahuje stav hodnota odpovídající jeho odpovídající pole.  
  
Například pro datový člen *m_OwnerID*, průvodce vygeneruje další datové členy stavu pole (*dwOwnerIDStatus*) a jinou pro délky pole (*dwOwnerIDLength*). Také vygeneruje mapu sloupců s COLUMN_ENTRY_LENGTH_STATUS položky.  
  
To je ukázáno v následujícím kódu:  
  
```cpp  
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
>  Pokud změníte název třídy záznamu uživatele nebo napsat vlastní příjemce, datových proměnných musí předcházet proměnné stavu a délky.  
  
Můžete použít hodnoty stavu pro účely ladění. Pokud kód vygenerovaný průvodce příjemcem ATL OLE DB generuje chyby kompilace, jako je například DB_S_ERRORSOCCURRED nebo DB_E_ERRORSOCCURRED, měli nejdřív podívat na aktuální hodnoty datoví členové stavu pole. Ty, které obsahují nenulové hodnoty odpovídají sloupcům problematické.  
  
Hodnoty stavu můžete použít také k nastavení hodnoty NULL pro určité pole. To vám pomůže v případech, ve kterých chcete odlišit hodnotu pole jako hodnotu NULL, spíše než nula. Je jenom na vás rozhodnout, zda je platná hodnota nebo hodnota NULL a rozhodnout, jak vaše aplikace bude pracovat. OLE DB definuje DBSTATUS_S_ISNULL jako správný způsob určení na obecné hodnotě NULL. Pokud příjemce čte data a hodnota je null, pole stavu nastavená na DBSTATUS_S_ISNULL. Pokud uživatel chce nastavit hodnotu NULL, příjemce nastaví stav hodnotu DBSTATUS_S_ISNULL před voláním metody zprostředkovatele.  
  
Dále otevřete Oledb.h a vyhledejte `DBSTATUSENUM`. Pak můžete porovnat číselnou hodnotu nenulovou stavu proti `DBSTATUSENUM` hodnot výčtu. Pokud název výčtu nestačí říct, co je špatně, naleznete v tématu "Stavu" v části "Vytvoření vazby dat hodnoty" [Příručka programátora technologie OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\)). Toto téma obsahuje tabulky stav hodnot použitá při načtení nebo nastavení data. Informace o hodnoty pro délku naleznete v tématu "Délku" ve stejném oddílu.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Načítání délku nebo stav sloupce  

Můžete získat délku sloupce s proměnlivou délkou nebo stav sloupce (Chcete-li zkontrolovat DBSTATUS_S_ISNULL, například):  
  
- Chcete-li získat délku, použijte COLUMN_ENTRY_LENGTH – makro.  
  
- Pokud chcete získat stav, použijte COLUMN_ENTRY_STATUS – makro.  
  
- Obě získáte pomocí COLUMN_ENTRY_LENGTH_STATUS, jak je znázorněno níže.  
  
```cpp  
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
  
Při použití `CDynamicAccessor`, délku a stav je vázána pro vás automaticky. Chcete-li načíst hodnoty délky a stavu, použijte `GetLength` a `GetStatus` členské funkce.  
  
## <a name="see-also"></a>Viz také  

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)