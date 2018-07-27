---
title: Iconverttypeimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0dfa073226dc4ddb3cd14b2aae31375a6f6ccc25
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269780"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl – třída
Poskytuje implementaci [IConvertType](https://msdn.microsoft.com/library/ms715926.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IConvertTypeImpl`.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Canconvert –](#canconvert)|Poskytuje informace o dostupnosti převody typů příkazu nebo pro sadu řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je povinná pro příkazy sady řádků a index sady řádků. `IConvertTypeImpl` implementuje rozhraní delegováním převodu objektu poskytnutých OLE DB.  

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert
Poskytuje informace o dostupnosti převody typů příkazu nebo pro sadu řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IConvertType::CanConvert](https://msdn.microsoft.com/library/ms711224.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  
 Používá převodu dat OLE DB v `MSADC.DLL`.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
