---
title: Isessionpropertiesimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3759b67ef5d9ee9832649b3b0d516dbfb04440b
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322017"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl – třída
Poskytuje implementaci [ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `ISessionPropertiesImpl`.  
  
 *PropClass*  
 Uživatelská vlastnost třídy, která výchozí hodnota je *T*.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Vrátí seznam vlastností ve skupině vlastností relace, které jsou aktuálně nastavená na relaci.|  
|[SetProperties –](#setproperties)|Nastaví vlastnosti ve skupině vlastností relace.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní na relace. Tato třída implementuje vlastnosti relace voláním statické funkce definované [mapy sady vlastností](../../data/oledb/begin-propset-map.md). Mapa set vlastnosti musí být zadán v třídě relace.  
  
## <a name="getproperties"></a> ISessionPropertiesImpl::GetProperties
Vrátí seznam vlastností v `DBPROPSET_SESSION` skupiny vlastností, které jsou aktuálně nastavená na relaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetProperties)(ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [ISessionProperties::GetProperties](https://msdn.microsoft.com/library/ms723643.aspx) v *referenční informace pro OLE DB programátory*. 

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties
Nastaví vlastnosti `DBPROPSET_SESSION` skupiny vlastností.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [ISessionProperties::SetProperties](https://msdn.microsoft.com/library/ms714405.aspx) v *referenční informace pro OLE DB programátory*.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
