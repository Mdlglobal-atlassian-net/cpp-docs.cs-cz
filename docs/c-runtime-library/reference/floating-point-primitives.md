---
title: S plovoucí desetinnou čárkou primitiv
ms.date: 01/31/2019
apiname:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703365"
---
# <a name="floating-point-primitives"></a>S plovoucí desetinnou čárkou primitiv

Primitivní funkce specifické pro společnost Microsoft, které se používají k implementaci některé standardní runtime funkce knihovny jazyka C (CRT) s plovoucí desetinnou čárkou. Pro úplnost jsou zdokumentované tady, ale nedoporučuje se používat. Některé z těchto funkcí jsou uvedené jako nevyužité, protože jste známé potíže v přesnost, zpracování výjimek a soulad s IEEE 754 chování. Existují v knihovně pouze z důvodu zpětné kompatibility. Pro správné chování, přenositelnost a dodržování standardů raději přes tyto funkce standardní funkce s plovoucí desetinnou čárkou.

## <a name="dclass-ldclass-fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Implementace těchto primitivních hodnot s plovoucí desetinnou čárkou C verze – makro CRT [fpclassify –](fpclassify.md) pro typy s plovoucí desetinnou čárkou. Klasifikace argument *x* se vrátí jako jednu z následujících konstant, definované v math.h:

|Hodnota|Popis|
|-----------|-----------------|
| **FP_NAN** | Tichý, signalizace nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizované nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná subnormal (Nenormalizovaná) hodnota |
| **FP_ZERO** | Pozitivní nebo negativní nulovou hodnotu |

Další podrobnosti, můžete použít specifické pro Microsoft [_fpclass _fpclassf](fpclass-fpclassf.md) funkce. Použití [fpclassify –](fpclassify.md) – makro nebo funkce pro přenositelnost.

## <a name="dsign-ldsign-fdsign"></a>_dsign _ldsign, _fdsign

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Implementace těchto primitivních hodnot s plovoucí desetinnou čárkou [signbit –](signbit.md) – makro nebo funkce CRT. Vrátí nenulovou hodnotu, pokud je bit znaménka nastavená v mantise (mantisa) argumentu *x*a 0, pokud není nastaven bit znaménka.

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Argumenty funkce s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Těchto primitivních hodnot s plovoucí desetinnou čárkou přijímají dva argumenty, *x* a *y*a vrátí hodnotu, která zobrazuje jejich pořadí vztahu, vyjádřené jako bitový nebo tyto konstanty definované v math.h:

| Hodnota | Popis |
|------------|-----------------|
| **_FP_LT** | *x* lze považovat za méně než *y* |
| **_FP_EQ** | *x* lze považovat za rovna *y* |
| **_FP_GT** | *x* lze považovat za větší než *y* |

Implementace těchto primitivních hodnot [isgreater isgreaterequal, isless, islessequal islessgreater a isunordered](floating-point-ordering.md) makra a funkce v CRT.

## <a name="dtest-ldtest-fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument typu s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Implementace těchto primitivních hodnot s plovoucí desetinnou čárkou C++ verze funkcí CRT [fpclassify –](fpclassify.md) pro typy s plovoucí desetinnou čárkou. Argument *x* se vyhodnotí a vrátí se jako jeden z následujících konstant, definované v math.h klasifikace:

|Hodnota|Popis|
|-----------|-----------------|
| **FP_NAN** | Tichý, signalizace nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizované nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná subnormal (Nenormalizovaná) hodnota |
| **FP_ZERO** | Pozitivní nebo negativní nulovou hodnotu |

Další podrobnosti, můžete použít specifické pro Microsoft [_fpclass _fpclassf](fpclass-fpclassf.md) funkce. Použití [fpclassify –](fpclassify.md) funkce pro přenositelnost.

## <a name="dint-ldint-fdint"></a>_d_int _ld_int, _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument typu s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako s integrálním typem.

### <a name="remarks"></a>Poznámky

Ukazatel na hodnotu s plovoucí desetinnou čárkou trvat těchto primitivních hodnot s plovoucí desetinnou čárkou *px* a hodnotu exponentu *exp*a odebírají zlomkovou část hodnoty s plovoucí desetinnou čárkou níže daný exponent, pokud je to možné . Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnota v *px* Pokud nekonečno a NaN a na výstupu hodnoty v *px* jinak.

## <a name="dscale-ldscale-fdscale"></a>_dscale _ldscale, _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument typu s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako s integrálním typem.

### <a name="remarks"></a>Poznámky

Ukazatel na hodnotu s plovoucí desetinnou čárkou trvat těchto primitivních hodnot s plovoucí desetinnou čárkou *px* a hodnotu exponentu *exp*, a škálovat hodnotu v *px* 2<sup> *exp*</sup>, pokud je to možné. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnota v *px* Pokud nekonečno a NaN a na výstupu hodnoty v *px* jinak. Přenositelnost, dáváte přednost [ldexp – ldexpf – a ldexpl](ldexp.md) funkce.

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parametry

*pexp*<br/>
Ukazatel na exponent jako s integrálním typem.

