---
title: ISpecifyPropertyPagesImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: c201cf6d9d89ab1a6a8e888deee1be79e5770490
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495414"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `ISpecifyPropertyPagesImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Vyplní počítané pole hodnot UUID. Každý UUID odpovídá identifikátoru CLSID pro jednu ze stránek vlastností, které lze zobrazit v seznamu vlastností objektu.|

## <a name="remarks"></a>Poznámky

Rozhraní [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) umožňuje klientovi získat seznam identifikátorů CLSID pro stránky vlastností podporované objektem. Třída `ISpecifyPropertyPagesImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

> [!NOTE]
>  Nezveřejňujte rozhraní `ISpecifyPropertyPages` , pokud váš objekt nepodporuje stránky vlastností.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Vyplní pole ve struktuře [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) identifikátory CLSID pro stránky vlastností, které lze zobrazit v seznamu vlastností objektu.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Poznámky

ATL používá mapu vlastností objektu k načtení každého identifikátoru CLSID.

Viz [ISpecifyPropertyPages::](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) GetPages v Windows SDK.

## <a name="see-also"></a>Viz také:

[IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
