---
title: "Zjednodušení přístupu k datům s použitím atributů databáze | Microsoft Docs"
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
- vc-attr.db_source
dev_langs: C++
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca857a5d304d137009161618bddeed49886233b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="simplifying-data-access-with-database-attributes"></a>Zjednodušení přístupu k datům s použitím atributů databáze
Toto téma ukazuje použití atributů databáze ke zjednodušení databázových operací.  
  
 Základní způsob pro přístup k informacím z databáze je vytvoření třídy příkazu (nebo tabulky) a třídu uživatelského záznamu pro konkrétní tabulku v databázi. Atributy databáze zjednodušují některé deklarace šablon, které jste dříve museli provést.  
  
 K předvedení použití atributů databáze, následující části vysvětlují dvě odpovídající tabulky a deklarace třídy uživatelského záznamu: atributy používá první a druhý šablony technologie OLE DB. Taková deklarace kódu je obvykle umístěn v záhlaví souboru s názvem tabulky nebo příkaz objektu, například Authors.h.  
  
 Srovnáním dva soubory se zobrazí, kolik jednodušší je použít atributy. Mezi rozdíly patří:  
  
-   Pomocí atributů, je třeba pouze jednu třídu deklarovat: `CAuthors`, zatímco se šablonami musíte deklarovat dvě: `CAuthorsNoAttrAccessor` a `CAuthorsNoAttr`.  
  
-   `db_source` Je ekvivalentní volání ve verzi s atributy `OpenDataSource()` volání v deklaraci šablony.  
  
-   **Db_table** volání ve verzi s atributy je ekvivalentní následující deklaraci šablony:  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
    ```  
  
-   **Db_column** volání ve verzi s atributy jsou ekvivalentní mapu sloupce (viz `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) v deklaraci šablony.  
  
 Atributy vložit deklaraci třídy záznamu uživatele. Třídy uživatelského záznamu je ekvivalentní `CAuthorsNoAttrAccessor` v deklaraci šablony. Pokud vaše třída tabulky `CAuthors`, třída záznamu vloženého uživatele se nazývá `CAuthorsAccessor`, a jeho deklaraci lze zobrazit pouze ve vloženém kódu. Další informace najdete v tématu "Vložené uživatelské atributy třídy záznamu" v [uživatelských záznamů](../../data/oledb/user-records.md).  
  
 Všimněte si, že v s atributy i kódu s použitím šablon, je třeba nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty`.  
  
 Informace o atributech uvedené v tomto tématu najdete v tématu [atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
## <a name="table-and-accessor-declaration-using-attributes"></a>Deklarace tabulky a přistupujícího objektu pomocí atributů  
 Následující kód volání `db_source` a **db_table** v třídě tabulky. `db_source`Určuje zdroj dat a připojení, který se má použít. **db_table** vloží kód příslušné šablony k deklaraci třídy tabulky. **db_column** zadejte mapu sloupce a vloží deklaraci přistupujícího objektu. Atributy příjemce technologie OLE DB můžete použít v jakékoli projekt, který podporuje knihovnu ATL.  
  
 Tady je tabulka a přistupujícího objektu deklaraci pomocí atributů:  
  
```  
//////////////////////////////////////////////////////////////////////  
// Table and accessor declaration using attributes  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// Table class declaration  
// (Note that you must provide your own connection string for db_source.)  
[  
   db_source(L"your connection string"),  
   db_table("Authors")  
]  
class CAuthors  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
};  
```  
  
## <a name="table-and-accessor-declaration-using-templates"></a>Deklarace tabulky a přistupujícího objektu pomocí šablony  
 Tady je tabulka a přistupujícího objektu deklaraci pomocí šablon.  
  
```  
//////////////////////////////////////////////////////////////////////  
// Table and user record class declaration using templates  
// authors.h  
//////////////////////////////////////////////////////////////////////  
  
// User record class declaration  
class CAuthorsNoAttrAccessor  
{  
public:  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
   LONG m_AuID;  
   TCHAR m_Author[51];  
   SHORT m_YearBorn;  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
   }  
   HRESULT OpenDataSource()  
   {  
      CDataSource _db;  
      HRESULT hr;  
      hr = _db.OpenFromInitializationString(L"your connection string");  
      if (FAILED(hr))  
      {  
#ifdef _DEBUG  
         AtlTraceErrorRecords(hr);  
#endif  
         return hr;  
      }  
      return m_session.Open(_db);  
   }  
   void CloseDataSource()  
   {  
      m_session.Close();  
   }  
   operator const CSession&()  
   {  
      return m_session;  
   }  
   CSession m_session;  
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)  
   END_COLUMN_MAP()  
};  
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor> >  
{  
public:  
   HRESULT OpenAll()  
   {  
      HRESULT hr;  
      hr = OpenDataSource();  
      if (FAILED(hr))  
         return hr;  
      __if_exists(GetRowsetProperties)  
      {  
         CDBPropSet propset(DBPROPSET_ROWSET);  
         __if_exists(HasBookmark)  
         {  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
         }  
         GetRowsetProperties(&propset);  
         return OpenRowset(&propset);  
      }  
      __if_not_exists(GetRowsetProperties)  
      {  
         __if_exists(HasBookmark)  
         {  
            CDBPropSet propset(DBPROPSET_ROWSET);  
            propset.AddProperty(DBPROP_IRowsetLocate, true);  
            return OpenRowset(&propset);  
         }  
      }  
      return OpenRowset();  
   }  
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
   {  
      HRESULT hr = Open(m_session, "Authors", pPropSet);  
#ifdef _DEBUG  
      if(FAILED(hr))  
         AtlTraceErrorRecords(hr);  
#endif  
      return hr;  
   }  
   void CloseAll()  
   {  
      Close();  
      CloseDataSource();  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md)   
 [Atributy návody](http://msdn.microsoft.com/en-us/73df1d5d-261a-4521-98fb-06dcbf5ec0d0)