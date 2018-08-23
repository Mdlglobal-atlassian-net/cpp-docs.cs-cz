---
title: Chaininterfaces – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0fc65d2aeab01de022e23d0645682800a7d555d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602362"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces – struktura

Určuje, ověřování a Inicializace funkce, které mohou být použity na sadu rozhraní ID.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename I0,
   typename I1,
   typename I2 = Details::Nil,
   typename I3 = Details::Nil,
   typename I4 = Details::Nil,
   typename I5 = Details::Nil,
   typename I6 = Details::Nil,
   typename I7 = Details::Nil,
   typename I8 = Details::Nil,
   typename I9 = Details::Nil
>
struct ChainInterfaces : I0;
template <
   typename DerivedType,
   typename BaseType,
   bool hasImplements,
   typename I1,
   typename I2,
   typename I3,
   typename I4,
   typename I5,
   typename I6,
   typename I7,
   typename I8,
   typename I9
>
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;
```

### <a name="parameters"></a>Parametry

*I0*  
(Povinné) ID rozhraní: 0.

*I1*  
(Povinné) ID rozhraní: 1.

*I2*  
(Volitelné) Rozhraní s ID 2.

*I3*  
(Volitelné) ID rozhraní 3.

*TYP I4*  
(Volitelné) ID rozhraní 4.

*I5*  
(Volitelné) ID rozhraní 5.

*I6*  
(Volitelné) ID rozhraní 6.

*I7*  
(Volitelné) Rozhraní ID 7.

*I8*  
(Volitelné) ID rozhraní 8.

*I9*  
(Volitelné) ID rozhraní 9.

*DerivedType*  
Odvozeného typu.

*BaseType*  
Základní typ odvozeného typu.

*hasImplements*  
Logická hodnota, že pokud **true**, znamená, že nemůžete použít [MixIn](../windows/mixin-structure.md) strukturu s třídou, která není odvozena od [implementuje](../windows/implements-structure.md) stucture.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[ChainInterfaces::CanCastTo – metoda](../windows/chaininterfaces-cancastto-method.md)|Určuje, jestli ID zadané rozhraní může být převeden na jednotlivé specializace určené **ChainInterface** parametry šablony.|
|[ChainInterfaces::CastToUnknown – metoda](../windows/chaininterfaces-casttounknown-method.md)|Přetypování ukazatele rozhraní typu definované *I0* parametr šablony na ukazatel na `IUnknown`.|
|[ChainInterfaces::FillArrayWithIid – metoda](../windows/chaininterfaces-fillarraywithiid-method.md)|Ukládá ID rozhraní určené *I0* parametr šablony v zadaném umístění v zadaném poli ID rozhraní.|
|[ChainInterfaces::Verify – metoda](../windows/chaininterfaces-verify-method.md)|Ověřuje, že každé rozhraní určené parametry šablony *I0* prostřednictvím *I9* dědí z `IUnknown` a/nebo `IInspectable`a že *I0* dědí z *I1* prostřednictvím *I9*.|

### <a name="protected-constants"></a>Chráněné konstanty

|Název|Popis|
|----------|-----------------|
|[ChainInterfaces::IidCount – konstanta](../windows/chaininterfaces-iidcount-constant.md)|Celkový počet rozhraní ID, které jsou součástí rozhraní určené parametry šablony *I0* prostřednictvím *I9*.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)