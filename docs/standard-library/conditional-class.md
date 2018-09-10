---
title: Conditional – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106610"
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
