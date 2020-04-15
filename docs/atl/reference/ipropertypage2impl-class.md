---
title: Třída iPropertyPage2impl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329596"
---
# <a name="ipropertypage2impl-class"></a>Třída iPropertyPage2impl

Tato třída `IUnknown` implementuje a dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPropertyPage2Impl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IPropertyPage2impl::EditProperty](#editproperty)|Určuje, který ovládací prvek vlastností obdrží fokus při aktivaci stránky vlastností. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) rozšiřuje [metodu IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) přidáním `EditProperty` metody. Tato metoda umožňuje klientovi vybrat určitou vlastnost v objektu stránky vlastnosti.

Třída `IPropertyPage2Impl` jednoduše vrátí `IPropertyPage2::EditProperty`E_NOTIMPL pro . Však dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) a `IUnknown` implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

Při vytváření stránky vlastností je vaše třída `IPropertyPageImpl`obvykle odvozena od . Chcete-li poskytnout `IPropertyPage2`další podporu , upravte `EditProperty` definici třídy a přepsat metodu.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertyPage2impl::EditProperty

Určuje, který ovládací prvek vlastností obdrží fokus při aktivaci stránky vlastností.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage2::EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída IperPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
