---
title: "CRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0774c82715ab2fd85098147ebe1697daf7d2d2fa
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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
|[Compare](../../data/oledb/crowset-compare.md)|Porovná dva záložky pomocí [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Vytvoří novou `CRowset` objektu a (volitelně) přidruží ji s **IRowset** rozhraní zadanou jako parametr.|  
|[Odstranit](../../data/oledb/crowset-delete.md)|Odstraní řádky ze sady řádků pomocí [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Vyhledá další odpovídající řádek po zadanou záložkou.|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|Vrátí přibližnou pozice řádku odpovídající záložky.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Načte data z dané sadě řádků kopii řádku.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Načte data z zadané vyrovnávací paměti.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Načte data naposledy načtených z nebo přeneseno do zdroje dat, ignoruje změny čekající na zpracování.|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|Vrátí stav všech řádků.|  
|[Vložení](../../data/oledb/crowset-insert.md)|Vytvoří a vloží nový řádek pomocí [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|Porovná zadaný řádek s aktuální řádek.|  
|[MoveFirst –](../../data/oledb/crowset-movefirst.md)|Počáteční pozice přemístí další načítání umístění.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Přejde na poslední záznam.|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|Načte data z další po sobě jdoucích řádků nebo zadaný počet pozic za na další řádek.|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|Přesun do předchozího záznamu.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Načte řádek označený záložkou nebo řádek na zadaný posun od tuto záložku.|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|Načte řádky od zlomkové pozice v dané sadě řádků.|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|Volání [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) k uvolnění aktuální popisovač řádku.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Nastaví hodnoty dat v některé sloupce řádku použití [IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[vrácení zpět](../../data/oledb/crowset-undo.md)|Vrátí zpět všechny změny na řádek od posledního načtení nebo [aktualizace](../../data/oledb/crowset-update.md).|  
|[Aktualizace](../../data/oledb/crowset-update.md)|Přenáší všechny neuložené změny provedené na aktuální řádek od posledního načtení nebo aktualizace.|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|Přenáší všechny neuložené změny provedené na všechny řádky od posledního načtení nebo aktualizace.|  
  
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