---
title: "CDBPropSet – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 919a448a33bae03cfb1da9ba8bbed864cc92129d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropset-class"></a>CDBPropSet – třída
Dědí z **DBPROPSET** struktury a přidá konstruktor, který inicializuje klíčová pole a taky `AddProperty` přístup metodě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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