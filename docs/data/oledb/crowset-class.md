---
title: CRowset – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c9a23c2e879f0d2fe1add1a970c64f6fbcc27b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098573"
---
# <a name="crowset-class"></a>CRowset – třída
Zapouzdří objekt sady řádků OLE DB a několik související rozhraní a poskytuje metody zpracování pro datové sady řádků.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu. Výchozí hodnota je `CAccessorBase`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows –](../../data/oledb/crowset-addrefrows.md)|Zvýší počet odkazů přidružené na aktuálním řádku.|  
|[Zavřete](../../data/oledb/crowset-close.md)|Uvolní řádků a aktuální `IRowset` rozhraní.|  
|[Porovnání](../../data/oledb/crowset-compare.md)|Porovná dva záložky pomocí [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Vytvoří novou `CRowset` objektu a (volitelně) přidruží ji s **IRowset** rozhraní zadanou jako parametr.|  
|[Odstranit](../../data/oledb/crowset-delete.md)|Odstraní řádky ze sady řádků pomocí [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Vyhledá další odpovídající řádek po zadanou záložkou.|  
|[Getapproximateposition –](../../data/oledb/crowset-getapproximateposition.md)|Vrátí přibližnou pozice řádku odpovídající záložky.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Načte data z dané sadě řádků kopii řádku.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Načte data z zadané vyrovnávací paměti.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Načte data naposledy načtených z nebo přeneseno do zdroje dat, ignoruje změny čekající na zpracování.|  
|[GetRowStatus –](../../data/oledb/crowset-getrowstatus.md)|Vrátí stav všech řádků.|  
|[Vložení](../../data/oledb/crowset-insert.md)|Vytvoří a vloží nový řádek pomocí [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[Issamerow –](../../data/oledb/crowset-issamerow.md)|Porovná zadaný řádek s aktuální řádek.|  
|[MoveFirst –](../../data/oledb/crowset-movefirst.md)|Počáteční pozice přemístí další načítání umístění.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Přejde na poslední záznam.|  
|[MoveNext –](../../data/oledb/crowset-movenext.md)|Načte data z další po sobě jdoucích řádků nebo zadaný počet pozic za na další řádek.|  
|[MovePrev –](../../data/oledb/crowset-moveprev.md)|Přesun do předchozího záznamu.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Načte řádek označený záložkou nebo řádek na zadaný posun od tuto záložku.|  
|[Movetoratio –](../../data/oledb/crowset-movetoratio.md)|Načte řádky od zlomkové pozice v dané sadě řádků.|  
|[Releaserows –](../../data/oledb/crowset-releaserows.md)|Volání [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) k uvolnění aktuální popisovač řádku.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Nastaví hodnoty dat v některé sloupce řádku použití [IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[vrácení zpět](../../data/oledb/crowset-undo.md)|Vrátí zpět všechny změny na řádek od posledního načtení nebo [aktualizace](../../data/oledb/crowset-update.md).|  
|[Aktualizace](../../data/oledb/crowset-update.md)|Přenáší všechny neuložené změny provedené na aktuální řádek od posledního načtení nebo aktualizace.|  
|[UpdateAll –](../../data/oledb/crowset-updateall.md)|Přenáší všechny neuložené změny provedené na všechny řádky od posledního načtení nebo aktualizace.|  
  
## <a name="remarks"></a>Poznámky  
 Sada řádků v OLE DB, je objekt, kterou program nastaví a načte data.  
  
 Tato třída není určena k instanci, ale spíše předán jako parametr šablony pro `CTable` nebo `CCommand` (`CRowset` je výchozí nastavení).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Ukázka DBViewer](../../visual-cpp-samples.md)   
 [Ukázka multiRead](../../visual-cpp-samples.md)   
 [Ukázka multiRead atributy](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)