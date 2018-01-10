---
title: "CBulkRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs: C++
helpviewer_keywords: CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 26ed8c0a3f58ae046ad3e4766b7e009023759be0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cbulkrowset-class"></a>CBulkRowset – třída
Načte a umožňuje pracovat s řádky, které chcete použít u dat v hromadné načtením více popisovačů řádků na základě jednoho volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|[MoveLast –](../../data/oledb/cbulkrowset-movelast.md)|Přejde na poslední řádek.|  
|[MoveNext –](../../data/oledb/cbulkrowset-movenext.md)|Načte na další řádek data.|  
|[MovePrev –](../../data/oledb/cbulkrowset-moveprev.md)|Přesune na předchozí řádek.|  
|[MoveToBookmark –](../../data/oledb/cbulkrowset-movetobookmark.md)|Načte řádek označený záložkou nebo řádek na zadaný posun od tuto záložku.|  
|[Movetoratio –](../../data/oledb/cbulkrowset-movetoratio.md)|Načte řádky od zlomkové pozice v dané sadě řádků.|  
|[Releaserows –](../../data/oledb/cbulkrowset-releaserows.md)|Nastaví na aktuálním řádku (**m_nCurrentRow**) na nule a uvolnit všechny řádky.|  
|[Setrows –](../../data/oledb/cbulkrowset-setrows.md)|Nastaví počet popisovačů řádků, které mají být načteny pomocí jednoho volání.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CBulkRowset` třídy.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)