---
title: CComEnumOnSTL – třída
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: ab11ea5e5347c9c8684e8710e9742fdbcad8a46b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497157"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL – třída

Tato třída definuje objekt enumerátoru COM na základě C++ standardní kolekce knihoven.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Enumerátor COM. Příklad najdete v tématu [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Ukazatel na ID rozhraní rozhraní enumerátoru.

*T*<br/>
Typ položky vystavený rozhraním enumerátoru.

*kopírování*<br/>
Třída [zásad kopírování](../../atl/atl-copy-policy-classes.md) .

*CollType*<br/>
Třída C++ kontejneru standardní knihovny.

## <a name="remarks"></a>Poznámky

`CComEnumOnSTL`definuje objekt enumerátoru COM na základě C++ standardní kolekce knihoven. Tato třída se dá použít samostatně nebo ve spojení s [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Typický postup použití této třídy je popsaný níže. Další informace naleznete v tématu [kolekce a čítače ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Chcete-li použít tuto třídu s ICollectionOnSTLImpl:

- **definice typedef** a specializace této třídy.

- Použijte **typedef** jako finální argument šablony v specializaci `ICollectionOnSTLImpl`.

Příklad naleznete v tématu [kolekce a výčty knihovny ATL](../../atl/atl-collections-and-enumerators.md) .

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Chcete-li použít tuto třídu nezávisle na ICollectionOnSTLImpl:

- **definice typedef** a specializace této třídy.

- Použijte **typedef** jako argument šablony v specializaci `CComObject`.

- Vytvořte instanci `CComObject` specializace.

- Inicializujte objekt enumerátoru voláním [IEnumOnSTLImpl:: init](../../atl/reference/ienumonstlimpl-class.md#init).

- Vrátí rozhraní enumerátoru klientovi.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

## <a name="example"></a>Příklad

Následující kód poskytuje obecnou funkci pro zpracování vytváření a inicializace objektu Enumerator:

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

Tato funkce šablony se dá použít k implementaci `_NewEnum` vlastnosti rozhraní kolekce, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

Tento kód vytvoří **typedef** `CComEnumOnSTL` pro, který `CComVariant`zpřístupňuje vektor s pomocí `IEnumVariant` rozhraní. Třída se jednoduše `CreateSTLEnumerator` specializuje pro práci s objekty enumerátoru tohoto typu. `CVariantCollection`

## <a name="see-also"></a>Viz také:

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Ukázka ATLCollections: Ukazuje třídy zásad pro ICollectionOnSTLImpl, CComEnumOnSTL a vlastní kopírování.](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl – třída](../../atl/reference/ienumonstlimpl-class.md)
