---
title: Vlastnosti a třídy stránky vlastností (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 05c3a67e278389bb2ab1b07e9d6cf63cbe347c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249623"
---
# <a name="properties-and-property-pages-classes"></a>Vlastnosti a třídy stránky vlastností

Vlastnosti a stránky vlastností podporují následující třídy:

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) načte nebo nastaví vlastnosti objektu prostřednictvím `IDispatch` ukazatele.

- [Cstockpropimpl –](../atl/reference/cstockpropimpl-class.md) implementuje uložených vlastnostech podporovaných ATL.

- [Iperpropertybrowsingimpl –](../atl/reference/iperpropertybrowsingimpl-class.md) přistupuje k informacím na stránkách vlastností objektu.

- [Ipersistpropertybagimpl –](../atl/reference/ipersistpropertybagimpl-class.md) ukládá vlastností objektu do kontejneru objektů dodaná klientem.

- [Ipropertypageimpl –](../atl/reference/ipropertypageimpl-class.md) spravuje konkrétní stránka vlastností v rámci seznamu vlastností.

- [Ipropertypage2impl –](../atl/reference/ipropertypage2impl-class.md) podobné `IPropertyPageImpl`, ale také umožňuje vybrat konkrétní vlastnost na stránce Vlastnosti klientovi.

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) získá CLSID pro stránky vlastností podporována objektem.

## <a name="related-articles"></a>Související články

[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md)

[ATL COM – stránky vlastností](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>Viz také:

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Makra map vlastností](../atl/reference/property-map-macros.md)
