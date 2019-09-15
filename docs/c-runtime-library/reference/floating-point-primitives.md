---
title: Primitiva s plovoucí desetinnou čárkou
ms.date: 01/31/2019
api_name:
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
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 25d70062a76f9c32692f5df3f7abb96b49892725
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957162"
---
# <a name="floating-point-primitives"></a>Primitiva s plovoucí desetinnou čárkou

Primitivní funkce specifické pro společnost Microsoft, které se používají k implementaci některých standardních funkcí s plovoucí desetinnou čárkou v jazyce C Runtime Library (CRT). Jsou zde popsány pro úplnost, ale nejsou doporučovány pro použití. Některé z těchto funkcí jsou označeny jako nepoužívané, protože se označují, že mají problémy s přesností, zpracování výjimek a soulad s chováním IEEE-754. Existují v knihovně pouze kvůli zpětné kompatibilitě. Pro správné chování, přenositelnost a dodržování standardů, preferovat standardní funkce s plovoucí desetinnou čárkou na těchto funkcích.

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

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

Tyto primitivy s plovoucí desetinnou čárkou implementují verze C makra CRT [fpclassify –](fpclassify.md) pro typy s plovoucí desetinnou čárkou. Klasifikace argumentu *x* je vrácena jako jedna z těchto konstant definovaná v Math. h:

|Value|Popis|
|-----------|-----------------|
| **FP_NAN** | Tiché, signalizace nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizovaná nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná hodnota subnormálního (Denormalizovaná) |
| **FP_ZERO** | Kladná nebo záporná nulová hodnota |

Další podrobnosti můžete použít ve funkcích [_fpclass](fpclass-fpclassf.md) specifických pro společnost Microsoft. Pro přenositelnost použijte makro nebo funkci [fpclassify –](fpclassify.md) .

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

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

Tyto primitivy s plovoucí desetinnou čárkou implementují makro nebo funkci [signbit –](signbit.md) v CRT. Vrátí nenulovou hodnotu, pokud je bit znaménka nastaven v mantisa (mantise) argumentu *x*a 0, pokud není bit znaménka nastaven.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

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

Tyto primitivy s plovoucí desetinnou čárkou přebírají dva argumenty, *x* a *y*a vrátí hodnotu, která zobrazuje jejich vztah řazení vyjádřený jako bitový nebo tyto konstanty definované v Math. h:

| Value | Popis |
|------------|-----------------|
| **_FP_LT** | *x* se dá považovat za míň než *y* . |
| **_FP_EQ** | *x* se dá vzít v úvahu jako *y* . |
| **_FP_GT** | *x* se dá považovat za větší než *y* . |

Tyto primitivní prvky implementují v CRT funkce [isgreaterequal, less, islessequal, islessgreater a isunordered](floating-point-ordering.md) .

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Tyto primitivní funkce s plovoucí desetinnou čárkou implementují C++ verze [fpclassify –](fpclassify.md) funkcí CRT pro typy s plovoucí desetinnou čárkou. Argument *x* je vyhodnocen a klasifikace je vrácena jako jedna z těchto konstant, definována v Math. h:

|Value|Popis|
|-----------|-----------------|
| **FP_NAN** | Tiché, signalizace nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizovaná nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná hodnota subnormálního (Denormalizovaná) |
| **FP_ZERO** | Kladná nebo záporná nulová hodnota |

Další podrobnosti můžete použít ve funkcích [_fpclass](fpclass-fpclassf.md) specifických pro společnost Microsoft. Pro přenositelnost použijte funkci [fpclassify –](fpclassify.md) .

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto primitivy s plovoucí desetinnou čárkou přijímají ukazatel na hodnotu *px* s plovoucí desetinnou čárkou a hodnotu exponentu *exp*a odstraní zlomkovou část hodnoty s plovoucí desetinnou čárkou pod daným exponentem, pokud je to možné. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnotě v *px* , pokud se jedná o NaN nebo nekonečno, a na výstupní hodnotu v *px* v opačném případě.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto primitivní prvky s plovoucí desetinnou čárkou přijímají ukazatel na hodnotu *px* s plovoucí desetinnou čárkou a hodnotu exponentu *exp*a hodnotu v *px* podle 2<sup>*exp*</sup>, pokud je to možné. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnotě v *px* , pokud se jedná o NaN nebo nekonečno, a na výstupní hodnotu v *px* v opačném případě. Pro přenositelnost dáváte přednost funkcím [ldexp –, ldexpf – a ldexpl](ldexp.md) .

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parametry

*pexp*<br/>
Ukazatel na exponent jako integrální typ.

*px*<br/>
Ukazatel na argument s plovoucí desetinnou čárkou.

### <a name="remarks"></a>Poznámky

