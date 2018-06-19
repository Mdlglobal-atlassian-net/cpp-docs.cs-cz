---
title: ICommandPropertiesImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25be1548bd41f832a007f102c138fc01f8818774
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098998"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl – třída
Představuje implementaci objektu [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
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