---
title: Matematické a podpora plovoucí desetinné čárky | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.math
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf4a6ce7e2ad98841c20fcef5fd9639a5797852
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392546"
---
# <a name="math-and-floating-point-support"></a>Matematické a podpora plovoucí desetinné čárky

Knihovna Universal C Runtime (UCRT) nabízí mnoho funkcí knihovny math integrální a s plovoucí desetinnou čárkou, včetně všech těchto vyžadovanou ISO C99. Funkce plovoucí desetinné čárky se implementují vyvážit výkonu s správnost. Vzhledem k vytváření správně zaokrouhlené výsledek může být výtažkovými, tyto funkce jsou navrženy pro efektivní vytvořit blízká aproximace správně zaokrouhlené výsledek. Ve většině případů výsledku vytvořeného je v rámci +/-1 ulp správně zaokrouhlené výsledku, i když může být případech níž se nachází větší nepřesnost.

Řadu procedura bodu matematické funkce knihovny mají různé implementace pro různé architektury procesoru. Například x86 32-bit CRT může mít jinou implementaci než 64-bit x64 CRT. Kromě toho některé funkce mohou mít více implementace pro danou architekturu procesoru. Nejúčinnější implementace je vybrán dynamicky za běhu v závislosti na sady instrukcí nepodporuje procesoru. Například v x86 32-bit CRT, některé funkce mají obě x87 implementaci a SSE2 implementace. Při spuštění na procesor, který podporuje SSE2, rychlejší implementace SSE2 se používá. Při spuštění na procesor, který nepodporuje SSE2, pomalejší x87, které slouží k implementaci. Protože různými implementacemi matematické funkce knihovny může používat jinou pokyny procesoru a různé algoritmy nepřineslo jejich výsledky, funkce mohou mít různé výsledky mezi procesory. Ve většině případů jsou výsledky v rámci +/-1 ulp správně zaokrouhlené výsledek, ale skutečný výsledek se může lišit mezi procesory.

Předchozí verze 16bitové Microsoft C/C++ a Microsoft Visual C++ podporované **long double** typ jako typ 80bitová přesnost dat s plovoucí desetinnou čárkou. V novějších verzích Visual C++ **long double** datový typ je s plovoucí desetinnou čárkou datový typ s přesností 64-bit identické **dvojité** typu. Kompilátor zpracovává **long double** a **dvojité** jako odlišné typy, ale **long double** funkce jsou stejné jako jejich **dvojité** svými protějšky. Poskytuje CRT **long double** verzích matematické funkce pro ISO C99 zdroje kompatibilitou kódu, ale Všimněte si, že binární reprezentace se můžou lišit od jiných kompilátory.

## <a name="supported-math-and-floating-point-routines"></a>Podporované matematické a rutiny s plovoucí desetinnou čárkou

