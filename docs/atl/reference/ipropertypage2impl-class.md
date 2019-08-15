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
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495598"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl Class

Tato třída implementuje `IUnknown` a dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPropertyPage2Impl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Určuje, který ovládací prvek vlastnosti dostane fokus, když je aktivována stránka vlastností. Implementace ATL Vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) rozšiřuje [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) přidáním `EditProperty` metody. Tato metoda umožňuje klientovi vybrat konkrétní vlastnost v objektu stránky vlastností.

Třída `IPropertyPage2Impl` jednoduše vrátí E_NOTIMPL pro `IPropertyPage2::EditProperty`. Ale dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestavení ladění.

Při vytváření stránky vlastností je vaše třída obvykle odvozena z `IPropertyPageImpl`. Chcete-li poskytnout dodatečnou `IPropertyPage2`podporu, upravte definici třídy a `EditProperty` přepište metodu.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

Určuje, který ovládací prvek vlastnosti dostane fokus, když je aktivována stránka vlastností.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) v Windows SDK.

## <a name="see-also"></a>Viz také:

[IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
