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
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326401"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl – třída

Tato třída `IUnknown` implementuje a poskytuje výchozí implementaci rozhraní [ISpecifyPropertyPages.](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Vyplní počítané pole hodnot UUID. Každé UUID odpovídá IDENTIFIKÁTORU CLSID pro jednu ze stránek vlastností, které lze zobrazit v seznamu vlastností objektu.|

## <a name="remarks"></a>Poznámky

Rozhraní [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) umožňuje klientovi získat seznam identifikátorů CLSID pro stránky vlastností podporované objektem. Třída `ISpecifyPropertyPagesImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

> [!NOTE]
> Nezveřejňujte `ISpecifyPropertyPages` rozhraní, pokud objekt nepodporuje stránky vlastností.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

Vyplní pole ve struktuře [CAUUID](/windows/win32/api/ocidl/ns-ocidl-cauuid) identifikátory CLSID pro stránky vlastností, které lze zobrazit v seznamu vlastností objektu.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá mapu vlastností objektu k načtení každého identifikátoru CLSID.

Viz [ISpecifyPropertyPages::GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída iPropertyPageimpl](../../atl/reference/ipropertypageimpl-class.md)<br/>
[Třída IperPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
