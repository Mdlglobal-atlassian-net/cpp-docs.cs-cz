---
title: Předávání parametrů
ms.date: 11/04/2016
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
ms.openlocfilehash: 1b7fb126ab3b140d0ab672067df35c5fc8df926e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648744"
---
# <a name="parameter-passing"></a>Předávání parametrů

První čtyři celočíselné argumenty jsou předány v registrech. Celočíselné hodnoty jsou předány (v pořadí zleva doprava) v RCX, RDX, R8 a R9. Argumenty 5 a vyšší jsou předány do zásobníku. Všechny argumenty jsou zarovnána vpravo v registrech. Uděláte to tak, že volaný může horní bity registru ignorovat, pokud musí být a máte přístup jenom část potřeby registrace.

S plovoucí desetinnou čárkou a dvojitou přesností argumenty jsou předány v XMM0 - XMM3 (až 4) se slotem celé číslo (RCX, RDX, R8 a R9), která se běžně používá pro tento základní slot se ignoruje (viz příklad) a naopak.

[__m128](../cpp/m128.md) typy, pole a řetězce jsou nebyl nikdy předán okamžitého zhodnocení, ale spíše je předán ukazatel na paměť přidělenou volajícím. Struktury/sjednocení velikosti 8, 16, 32 nebo 64 bitů a __m64 jsou předány jako by byly celých čísel stejné velikosti. Struktury/sjednocení než tyto velikosti jsou předány jako ukazatele na paměť přidělenou volajícím. Pro tyto typy předány jako ukazatele (včetně \__m128), volající – přidělené dočasné paměti bude zarovnán na 16 bajtů.

Vnitřní funkce, které nepřidělujte místo v zásobníku a nevyžadují další funkce můžete použít další závislé registry k předávání argumentů další registru protože těsné vazby mezi kompilátor a provádění vnitřní funkce. Toto je další příležitosti pro zlepšení výkonu.

Volaný má na starost vypsání parametry registru do jejich stínové místo v případě potřeby.

Následující tabulka shrnuje, jak jsou předávány parametry:

|Typ parametru|Jak předávat|
|--------------------|----------------|
|Plovoucí desetinná čárka|První 4 parametry - XMM0 prostřednictvím XMM3. Ostatní předány v zásobníku.|
|Integer|První 4 parametry – RCX, RDX, R8 R9. Ostatní předány v zásobníku.|
|Agregace (8, 16, 32 nebo 64 bitů) a __m64|První 4 parametry – RCX, RDX, R8 R9. Ostatní předány v zásobníku.|
|Agregace (ostatní)|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|
|__m128|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|

## <a name="example-of-argument-passing-1---all-integers"></a>Příklad 1 - všech celých čísel předávání argumentů

```
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

## <a name="example-of-argument-passing-2---all-floats"></a>Příklad 2 – všechny floaty předávání argumentů

```
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Příklad 3 - smíšené celá čísla a float předávání argumentů

```
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Příklad 4 předávání argumentů-__m64, \__m128 a agregace

```
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)