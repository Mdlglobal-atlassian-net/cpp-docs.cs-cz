---
title: Třída IOleControlImpl
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329612"
---
# <a name="iolecontrolimpl-class"></a>Třída IOleControlImpl

Tato třída poskytuje výchozí `IOleControl` implementaci rozhraní `IUnknown`a implementuje .

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IOleControlImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Označuje, zda kontejner ignoruje nebo přijímá události z ovládacího prvku.|
|[IOleControlimpl::GetControlInfo](#getcontrolinfo)|Vyplní informace o chování klávesnice ovládacího prvku. Implementace ATL vrátí E_NOTIMPL.|
|[iOleControlimpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje ovládací prvek, že došlo ke změně jedné nebo více vlastností okolí kontejneru. Implementace ATL vrátí S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje ovládací prvek, že uživatel stiskl zadaný stisk klávesy. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Třída `IOleControlImpl` poskytuje výchozí implementaci rozhraní [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestaveníladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents

V implementaci atl `FreezeEvents` zintáží datový člen `m_nFreezeEvents` třídy `bFreeze` ovládacího prvku, pokud `m_nFreezeEvents` `bFreeze` je TRUE, a snížení, pokud je FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Poznámky

`FreezeEvents`pak vrátí S_OK.

Viz [IOleControl::FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) v sadě Windows SDK.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlimpl::GetControlInfo

Vyplní informace o chování klávesnice ovládacího prvku.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Poznámky

Viz [IOleControl:GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>iOleControlimpl::OnAmbientPropertyChange

Informuje ovládací prvek, že došlo ke změně jedné nebo více vlastností okolí kontejneru.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleControl::OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) v sadě Windows SDK.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

Informuje ovládací prvek, že uživatel stiskl zadaný stisk klávesy.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleControl::OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
