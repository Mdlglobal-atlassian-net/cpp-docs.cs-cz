---
title: conditional – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457327"
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

*B*\
Hodnota, která určuje vybraný typ.

*LINCE*\
Výsledek typu při hodnotě B je true.

*T2*\
Výsledek typu, když B je false.

## <a name="remarks"></a>Poznámky

Definice `conditional<B, T1, T2>::type` typedef člena šablony je vyhodnocena jako *T1* , pokud je *b* vyhodnocena jako **true**, a je vyhodnocena jako *T2* , pokud je *b* vyhodnocena jako **false**.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
