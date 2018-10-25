---
title: ISpecifyPropertyPagesImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86ad1f489553d1637683ac1310bfe2b9be04ffb0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064755"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `ISpecifyPropertyPagesImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Vyplní hodnoty počítá pole UUID. Každý identifikátor UUID odpovídá CLSID pro jednu ze stránek vlastností, které se dají zobrazit v seznamu vlastností objektu.|

## <a name="remarks"></a>Poznámky

[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) rozhraní umožňuje klientům získat seznam CLSID pro stránky vlastností podporována objektem. Třída `ISpecifyPropertyPagesImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

> [!NOTE]
>  Nezveřejňujte `ISpecifyPropertyPages` rozhraní, pokud objekt nepodporuje stránky vlastností.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getpages"></a>  ISpecifyPropertyPagesImpl::GetPages

Vyplní pole [CAUUID](/windows/desktop/api/ocidl/ns-ocidl-tagcauuid) strukturu s CLSID pro stránky vlastností, které se dají zobrazit v seznamu vlastností objektu.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Poznámky

ATL – používá k načtení každý identifikátor CLSID mapy vlastností objektu.

Zobrazit [ISpecifyPropertyPages::GetPages](/windows/desktop/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) ve Windows SDK.

## <a name="see-also"></a>Viz také

[IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
