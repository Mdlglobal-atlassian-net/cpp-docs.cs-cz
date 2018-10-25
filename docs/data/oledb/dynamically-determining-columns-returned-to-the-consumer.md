---
title: Dynamické určování sloupců vrácených příjemci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa1e10c8b6a8f440cc74348ce06c44fdd9d24628
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064287"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamické určování sloupců vrácených příjemci

PROVIDER_COLUMN_ENTRY makra obvykle zpracovávají `IColumnsInfo::GetColumnsInfo` volání. Ale protože příjemce rozhodnout, že chcete používat záložky, zprostředkovatele musí být změnit sloupců vrácených v závislosti na tom, zda uživatel požádá o záložku.

Zpracování `IColumnsInfo::GetColumnsInfo` volání, odstraňte Provider Column Map, který definuje funkci `GetColumnInfo`, z `CAgentMan` uživatel záznam v CustomRS.h a nahraďte ho vlastní definice `GetColumnInfo` funkce:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CAgentMan
{
public:
   DWORD dwBookmark;
   TCHAR szCommand[256];
   TCHAR szText[256];
   TCHAR szCommand2[256];
   TCHAR szText2[256];

   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CAgentMan& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }

};
```

V dalším kroku implementovat `GetColumnInfo` fungovat v CustomRS.cpp, jak je znázorněno v následujícím kódu.

`GetColumnInfo` kontroluje, první Pokud vlastnost OLE DB `DBPROP_BOOKMARKS` nastavena. Chcete-li získat vlastnost, `GetColumnInfo` používá ukazatel (`pRowset`) k objektu sady řádků. `pThis` Ukazatel představuje třídu, která vytvoří sadu řádků, což je třída ukládat mapy vlastností. `GetColumnInfo` zaokrouhlovat `pThis` ukazatel `RCustomRowset` ukazatele.

Hledat `DBPROP_BOOKMARKS` vlastnost `GetColumnInfo` používá `IRowsetInfo` rozhraní, které lze získat voláním `QueryInterface` na `pRowset` rozhraní. Jako alternativu můžete použít knihovny ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) metoda místo.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;

   // Check the property flag for bookmarks; if it is set, set the zero
   // ordinal entry in the column map with the bookmark information.
   CAgentRowset* pRowset = (CAgentRowset*) pThis;
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
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }

   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CAgentMan, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CAgentMan, szText)
   ulCols++;

   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CAgentMan, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,
      GUID_NULL, CAgentMan, szText2)
   ulCols++;

   if (pcCols != NULL)
      *pcCols = ulCols;

   return _rgColumns;
}
```

Tento příklad používá statického pole obsahující informace o sloupci. Pokud uživatel nechce sloupec záložky, jedna položka v poli se nepoužívá. Pro zpracování informací, vytvoříte dvě pole makra: ADD_COLUMN_ENTRY a ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX přijímá parametr navíc `flags`, který je nutný v případě, že určíte sloupec záložky.

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

Teď můžete zkompilovat a spustit Vylepšený zprostředkovatel služeb. Otestovat poskytovateli, upravte test příjemce, jak je popsáno v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md). Spusťte test příjemce s tímto poskytovatelem. Ověřte, že příjemce testů obdrží správné řetězce od poskytovatele po kliknutí **spustit** tlačítko **zkušební příjemce** dialogové okno.

## <a name="see-also"></a>Viz také

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)