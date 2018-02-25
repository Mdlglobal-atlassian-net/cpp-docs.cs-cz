---
title: "CBulkRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 288599a85cc63c59bf8b1bd013e197908adc9cc8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cbulkrowset-class"></a>CBulkRowset – třída
Načte a umožňuje pracovat s řádky, které chcete použít u dat v hromadné načtením více popisovačů řádků na základě jednoho volání.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows –](../../data/oledb/cbulkrowset-addrefrows.md)|Zvýší počet odkazů.|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|Konstruktor|  
|[MoveFirst –](../../data/oledb/cbulkrowset-movefirst.md)|Načte první řádek dat, provádění nové hromadné načtení v případě potřeby.|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|Přejde na poslední řádek.|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|Načte na další řádek data.|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|Přesune na předchozí řádek.|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|Načte řádek označený záložkou nebo řádek na zadaný posun od tuto záložku.|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|Načte řádky od zlomkové pozice v dané sadě řádků.|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|Nastaví na aktuálním řádku (**m_nCurrentRow**) na nule a uvolnit všechny řádky.|  
|[Setrows –](../../data/oledb/cbulkrowset-setrows.md)|Nastaví počet popisovačů řádků, které mají být načteny pomocí jednoho volání.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CBulkRowset` třídy.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)