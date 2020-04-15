---
title: Třída IQuickActivateImpl
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
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329552"
---
# <a name="iquickactivateimpl-class"></a>Třída IQuickActivateImpl

Tato třída kombinuje inicializaci řízení kontejnerů do jednoho volání.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IQuickActivateImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iQuickActivateImpl::GetContentExtent](#getcontentextent)|Načte aktuální velikost zobrazení pro spuštěný ovládací prvek.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Provádí rychlou inicializaci načítaných ovládacích prvků.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje ovládací prvek o tom, kolik místa zobrazení kontejneru má přiřazen.|

## <a name="remarks"></a>Poznámky

Rozhraní [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) pomáhá kontejnerům vyhnout se zpoždění při načítání ovládacích prvků kombinací inicializace v jednom volání. Metoda `QuickActivate` umožňuje kontejneru předat ukazatel [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) struktury, která obsahuje ukazatele na všechna rozhraní, které ovládací prvek potřebuje. Po návratu ovládací prvek předá zpět ukazatel [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) struktury, která obsahuje ukazatele na vlastní rozhraní, které jsou používány kontejneru. Třída `IQuickActivateImpl` poskytuje výchozí `IQuickActivate` implementaci a `IUnknown` implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>iQuickActivateImpl::GetContentExtent

Načte aktuální velikost zobrazení pro spuštěný ovládací prvek.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost je určena pro úplné vykreslování ovládacího prvku a je určena v jednotkách HIMETRIC.

Viz [IQuickActivate::GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) v sadě Windows SDK.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Provádí rychlou inicializaci načítaných ovládacích prvků.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Poznámky

Struktura obsahuje ukazatele na rozhraní potřebné ovládací prvek a hodnoty některých vlastností okolí. Po návratu ovládací prvek předá ukazatel [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) struktury, která obsahuje ukazatele na vlastní rozhraní, které vyžaduje kontejner a další informace o stavu.

Viz [IQuickActivate::QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) v sadě Windows SDK.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informuje ovládací prvek o tom, kolik místa zobrazení kontejneru má přiřazen.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost je specifikována v jednotkách HIMETRIC.

Viz [IQuickActivate::SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
