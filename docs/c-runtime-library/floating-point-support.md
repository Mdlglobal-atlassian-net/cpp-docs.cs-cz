---
title: Matematické a podpora plovoucí desetinné čárky
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: 1d03333dee12989af5897c34ba96484930a39673
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703126"
---
# <a name="math-and-floating-point-support"></a>Matematické a podpora plovoucí desetinné čárky

Modul Universal C Runtime library (UCRT) poskytuje mnoho s plovoucí desetinnou čárkou a integrální matematických knihovních funkcí, včetně všech funkcí, které jsou vyžadované ISO C99. Funkce s plovoucí desetinnou čárkou jsou implementovány vyvážit výkon s správnosti. Protože vytváření správně zakulacený výsledky mohou být nepřekonatelně drahé, tyto funkce jsou navržené tak efektivně vytvářet aproximace správně zakulacený výsledek. Ve většině případů výsledek vytvořený je v rámci +/-1 ulp výsledku správně zakulacený, ale můžou nastat případy, ve kterých je větší nepřesnost.

Hodnoty s plovoucí mnoho matematických knihovních funkcí mají různé implementace pro rozdílné architektury procesoru bodu. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít několik implementací pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na instrukční sadu podporovaných procesoru. Například v 32bitové x86 CRT, některé funkce mají obě x87 provádění a implementaci SSE2. Při spuštění na procesor, který podporuje SSE2, se používá rychlejší provádění SSE2. Když se používá Procesorem, který nepodporuje SSE2, pomalejší x87 použita implementace. Protože různé implementace matematických knihovních funkcí může pomocí různých procesorů pokyny a různé algoritmy jejich výsledky, funkce mohou mít různé výsledky mezi procesory. Ve většině případů jsou výsledky v rámci +/-1 ulp výsledku správně zakulacený, ale skutečné výsledky se mohou lišit mezi procesory.

Předchozí verze 16bitové Microsoft C/C++ a Microsoft Visual C++ nepodporuje **long double** typ jako typ s plovoucí desetinnou čárkou data 80bitová přesnost. V novějších verzích Visual C++ **long double** datový typ je 64 bitů přesnosti s plovoucí desetinnou čárkou datový typ shodný s **double** typu. Kompilátor zpracovává **long double** a **double** jako různé typy, ale **long double** funkce jsou shodné s jejich **double** protějšky. Poskytuje CRT **long double** verzích matematické funkce pro ISO C99 zdrojového kódu kompatibility, ale mějte na paměti, že binární reprezentace může lišit od jiné kompilátory.

## <a name="supported-math-and-floating-point-routines"></a>Podporované matematické a rutiny s plovoucí desetinnou čárkou

