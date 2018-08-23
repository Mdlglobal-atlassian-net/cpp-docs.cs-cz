---
title: Interfacetraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 966759acdac3cf78625cfd072471245a6e42ad63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597112"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   typename I0
>
struct __declspec(novtable) InterfaceTraits;
template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parametry

*I0*  
Název rozhraní.

*CloakedType*  
Pro `RuntimeClass`, `Implements` a `ChainInterfaces`, rozhraní, které nesmí být v seznamu nepodporuje ID rozhraní.

## <a name="remarks"></a>Poznámky

Implementuje běžné vlastnosti rozhraní.

Druhá šablona je specializací skrytá rozhraní. Třetí šablony je specializací Nil parametrů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`Base`|Synonymum pro *I0* parametr šablony.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[InterfaceTraits::CanCastTo – metoda](../windows/interfacetraits-cancastto-method.md)|Určuje, zda je zadaný ukazatel může být převeden na ukazatel na `Base`.|
|[InterfaceTraits::CastToBase – metoda](../windows/interfacetraits-casttobase-method.md)|Přetypování zadaný ukazatel na ukazatel na `Base`.|
|[InterfaceTraits::CastToUnknown – metoda](../windows/interfacetraits-casttounknown-method.md)|Přetypování zadaný ukazatel na ukazatel na `IUnknown`.|
|[InterfaceTraits::FillArrayWithIid – metoda](../windows/interfacetraits-fillarraywithiid-method.md)|Přiřadí Identifikátor rozhraní `Base` k prvku pole určená argumentem indexu.|
|[InterfaceTraits::Verify – metoda](../windows/interfacetraits-verify-method.md)|Ověřuje, že `Base` správně pochází.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[InterfaceTraits::IidCount – konstanta](../windows/interfacetraits-iidcount-constant.md)|Obsahuje počet rozhraní přidružené k aktuální ID **interfacetraits –** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)