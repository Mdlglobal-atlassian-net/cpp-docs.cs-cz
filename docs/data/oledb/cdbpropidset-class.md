---
title: "CDBPropIDSet – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 32048b9f8e6ab528a3a31ed475cfb2725c20918e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet – třída
Dědí z **DBPROPIDSET** struktury a přidá konstruktor, který inicializuje klíčová pole a taky [addpropertyid –](../../data/oledb/cdbpropidset-addpropertyid.md) přístup metodě.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Přidá k vlastnost ID nastavenou vlastnost.|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|Konstruktor|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|Nastaví nastavit GUID Identifikátor vlastnosti.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../../data/oledb/cdbpropidset-operator-equal.md)|Přiřadí obsah jednu vlastnost ID nastaven na jiný.|  
  
## <a name="remarks"></a>Poznámky  
 Použití příjemci knihovny OLE DB **DBPROPIDSET** struktury předat pole ID vlastnost, pro které chce příjemce získat informace o vlastnosti. Vlastnosti v jedné identifikuje [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktura patří do sady jednu vlastnost.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)