*px*<br/>
Ukazatel na argument typu s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Těchto primitivních hodnot s plovoucí desetinnou čárkou rozdělit hodnotu s plovoucí desetinnou čárkou, na kterou odkazoval *px* mantisy (mantisa) a exponent, pokud je to možné. Mantisa je škálovat tak, aby absolutní hodnota je větší než nebo rovna hodnotě 0,5 a menší než 1,0. Exponent je hodnota *n*, kde původní hodnotu s plovoucí desetinnou čárkou je rovna škálován mantisy krát 2<sup>*n*</sup>. Toto celé číslo exponent *n* je uložen v umístění, na které odkazuje *pexp*. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnota v *px* Pokud nekonečno a NaN a na jinak výstupní hodnoty. Přenositelnost, dáváte přednost [frexp – frexpf –, frexpl –](frexp.md) funkce.

## <a name="dexp-ldexp-fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parametry

*y*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*px*<br/>
Ukazatel na argument typu s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako s integrálním typem.

### <a name="remarks"></a>Poznámky

Vytvoření těchto primitivních hodnot s plovoucí desetinnou čárkou hodnotu s plovoucí desetinnou čárkou v umístění, na kterou odkazoval *px* rovna *y* * 2<sup>*exp*</sup>. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnota v *y* Pokud nekonečno a NaN a na výstupu hodnoty v *px* jinak. Přenositelnost, dáváte přednost [ldexp – ldexpf – a ldexpl](ldexp.md) funkce.

## <a name="dnorm-fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*PS*<br/>
Ukazatel na bitové reprezentace hodnotu s plovoucí desetinnou čárkou, vyjádřené jako pole **bez znaménka** **krátký**.

### <a name="remarks"></a>Poznámky

Těchto primitivních hodnot s plovoucí desetinnou čárkou normalizovat zlomkovou část underflowed s plovoucí desetinnou čárkou a upravit *charakteristiku*, nebo posunutého exponent, tak, aby odpovídaly. Je hodnota předána jako bitové reprezentace typu s plovoucí desetinnou čárkou převést na celou řadu **bez znaménka** **krátký** prostřednictvím `_double_val`, `_ldouble_val`, nebo `_float_val` typu punning sjednocení deklarovaná v math.h. Vrácená hodnota je výsledek **fpclassify –** vstupní hodnotu s plovoucí desetinnou čárkou, pokud je nekonečno a NaN a jinak výstupní hodnoty.

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly _ldpoly, _fdpoly

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*Tabulka*<br/>
Ukazatel na tabulku konstantní koeficienty pro polynomu.

*n*<br/>
Pořadí stupeň polynomu k vyhodnocení.

### <a name="remarks"></a>Poznámky

Těchto primitivních hodnot s plovoucí desetinnou čárkou vrátit vyhodnocení *x* v polynomu pořadí *n* jehož koeficienty jsou reprezentovány odpovídající konstantních hodnot v *tabulky*. Například pokud *tabulky*\[0] = 3.0, *tabulky*\[1] = 4.0, *tabulky*\[2] = 5.0, a *n* = 2, představuje polynomické 5.0 x<sup>2</sup> + 4.0 x + 3.0. Pokud tento polynomial vyhodnotí *x* 2.0, výsledkem je 31.0. Tyto funkce se používá interně.

## <a name="dlog-dlog-dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*base_flag*<br/>
Příznak, který určuje základ pro použití, 0 pro základ *e* a nenulové pro základní 10.

### <a name="remarks"></a>Poznámky

Vrátí přirozený protokolu těchto primitivních hodnot s plovoucí desetinnou čárkou *x*, ln (*x*) nebo protokolu<sub>*e*</sub>(*x*), Když *base_flag* je 0. Vrátí základní 10 protokolu *x*, nebo protokol<sub>10</sub>(*x*), kdy *base_flag* je nulová. Tyto funkce se používá interně. Přenositelnost, dáváte přednost funkce [protokolu, logf –, logl, log10, log10f – a log10l](log-logf-log10-log10f.md).

## <a name="dsin-ldsin-fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*quadrant společnosti Gartner*<br/>
Kvadrant posun 0, 1, 2 nebo 3 a použijte k vytvoření `sin`, `cos`, `-sin`, a `-cos` výsledky.

### <a name="remarks"></a>Poznámky

Vrátí sinus těchto primitivních hodnot s plovoucí desetinnou čárkou *x* posunu podle *kvadrantu* modulo 4. Efektivně, vrátí hodnotu sinus, kosinus, - sinus a - kosinus *x* při *kvadrantu* modulo 4 je 0, 1, 2 nebo 3, v uvedeném pořadí. Tyto funkce se používá interně. Přenositelnost, dáváte přednost [sin, sinf –, sinl –](sin-sinf-sinl.md), [cos cosf – a cosl –](cos-cosf-cosl.md) funkce.

## <a name="requirements"></a>Požadavky

Záhlaví: \<math.h >

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf –](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[Cos cosf –, cosl –](cos-cosf-cosl.md)<br/>
[frexp – frexpf –, frexpl –](frexp.md)<br/>
[ldexp – ldexpf – a ldexpl](ldexp.md)<br/>
[protokol, logf –, logl, log10, log10f –, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
