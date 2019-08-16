---
title: IQuickActivateImpl – třída
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
ms.openlocfilehash: 2169686ebbf756c5caf9232f5031532c62ac8265
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495511"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl – třída

Tato třída kombinuje inicializaci ovládacího prvku Containers do jednoho volání.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IQuickActivateImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Načte aktuální velikost zobrazení běžícího ovládacího prvku.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Provádí rychlou inicializaci ovládacích prvků, které jsou načítány.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informuje ovládací prvek o velikosti zobrazovaného prostoru, ke kterému je kontejner přiřazen.|

## <a name="remarks"></a>Poznámky

Rozhraní [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) pomáhá kontejnerům zabránit prodlevám při načítání ovládacích prvků kombinací inicializace v jednom volání. Metoda umožňuje kontejneru předat ukazatel na strukturu QACONTAINER, která obsahuje ukazatele na všechna rozhraní, které ovládací prvek potřebuje. [](/windows/win32/api/ocidl/ns-ocidl-qacontainer) `QuickActivate` Při návratu ovládací prvek předává zpět ukazatel do struktury [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) , která obsahuje ukazatele na vlastní rozhraní, která jsou používána kontejnerem. Třída `IQuickActivateImpl` poskytuje výchozí `IQuickActivate` implementaci a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Načte aktuální velikost zobrazení běžícího ovládacího prvku.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost je určena pro úplné vykreslování ovládacího prvku a je zadáno v HIMETRIC jednotkách.

Viz [IQuickActivate:: GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) v Windows SDK.

##  <a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Provádí rychlou inicializaci ovládacích prvků, které jsou načítány.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Poznámky

Struktura obsahuje ukazatele na rozhraní, které vyžaduje ovládací prvek a hodnoty některých vlastností okolí. Po návratu ovládací prvek předává ukazatel na strukturu [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) , která obsahuje ukazatele na vlastní rozhraní, které kontejner vyžaduje, a další informace o stavu.

Viz [IQuickActivate:: QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) v Windows SDK.

##  <a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informuje ovládací prvek o velikosti zobrazovaného prostoru, ke kterému je kontejner přiřazen.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Poznámky

Velikost je určena v jednotkách HIMETRIC.

Viz [IQuickActivate:: SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
