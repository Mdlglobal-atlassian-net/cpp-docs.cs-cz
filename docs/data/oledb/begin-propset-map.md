---
title: BEGIN_PROPSET_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 41a19fb9104c5756693e8120f38d36ec882e43d4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
Značky začátku vlastnosti nastavit položek mapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *– Třída*  
 [v] Je zadána třída, ve kterém tuto vlastnost nastavit. Sada vlastností můžete určit následující objekty OLE DB:  
  
-   [Objekty zdroje dat](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [Objekty relace](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [Příkazy](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>Příklad  
 Tady je ukázkové sady mapování vlastností:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)