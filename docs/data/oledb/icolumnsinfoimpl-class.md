---
title: IColumnsInfoImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
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
ms.openlocfilehash: 2eb7714762de8ccf810a8fdd04ee33ae24e9d431
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447060"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl – třída

Poskytuje implementaci rozhraní [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo, 
   public CDBIDOps
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IColumnsInfoImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetColumnInfo –](#getcolumninfo)|Vrátí metadata sloupce potřebná pro většinu uživatelů.|
|[MapColumnIDs](#mapcolumnids)|Vrátí pole pořadí sloupců v sadě řádků, které jsou identifikovány zadanými ID sloupců.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní pro sady řádků a příkazy. Pokud chcete upravit chování `IColumnsInfo` implementace vašeho poskytovatele, musíte upravit mapu sloupce poskytovatele.

## <a name="getcolumninfo"></a>IColumnsInfoImpl –:: GetColumnInfo

Vrátí metadata sloupce potřebná pro většinu uživatelů.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>Parametry

Viz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci OLE DB programátora*.

## <a name="mapcolumnids"></a>IColumnsInfoImpl –:: MapColumnIDs

Vrátí pole pořadí sloupců v sadě řádků, které jsou identifikovány zadanými ID sloupců.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>Parametry

Viz [IColumnsInfo:: MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)