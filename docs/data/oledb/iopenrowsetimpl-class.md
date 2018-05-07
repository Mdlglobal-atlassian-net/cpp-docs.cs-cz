---
title: IOpenRowsetImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd34987fcff3bee663a06276e3ded3c44d7ae77c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl – třída
Poskytuje implementaci pro `IOpenRowset` rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `SessionClass`  
 Vlastní třídy odvozené od `IOpenRowsetImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Createrowset –](../../data/oledb/iopenrowsetimpl-createrowset.md)|Vytvoří objekt sady řádků. Není volána přímo uživatelem.|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|Otevře a vrací sadu řádků, který zahrnuje všechny řádky z jedné základní tabulky nebo indexu. (Ne ve ATLDB. H)|  
  
## <a name="remarks"></a>Poznámky  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) rozhraní je povinné pro objekt relace. Otevře a vrací sadu řádků, který zahrnuje všechny řádky z jedné základní tabulky nebo indexu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)