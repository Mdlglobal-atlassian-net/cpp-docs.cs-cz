---
title: Podpora matematických a plovoucích bodů
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: a0ee21378a6feb7ada39dc00f0e181672470e231
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821509"
---
# <a name="math-and-floating-point-support"></a>Podpora matematických a plovoucích bodů

Knihovna Universal C Runtime Library (UCRT) poskytuje mnoho integrálních a plovoucích funkcí matematické knihovny, včetně všech těch, které vyžaduje ISO C99. Funkce s plovoucí desetinnou čárkou jsou implementovány pro rovnováhu výkonu se správností. Vzhledem k tomu, že výsledkem správného zaokrouhlení výsledku může být nenáročná, jsou tyto funkce navrženy tak, aby efektivně přinesly přibližné přibližné shody se správným zaobleným výsledkem. Ve většině případů se výsledek vygeneroval do +/-1 ulpy správně zaokrouhleného výsledku, i když existují případy s větším nepřesností.

Mnoho funkcí matematické knihovny s plovoucí desetinnou čárkou má různé implementace pro různé architektury PROCESORů. Například 32 x86 CRT může mít jinou implementaci než 64 CRT. Kromě toho mohou mít některé funkce pro danou architekturu procesoru více implementací. Nejúčinnější implementace je vybrána dynamicky za běhu v závislosti na sadách instrukcí, které CPU podporuje. Například v 32 x86 CRT některé funkce mají implementaci x87 i implementaci SSE2. Při spuštění na procesoru, který podporuje SSE2, se použije rychlejší implementace SSE2. Při spuštění na procesoru, který nepodporuje SSE2, se použije pomalejší implementace x87. Vzhledem k tomu, že různé implementace funkcí matematické knihovny mohou používat různé instrukce procesoru a různé algoritmy pro vytváření jejich výsledků, funkce mohou v různých procesorech vydávat různé výsledky. Ve většině případů jsou výsledky v rámci většího zaokrouhleného výsledku mezi +/-1 ULP, ale skutečné výsledky se můžou v různých procesorech lišit.

Předchozí 16bitové verze Microsoft C/C++ a Microsoft Visual C++ podporují typ **Long Double** jako datový typ s plovoucí desetinnou čárkou 80. V novějších verzích vizuálu C++je datový typ **long double** typu 64-bitová přesnost s plovoucí desetinnou čárkou, která je shodná s typem **Double** . Kompilátor zpracovává **dlouhé Double** a **Double** jako odlišné typy, ale **dlouhé dvojité** funkce jsou identické s jejich **dvojitými** protějšky. CRT poskytuje **dlouhé dvojité** verze matematických funkcí pro kompatibilitu zdrojového kódu ISO C99, ale Všimněte si, že binární reprezentace se může lišit od ostatních kompilátorů.

## <a name="supported-math-and-floating-point-routines"></a>Podporované rutiny matematické a plovoucí desetinné čárky