Tyto primitivní prvky s plovoucí desetinnou čárkou rozdělují hodnotu s plovoucí desetinnou čárkou, na kterou odkazuje *px* na mantisa (Mantis) a exponent, pokud je to možné. Mantisa se škáluje tak, že absolutní hodnota je větší než nebo rovna 0,5 a menší než 1,0. Exponent je hodnota *n*, kde je původní hodnota s plovoucí desetinnou čárkou rovna mantisa krátě zvětšené 2<sup>*n*</sup>. Celočíselný exponent *n* je uložený v umístění, na které odkazuje *pexp*. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnotě v *px* , pokud se jedná o NaN nebo nekonečno, a na výstupní hodnotě v opačném případě. Pro přenositelnost dáváte přednost funkci [frexp –, frexpf – a frexpl](frexp.md) .

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

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
Ukazatel na argument s plovoucí desetinnou čárkou.

*exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto primitivy s plovoucí desetinnou čárkou vytvoří hodnotu s plovoucí desetinnou čárkou v umístění, na které je odkazováno v *px* rovném *y* * 2<sup>*exp*</sup>. Vrácená hodnota je výsledkem **fpclassify –** na vstupní hodnotě v *y* , pokud se jedná o NaN nebo nekonečno a výstupní hodnotu v *px* v opačném případě. Pro přenositelnost dáváte přednost funkcím [ldexp –, ldexpf – a ldexpl](ldexp.md) .

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*PS*<br/>
Ukazatel na bitovou reprezentaci hodnoty s plovoucí desetinnou čárkou vyjádřenou jako pole **krátkého** **nepodepsaného znaménka** .

### <a name="remarks"></a>Poznámky

Tyto primitivy s plovoucí desetinnou čárkou normalizují zlomkovou část hodnoty s plovoucí desetinnou čárkou a upraví *charakteristiky*nebo posunuté exponenty tak, aby odpovídaly. Hodnota je předána jako bitová reprezentace typu s plovoucí `_double_val`desetinnou čárkou, která je převedena na pole **bez znaménka** **short** pomocí, `_ldouble_val`nebo `_float_val` typu punning Union deklarovaného v Math. h. Návratová hodnota je výsledkem **fpclassify –** na vstupní hodnoty s plovoucí desetinnou čárkou, pokud se jedná o NaN nebo nekonečno a na výstupní hodnotě v opačném případě.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*stolní*<br/>
Ukazatel na tabulku konstantních koeficientů pro polynom.

*n*<br/>
Pořadí polynomu k vyhodnocení.

### <a name="remarks"></a>Poznámky

Tyto primitivy s plovoucí desetinnou čárkou vrací vyhodnocení *x* ve polynomu *n* , jejichž součinitele jsou reprezentovány odpovídajícími konstantními hodnotami v *tabulce*. Například pokud *tabulka*\[0] = 3,0, *tabulka*\[1] = 4,0, *tabulka*\[2] = 5,0 a *n* = 2, představuje polynom 5.0 x<sup>2</sup> + 4.0 x + 3,0. Pokud se tato polynom hodnotí pro *x* z 2,0, výsledek je 31,0. Tyto funkce se nepoužívají interně.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

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
Příznak, který řídí základ pro použití, 0 pro základní *e* a nenulovou hodnotu pro základní 10.

### <a name="remarks"></a>Poznámky

Tyto primitivní funkce s plovoucí desetinnou čárkou Vrátí přirozený protokol *x*, LN (*x*) nebo protokolu<sub>*e*</sub>(*x*), pokud je *base_flag* 0. Vrátí protokolový základ 10 z *x*nebo protokol<sub>10</sub>(*x*), pokud *base_flag* není nula. Tyto funkce se nepoužívají interně. Pro přenositelnost, preferovat protokoly funkcí [, logf –, logl, log10 –, log10f – a log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkce s plovoucí desetinnou čárkou.

*-*<br/>
Časový posun od 0, 1, 2 nebo 3, který se má použít `sin`k `cos`vytváření `-sin`výsledků, `-cos` , a.

### <a name="remarks"></a>Poznámky

Tyto primitivy s plovoucí desetinnou čárkou vrací sinus posunu x *kvadrantem* modulo 4. Efektivně Vrátí sinus, kosinus,-sinus a-kosinus hodnoty *x* , pokud je v případě *, že modulo* 4 je 0, 1, 2 nebo 3, v uvedeném pořadí. Tyto funkce se nepoužívají interně. Pro přenositelnost můžete upřednostnit funkce [Sin, sinf –, Sinl](sin-sinf-sinl.md), [cos, cosf – a cosl](cos-cosf-cosl.md) .

## <a name="requirements"></a>Požadavky

Header: \<Math. h >

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp –, frexpf –, frexpl](frexp.md)<br/>
[ldexp –, ldexpf – a ldexpl](ldexp.md)<br/>
[log, logf –, logl, log10 –, log10f –, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
