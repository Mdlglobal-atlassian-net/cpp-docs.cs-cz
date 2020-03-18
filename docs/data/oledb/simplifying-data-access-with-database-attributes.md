---
title: Zjednodušení přístupu k datům s použitím atributů databáze
ms.date: 10/19/2018
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
ms.openlocfilehash: 5fc30596058271523f64cc9108ee6f39eb5016fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444139"
---
# <a name="simplifying-data-access-with-database-attributes"></a>Zjednodušení přístupu k datům s použitím atributů databáze

Toto téma ukazuje použití atributů databáze pro zjednodušení databázových operací.

Základní způsob, jak získat přístup k informacím z databáze, je vytvořit třídu příkazu (nebo tabulky) a třídu záznamu uživatele pro konkrétní tabulku v databázi. Atributy databáze zjednodušují některé deklarace šablon, které jste předtím museli provádět.

Pro demonstraci použití atributů databáze v následujících částech jsou uvedeny dvě ekvivalentní deklarace třídy tabulky a uživatele: první používá atributy a druhý používá OLE DB šablon. Takový kód deklarace je obvykle umístěn v hlavičkovém souboru s názvem pro objekt tabulky nebo příkazu, například Authors. h.

Porovnáním těchto dvou souborů zjistíte, jak daleko jednodušší je použít atributy. Mezi rozdíly patří:

- Pomocí atributů stačí deklarovat jednu třídu: `CAuthors`, zatímco se šablonami, které je třeba deklarovat dvakrát: `CAuthorsNoAttrAccessor` a `CAuthorsNoAttr`.

- Volání `db_source` v atributu verze je ekvivalentem volání `OpenDataSource()` v deklaraci šablony.

- Volání `db_table` v atributu verze je ekvivalentní následující deklaraci šablony:

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- `db_column` volání v atributu verze jsou ekvivalentní k mapě sloupce (viz `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`) v deklaraci šablony.

Atributy vkládají deklaraci třídy záznamu uživatele za vás. Třída záznamu uživatele je rovna `CAuthorsNoAttrAccessor` v deklaraci šablony. Pokud je třída tabulky `CAuthors`, vložená třída záznamu uživatele je pojmenována `CAuthorsAccessor`a můžete zobrazit pouze její deklaraci v vloženém kódu. Další informace naleznete v části "atributy vložené uživatelem třídy záznamů" v [záznamech uživatelů](../../data/oledb/user-records.md).

V obou atributech i v kódu se šablonami musíte nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty`.

Informace o atributech popsaných v tomto tématu naleznete v tématu [OLE DB atributy příjemce](../../windows/ole-db-consumer-attributes.md).

> [!NOTE]
> Následující příkazy `include` jsou požadovány ke kompilaci níže uvedených příkladů:

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>Deklarace tabulky a přístupových objektů pomocí atributů

Následující kód volá `db_source` a `db_table` ve třídě Table. `db_source` Určuje zdroj dat a připojení, které se má použít. `db_table` vloží příslušný kód šablony k deklaraci třídy tabulky. `db_column` zadat mapu sloupce a vložit deklaraci přistupujícího objektu. Atributy příjemce OLE DB můžete použít v jakémkoli projektu, který podporuje ATL.

Tady je deklarace tabulky a přístupového objektu pomocí atributů:

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
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>Deklarace tabulky a přístupového objektu pomocí šablon

Tady je deklarace tabulky a přístupového objektu pomocí šablon.

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
