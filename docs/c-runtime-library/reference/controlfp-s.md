---
title: _controlfp_s – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- controlfp_s
- _controlfp_s
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 559e3fcd0a4e5d7f71ff4644fa0fd58c9fb20137
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="controlfps"></a>_controlfp_s

Získá a nastaví s plovoucí desetinnou čárkou řídicího slova. Tato verze [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md) má rozšířené zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*currentControl*<br/>
Aktuální hodnota bit řídicího slova.

*newControl*<br/>
Nové hodnoty bit řídicího slova.

*Maska*<br/>
Maska pro novou službu bits řídicího slova nastavit.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, nebo **errno** hodnotu kód chyby.

## <a name="remarks"></a>Poznámky

**_Controlfp_s –** funkce je nezávislé na platformě a bezpečnější verze **_control87 –**, který získá s plovoucí desetinnou čárkou řídicího slova do adresu, která je uložená v  *currentControl* a nastaví jej pomocí *newControl*. Bity v hodnoty označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav s plovoucí desetinnou čárkou řízení umožňuje program, který chcete změnit přesnost, zaokrouhlení a infinity režimy v balíčku s plovoucí desetinnou čárkou matematické, v závislosti na platformu. Můžete také použít **_controlfp_s –** maskování nebo odmaskujte s plovoucí desetinnou čárkou výjimky.

Pokud hodnota *maska* rovná 0, **_controlfp_s –** získá s plovoucí desetinnou čárkou řídicího slova a ukládá načtené hodnoty v *currentControl*.

Pokud *maska* je nenulové hodnoty, nastavena novou hodnotu řídicího slova: pro všechny verze, který je nastavený (který je rovno 1) v *maska*, příslušné bity *nové* se používá k aktualizaci ovládacího prvku aplikace Word. Jinými slovy *fpcntrl* = ((*fpcntrl* & ~*maska*) &#124; (*newControl* & *maska* )) kde *fpcntrl* je s plovoucí desetinnou čárkou řídicího slova. V tomto scénáři *currentControl* je nastaven na hodnotu po dokončení změn; není původní hodnoty bit řídicího slova.

> [!NOTE]
> Ve výchozím nastavení masku běhové knihovny všechny výjimky s plovoucí desetinnou čárkou.

**_controlfp_s –** je téměř shodná **_control87 –** fungovat na Intel (x86), x64 a ARM platformy. Pokud volíte x86, x64 nebo ARM platformy, můžete použít **_control87 –** nebo **_controlfp_s –**.

Rozdíl mezi **_control87 –** a **_controlfp_s –** je v tom, jak se považovat denormal hodnoty. Pro technologii Intel (x86), x 64 a ARM platformy **_control87 –** můžete nastavit a vymazat maska DENORMAL OPERAND výjimka. **_controlfp_s –** nedojde ke změně maska DENORMAL OPERAND výjimka. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Možné hodnoty pro maska konstanta (*maska*) a nové hodnoty ovládacího prvku (*newControl*) jsou uvedené v následující tabulce šestnáctkové hodnoty. Pomocí přenosného konstanty uvedené níže (**_MCW_EM**, **_EM_INVALID**a tak dále) jako argumenty pro tyto funkce místo zadávání hexadecimální hodnoty explicitně.

Intel (x86) odvozené platformy podporují DENORMAL vstupní a výstupní hodnoty v hardwaru. X86 chování je zachování DENORMAL hodnoty. Platforma ARM a x64, které podporují platformy, které mají SSE2 povolit DENORMAL operandy a výsledky vyprázdněny, nebo nuceno nula. **_Controlfp_s –**, **_controlfp –**, a **_control87 –** funkce zadejte masku toto chování změnit. Následující příklad ukazuje použití tuto masku:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM **_controlfp_s –** funkce se vztahuje na FPSCR registrace. Na x64 architektury, pouze řídicího slova SSE2, která je uložená v MXCSR registrace vliv. Na platformách Intel (x86) **_controlfp_s –** ovlivňuje slova ovládacího prvku x87 a SSE2, pokud je k dispozici. Je možné pro dvě řízení slova být navzájem konzistentní (z důvodu předchozích volání [__control87_2 –](control87-controlfp-control87-2.md), například); Pokud existuje nekonzistence mezi dvěma řízení slova, **_controlfp_s –** nastaví **EM_AMBIGUOUS** příznak v *currentControl*. Toto je upozornění, že vrácený řídicího slova nemusí přesně vyjadřovat stav obou slova plovoucí desetinné čárky ovládacího prvku.

Na ARM a x64 architektury, změna režimu infinity nebo s plovoucí desetinnou čárkou přesnost nepodporuje. Pokud se používá maska přesnost ovládací prvek na x64 platformy, funkce vyvolá kontrolní výrazy a volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Pokud maska není správně nastavený, tato funkce vygeneruje výjimku neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **einval –** a nastaví **errno** k **einval –**.

Tato funkce se ignoruje, pokud používáte [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) kompilovat, protože modul CLR (CLR) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

### <a name="mask-constants-and-values"></a>Maska konstanty a hodnoty

Pro **_MCW_EM** maska, zrušením zaškrtnutí nastaví výjimku, která umožní výjimky hardwaru; jeho nastavení skryje výjimku. Pokud **_EM_UNDERFLOW** nebo **_EM_OVERFLOW** dojde, je vyvolána výjimka žádný hardware, dokud se spustí další instrukce s plovoucí desetinnou čárkou. Ke generování výjimek hardwaru ihned po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, volání FWAIT MASM instrukcí.

|Maska|Šestnáctkové hodnoty|Konstanta|Šestnáctkové hodnoty|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (denormal řízení)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (přerušení výjimka maska)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (infinity řízení)<br /><br /> (Nejsou podporovány na ARM nebo x64 platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (zaokrouhlení řízení)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (přesnost řízení)<br /><br /> (Nejsou podporovány na ARM nebo x64 platformy.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64bitová verze)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_controlfp_s**|\<float.h – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
