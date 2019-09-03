---
title: intrinsic – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: bb4403abf5e278ed3727af660579e22ab69592c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220940"
---
# <a name="intrinsic-pragma"></a>intrinsic – direktiva pragma

Určuje, že volání funkcí zadaných v seznamu argumentů direktivy pragma jsou vnitřní.

## <a name="syntax"></a>Syntaxe

> **vnitřní #pragma (** *Function1* [ **;** _function2_ ...]) **)**

## <a name="remarks"></a>Poznámky

**Vnitřní** direktiva pragma říká kompilátoru, že funkce má známé chování. Kompilátor může funkci zavolat a nenahradit volání vloženými instrukcemi, pokud tím bude zvýšen výkon.

Funkce knihoven s vnitřními formami jsou uvedeny níže. Jakmile se zobrazí **vnitřní** direktiva pragma, projeví se v první definici funkce obsahující zadanou vnitřní funkci. Efekt pokračuje do konce zdrojového souboru nebo do výskytu `function` direktivy pragma, která určuje stejnou vnitřní funkci. **Vnitřní** direktivu pragma lze použít pouze mimo definici funkce na globální úrovni.

Následující funkce mají vnitřní formy a vnitřní formuláře se používají při zadání [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs –](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Programy, které používají vnitřní funkce, jsou rychlejší, protože nemají režii volání funkce, ale mohou být větší z důvodu vygenerování dalšího kódu.

**Specifické pro procesory x86**

Vnitřní objekty `_enable` a generují instrukce režimu jádra, které zakazují nebo povolují přerušení a můžou být užitečné v ovladačích režimu jádra. `_disable`

### <a name="example"></a>Příklad

Zkompilujte následující kód z příkazového řádku s `cl -c -FAs sample.c` a podívejte se na Sample. asm a podívejte se, že se na něj dostanou příkazy rozhraní příkazového řádku x86 a STI:

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

**Specifické pro konec x86**

Funkce s plovoucí desetinnou čárkou uvedené níže nemají skutečné vnitřní formy. Namísto nich mají verze, které argumenty předávají přímo do čipu plovoucí desetinné čárky místo jejich ukládání do zásobníku programu:

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/pow-powf-powl.md)|[tanh –](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|[FMOD –](../c-runtime-library/reference/fmod-fmodf.md)|[sinh –](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

Funkce s plovoucí desetinnou čárkou uvedené níže mají skutečné vnitřní formy při zadání [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/og](../build/reference/og-global-optimizations.md)a [/FP: Fast](../build/reference/fp-specify-floating-point-behavior.md) (nebo jakékoli možnosti, která zahrnuje/Og: [/Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)a [/O2](../build/reference/o1-o2-minimize-size-maximize-speed.md)):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[protokolu](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tlačítek](../c-runtime-library/reference/sin-sinf-sinl.md)|[nádrž](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[Cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Můžete použít [/FP: Strict](../build/reference/fp-specify-floating-point-behavior.md) nebo [/za](../build/reference/za-ze-disable-language-extensions.md) k přepsání generace skutečných možností s plovoucí desetinnou čárkou. V tomto případě jsou funkce generovány jako rutiny knihoven, které předávají argumenty přímo do čipu plovoucí desetinné čárky namísto jejich ukládání do zásobníku programu.

Informace a příklad, jak povolit nebo zakázat vnitřní objekty pro blok zdrojového textu, naleznete v tématu [#pragma Functions](../preprocessor/function-c-cpp.md) .

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
