---
title: Igetdatasourceimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0101f0d32ebf5fa5a46d735f64fea03b7e5208da
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082576"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl – třída

Poskytuje implementaci [IGetDataSource](/previous-versions/windows/desktop/ms709721) objektu.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Vaše třída odvozena od `IGetDataSourceImpl`.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|Vrátí ukazatel rozhraní objektu zdroje dat, která byla relace vytvořena.|  
  
## <a name="remarks"></a>Poznámky  

Toto je povinné rozhraní relace k získání ukazatele rozhraní objektu zdroje dat.  

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource

Vrátí ukazatel rozhraní objektu zdroje dat, která byla relace vytvořena.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  

Je užitečné, pokud potřebujete přístup k vlastnostem v objektu zdroje dat.  
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)