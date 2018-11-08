---
title: Dynamické určování sloupců vrácených příjemci
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 7db319aa153cb281c8fd8b4eec16972f5ac0c2c9
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265175"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamické určování sloupců vrácených příjemci

PROVIDER_COLUMN_ENTRY makra obvykle zpracovávají `IColumnsInfo::GetColumnsInfo` volání. Ale protože příjemce rozhodnout, že chcete používat záložky, zprostředkovatele musí být změnit sloupců vrácených v závislosti na tom, zda uživatel požádá o záložku.

Zpracování `IColumnsInfo::GetColumnsInfo` volání, odstraňte Provider Column Map, který definuje funkci `GetColumnInfo`, z `CCustomWindowsFile` záznam uživatele v *vlastní*RS.h a nahraďte ho vlastní definice `GetColumnInfo` funkce:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CCustomWindowsFile
{
public:
   DWORD dwBookmark;
   static const int iSize = 256;
   TCHAR szCommand[iSize];
   TCHAR szText[iSize];
   TCHAR szCommand2[iSize];
   TCHAR szText2[iSize];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CCustomWindowsFile& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

V dalším kroku implementovat `GetColumnInfo` fungovat v *vlastní*RS.cpp, jak je znázorněno v následujícím kódu.

`GetColumnInfo` kontroluje, první Pokud vlastnost OLE DB `DBPROP_BOOKMARKS` nastavena. Chcete-li získat vlastnost, `GetColumnInfo` používá ukazatel (`pRowset`) k objektu sady řádků. `pThis` Ukazatel představuje třídu, která vytvoří sadu řádků, což je třída ukládat mapy vlastností. `GetColumnInfo` zaokrouhlovat `pThis` ukazatel `RCustomRowset` ukazatele.

Hledat `DBPROP_BOOKMARKS` vlastnost `GetColumnInfo` používá `IRowsetInfo` rozhraní, které lze získat voláním `QueryInterface` na `pRowset` rozhraní. Jako alternativu můžete použít knihovny ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) metoda místo.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CCustomWindowsFile::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero 
   // ordinal entry in the column map with the bookmark information.
   CCustomRowset* pRowset = (CCustomRowset*) pThis;
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;
  
   CDBPropIDSet set(DBPROPSET_ROWSET);
   set.AddPropertyID(DBPROP_BOOKMARKS);
   DBPROPSET* pPropSet = NULL;
   ULONG ulPropSet = 0;
   HRESULT hr;
  
   if (spRowsetProps)
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);
  
   if (pPropSet)
   {
      CComVariant var = pPropSet->rgProperties[0].vValue;
      CoTaskMemFree(pPropSet->rgProperties);
      CoTaskMemFree(pPropSet);
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
      {
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), 
         DBTYPE_BYTES, 0, 0, GUID_NULL, CCustomWindowsFile, dwBookmark, 
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

Tento příklad používá statické pole pro uložení informace o sloupci. Pokud uživatel nechce sloupec záložky, jedna položka v poli se nepoužívá. Pro zpracování informací, vytvoříte dvě pole makra: ADD_COLUMN_ENTRY a ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX přijímá parametr navíc *příznaky*, který je nutný v případě, že určíte sloupec záložky.

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

V `GetColumnInfo` funkce, makro záložky se používá takto:

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Teď můžete zkompilovat a spustit Vylepšený zprostředkovatel služeb. Otestovat poskytovateli, upravte test příjemce, jak je popsáno v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md). Spusťte test příjemce s tímto poskytovatelem a ověřte, že příjemce testů obdrží od zprostředkovatele správné řetězce.

## <a name="see-also"></a>Viz také

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
