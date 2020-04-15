---
title: Primitiva s plovoucí desetinnou čárkou
ms.date: 4/2/2020
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
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346715"
---
# <a name="floating-point-primitives"></a>Primitiva s plovoucí desetinnou čárkou

Základní funkce specifické pro Microsoft, které se používají k implementaci některých standardních funkcí knihovny runtime C (CRT). Jsou zde zdokumentovány z důvodu úplnosti, ale nejsou doporučeny pro použití. Některé z těchto funkcí jsou označeny jako nepoužívané, protože je známo, že mají problémy s přesností, zpracování výjimek a shody s chováním IEEE-754. Existují v knihovně pouze pro zpětnou kompatibilitu. Pro správné chování, přenositelnost a dodržování standardů, přednost standardní funkce s plovoucí desetinnou tágo u těchto funkcí.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

### <a name="remarks"></a>Poznámky

Tyto základní s plovoucí desetinnou tálovou třídou implementují verze C makro [CRT fpclassify](fpclassify.md) pro typy s plovoucí desetinnou tázkem. Klasifikace argumentu *x* je vrácena jako jedna z těchto konstant definovaných v math.h:

|Hodnota|Popis|
|-----------|-----------------|
| **FP_NAN** | Tichý, signalizační nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizovaná nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná podnormální (nenormalizovaná) hodnota |
| **FP_ZERO** | Kladná nebo záporná nulová hodnota |

Další podrobnosti můžete použít _fpclass specifické pro společnost [Microsoft, _fpclassf](fpclass-fpclassf.md) funkce. Pro přenositelnost použijte makro nebo funkci [fpclassify.](fpclassify.md)

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

### <a name="remarks"></a>Poznámky

Tyto základní s plovoucí desetinnou tálovou) implementují makro nebo funkci [znaku](signbit.md) v CRT. Vrátí nenulovou hodnotu, pokud je znaménkový bit nastaven v significand (mantisa) argumentu *x*a 0, pokud není nastaven znaménkový bit.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Syntaxe

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Argumenty funkce s plovoucí desetinnou desetinnou desetinnou desetinnou a střední.

### <a name="remarks"></a>Poznámky

Tyto primitiva s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou hodnotou zaberou dva argumenty, *x* a *y*, a vrátí hodnotu, která ukazuje jejich vztah řazení, vyjádřený jako bitový nebo těchto konstant definovaných v math.h:

| Hodnota | Popis |
|------------|-----------------|
| **_FP_LT** | *x* lze považovat za méně než *y* |
| **_FP_EQ** | *x* lze považovat *y* za rovno |
| **_FP_GT** | *x* lze považovat za větší než *y* |

Tyto primitivy implementovat [isgreater, isgreaterequal, islessequal, islessvětší a isunordered](floating-point-ordering.md) makra a funkce v CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou tázkou.

### <a name="remarks"></a>Poznámky

Tyto primitivní s plovoucí desetinnou tálovou třídou implementují verze C++ funkce CRT [fpclassify](fpclassify.md) pro typy s plovoucí desetinnou tál. Argument *x* je vyhodnocen a klasifikace je vrácena jako jedna z těchto konstant definovaných v math.h:

|Hodnota|Popis|
|-----------|-----------------|
| **FP_NAN** | Tichý, signalizační nebo neurčitý NaN |
| **FP_INFINITE** | Kladné nebo záporné nekonečno |
| **FP_NORMAL** | Kladná nebo záporná normalizovaná nenulová hodnota |
| **FP_SUBNORMAL** | Kladná nebo záporná podnormální (nenormalizovaná) hodnota |
| **FP_ZERO** | Kladná nebo záporná nulová hodnota |

Další podrobnosti můžete použít _fpclass specifické pro společnost [Microsoft, _fpclassf](fpclass-fpclassf.md) funkce. Pro přenositelnost použijte funkci [fpclassify.](fpclassify.md)

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou tázkou.

*Exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto základní prvky s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou hodnotou převezmou ukazatel na hodnotu *px* s plovoucí desetinnou hodnotou a exponentní hodnotou *exp*a pokud možno odeberou zlomkovou část hodnoty s plovoucí desetinnou desetinnou hodnotou pod daným exponentem. Vrácená hodnota je výsledkem **fpclassify** na vstupní hodnotu v *px,* pokud je NaN nebo nekonečno, a na výstupní hodnotu v *px* jinak.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Ukazatel na argument s plovoucí desetinnou tázkou.

*Exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto základní prvky s plovoucí desetinnou desetinnou desetinnou hodnotou převezmou ukazatel na hodnotu *px* s plovoucí desetinnou hodnotou a exponentní hodnotu *exp*a pokud je to možné, zhodnotí hodnotu v *px* o 2<sup>*exp*</sup>. Vrácená hodnota je výsledkem **fpclassify** na vstupní hodnotu v *px,* pokud je NaN nebo nekonečno, a na výstupní hodnotu v *px* jinak. Pro přenositelnost preferujte funkce [ldexp, ldexpf a ldexpl.](ldexp.md)

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
Ukazatel na argument s plovoucí desetinnou tázkou.

