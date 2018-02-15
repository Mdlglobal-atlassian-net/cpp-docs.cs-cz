---
title: "Podpora zprostředkovatele pro záložky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e69f0cd9b77f4d492e5011a6c8e653515ea784e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="provider-support-for-bookmarks"></a>Podpora zprostředkovatele pro záložky
Příklad v tomto tématu přidá `IRowsetLocate` rozhraní k `CMyProviderRowset` třídy. Ve většině případů je nejprve přidání rozhraní ke stávající objekt COM. Potom ji můžete otestovat přidáním další volání z šablony příjemce. Příklad ukazuje, jak:  
  
-   Přidání rozhraní ke zprostředkovateli.  
  
-   Dynamické určování sloupců se vrátit k příjemce.  
  
-   Přidáte podporu záložky.  
  
 `IRowsetLocate` Rozhraní dědí z `IRowset` rozhraní. Chcete-li přidat `IRowsetLocate` rozhraní, dědí `CMyProviderRowset` z [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).  
  
 Přidávání `IRowsetLocate` rozhraní je trochu liší od většiny rozhraní. Aby bylo možné řádek virtuálních tabulek si OLE DB šablony zprostředkovatele mít parametr šablony ke zpracování odvozené rozhraní. Následující kód ukazuje nový seznam dědičnosti:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>>  
```  
  
 Čtvrtý, pátý a šestý parametr je přidaný. Tento příklad používá výchozí hodnoty pro čtvrtý a pátý parametr a specifikuje `IRowsetLocateImpl` jako šestého parametru. `IRowsetLocateImpl` je třída šablony OLE DB, která přebírá dva parametry šablony: ty připojí `IRowsetLocate` rozhraní k `CMyProviderRowset` třídy. Při přidávání většiny rozhraní, můžete tento krok přeskočit a přesun na další stránku. Pouze `IRowsetLocate` a `IRowsetScroll` rozhraní je nutné zacházet tímto způsobem.  
  
 Pak budete muset zadat `CMyProviderRowset` volat `QueryInterface` pro `IRowsetLocate` rozhraní. Přidejte řádek `COM_INTERFACE_ENTRY(IRowsetLocate)` na mapě. Mapa rozhraní pro `CMyProviderRowset` by se měla objevit, jak je znázorněno v následujícím kódu:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>> _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Budete také muset připojit mapu do `CRowsetImpl` třídy. Přidejte makro COM_INTERFACE_ENTRY_CHAIN napojit v `CRowsetImpl` mapy. Také vytvořit definici typu nazvanou `RowsetBaseClass` , obsahuje informace o dědičnosti. Tato definice typu libovolný a můžete ignorovat.  
  
 Nakonec zpracování **IColumnsInfo::GetColumnsInfo** volání. Makra PROVIDER_COLUMN_ENTRY obvykle využije k tomu. Příjemce se však může chtít použít záložky. Musíte být schopni změnit sloupce, které zprostředkovatel vrátí v závislosti na tom, jestli příjemce požádá o záložku.  
  
 Zpracování **IColumnsInfo::GetColumnsInfo** volání, odstraňte **PROVIDER_COLUMN** mapování v `CTextData` – třída. Makro Provider Column Map definuje funkci `GetColumnInfo`. Je třeba definovat vlastní `GetColumnInfo` funkce. Deklarace funkce by měl vypadat takto:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 Potom implementovat `GetColumnInfo` fungovat v souboru MyProviderRS.cpp takto:  
  
```cpp
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
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
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
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
  
 `GetColumnInfo` první kontroluje, zda vlastnost s názvem **DBPROP_IRowsetLocate** nastavena. OLE DB má vlastnosti pro každou z volitelných rozhraní mimo objektu sady řádků. Pokud chce použít jednu z těchto volitelných rozhraní příjemce, nastaví vlastnost na hodnotu true. Zprostředkovatel můžete tuto vlastnost zkontrolovat a zvláštní akce založených na.  
  
 V implementaci get pro vlastnost pomocí má ukazatel na objekt příkazu. `pThis` Ukazatel představuje třídy sady řádků nebo příkaz. Vzhledem k tomu, že používáte šablony, je nutné předat to jako `void` nekompiluje se ukazatel myši nebo kód.  
  
 Zadejte statické pole tak, aby obsahovala informace o sloupci. Pokud příjemce nechce sloupec záložky, je ke znehodnocení části položku v poli. Toto pole můžete dynamicky přidělit ale měli byste zajistit, chcete-li zničit správně. Tento příklad definuje a používá makra ADD_COLUMN_ENTRY a ADD_COLUMN_ENTRY_EX vložení informací do pole. Můžete přidat makra souboru MyProviderRS.H, jak je znázorněno v následujícím kódu:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
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
  
 Chcete-li otestovat kód v příjemci, je potřeba udělat pár změny, které `OnRun` obslužné rutiny. První změna funkce je, že přidáte kód pro přidání vlastnosti do sady vlastností. Nastaví kód **DBPROP_IRowsetLocate** vlastnost na hodnotu true, říká zprostředkovatele, který má sloupec záložky. `OnRun` Kód pro obslužnou rutinu by měl vypadat takto:  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
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
  
 Chvíli smyčky obsahuje kód pro volání `Compare` metoda v `IRowsetLocate` rozhraní. Kód, měli byste měli vždycky předávat protože porovnáváte přesně stejné záložky. Uložte také jeden záložku v dočasné proměnné tak, aby ho můžete poté, co while dokončí volání `MoveToBookmark` funkce v šablonách příjemce. `MoveToBookmark` Volání funkce `GetRowsAt` metoda v `IRowsetLocate`.  
  
 Také musíte aktualizovat záznam uživatele v příjemce. Přidejte záznam do třídy pro zpracování záložky a položku v **COLUMN_MAP**:  
  
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
  
 Po aktualizaci kód, by měl být schopni sestavit a spustit zprostředkovatele s `IRowsetLocate` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)