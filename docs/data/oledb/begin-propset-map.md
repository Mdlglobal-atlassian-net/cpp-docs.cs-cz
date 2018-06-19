---
title: BEGIN_PROPSET_MAP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b1596797672c0fff92531ff90f67b94bfd6101e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089461"
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