|Rutina|Použití|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Vypočítá absolutní hodnotu typu Integer.
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Vypočítá kosinus oblouku.
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Vypočítá kosinus hyperbolický oblouku.
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Vypočítá sinus oblouku.
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Vypočítá sinus hyperbolický oblouku.
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Vypočítá tečnu oblouku.
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Vypočítá tangens hyperbolický oblouku.
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec specifický pro národní prostředí na **typ Double** .
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede řetězec na **typ Double** .
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec specifický pro národní prostředí na typ **float** nebo **Long Double** .
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Vypočítá kořen datové krychle.
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Vypočítá strop
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Vypočítá doplněk doplňkového textu.
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Získá a vymaže registr stavu s plovoucí desetinnou čárkou.
[_control87, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Získá a nastaví řídicí slovo s plovoucí desetinnou čárkou.
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Zabezpečená verze **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Vrátí hodnotu, která má velikost jednoho argumentu a znaménko jiného.
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|Vypočítá sinus.
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Vypočítá hyperbolický sinus.
[div, ldiv, lldiv](../c-runtime-library/reference/div.md)|Vypočítá podíl a zbytek dvou celočíselných hodnot.
[_ecvt](../c-runtime-library/reference/ecvt.md), [ECVT](../c-runtime-library/reference/posix-ecvt.md)|Převede **Double** na řetězec.
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Zabezpečená verze **_ecvt**
[ERF, erff –, erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá chybovou funkci.
[ERFC –, erfcf –, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá doplňkovou chybu funkce.
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Vypočítá exponenciální e-<sup>x</sup> .
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Vypočítá exponenciální 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Výpočty *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Vypočítá absolutní hodnotu typu s plovoucí desetinnou čárkou.
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|Převede číslo s plovoucí desetinnou čárkou na řetězec.
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Zabezpečená verze **_fcvt**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Určuje kladný rozdíl mezi dvěma hodnotami.
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Vymaže zadané výjimky s plovoucí desetinnou čárkou.
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Ukládá aktuální prostředí s plovoucí desetinnou čárkou.
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Získá zadaný stav výjimky s plovoucí desetinnou čárkou.
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Získá režim zaokrouhlení s plovoucí desetinnou čárkou.
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Nastaví režim výjimky s plovoucí desetinnou čárkou, který není zazastavený.
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Vyvolává zadané výjimky s plovoucí desetinnou čárkou.
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Nastaví aktuální prostředí s plovoucí desetinnou čárkou.
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Nastaví zadané příznaky stavu s plovoucí desetinnou čárkou.
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Nastaví určený režim zaokrouhlení s plovoucí desetinnou čárkou.
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Určuje, které příznaky stavu výjimky s plovoucí desetinnou čárkou jsou nastaveny.
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Obnoví prostředí s plovoucí desetinnou čárkou a potom vyvolá předchozí výjimky.
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Vypočítá podlahovou základnu.
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Vypočítá vynásobení s vynásobeným sečtením
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Vypočítá maximum argumentů.
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Vypočítá minimální počet argumentů.
[FMOD –, fmodf –, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Vypočítá zbytek s plovoucí desetinnou čárkou.
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Vrátí klasifikaci hodnoty s plovoucí desetinnou čárkou.
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Vrátí klasifikaci hodnoty s plovoucí desetinnou čárkou.
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Nastaví obslužnou rutinu pro výjimky s plovoucí desetinnou čárkou.
[_fpreset](../c-runtime-library/reference/fpreset.md)|Obnoví prostředí s plovoucí desetinnou čárkou.
[frexp –, frexpf –, frexpl](../c-runtime-library/reference/frexp.md)|Získá mantisu a exponent čísla s plovoucí desetinnou čárkou.
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|Převede číslo s plovoucí desetinnou čárkou na řetězec.
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Zabezpečená verze **_gcvt**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Získá nebo nastaví příznak pro použití instrukcí FMA3 na platformě x64.
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Vypočítá přepony
[ilogb –, ilogbf –, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Vypočítá celočíselný exponent desítkového čísla 2.
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Vypočítá absolutní hodnotu typu Integer.
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Vypočítá podíl a zbytek dvou celočíselných hodnot.
[isfinite, _finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Určuje, jestli je hodnota konečná.
[isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered](../c-runtime-library/reference/floating-point-ordering.md)|Porovnat pořadí dvou hodnot s plovoucí desetinnou čárkou
[isinf](../c-runtime-library/reference/isinf.md)|Určuje, zda je hodnota s plovoucí desetinnou čárkou nekonečná.
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Testuje hodnotu s plovoucí desetinnou čárkou pro NaN.
[isnormal](../c-runtime-library/reference/isnormal.md)|Testuje, jestli je hodnota s plovoucí desetinnou čárkou konečná i Nenormalizovaná.
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovu funkci
[ldexp –, ldexpf –, ldexpl](../c-runtime-library/reference/ldexp.md)|Computes x*2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Vypočítá přirozený logaritmus absolutní hodnoty funkce gamma.
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhou** dlouhou hodnotu.
[llround, llroundf, llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhou** dlouhou hodnotu.
[log, logf –, logl, log10 –, log10f –, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Vypočítá logaritmus přirozený nebo dekadický-10.
[log1p –, log1pf –, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Vypočítá přirozený logaritmus hodnoty 1 + x.
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Vypočítá logaritmus o základu 2.
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Vrátí Exponent hodnoty s plovoucí desetinnou čárkou.
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhou** hodnotu.
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Otočí celočíselnou hodnotu vlevo nebo vpravo.
[lround, lroundf, lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhou** hodnotu.
[_matherr](../c-runtime-library/reference/matherr.md)|Výchozí obslužná rutina matematické chyby
[__max](../c-runtime-library/reference/max.md)|Makro, které vrací větší ze dvou hodnot
[__min](../c-runtime-library/reference/min.md)|Makro, které vrací menší ze dvou hodnot
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Rozdělí hodnotu s plovoucí desetinnou čárkou na zlomky a celočíselné části.
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Vrátí hodnotu tichého NaN.
[nearbyint, nearbyintf, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Vrátí zaoblenou hodnotu.
[nextafter –, nextafterf –, nextafterl, _nextafter _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Vrátí další reprezentovatelné číslo s plovoucí desetinnou čárkou.
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Vrátí další reprezentovatelné číslo s plovoucí desetinnou čárkou.
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Vrátí hodnotu *x*<sup>*y*</sup> .
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Vypočítá zbytek podílu dvou hodnot s plovoucí desetinnou čárkou.
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Vypočítá zbytek dvou celočíselných hodnot.
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou.
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Otočí bity v celých typech.
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou.
[_scalb _scalbf](../c-runtime-library/reference/scalb.md)|Škáluje argument mocninou mocniny 2.
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Vynásobí číslo s plovoucí desetinnou čárkou integrálním výkonem **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Nastaví řídicí slovo s plovoucí desetinnou čárkou.
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Povolí nebo zakáže pokyny pro SSE2.
[signbit](../c-runtime-library/reference/signbit.md)|Testuje bit znaménka hodnoty s plovoucí desetinnou čárkou.
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Vypočítá sinus.
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Vypočítá hyperbolický sinus.
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Vypočítá druhou odmocninu
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Získá stavové slovo s plovoucí desetinnou čárkou.
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Převede řetězec na typ **float** .
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Převede řetězec na typ **Long** **Double** .
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Vypočítá tangens.
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Vypočítá hyperbolický tangens.
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Vypočítá funkci gamma.
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Zkrátí zlomkovou část.
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede velký řetězec na **typ Double** .
[_y0, _y1 _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovu funkci

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Primitiva s plovoucí desetinnou čárkou](../c-runtime-library/reference/floating-point-primitives.md)<br/>
