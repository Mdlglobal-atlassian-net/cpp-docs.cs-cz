---
title: IPropertyPage2Impl Class
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
ms.openlocfilehash: bf76182242f7b76e3a2c18f85b72674e88afa737
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287502"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl Class

Tato třída implementuje `IUnknown` a zdědí výchozí implementace [ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPropertyPage2Impl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Určuje, který vlastnost ovládací prvek získá fokus, když je aktivován na stránce vlastností. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2) rozhraní rozšiřuje [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) tak, že přidáte `EditProperty` metody. Tato metoda umožňuje vybrat konkrétní vlastnost v objektu vlastností stránky klientovi.

Třída `IPropertyPage2Impl` jednoduše vrací E_NOTIMPL pro `IPropertyPage2::EditProperty`. Ale dědí výchozí implementace [ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md) a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

Při vytváření stránky vlastností vaší třídy je obvykle odvozen z `IPropertyPageImpl`. Kvůli další podpoře `IPropertyPage2`, úpravě vaší definice třídy a přepsat `EditProperty` metody.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Určuje, který vlastnost ovládací prvek získá fokus, když je aktivován na stránce vlastností.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IPropertyPage2::EditProperty](/windows/desktop/api/ocidl/nf-ocidl-ipropertypage2-editproperty) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
