---
title: IOleControlImpl – třída
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
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864948"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl – třída

Tato třída poskytuje výchozí implementaci rozhraní `IOleControl` a implementuje `IUnknown`.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IOleControlImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IOleControlImpl:: Freezeevents.](#freezeevents)|Označuje, zda kontejner ignoruje nebo přijímá události z ovládacího prvku.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Vyplní informace o chování klávesnice ovládacího prvku. Implementace ATL vrací E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje ovládací prvek o tom, že se změnila jedna nebo více vlastností okolí kontejneru. Implementace ATL vrací S_OK.|
|[IOleControlImpl::-Symbolickéy](#onmnemonic)|Informuje ovládací prvek o tom, že uživatel stiskl zadaný klávesovou zkratku. Implementace ATL vrací E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Třída `IOleControlImpl` poskytuje výchozí implementaci rozhraní [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

Kurz **související články** [ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="freezeevents"></a>IOleControlImpl:: Freezeevents.

V implementaci knihovny ATL `FreezeEvents` zvýší datový člen `m_nFreezeEvents` třídy ovládacího prvku, pokud je `bFreeze` TRUE, a snižuje `m_nFreezeEvents`, pokud `bFreeze` má hodnotu FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Poznámky

`FreezeEvents` pak vrátí S_OK.

Viz [IOleControl:: freezeevents.](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) v Windows SDK.

##  <a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

Vyplní informace o chování klávesnice ovládacího prvku.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Poznámky

Viz [IOleControl: GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange

Informuje ovládací prvek o tom, že se změnila jedna nebo více vlastností okolí kontejneru.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) v Windows SDK.

##  <a name="onmnemonic"></a>IOleControlImpl::-Symbolickéy

Informuje ovládací prvek o tom, že uživatel stiskl zadaný klávesovou zkratku.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleControl::](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) v Windows SDK.

## <a name="see-also"></a>Viz také

[IOleObjectImpl – třída](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
