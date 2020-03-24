---
title: Podpora zprostředkovatele pro záložky
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: e8ea949653c7e62f39ab9d1b181c419cf51fe3cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209830"
---
# <a name="provider-support-for-bookmarks"></a>Podpora zprostředkovatele pro záložky

Příklad v tomto tématu přidá rozhraní `IRowsetLocate` do třídy `CCustomRowset`. V téměř všech případech můžete začít přidáním rozhraní do existujícího objektu COM. Pak ji můžete otestovat přidáním dalších volání ze šablon zákazníků. Příklad ukazuje, jak:

- Přidat rozhraní k poskytovateli.

- Umožňuje dynamicky určit sloupce, které se mají vrátit příjemci.

- Přidejte podporu záložky.

Rozhraní `IRowsetLocate` dědí z rozhraní `IRowset`. Chcete-li přidat rozhraní `IRowsetLocate`, převezmou `CCustomRowset` z [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).

Přidání rozhraní `IRowsetLocate` je trochu odlišné od většiny rozhraní. Chcete-li vytvořit tabulku VTABLE, šablony poskytovatele OLE DB mají parametr šablony pro zpracování odvozeného rozhraní. Následující kód ukazuje nový seznam dědičnosti:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Čtvrtý, pátý a šestý parametr jsou přidány. V tomto příkladu se používá výchozí hodnoty pro čtvrtý a pátý parametr, ale jako šestý parametr se zadá `IRowsetLocateImpl`. `IRowsetLocateImpl` je Třída šablon OLE DB, která přebírá dva parametry šablony: tyto `IRowsetLocate` rozhraní připojovat k třídě `CCustomRowset`. Chcete-li přidat většinu rozhraní, můžete tento krok přeskočit a přejít k následujícímu. Tímto způsobem musí být zpracována pouze rozhraní `IRowsetLocate` a `IRowsetScroll`.

Pak je nutné sdělit `CCustomRowset`, aby volal `QueryInterface` rozhraní `IRowsetLocate`. Přidejte `COM_INTERFACE_ENTRY(IRowsetLocate)` čáry k mapě. `CCustomRowset` by se měla zobrazit mapa rozhraní, jak je znázorněno v následujícím kódu:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Také je nutné připojit mapu do `CRowsetImpl` třídy. Přidejte do makra COM_INTERFACE_ENTRY_CHAIN, aby se připojilo k mapě `CRowsetImpl`. Také vytvořte definici TypeDef nazvanou `RowsetBaseClass`, která se skládá z informací o dědičnosti. Tato definice typedef je libovolná a je možné ji ignorovat.

Nakonec zpracujte volání `IColumnsInfo::GetColumnsInfo`. K tomu byste normálně použili PROVIDER_COLUMN_ENTRY makra. Příjemce ale může chtít použít záložky. Je nutné, aby bylo možné změnit sloupce, které zprostředkovatel vrátí, podle toho, zda příjemce požaduje zadání záložky.

Chcete-li zpracovat `IColumnsInfo::GetColumnsInfo` volání, odstraňte mapování PROVIDER_COLUMN ve třídě `CTextData`. PROVIDER_COLUMN_MAP makro definuje funkci `GetColumnInfo`. Definujte vlastní funkci `GetColumnInfo`. Deklarace funkce by měla vypadat takto:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

Potom implementujte funkci `GetColumnInfo` v *vlastním*souboru RS. cpp následujícím způsobem:

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

template <class TInterface>
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   CComQIPtr<TInterface> spProps = pPropsUnk;

   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;

   if (spProps)
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

   // Check the property flag for bookmarks, if it is set, set the
