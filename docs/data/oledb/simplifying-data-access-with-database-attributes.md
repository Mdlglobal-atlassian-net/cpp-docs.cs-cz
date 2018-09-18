---
title: Zjednodušení přístupu k datům s použitím atributů databáze | Dokumentace Microsoftu
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
- vc-attr.db_source
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 41d1692fc69ba4ff29e091ca736cae60b10a402a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054074"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Zjednodušení přístupu k datům s použitím atributů databáze

Toto téma popisuje použití atributů databáze pro zjednodušení databázových operací.  
  
Základní způsob pro přístup k informacím z databáze je vytvoření příkazu (nebo tabulky) třídy a třídy uživatelského záznamu pro určitou tabulku v databázi. Atributy databáze Zjednodušte některé deklarace šablon, které jste dřív měli provést.  
  
Pro demonstraci použití atributů databáze, následující části vysvětlují dvě odpovídající tabulky a deklarace třídy uživatelského záznamu: atributy použije první a druhý používá šablony technologie OLE DB. Takové deklarace je obvykle umístěn kód v hlavičkovém souboru s názvem pro objekt příkazu nebo tabulky, například Authors.h.  
  
Porovnáním dvou souborů uvidíte, jak mnohem jednodušší je používat atributy. Mezi rozdíly jsou:  
  
- Pomocí atributů, stačí jenom jednu třídu deklarovat: `CAuthors`, zatímco se šablonami, je třeba deklarovat dvě: `CAuthorsNoAttrAccessor` a `CAuthorsNoAttr`.  
  
- `db_source` Je ekvivalentní volání ve verzi s atributy `OpenDataSource()` volání v deklaraci šablony.  
  
- `db_table` Volání ve verzi s atributy je ekvivalentní deklaraci šablony následující:  
  
    ```  
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
    ```  
  
- `db_column` Volání ve verzi s atributy jsou ekvivalentní a mapováním sloupců (viz `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) v deklaraci šablony.  
  
Atributy vložení deklarace třídy záznamů uživatele. Třída záznamů uživatele je ekvivalentní `CAuthorsNoAttrAccessor` v deklaraci šablony. Pokud vaše třída tabulky `CAuthors`, názvem třídy vloženého uživatelského záznamu `CAuthorsAccessor`, a jeho deklaraci lze zobrazit pouze ve vloženém kódu. Další informace najdete v tématu "Vložené uživatel záznam třídy" v [uživatelských záznamů](../../data/oledb/user-records.md).  
  
Všimněte si, že v současně s atributy a kód bez vizuálního vzhledu, je třeba nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty`.  
  
Informace o atributech popsané v tomto tématu najdete v tématu [atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
## <a name="table-and-accessor-declaration-using-attributes"></a>Tabulky a deklarace přistupujícího objektu pomocí atributů  

Následující kód volá `db_source` a `db_table` na tabulkovou třídu. `db_source` Určuje zdroj dat a připojení, který se má použít. `db_table` vloží příslušný kód šablony pro deklaraci třídy tabulky. `db_column` zadat mapování sloupce a vložit deklarace přistupujícího objektu. Atributy příjemce technologie OLE DB můžete používat v jakémkoli projektu, který podporuje knihovnu ATL.  
  
Tady je tabulka a přístupového objektu deklarace pomocí atributů:  
  
```cpp
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
  
## <a name="table-and-accessor-declaration-using-templates"></a>Tabulky a deklarace přistupujícího objektu pomocí šablon  

Tady je tabulka a přístupového objektu deklarace pomocí šablon.  
  
```cpp
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
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>  
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
