---
title: conditional – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: be81a1bc32f2f86f1d79970868933bddb8dc3620
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212102"
---
# <a name="conditional-class"></a>conditional – třída

Vybere jeden ze dvou typů v závislosti na zadané podmínce.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Parametry

*B*<br/>
Hodnota, která určuje vybraný typ.

*T1*<br/>
Typ výsledku při B má hodnotu true.

*T2*<br/>
Typ výsledku při B má hodnotu false.

## <a name="remarks"></a>Poznámky

Definice typu člena šablony `conditional<B, T1, T2>::type` vyhodnotí jako *T1* při *B* vyhodnotí jako **true**a je vyhodnocena jako *T2* při  *B* vyhodnotí jako **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
