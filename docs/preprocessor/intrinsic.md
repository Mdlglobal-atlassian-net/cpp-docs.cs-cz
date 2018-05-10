---
title: vnitřní | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e908a07253e924fa3cfc0a11cdef57a9253eee00
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="intrinsic"></a>– vnitřní funkce

Určuje, že volání funkcí zadaných v seznamu argumentů direktivy pragma jsou vnitřní.

## <a name="syntax"></a>Syntaxe

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>Poznámky

**Vnitřní** – Direktiva pragma říká kompilátoru, že funkce má známé chování.  Kompilátor může funkci zavolat a nenahradit volání vloženými instrukcemi, pokud tím bude zvýšen výkon.

Funkce knihoven s vnitřními formami jsou uvedeny níže. Jednou **vnitřní** – Direktiva pragma je vidět, projeví se v definici funkce první obsahující zadaná vnitřní funkce. Účinek pokračuje na konec zdrojový soubor a vzhled **funkce** – Direktiva pragma zadání stejné vnitřní funkce. **Vnitřní** – Direktiva pragma lze použít pouze mimo definici funkce – na globální úrovni.

Následující funkce obsahují vnitřní formulářů a vnitřní formuláře se používají, když zadáte [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp –](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp –](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen –](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy –](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[Abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Programy používající vnitřní funkce jsou rychlejší, protože neobsahují režii volání funkcí, mohou však být větší kvůli většímu množství dodatečně vygenerovaného kódu.

**x86 konkrétní**

**_Disable** a **_zapnout** vnitřní funkce generování pokyny režimu jádra pro přerušení zapnout/vypnout a může být užitečné při ovladače režimu jádra.

### <a name="example"></a>Příklad

Zkompilujte následující kód z příkazového řádku příkazem „cl -c -FAs sample.c“ a prohlédněte si soubor sample.asm, v němž lze vidět, že instrukce byly převedeny do instrukcí CLI a STI architektury x86.

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

**Konkrétní end x86**

Funkce s plovoucí desetinnou čárkou uvedené níže nemají skutečné vnitřní formy. Namísto nich mají verze, které argumenty předávají přímo do čipu plovoucí desetinné čárky místo jejich ukládání do zásobníku programu:

|||||
|-|-|-|-|
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[COSH](../c-runtime-library/reference/cosh-coshf-coshl.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[TANH](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

 Funkce plovoucí desetinné čárky níže uvedené máte true vnitřní formuláře, když zadáte [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/Og](../build/reference/og-global-optimizations.md), a [/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) (nebo jakákoliv možnost, která zahrnuje /Og: [/ Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)a/O2):

|||||
|-|-|-|-|
|[Atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[Protokolu](../c-runtime-library/reference/log-logf-log10-log10f.md)|[Sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[Tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[Cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Můžete použít [/fp: striktní](../build/reference/fp-specify-floating-point-behavior.md) nebo [/Za](../build/reference/za-ze-disable-language-extensions.md) potlačit generování true možnosti vnitřní s plovoucí desetinnou čárkou. V tomto případě jsou funkce generovány jako rutiny knihoven, které předávají argumenty přímo do čipu plovoucí desetinné čárky namísto jejich ukládání do zásobníku programu.

V tématu [funkce #pragma](../preprocessor/function-c-cpp.md) informace a příklad o tom, jak povolit nebo zakázat vnitřní funkce pro blok zdrojový text.

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
