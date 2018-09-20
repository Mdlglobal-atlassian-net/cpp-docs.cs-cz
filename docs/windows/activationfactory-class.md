---
title: Activationfactory – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55c82290c3a96ab71419b36a7ec4a4eb2b528753
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419812"
---
# <a name="activationfactory-class"></a>ActivationFactory – třída

Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename I0 = Details::Nil,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil
>
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
ID nultého rozhraní.

*I1*<br/>
První rozhraní.

*I2*<br/>
Druhé síťové rozhraní.

## <a name="remarks"></a>Poznámky

**Activationfactory –** poskytuje metody registrace a základní funkce pro `IActivationFactory` rozhraní. **Activationfactory –** také umožňuje poskytnout implementaci vlastní objekt pro vytváření.

Následující fragment kódu symbolicky ukazuje, jak používat activationfactory –.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]

Následující fragment kódu ukazuje způsob použití [implementuje](../windows/implements-structure.md) struktury zadat více než tři ID rozhraní.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[ActivationFactory::ActivationFactory – konstruktor](../windows/activationfactory-activationfactory-constructor.md)|Inicializuje **activationfactory –** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ActivationFactory::AddRef – metoda](../windows/activationfactory-addref-method.md)|Zvýší počet odkazů aktuálního **activationfactory –** objektu.|
|[ActivationFactory::GetIids – metoda](../windows/activationfactory-getiids-method.md)|Načte pole ID implementovaného rozhraní.|
|[ActivationFactory::GetRuntimeClassName – metoda](../windows/activationfactory-getruntimeclassname-method.md)|Získá název třídy runtime objektu, který aktuální **activationfactory –** vytvoří instanci.|
|[ActivationFactory::GetTrustLevel – metoda](../windows/activationfactory-gettrustlevel-method.md)|Získá úroveň důvěryhodnosti objektu, který aktuální **activationfactory –** vytvoří instanci.|
|[ActivationFactory::QueryInterface – metoda](../windows/activationfactory-queryinterface-method.md)|Načte ukazatel na rozhraní zadané.|
|[ActivationFactory::Release – metoda](../windows/activationfactory-release-method.md)|Sníží počet odkaz na aktuální **activationfactory –** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)