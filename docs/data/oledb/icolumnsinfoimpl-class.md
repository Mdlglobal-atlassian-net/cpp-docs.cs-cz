---
title: Icolumnsinfoimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1aa70a8efea82660632cf0219c76009eea44f606
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269810"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl – třída
Poskytuje implementaci [IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IColumnsInfoImpl`.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetColumnInfo –](#getcolumninfo)|Vrátí metadata sloupce vyžadované většina uživatelů.|  
|[Mapcolumnids –](#mapcolumnids)|Vrátí pole řadové číslovky sloupců v sadě řádků, které se identifikují pomocí ID zadaného sloupce.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní sady řádků a příkazy. Chcete změnit chování váš poskytovatel `IColumnsInfo` implementace, budete muset upravit mapování sloupce poskytovatele.  

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo
Vrátí metadata sloupce vyžadované většina uživatelů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/library/ms722704.aspx) v *referenční informace pro OLE DB programátory*.  

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs
Vrátí pole řadové číslovky sloupců v sadě řádků, které se identifikují pomocí ID zadaného sloupce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IColumnsInfo::MapColumnIDs](https://msdn.microsoft.com/library/ms714200.aspx) v *referenční informace pro OLE DB programátory*.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
