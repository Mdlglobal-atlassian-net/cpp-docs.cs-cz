---
title: CDBPropSet – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d75715ed0dc65fbbf5b581bfea48816e5bd00ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096324"
---
# <a name="cdbpropset-class"></a>CDBPropSet – třída
Dědí z **DBPROPSET** struktury a přidá konstruktor, který inicializuje klíčová pole a taky `AddProperty` přístup metodě.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddProperty –](../../data/oledb/cdbpropset-addproperty.md)|Přidá k vlastností nastavenou vlastnost.|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|Konstruktor|  
|[Setguid –](../../data/oledb/cdbpropset-setguid.md)|Nastaví **guidPropertySet** pole z **DBPROPSET** struktury.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../../data/oledb/cdbpropset-operator-equal.md)|Přiřadí obsah jednu vlastnost nastavit na jiný.|  
  
## <a name="remarks"></a>Poznámky  
 OLE DB pomocí poskytovatelů a spotřebitelé **DBPROPSET** struktury předat pole `DBPROP` struktury. Každý `DBPROP` struktura představuje jednu vlastnost, která můžete nastavit.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet – třída](../../data/oledb/cdbpropidset-class.md)   
 [Struktura DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [Struktura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)