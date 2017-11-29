---
title: "ICommandPropertiesImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs: C++
helpviewer_keywords: ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c00256109998dbef41c1c16d8e66d9bea3b57b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl – třída
Představuje implementaci objektu [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vaše třídy odvozené od  
  
 `PropClass`  
 Třídě vlastnosti.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties –](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Vrátí seznam vlastností ve skupině vlastností sady řádků, která jsou momentálně požadováno pro sadu řádků.|  
|[SetProperties –](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Nastaví vlastnosti ve skupině vlastností sady řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Toto je povinná na příkazy. Poskytuje implementaci statickou funkci definované [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) makro.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)