---
title: Irowsetcreatorimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
- SetSite method
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c828708a088c8fe31075a8fe8504f3a1f8c14b4
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337094"
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl – třída
Provádí stejné funkce jako `IObjectWithSite` ale taky umožňuje vlastnosti OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS`.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Třída odvozená z `IRowsetCreator`.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Setsite –](#setsite)|Nastaví lokalitu, která obsahuje objektu sady řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída dědí z [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) a přepíše [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Vytvoří objekt příkazu nebo v jiné relaci zprostředkovatele sady řádků, volá `QueryInterface` na objektu sady řádků hledáte `IObjectWithSite` a volání `SetSite` předání objektu sady řádků `IUnkown` rozhraní jako rozhraní webu.  

## <a name="setsite"></a> IRowsetCreatorImpl::SetSite
Nastaví lokalitu, která obsahuje objektu sady řádků. Další informace najdete v tématu [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pCreator*  
 [in] Ukazatel `IUnknown` ukazatel rozhraní objektu sady řádků Správa lokality.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Kromě toho `IRowsetCreatorImpl::SetSite` umožňuje OLE DB `DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS` vlastnosti. 

## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)