### <a name="remarks"></a>Poznámky

Tyto základní s plovoucí desetinnou tištěnou položkou rozdělit hodnotu s plovoucí desetinnou desetinnou hodnotu ukázal *px* do significand (mantisa) a exponent, pokud je to možné. Velikost significand je zmenšena tak, že absolutní hodnota je větší nebo rovna 0,5 a menší než 1,0. Exponent je hodnota *n*, kde původní hodnota s plovoucí desetinnou hodnotou se rovná měřítku a krát 2<sup>*n*</sup>. Tento integer exponent *n* je uložen v umístění, na které poukazuje *pexp*. Vrácená hodnota je výsledkem **fpclassify** na vstupní hodnotu v *px,* pokud je NaN nebo nekonečno, a na výstupní hodnotu jinak. Pro přenositelnost, raději [frexp, frexpf, frexpl](frexp.md) funkce.

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parametry

*Y*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

*px*<br/>
Ukazatel na argument s plovoucí desetinnou tázkou.

*Exp*<br/>
Exponent jako integrální typ.

### <a name="remarks"></a>Poznámky

Tyto základní s plovoucí desetinnou tištěnou desetinnou tázkou vytvoří hodnotu s plovoucí desetinnou tištěnou v umístění, na které je odkazováno *hodnotou px* rovnou *y* * 2<sup>*exp*</sup>. Vrácená hodnota je výsledkem **fpclassify** na vstupní hodnotu v *y,* pokud je NaN nebo nekonečno, a na výstupní hodnotu v *px* jinak. Pro přenositelnost preferujte funkce [ldexp, ldexpf a ldexpl.](ldexp.md)

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Syntaxe

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*Ps*<br/>
Ukazatel na bitovou reprezentaci hodnoty s plovoucí desetinnou desetinnou hodnotou vyjádřenou jako pole **nepodepsané** **krátké**.

### <a name="remarks"></a>Poznámky

Tyto primitiva s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou hodnotou normalizují zlomkovou část podtékané hodnoty s plovoucí desetinnou desetinnou hodnotou a upravují *charakteristiku*nebo neobjektivní exponent tak, aby odpovídala. Hodnota je předána jako bitová reprezentace typu s plovoucí desetinnou desetinnou `_float_val` hodnotou převedená na pole **nepodepsané** **krátké** prostřednictvím `_double_val`, `_ldouble_val`nebo typ punning unie deklarované v math.h. Vrácená hodnota je výsledkem **fpclassify** na vstupní hodnotu s plovoucí desetinnou hodnotou, pokud je NaN nebo nekonečno, a na výstupní hodnotu jinak.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

*Tabulka*<br/>
Ukazatel na tabulku konstantních koeficientů pro polynom.

*N*<br/>
Pořadí polynomu k vyhodnocení.

### <a name="remarks"></a>Poznámky

Tyto primitiva s plovoucí desetinnou čárkou vrátí vyhodnocení *x* v polynomu řádu *n,* jehož koeficienty jsou reprezentovány odpovídajícími konstantními hodnotami v *tabulce*. Například pokud *tabulka*\[0] = 3.0, *tabulka*\[1] = 4.0, *tabulka*\[2] = 5.0 a *n* = 2, představuje polynom 5.0x<sup>2</sup> + 4.0x + 3.0. Pokud je tento polynom vyhodnocen pro *x* 2.0, výsledek je 31.0. Tyto funkce se nepoužívají interně.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

*base_flag*<br/>
Příznak, který řídí základnu k použití, 0 pro základní *e* a nenulová pro základnu 10.

### <a name="remarks"></a>Poznámky

Tyto primitiva s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou tázkem vrátí přirozený protokol *x*, ln(*x*) nebo log<sub>*e*</sub>(*x*), když *je base_flag* 0. Vrátí základnu protokolu 10 *x*nebo log<sub>10</sub>(*x*), pokud *je base_flag* nenulová. Tyto funkce se nepoužívají interně. Pro přenositelnost, raději funkce [log, logf, logl, log10, log10f a log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Syntaxe

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkce s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou t

*Kvadrantu*<br/>
Odsazení kvadrantu 0, 1, `sin` `cos`2 `-sin`nebo `-cos` 3 pro výrobu , , a výsledků.

### <a name="remarks"></a>Poznámky

Tyto primitiva s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou hlavou vrátí sinus *x* posunutý *kvadrantovým* modulem 4. Účinně vrátí sinus, kosinus, -sinus a -kosinus *x,* když *kvadrant* modulo 4 je 0, 1, 2 nebo 3, resp. Tyto funkce se nepoužívají interně. Pro přenositelnost, raději [hřích, sinf, sinl](sin-sinf-sinl.md), [cos, cosf, a cosl](cos-cosf-cosl.md) funkce.

## <a name="requirements"></a>Požadavky

Záhlaví: \<math.h>

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf a ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
