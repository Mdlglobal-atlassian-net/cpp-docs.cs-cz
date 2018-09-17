---
title: literály typu chrono | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1508927300cad6d7b8c244bc341aaf4a44e7bb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711053"
---
# <a name="chrono-literals"></a>literály typu chrono

(C ++ 14) \<Chrono > záhlaví definuje 12 [uživateli definované literály](../cpp/user-defined-literals-cpp.md) usnadnit pomocí literály, které představují hodiny, minuty, sekundy, milisekund, mikrosekundách a nanosekundách. Každý uživatelem definovaného literálu má integral a s plovoucí desetinnou čárkou přetížení. Literály jsou definovány v oboru názvů vloženého literals::chrono_literals, což je přeneseny do rozsahu automaticky při std::chrono je v oboru.

## <a name="syntax"></a>Syntaxe

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>Návratová hodnota

Literály, které provést **long long** argument vrací hodnotu nebo odpovídající typ. Literály, které trvat plovoucí bodu návratový argument [doba trvání](../standard-library/duration-class.md).

## <a name="example"></a>Příklad

Následující příklady zasaďte použití literály typu chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="requirements"></a>Požadavky

**Hlavička**: \<chrono >

**Namespace**: std::literals::chrono_literals

## <a name="see-also"></a>Viz také:

[\<chrono>](../standard-library/chrono.md)<br/>