|Rutina|Použití|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Vypočítá absolutní hodnota typu integer
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Vypočítá kosinus oblouk
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Vypočítá hyperbolický kosinus oblouk
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Vypočítá sinus oblouk
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Vypočítá hyperbolický sinus oblouk
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Vypočítá tangens oblouk
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Vypočítá hyperbolický tangens oblouk
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec na konkrétní národní prostředí **double**
[atof –, _atof_l –](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede řetězec na **double**
[_atoflt –, _atoflt_l –, _atoldbl –, _atoldbl_l –](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Převede řetězec na konkrétní národní prostředí **float** nebo **long double**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Vypočítá kořenu datové krychle
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Vypočítá horní meze.
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Vypočítá inverzní doplňkové
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Získá a vymaže s plovoucí desetinnou čárkou stav registrace
[_control87 –, \__control87_2, _controlfp –](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Získá a nastaví s plovoucí desetinnou čárkou řídicího slova
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Zabezpečené verzi **_controlfp –**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Vrátí hodnotu, která má odhad jeden argument a přihlašovací jiného
[Cos, cosf –, cosl –](../c-runtime-library/reference/cos-cosf-cosl.md)|Vypočítá sinus
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Vypočítá hyperbolický sinus
[div, ldiv –, lldiv –](../c-runtime-library/reference/div.md)|Vypočítá podílu a zbývající dva celočíselné hodnoty
[_ecvt –](../c-runtime-library/reference/ecvt.md), [ecvt –](../c-runtime-library/reference/posix-ecvt.md)|Převede **dvojité** na řetězec
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Zabezpečené verzi **_ecvt –**
[ERF – erff –, erfl –](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá chybovou funkci.
[ERFC – erfcf –, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Vypočítá doplňkovou chybovou funkci
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Vypočítá exponent *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Vypočítá exponenciální 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Vypočítá *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Vypočítá absolutní hodnotu typu s plovoucí desetinnou čárkou
[_fcvt –](../c-runtime-library/reference/fcvt.md), [fcvt –](../c-runtime-library/reference/posix-fcvt.md)|Převede na řetězec číslo s plovoucí desetinnou čárkou
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Zabezpečené verzi **_fcvt –**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Určuje kladné rozdíl mezi dvěma hodnotami
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Vymaže zadané výjimky s plovoucí desetinnou čárkou
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Uloží aktuální prostředí s plovoucí desetinnou čárkou
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Získá stav zadané výjimek plovoucí desetinné čárky
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Získá režim zaokrouhlení s plovoucí desetinnou čárkou
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Nastaví režim bez zastavení výjimek plovoucí desetinné čárky
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Vyvolá zadané výjimky s plovoucí desetinnou čárkou
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Nastaví aktuální prostředí s plovoucí desetinnou čárkou
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Nastaví příznaky zadaný stav s plovoucí desetinnou čárkou
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Nastaví zadaný režim zaokrouhlení s plovoucí desetinnou čárkou
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Určuje, jsou-li nastavit příznacích stav výjimek plovoucí desetinné čárky
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Obnoví s plovoucí desetinnou čárkou prostředí poté vyvolá předchozí výjimky
[_finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Určuje, zda je hodnota konečné
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Vypočítá podlaží
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Vypočítá roztaveného multiply-add
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Vypočítá maximální počet argumentů
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Vypočítá minimální argumentů
[fmod, fmodf –, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Vypočítá zbytek s plovoucí desetinnou čárkou
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Vrátí klasifikaci hodnotu s plovoucí desetinnou čárkou
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Vrátí klasifikaci hodnotu s plovoucí desetinnou čárkou
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Nastaví obslužnou rutinu výjimky s plovoucí desetinnou čárkou
[_fpreset](../c-runtime-library/reference/fpreset.md)|Obnoví v prostředí s plovoucí desetinnou čárkou
[frexp – frexpf –, frexpl –](../c-runtime-library/reference/frexp.md)|Získá mantisa a exponent čísla s plovoucí desetinnou čárkou
[_gcvt –](../c-runtime-library/reference/gcvt.md), [gcvt –](../c-runtime-library/reference/posix-gcvt.md)|Převede na řetězec číslo s plovoucí desetinnou čárkou
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Zabezpečené verzi **_gcvt –**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Získá nebo nastaví příznak pro použití FMA3 pokyny na x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Vypočítá přepony
[ilogb – ilogbf –, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Vypočítá základní 2 exponent celé číslo
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Vypočítá absolutní hodnota typu integer
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Vypočítá podílu a zbývající dva celočíselné hodnoty
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Testy hodnotu s plovoucí desetinnou čárkou pro NaN.
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovy funkce
[ldexp – ldexpf –, ldexpl](../c-runtime-library/reference/ldexp.md)|Vypočítá x * 2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Vypočítá přirozený logaritmus absolutní hodnotu gama funkce
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Hodnotu s plovoucí desetinnou čárkou na zaokrouhlí na nejbližší **dlouho dlouho** hodnota
[llround – llroundf –, llroundl –](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Hodnotu s plovoucí desetinnou čárkou na zaokrouhlí na nejbližší **dlouho dlouho** hodnota
[protokol, logf –, logl, log10, log10f –, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Vypočítá přírodních nebo základu 10 logaritmus
[log1p – log1pf –, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Vypočítá přirozený logaritmus 1 + x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Vypočítá logaritmus o základu 2
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Vrátí exponent hodnotu s plovoucí desetinnou čárkou
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Hodnotu s plovoucí desetinnou čárkou na zaokrouhlí na nejbližší **dlouho** hodnota
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Otočí celočíselnou hodnotu doleva nebo doprava
[lround – lroundf –, lroundl –](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Hodnotu s plovoucí desetinnou čárkou na zaokrouhlí na nejbližší **dlouho** hodnota
[_matherr](../c-runtime-library/reference/matherr.md)|Výchozí obslužnou rutinu matematické chyby
[__max](../c-runtime-library/reference/max.md)|Makro, který vrací větší ze dvou hodnot
[__min](../c-runtime-library/reference/min.md)|Makro, který vrací menší ze dvou hodnot
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Rozdělí do desetinnou hodnotu s plovoucí desetinnou čárkou a částí celé číslo
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Vrátí hodnotu quiet NaN.
[nearbyint – nearbyintf –, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Vrátí zaokrouhlené hodnotu
[nextafter –, nextafterf –, nextafterl, _nextafter –, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Vrátí hodnotu dalšího reprezentovat s plovoucí desetinnou čárkou
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Vrátí hodnotu dalšího reprezentovat s plovoucí desetinnou čárkou
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Vrátí hodnotu *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Vypočítá zbytek podíl dvou hodnot s plovoucí desetinnou čárkou
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Vypočítá zbytek dvě hodnoty celé číslo
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrouhlí číslo s plovoucí desetinnou čárkou
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Otočí bitů typy celého čísla
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrouhlí číslo s plovoucí desetinnou čárkou
[_scalb –, _scalbf](../c-runtime-library/reference/scalb.md)|Argument měřítka ve power 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Vynásobí číslo s plovoucí desetinnou čárkou integrální výkon **flt_radix –**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Nastaví s plovoucí desetinnou čárkou řídicího slova
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Povolí nebo zakáže SSE2 pokyny
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Vypočítá sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Vypočítá hyperbolický sinus
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Vypočítá druhou odmocninu
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Získá s plovoucí desetinnou čárkou stavového slova
[strtof –, _strtof_l –](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Převede řetězec na **float**
[strtold _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Převede řetězec na **dlouho** **double**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Vypočítá tangens
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Vypočítá hyperbolický tangens
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Vypočítá gama funkce
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Zkrátí zlomkové části
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Převede řetězec na široké **double**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Vypočítá Besselovy funkce

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
