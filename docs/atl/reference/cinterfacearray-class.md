---
title: Cinterfacearray – třída
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 64271cbdb634284a5abcdd17b2c14d23a496b3f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614246"
---
# <a name="cinterfacearray-class"></a>Cinterfacearray – třída

Tato třída poskytuje metody, které jsou užitečné při vytváření pole z ukazatele rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní modelu COM zadání typu ukazatel na Uložit.

*piid*<br/>
Ukazatel na IID *můžu*.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Konstruktor pro pole rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozené metody pro vytvoření pole ukazatelů rozhraní modelu COM. Použití [cinterfacelist –](../../atl/reference/cinterfacelist-class.md) při seznam je povinný.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

Konstruktor

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje pole inteligentního ukazatele.

## <a name="see-also"></a>Viz také

[CAtlArray – třída](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr – třída](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
