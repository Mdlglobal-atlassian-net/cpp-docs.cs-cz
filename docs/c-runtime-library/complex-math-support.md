---
title: Podpora komplexní matematické C | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.complex
dev_langs:
- C++
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 661e1367ea64713cf7a143f276cd195d54fecf85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-complex-math-support"></a>Podpora komplexní matematické C

Knihovna Microsoft C Runtime (CRT) poskytuje komplexní matematické funkce knihovny, včetně všech těchto vyžadovanou ISO C99. Kompilátor nepodporuje přímo **komplexní** nebo **_complex –** – klíčové slovo, proto implementace Microsoft používá typy struktur k reprezentaci komplexní čísla.

Tyto funkce jsou implementované vyvážit výkonu s správnost. Vzhledem k vytváření správně zaokrouhlené výsledek může být výtažkovými, tyto funkce jsou navrženy pro efektivní vytvořit blízká aproximace správně zaokrouhlené výsledek. Ve většině případů výsledku vytvořeného je v rámci +/-1 ulp správně zaokrouhlené výsledku, i když může být případech níž se nachází větší nepřesnost.

Komplexní matematické rutiny spoléhají na procedura bodu matematické funkce knihovny pro jejich implementaci. Tyto funkce mají různé implementace pro různé architektury procesoru. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít více implementace pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na sady instrukcí nepodporuje procesoru. Například v x86 32-bit CRT, některé funkce mají obě x87 implementaci a SSE2 implementace. Při spuštění na procesor, který podporuje SSE2, rychlejší implementace SSE2 se používá. Při spuštění na procesor, který nepodporuje SSE2, pomalejší x87, které slouží k implementaci. Protože různými implementacemi matematické funkce knihovny může používat jinou pokyny procesoru a různé algoritmy nepřineslo jejich výsledky, funkce mohou mít různé výsledky mezi procesory. Ve většině případů jsou výsledky v rámci +/-1 ulp správně zaokrouhlené výsledek, ale skutečný výsledek se může lišit mezi procesory.

## <a name="types-used-in-complex-math"></a>Typy používané v komplexní matematické

Implementace Microsoft complex.h hlavičky, která definuje tyto typy jako ekvivalenty pro C99 standardní nativní komplexní typy:

|Standardní typ|Typ Microsoft|
|-|-|
|**float komplexní** nebo **float _complex –**|**_FComplex**|
|**dvojité komplexní** nebo **dvojité _complex –**|**_DComplex**|
|**long double komplexní** nebo **_complex – long double**|**_LComplex**|

Záhlaví math.h definuje samostatný typ, **_complex – struktura**používané k [_cabs –](../c-runtime-library/reference/cabs.md) funkce. **_Complex – struktura** typ není používán ekvivalentní komplexní matematické funkce [soubory CAB, cabsf, cabsl –](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Komplexní konstanty a makra

**I** je definován jako **float** komplexní typ **_FComplex** iniciovány `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Trigonometrické funkce

|Funkce|Popis|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Výpočetní komplexní oblouk kosinus komplexní čísla|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Výpočetní komplexní oblouk sinus komplexní čísla|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Výpočetní komplexní oblouk tangens komplexní čísla|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Výpočetní komplexní kosinus komplexní čísla|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Výpočetní komplexní sinus reprezentující komplexní čísla|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Výpočetní komplexní tangens reprezentující komplexní čísla|

## <a name="hyperbolic-functions"></a>Hyperbolické funkce

|Funkce|Popis|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Výpočetní komplexní oblouk hyperbolický kosinus reprezentující komplexní čísla|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Výpočetní komplexní oblouk hyperbolický sinus reprezentující komplexní čísla|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Výpočetní komplexní oblouk hyperbolický tangens reprezentující komplexní čísla|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Výpočetní komplexní hyperbolický kosinus reprezentující komplexní čísla|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Výpočetní komplexní hyperbolický sinus reprezentující komplexní čísla|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Výpočetní komplexní hyperbolický tangens reprezentující komplexní čísla|

## <a name="exponential-and-logarithmic-functions"></a>Exponenciální a logaritmické funkce

|Funkce|Popis|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Výpočetní komplexní základní -*e* exponenciální komplexního čísla.|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Výpočetní komplexní přirozený (základní -*e*) logaritmus komplexní čísla|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Výpočetní komplexní základu 10 logaritmus komplexní čísla|

## <a name="power-and-absolute-value-functions"></a>Napájení a absolutní hodnota funkce

|Funkce|Popis|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Výpočetní komplexní absolutní hodnotu (také nazývané norm, numerického zbytku nebo rozsahem) reprezentující komplexní čísla|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Výpočetní funkci komplexní power x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Výpočetní komplexní druhou odmocninu komplexního čísla.|

## <a name="manipulation-functions"></a>Funkce pro zpracování

|Funkce|Popis|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Vytvořit komplexní číslo od skutečné a pomyslná částí|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Výpočetní argument (také nazývané úhel fáze) komplexního čísla.|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Výpočetní pomyslná součástí reprezentující komplexní čísla|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Výpočetní sdružené reprezentující komplexní čísla|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Výpočetní projekci komplexního čísla do oblasti Riemannův|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Výpočetní skutečné součástí reprezentující komplexní čísla|
|[Norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Výpočetní kvadratických odhad reprezentující komplexní čísla|

## <a name="operation-functions"></a>Operace funkce

Protože komplexní čísla nejsou nativního typu v kompilátoru Microsoft, standardní aritmetické operátory nejsou definované v komplexní typy. Pro usnadnění práce jsou k dispozici tyto funkce knihovny math komplexní povolit omezený zpracování komplexní čísla v uživatelském kódu:

|Funkce|Popis|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Vynásobit dvě komplexní čísla|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Násobit komplexní a číslem s plovoucí desetinnou čárkou|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
