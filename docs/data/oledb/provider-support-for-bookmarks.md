---
title: Podpora zprostředkovatele pro záložky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ce718e84d50552e01c84e9d0df01c9f169bdf322
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077007"
---
# <a name="provider-support-for-bookmarks"></a>Podpora zprostředkovatele pro záložky

V příkladu v tomto tématu je přidán `IRowsetLocate` rozhraní při `CCustomRowset` třídy. V téměř všech případech je spustit tak, že přidáte na existující objekt modelu COM rozhraní. Potom ji můžete otestovat tak, že přidáte další volání z šablony příjemce. Tento příklad ukazuje, jak:

- Přidání rozhraní ke zprostředkovateli.

- Dynamické určování sloupců se vraťte do příjemce.

- Přidání podpory záložek.

`IRowsetLocate` Rozhraní zdědí `IRowset` rozhraní. Chcete-li přidat `IRowsetLocate` rozhraní, dědí `CCustomRowset` z [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).

Přidávání `IRowsetLocate` rozhraní se trochu liší od většiny rozhraní. Aby bylo možné řádek tabulky vtable nahoru, OLE DB poskytovatele šablony mají parametru šablony pro zpracování odvozené rozhraní. Následující kód ukazuje nový seznam dědičnosti:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Čtvrtý, pátý a šestý parametry jsou přidány všechny. Tento příklad používá výchozí hodnoty pro čtvrtý a pátý parametry, ale uvedete `IRowsetLocateImpl` jako šestého parametru. `IRowsetLocateImpl` je třída šablony technologie OLE DB, který přebírá dva parametry šablony: Toto připojení `IRowsetLocate` rozhraní při `CCustomRowset` třídy. Přidání Většina rozhraní, můžete tento krok přeskočit a přejít k dalšímu. Pouze `IRowsetLocate` a `IRowsetScroll` rozhraní musí být spravovány tímto způsobem.

Bude potřeba zjistit, `CCustomRowset` volat `QueryInterface` pro `IRowsetLocate` rozhraní. Přidejte řádek `COM_INTERFACE_ENTRY(IRowsetLocate)` do mapy. Mapu rozhraní pro `CCustomRowset` by se měla objevit, jak je znázorněno v následujícím kódu:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Je také potřeba připojit mapu do `CRowsetImpl` třídy. Přidat připojení v makru COM_INTERFACE_ENTRY_CHAIN `CRowsetImpl` mapy. Také vytvořit typu nazvanou `RowsetBaseClass` , který obsahuje informace o dědičnosti. Tato definice typedef je volitelný a můžete ignorovat.

A konečně, zpracovat `IColumnsInfo::GetColumnsInfo` volání. Obvykle by k tomu použít makra PROVIDER_COLUMN_ENTRY. Příjemce však může být vhodné použít záložky. Musíte změnit sloupce, které vrátí poskytovateli v závislosti na tom, zda uživatel požádá o záložku.

Pro zpracování `IColumnsInfo::GetColumnsInfo` volání, odstraňte `PROVIDER_COLUMN` si namapují `CTextData` třídy. Makro Provider Column Map definuje funkci `GetColumnInfo`. Je třeba definovat vlastní `GetColumnInfo` funkce. Deklarace funkce by měl vypadat nějak takto:

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

Pak implementovat `GetColumnInfo` funkce v souboru CustomRS.cpp následujícím způsobem:

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

`GetColumnInfo` nejprve zkontroluje, zda vlastnost s názvem `DBPROP_IRowsetLocate` nastavena. OLE DB má vlastnosti pro každý volitelný rozhraní mimo objektu sady řádků. Pokud chcete použít jeden z těchto volitelných rozhraní chce příjemce, nastaví vlastnost na hodnotu true. Zprostředkovatel můžete zkontrolovat tuto vlastnost a zvláštní akci na jejím základě.

Ve vaší implementaci získat vlastnost pomocí ukazatele na objekt příkazu. `pThis` Ukazatel představuje třídu příkazu nebo sady řádků. Vzhledem k tomu, že používáte šablony, musíte předat to jako `void` ukazatel nebo kód nebude zkompilován.

Zadejte statického pole obsahující informace o sloupci. Pokud uživatel nechce sloupec záložky, položky v poli nevyužité. Můžou dynamicky alokovat toto pole, ale je třeba Ujistěte se, že ke zničení správně. Tento příklad definuje a používá makra ADD_COLUMN_ENTRY a ADD_COLUMN_ENTRY_EX vložení informací do pole. Makra můžete přidat do souboru CustomRS.H, jak je znázorněno v následujícím kódu:

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

Chcete-li otestovat kód v příjemci, budete muset provést několik změn do `OnRun` obslužné rutiny. První změnit funkci je, že přidáte kód pro přidání vlastnosti do sady vlastností. Nastaví kód `DBPROP_IRowsetLocate` vlastnost na hodnotu true, proto sděluje zprostředkovatele, který má sloupec záložky. `OnRun` Kód obslužné rutiny by měl vypadat následovně:

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

**Při** smyčka obsahuje kód pro volání `Compare` metodu `IRowsetLocate` rozhraní. Kód, který máte by měly vždy předat, protože při porovnávání přesně stejné záložky. Uložte také jednu záložku v dočasné proměnné tak, aby ho po můžete použít **při** smyčky dokončí volání `MoveToBookmark` funkce v šablonách příjemců. `MoveToBookmark` Volání funkce `GetRowsAt` metoda ve `IRowsetLocate`.

Také musíte aktualizovat záznam uživatele v příjemci. Přidejte záznam do třídy pro zpracování záložky a položky v `COLUMN_MAP`:

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

Když jste aktualizovali kód, byste měli moct sestavit a spustit poskytovatele se `IRowsetLocate` rozhraní.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)