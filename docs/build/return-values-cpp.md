---
title: Návratové hodnoty (C++)
ms.date: 11/04/2016
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
ms.openlocfilehash: 047058a18597384a3da47d1c22874c7a297f1a48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463567"
---
# <a name="return-values-c"></a>Návratové hodnoty (C++)

Skalární návratovou hodnotu, která se vejde do 64 bitů, je vrácena prostřednictvím RAX – to zahrnuje typů __m64. Non Skalární typy, včetně float, Double a typy vektoru, jako [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) jsou vráceny v XMM0. Stav nevyužité bity v hodnotě vrácené v RAX nebo XMM0 není definován.

Uživatelem definované typy mohou být vráceny hodnotou z globální funkce a statické členské funkce. Má být vrácena hodnota v RAX VRÁTÍ, uživatelem definované typy musí mít délku 1, 2, 4, 8, 16, 32 nebo 64 bitů; žádné uživatelem definovaný konstruktor, destruktor ani operátor copy assignment; žádné soukromé nebo chráněné nestatické datové členy. žádné nestatické datové členy typu odkazu; žádné základní třídy; žádné virtuální funkce. a žádné datové členy, které nesplňují také tyto požadavky. (To je v podstatě definice C ++ 03 typem POD. Protože došlo ke změně definice v C ++ 11 standard, nedoporučujeme použití `std::is_pod` pro tento test.) V opačném případě volající předpokládá odpovědnost přidělení paměti a předání ukazatele pro vrácenou hodnotu jako první argument. Další argumenty jsou potom posunuty o jeden argument vpravo. Stejný ukazatel musí být vrácen volaným v RAX.

Tyto příklady ukazují, jak předané parametry a návratové hodnoty pro funkce s zadané deklarace:

## <a name="example-of-return-value-1---64-bit-result"></a>Příklad výsledku návratovou hodnotu 1 – 64 bitů

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

## <a name="example-of-return-value-2---128-bit-result"></a>Příklad 2 128bitové výsledku návratová hodnota

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

## <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Příklad vrácené hodnoty 3 – výsledek uživatelského typu ukazatel

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

## <a name="example-of-return-value-4---user-type-result-by-value"></a>Příklad vrácené hodnoty 4 – výsledek uživatelského typu podle hodnoty

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)