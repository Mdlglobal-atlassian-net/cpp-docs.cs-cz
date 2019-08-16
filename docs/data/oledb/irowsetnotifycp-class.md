---
title: IRowsetNotifyCP – třída
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: 481c2c0ec28972e9cef8d1103e49afa2037c2393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501382"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP – třída

Implementuje web poskytovatele pro rozhraní připojovacího bodu rozhraní [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída odvozená z `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Třída mutex, která podporuje vícenásobný přístup (výchozí hodnota je `CComSharedMutex`). Mutex je synchronizační objekt, který umožňuje jednomu vláknu vzájemně exkluzivní přístup k prostředku.

*piid*<br/>
Ukazatel ID rozhraní (`IID*`) `IRowsetNotify` pro rozhraní spojovacího bodu. Výchozí hodnota je `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
Pole typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), což je dynamicky přidělené pole `IUnknown` ukazatelů na rozhraní jímky klienta.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Upozorní spotřebitele na změnu hodnoty sloupce.|
|[Fire_OnRowChange](#onrowchange)|Upozorňuje spotřebitele na změnu ovlivňující řádky.|
|[Fire_OnRowsetChange](#onrowsetchange)|Upozorňuje spotřebitele na změnu ovlivňující celou sadu řádků.|

## <a name="remarks"></a>Poznámky

`IRowsetNotifyCP`implementuje všesměrové funkce pro poradenství naslouchací procesy v `IID_IRowsetNotify` bodu připojení změny obsahu sady řádků.

Všimněte si, že musíte také implementovat a `IRowsetNotify` registrovat na příjemce (také označovaný jako "jímka") pomocí [IRowsetNotifyImpl –](../../data/oledb/irowsetnotifyimpl-class.md) , aby příjemce mohl zpracovávat oznámení. Viz [přijímání oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bodu připojení na příjemce.

Podrobné informace o implementaci oznámení najdete v části "podpora oznámení" v tématu [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md).

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange

Vysílá událost [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) , která upozorní uživatele na změnu hodnoty sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parametry

Viz rozhraní [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange

Vysílá událost [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) do všech posluchačů v bodu `IID_IRowsetNotify` připojení, aby upozornila uživatele na změnu ovlivňující řádky.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parametry

Viz rozhraní [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange

Vysílá událost [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) do všech posluchačů v bodu `IID_IRowsetNotify` připojení, aby upozornila uživatele na změnu ovlivňující celou sadu řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parametry

Viz rozhraní [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také:

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Oznámení (COM)](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)