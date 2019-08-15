---
title: CComEnum – třída
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 7252eb2fa5d34618a1c38484a2506bae27a1106a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497212"
---
# <a name="ccomenum-class"></a>CComEnum – třída

Tato třída definuje objekt enumerátoru COM založený na poli.

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

*Základ*<br/>
Rozhraní enumerátoru COM. Příklad najdete v tématu [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Ukazatel na ID rozhraní rozhraní enumerátoru.

*T*<br/>
Typ položky vystavený rozhraním enumerátoru.

*kopírování*<br/>
[Třída zásad](../../atl/atl-copy-policy-classes.md)pro homogenní kopírování.

*ThreadModel*<br/>
Model vláken třídy. Tento parametr má výchozí hodnotu pro model vláken globálního objektu použitý v projektu.

## <a name="remarks"></a>Poznámky

`CComEnum`definuje objekt enumerátoru COM založený na poli. Tato třída je analogická k [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) , která implementuje enumerátor na základě C++ standardního kontejneru knihovny. Typický postup použití této třídy je popsaný níže. Další informace naleznete v tématu [kolekce a čítače ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Chcete-li použít tuto třídu:

- **definice typedef** a specializace této třídy.

- Použijte **typedef** jako argument šablony v specializaci `CComObject`.

- Vytvořte instanci `CComObject` specializace.

- Inicializujte objekt enumerátoru voláním [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init).

- Vrátí rozhraní enumerátoru klientovi.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

## <a name="example"></a>Příklad

Níže uvedený kód poskytuje opakovaně použitelnou funkci pro vytvoření a inicializaci objektu enumerátoru.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Tato funkce šablony se dá použít k implementaci `_NewEnum` vlastnosti rozhraní kolekce, jak je znázorněno níže:

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Tento kód vytvoří **typedef** pro `CComEnum` , který zpřístupňuje vektor variant prostřednictvím `IEnumVariant` rozhraní. Třída se jednoduše `CreateEnumerator` specializuje pro práci s objekty enumerátoru tohoto typu a předá potřebné argumenty. `CVariantArrayCollection`

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl – třída](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)