// zero ordinal entry in the column map with the bookmark
// information.

   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);

      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                     sizeof(DWORD), DBTYPE_BYTES,
            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                        DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next set the other columns up.
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)
   ulCols++;
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
     ULONG* pcCols)
{
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),
        pcCols);
}

ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)
{
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);
}
```

`GetColumnInfo` nejprve zkontroluje, zda je nastavena vlastnost s názvem `DBPROP_IRowsetLocate`. OLE DB má vlastnosti pro každé z volitelných rozhraní mimo objekt sady řádků. Pokud chce příjemce použít jedno z těchto volitelných rozhraní, nastaví vlastnost na hodnotu true. Poskytovatel pak může tuto vlastnost ověřit a na základě ní provést zvláštní akci.

V implementaci získáte vlastnost pomocí ukazatele na objekt příkazu. Ukazatel `pThis` představuje sadu řádků nebo třídu příkazů. Vzhledem k tomu, že používáte šablony zde, je nutné předat to jako ukazatel **void** nebo kód nebude zkompilován.

Zadejte statické pole, ve kterém budou uloženy informace o sloupci. Pokud spotřebitel nechce, aby byl sloupec záložky, položka v poli je nevyužitá. Toto pole lze dynamicky přidělit, ale je nutné se ujistit, že je zničena správně. Tento příklad definuje a používá makra ADD_COLUMN_ENTRY a ADD_COLUMN_ENTRY_EX k vložení informací do pole. Makra můžete přidat do *vlastního*RS. Soubor H, jak je znázorněno v následujícím kódu:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = 0; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);

#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \
   _rgColumns[ulCols].dwFlags = flags; \
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \
   _rgColumns[ulCols].wType = (DBTYPE)type; \
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \
   _rgColumns[ulCols].bScale = (BYTE)scale; \
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;
```

Chcete-li otestovat kód ve spotřebiteli, je nutné provést několik změn obslužné rutiny `OnRun`. První Změna funkce je, že přidáte kód pro přidání vlastnosti do sady vlastností. Kód nastaví vlastnost `DBPROP_IRowsetLocate` na hodnotu true, čímž oznámí poskytovateli, že chcete sloupec záložky. Kód obslužné rutiny `OnRun` by měl vypadat takto:

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
          NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   CDBPropSet propset(DBPROPSET_ROWSET);
   propset.AddProperty(DBPROP_IRowsetLocate, true);
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),
          &propset) != S_OK)
      return;

   CBookmark<4> tempBookmark;
   ULONG ulCount=0;
   while (table.MoveNext() == S_OK)
   {

      DBCOMPARE compare;
      if (ulCount == 2)
         tempBookmark = table.bookmark;

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,
                 &compare);
      if (FAILED(hr))
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);
      else
         _ASSERTE(compare == DBCOMPARE_EQ);

      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
      ulCount++;
   }

   table.MoveToBookmark(tempBookmark);
   m_ctlString1.AddString(table.szField1);
   m_ctlString2.AddString(table.szField2);
}
```

Smyčka **while** obsahuje kód pro volání metody `Compare` v rozhraní `IRowsetLocate`. Kód, který by měl být vždy splněn, protože porovnáváte přesně stejné záložky. Také uložte jednu záložku do dočasné proměnné tak, aby ji bylo možné použít po skončení cyklu **while** volání funkce `MoveToBookmark` v šablonách spotřebitele. Funkce `MoveToBookmark` volá metodu `GetRowsAt` v `IRowsetLocate`.

Také je potřeba aktualizovat záznam uživatele v příjemci. Přidejte položku ve třídě pro zpracování záložky a položku v COLUMN_MAP:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

class CProvider
{
// Attributes
public:
   CBookmark<4>    bookmark;  // Add this line
   char   szCommand[16];
   char   szText[256];

   // Binding Maps
BEGIN_ACCESSOR_MAP(CProvider, 1)
   BEGIN_ACCESSOR(0, true)   // auto accessor
      BOOKMARK_ENTRY(bookmark)  // Add this line
      COLUMN_ENTRY(1, szField1)
      COLUMN_ENTRY(2, szField2)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Když jste aktualizovali kód, měli byste být schopni sestavit a spustit poskytovatele s rozhraním `IRowsetLocate`.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)
