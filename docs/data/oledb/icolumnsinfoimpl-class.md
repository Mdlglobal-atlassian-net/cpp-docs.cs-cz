---
title: IColumnsInfoImpl – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 149d8ea9b23abffb73b5ea620ea094d6f5b792b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498927"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl – třída

Poskytuje implementaci [IColumnsInfo](/previous-versions/windows/desktop/ms724541) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,  
   public CDBIDOps
```

### <a name="parameters"></a>Parametry

*T*<br/>
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

Zobrazit [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *referenční informace pro OLE DB programátory*.

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

Vrátí pole řadové číslovky sloupců v sadě řádků, které se identifikují pomocí ID zadaného sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200) v *referenční informace pro OLE DB programátory*.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)