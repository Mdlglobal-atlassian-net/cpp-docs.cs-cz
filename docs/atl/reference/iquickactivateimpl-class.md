---
title: Iquickactivateimpl – třída
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 2a2b11746249b6ee4f6ddd578717aacc374d53bc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265246"
---
# <a name="iquickactivateimpl-class"></a>Iquickactivateimpl – třída

Tato třída kombinuje Inicializace řízení kontejnerů do jednoho volání.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IQuickActivateImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Provádí rychlé inicializace načítání ovládacích prvků.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje o kontrolu nad kolik prostor pro zobrazení je přiřazeno kontejneru.|

## <a name="remarks"></a>Poznámky

[IQuickActivate](/windows/desktop/api/ocidl/nn-ocidl-iquickactivate) rozhraní pomáhá kontejnery vyhnuli prodlevám při načítání ovládacích prvků kombinací inicializace v jednom volání. `QuickActivate` Metoda umožňuje předat ukazatel na kontejneru [QACONTAINER](/windows/desktop/api/ocidl/ns-ocidl-tagqacontainer) potřebuje struktura, která obsahuje odkazy na všechna rozhraní ovládacího prvku. Při návratu, ovládací prvek předává zpět ukazatel [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) struktura, která obsahuje odkazy na vlastní rozhraní, které jsou používány obalu. Třída `IQuickActivateImpl` poskytuje výchozí implementaci třídy `IQuickActivate` a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent

Načte aktuální velikost zobrazení pro ovládací prvek spuštěné.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost je pro úplné vykreslování ovládacího prvku a je zadán v jednotkách HIMETRIC.

Zobrazit [IQuickActivate::GetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) ve Windows SDK.

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

Provádí rychlé inicializace načítání ovládacích prvků.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Poznámky

Struktura obsahuje odkazy na rozhraní, které jsou potřeba pro ovládací prvek a hodnoty vlastnosti některé prostředí. Po návratu, ovládací prvek předává ukazatel [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) strukturu, která obsahuje odkazy na vlastní rozhraní, které vyžaduje kontejneru a doplňkové informace o stavu.

Zobrazit [IQuickActivate::QuickActivate](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-quickactivate) ve Windows SDK.

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

Informuje o kontrolu nad kolik prostor pro zobrazení je přiřazeno kontejneru.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost se zadává v jednotkách HIMETRIC.

Zobrazit [IQuickActivate::SetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
