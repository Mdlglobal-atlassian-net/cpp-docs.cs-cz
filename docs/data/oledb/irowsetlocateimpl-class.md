---
title: "IRowsetLocateImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27af767c9104159d6c398db226a5a45a36e01e2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl – třída
Implementuje OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) rozhraní, která načte libovolný řádky ze sady řádků.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
       T,   
       RowsetInterface,   
       RowClass,   
       MapClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z `IRowsetLocateImpl`.  
  
 `RowsetInterface`  
 Třída odvozená z `IRowsetImpl`.  
  
 `RowClass`  
 Jednotky úložiště pro **HROW**.  
  
 `MapClass`  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  
  
 `BookmarkKeyType`  
 Typ záložku, jako typ LONG nebo řetězec. Obyčejnou záložky musí mít délku aspoň dva bajty. (Jednobajtové délka je vyhrazený pro OLE DB [standardní záložky](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**, **DBBMK_LAST**, a **DBBMK_INVALID**.)  
  
 `BookmarkType`  
 Mapování mechanismus pro údržbu záložku data relace.  
  
 `BookmarkMapClass`  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat záložkou.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|Porovná dvě záložky.|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|Načte řádky počínaje řádkem určeného posun vůči záložky.|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|Načte řádky, které odpovídají zadané záložky.|  
|[Hash](../../data/oledb/irowsetlocateimpl-hash.md)|Vrátí hodnotu hash hodnoty pro zadaný záložky.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|Pole záložky.|  
  
## <a name="remarks"></a>Poznámky  
 `IRowsetLocateImpl` představuje implementaci šablony technologie OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) rozhraní. `IRowsetLocate` slouží k načtení libovolné řádky ze sady řádků. Sada řádků, který neimplementuje toto rozhraní je `sequential` sady řádků. Když `IRowsetLocate` je k dispozici pro sadu řádků, sloupců 0 je záložku řádků; čtení v tomto sloupci se získat hodnotu záložku, která lze změnit umístění na stejný řádek.  
  
 `IRowsetLocateImpl` slouží k implementaci podpora záložek ve zprostředkovatelích. Záložky jsou zástupné symboly (indexů pro sadu řádků) umožňující příjemce rychle vrátit na řádek, což vysokorychlostní přístup k datům. Určuje zprostředkovatele, co záložky lze jedinečně identifikovat řádek. Pomocí `IRowsetLocateImpl` metod, můžete porovnat záložky, načtení řádků pomocí posun načtení řádků záložkou a návratové hodnoty hash pro záložky.  
  
 Pro podporu technologie OLE DB záložky v sadě řádků, zkontrolujte řádků z této třídy dědit.  
  
 Informace o implementaci podpora záložek naleznete v tématu [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md) v *Visual C++ – příručka pro vývojáře* a [záložky](https://msdn.microsoft.com/en-us/library/ms709728.aspx) v *Referenční příručka programátora prostředí OLE DB* v platformě SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md)   
 [Záložky](https://msdn.microsoft.com/en-us/library/ms709728.aspx)