|Rutina|Použití|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Vypočítá absolutní hodnotu celočíselného typu.
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Vypočítá Arkus kosinus
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Vypočte hyperbolický Arkus kosinus
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Vypočítá arkussinus
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Vypočte hyperbolický Arkus sinus
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Vypočítá arkustangens
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Vypočte hyperbolický Arkus tangens
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec na specifických pro národní prostředí **double**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede řetězec na **double**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec na specifických pro národní prostředí **float** nebo **long double**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Vypočítá kořenové datové krychle
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Vypočítá horní mez
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Vypočítá inverzní additive
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Načte a vymaže stav s plovoucí desetinnou čárkou registru
[_control87, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Získá a nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Zabezpečené verze **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Vrátí hodnotu, která má velikost jednoho argumentu a znaménko druhého
[Cos cosf –, cosl –](../c-runtime-library/reference/cos-cosf-cosl.md)|Vypočítá sinus
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Vypočte hyperbolický sinus
[div, ldiv, lldiv](../c-runtime-library/reference/div.md)|Počítá podíl a zbytek dvou celočíselných hodnot
[_ecvt](../c-runtime-library/reference/ecvt.md), [ecvt](../c-runtime-library/reference/posix-ecvt.md)|Převede **double** na řetězec
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Zabezpečené verze **_ecvt –**
[ERF – erff –, erfl –](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá chybovou funkci
[ERFC – erfcf –, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá doplňkovou chybovou funkci
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Vypočítá exponent *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Vypočítá exponenciální 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Vypočítá *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Vypočítá absolutní hodnotu s plovoucí desetinnou čárkou
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|Převede číslo s plovoucí desetinnou čárkou na řetězec
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Zabezpečené verze **_fcvt –**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Určuje pozitivní rozdíl mezi dvěma hodnotami
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Vymaže zadané výjimky s plovoucí desetinnou čárkou
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Uloží aktuální prostředí s plovoucí desetinnou čárkou
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Získá stav zadané výjimky s plovoucí desetinnou čárkou
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Získá režim zaokrouhlení s plovoucí desetinnou čárkou
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Režim výjimky s plovoucí desetinnou čárkou bez zastavení sady
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Vyvolá zadané výjimky s plovoucí desetinnou čárkou
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Nastaví aktuální prostředí s plovoucí desetinnou čárkou
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Nastaví příznaky zadaný stav s plovoucí desetinnou čárkou
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Nastaví zadanou režimu zaokrouhlení s plovoucí desetinnou čárkou
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Určuje stav příznacích výjimky s plovoucí desetinnou čárkou jsou nastavené.
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Obnoví prostředí s plovoucí desetinnou čárkou a vyvolává předchozí výjimky
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Vypočítá dolní mez
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Vypočítá roztaveného přičti
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Vypočítá maximální počet argumentů
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Vypočítá minimální argumenty
[fmod – fmodf –, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Vypočítá zbytek s plovoucí desetinnou čárkou
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Vrátí klasifikace s plovoucí desetinnou čárkou
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Vrátí klasifikace s plovoucí desetinnou čárkou
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Nastaví obslužnou rutinu výjimky s plovoucí desetinnou čárkou
[_fpreset](../c-runtime-library/reference/fpreset.md)|Nastaví výchozí hodnoty s plovoucí desetinnou čárkou prostředí
[frexp – frexpf –, frexpl –](../c-runtime-library/reference/frexp.md)|Načte mantisu a exponent čísla s plovoucí desetinnou čárkou
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|Převede číslo s plovoucí desetinnou čárkou na řetězec
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Zabezpečené verze **_gcvt –**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Získá nebo nastaví příznak pro použití instrukcí FMA3 x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Vypočítá přepony
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Vypočítá základní 2 exponent celé číslo
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Vypočítá absolutní hodnotu celočíselného typu.
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Počítá podíl a zbytek dvou celočíselných hodnot
[isfinite, _finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Určuje, zda hodnota je omezené
[isgreater isgreaterequal, isless, islessequal, islessgreater, isunordered](../c-runtime-library/reference/floating-point-ordering.md)|Porovnání pořadí dvě hodnoty plovoucího bodu
[isinf –](../c-runtime-library/reference/isinf.md)|Určuje, zda je nekonečnou hodnotu s plovoucí desetinnou čárkou
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Testy s plovoucí desetinnou čárkou hodnota NaN
[isnormal](../c-runtime-library/reference/isnormal.md)|Testuje, jestli hodnotu s plovoucí desetinnou čárkou je omezené a ne subnormal
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovy funkce
[ldexp – ldexpf –, ldexpl](../c-runtime-library/reference/ldexp.md)|Computes x*2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Vypočítá absolutní hodnotu funkce gamma přirozený logaritmus
[llrint llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **long long** hodnota
[llround – llroundf –, llroundl –](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **long long** hodnota
[protokol, logf –, logl, log10, log10f –, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Vypočítá logaritmus o fyzické nebo základu 10
[log1p – log1pf –, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Vypočítá přirozený logaritmus 1 + x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Vypočítá logaritmus o základu 2
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Vrátí exponent hodnotu s plovoucí desetinnou čárkou
[lrint lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhé** hodnota
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Otočí celočíselnou hodnotu doleva nebo doprava
[lround – lroundf –, lroundl –](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou na nejbližší **dlouhé** hodnota
[_matherr](../c-runtime-library/reference/matherr.md)|Obslužnou rutinu výchozí matematické chyby
[__max](../c-runtime-library/reference/max.md)|Makro, které vrátí větší ze dvou hodnot
[__min](../c-runtime-library/reference/min.md)|Makro, které vrátí menší ze dvou hodnot
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Rozdělí hodnotu s plovoucí desetinnou čárkou na frakce a celá čísla
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Vrátí hodnotu tichý NaN
[nearbyint – nearbyintf –, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Vrátí zaoblenými hodnota
[nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Vrátí následující reprezentovatelnou hodnotu s plovoucí desetinnou čárkou
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Vrátí následující reprezentovatelnou hodnotu s plovoucí desetinnou čárkou
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Vrátí hodnotu *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Vypočítá zbytek z podílu dvou hodnot s plovoucí desetinnou čárkou
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Vypočítá zbytek dvou celočíselných hodnot
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Otočí bitů v typy celých čísel
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrouhlí hodnotu s plovoucí desetinnou čárkou
[_scalb – _scalbf](../c-runtime-library/reference/scalb.md)|Argument měřítka ve mocninou čísla 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Vynásobí číslo s plovoucí desetinnou čárkou integrální sílu **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Povolí nebo zakáže SSE2 pokyny
[signbit –](../c-runtime-library/reference/signbit.md)|Testuje na bit znaménka s plovoucí desetinnou čárkou
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Vypočítá sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Vypočte hyperbolický sinus
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Vypočítá druhou odmocninu
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Získá slovo stav s plovoucí desetinnou čárkou
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Převede řetězec na **plovoucí desetinnou čárkou**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Převede řetězec na **dlouhé** **double**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Vypočítá tangens
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Vypočte hyperbolický tangens
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Vypočítá funkce gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Zkrátí zlomkové části
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede řetězec na široké **double**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovy funkce

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[S plovoucí desetinnou čárkou primitiv](../c-runtime-library/reference/floating-point-primitives.md)<br/>
