---
title: Ccomenum – třída
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 8e0bf49b48c2c0f1a202231e67364637375f9342
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623532"
---
# <a name="ccomenum-class"></a>Ccomenum – třída

Tato třída definuje objekt enumerátoru modelu COM na základě pole.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Parametry

*základ*<br/>
Enumerátor rozhraní modelu COM. Zobrazit [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) příklad.

*piid*<br/>
Ukazatel na Identifikátor rozhraní rozhraní enumerátor.

*T*<br/>
Typ položky, které jsou vystavené rozhraní enumerátor.

*kopírování*<br/>
Homogenní [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md).

*ThreadModel*<br/>
Model vláken třídy. Tento parametr výchozí hodnota je globální objektový model vláken použitých v projektu.

## <a name="remarks"></a>Poznámky

`CComEnum` definuje objekt enumerátoru modelu COM na základě pole. Tato třída je obdobou [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) který implementuje enumerátor podle kontejneru standardní knihovny C++. Typické postupy použití této třídy jsou popsány níže. Další informace najdete v tématu [ATL – kolekce a enumerátory](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Chcete-li použít tuto třídu:

- **Definice TypeDef** specializace této třídy.

- Použití **typedef** jako argument šablony ve specializaci `CComObject`.

- Vytvoření instance `CComObject` specializace.

- Inicializovat objekt enumerator voláním [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).

- Vrátí enumerátor rozhraní do klienta.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[Ccomenumimpl –](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

## <a name="example"></a>Příklad

Kód níže obsahuje opakovaně použitelné funkce pro vytváření a inicializaci objekt enumerátoru.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Tuto funkci je možné implementovat `_NewEnum` vlastnost kolekce rozhraní, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Tento kód vytvoří **typedef** pro `CComEnum` , která zveřejní vektor varianty prostřednictvím `IEnumVariant` rozhraní. `CVariantArrayCollection` Třídy jednoduše specializuje `CreateEnumerator` pro práci s enumerátor objekty tohoto typu a předá nezbytné argumenty.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl – třída](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)
