---
title: Iolecontrolimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28404c4f8dddeafb624b873448d4dc7aaa5dc0d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076811"
---
# <a name="iolecontrolimpl-class"></a>Iolecontrolimpl – třída

Tato třída poskytuje výchozí implementaci třídy `IOleControl` rozhraní a implementuje `IUnknown`.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IOleControlImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Označuje, zda kontejner ignoruje nebo přijímá události z ovládacího prvku.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Vyplní informace o chování klávesnice ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informuje o ovládací prvek, jeden nebo více vedlejším vlastnostem kontejneru se změnila. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informuje o ovládací prvek, že uživatel stiskl zadané stisk klávesy. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Třída `IOleControlImpl` poskytuje výchozí implementaci třídy [IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol) rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

V implementaci ATL `FreezeEvents` zvýší třídy ovládacího prvku `m_nFreezeEvents` datový člen Pokud `bFreeze` má hodnotu TRUE a sníží `m_nFreezeEvents` Pokud `bFreeze` je FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Poznámky

`FreezeEvents` Vrátí hodnotu S_OK.

Zobrazit [: IOleControl::FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) ve Windows SDK.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Vyplní informace o chování klávesnice ovládacího prvku.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Informuje o ovládací prvek, jeden nebo více vedlejším vlastnostem kontejneru se změnila.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) ve Windows SDK.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informuje o ovládací prvek, že uživatel stiskl zadané stisk klávesy.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) ve Windows SDK.

## <a name="see-also"></a>Viz také

[IOleObjectImpl – třída](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Rozhraní – ovládací prvky ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
