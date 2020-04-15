---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348524"
---
# <a name="_controlfp_s"></a>_controlfp_s

Získá a nastaví slovo ovládacího prvku s plovoucí desetinnou táhou. Tato verze [_control87, \__controlfp, _control87_2](control87-controlfp-control87-2.md) obsahuje vylepšení zabezpečení, jak je popsáno v části [Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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
Aktuální hodnota bitu ctrl-word.

*newControl*<br/>
Nové hodnoty bitu řídicího slova.

*Vlastnost maska*<br/>
Maska pro nové bity řídicího slova, které chcete nastavit.

## <a name="return-value"></a>Návratová hodnota

Nula, pokud je **úspěšná,** nebo kód chybné hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **_controlfp_s** je platforma nezávislé a bezpečnější verze **_control87**, který získá slovo ovládacího prvku s plovoucí desetinnou tištěnou do adresy, která je uložena v *currentControl* a nastaví ji pomocí *newControl*. Bity v hodnotách označují stav řízení s plovoucí desetinnou desetinnou tísní. Stav řízení s plovoucí desetinnou desetinnou desetinnou desetinnou a rychlou s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou mez í v závislosti na platformě umožňuje programu změnit režimy přesnosti, zaokrouhlení a nekonečna v matematickém balíčku s plovoucí desetinnou desetinnou desetinnou desetinnou. Můžete také použít **_controlfp_s** maskovat nebo odmaskovat výjimky s plovoucí desetinnou tálicí.

Pokud je hodnota *masky* rovna 0, **_controlfp_s** získá řídicí slovo s plovoucí desetinnou desetinnou a uloží načtenou hodnotu v *currentControl*.

Pokud je *maska* nenulová, je nastavena nová hodnota pro řídicí slovo: Pro libovolný bit, který je nastaven (tj. rovno 1) v *masce*, odpovídající bit v *novém* se používá k aktualizaci řídicího slova. Jinými slovy, *fpcntrl* = ((*fpcntrl* & ~*maska)*&#124; (*newControl* & *maska*)), kde *fpcntrl* je plovoucí-bod ovládacího slova. V tomto scénáři *currentControl* je nastavena na hodnotu po dokončení změny; není stará hodnota bitu řídicího slova.

> [!NOTE]
> Ve výchozím nastavení knihovny za běhu maskují všechny výjimky s plovoucí desetinnou tácek.

**_controlfp_s** je téměř totožný **s funkcí _control87** na platformách Intel (x86), x64 a ARM. Pokud cílíte na platformy x86, x64 nebo ARM, můžete použít **_control87** nebo **_controlfp_s**.

Rozdíl mezi **_control87** a **_controlfp_s** spočine na to, jak zacházejí s denormálními hodnotami. Pro platformy Intel (x86), x64 a ARM může **_control87** nastavit a vymazat masku výjimky DENORMAL OPERAND. **_controlfp_s** nezmění masku výjimky DENORMÁLNÍ OPERAND. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Možné hodnoty konstanty masky (*maska*) a nové řídicí hodnoty *(newControl)* jsou uvedeny v následující tabulce Hexadecimálních hodnot. Použijte přenosné konstanty uvedené níže (**_MCW_EM**, **_EM_INVALID**a tak dále) jako argumenty pro tyto funkce, nikoli explicitní dodávání šestnáctkových hodnot.

Platformy odvozené od Intelu (x86) podporují vstupní a výstupní hodnoty DENORMAL v hardwaru. Chování x86 je zachovat hodnoty DENORMAL. Platforma ARM a platformy x64, které mají podporu SSE2, umožňují vyprázdnění operandů DENORMAL a výsledků nebo vynucenou nulou. Funkce **_controlfp_s**, **_controlfp**a **_control87** poskytují masku pro změnu tohoto chování. Následující příklad ukazuje použití této masky:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM se **funkce _controlfp_s** vztahuje na registr FPSCR. Na architekturách x64 je ovlivněno pouze řídicí slovo SSE2, které je uloženo v registru MXCSR. Na platformách Intel (x86) **_controlfp_s** ovlivňuje řídicí slova pro x87 a SSE2, pokud je k dispozici. Je možné, že dvě kontrolní slova jsou vzájemně nekonzistentní (například z důvodu předchozího volání [__control87_2);](control87-controlfp-control87-2.md) Pokud je nesoulad mezi dvěma řídicími slovy, **_controlfp_s** nastaví **příznak EM_AMBIGUOUS** v *currentControl*. Toto je upozornění, že vrácené řídicí slovo nemusí přesně představovat stav obou řídicích slov s plovoucí desetinnou desetinnou tágou.

Na architektury ARM a x64 není podporována změna režimu nekonečna nebo přesnosti s plovoucí desetinnou desetinnou desetinnou tázkem. Pokud je na platformě x64 použita maska řízení přesnosti, funkce vyvolá kontrolní výraz a je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md).

Pokud maska není správně nastavena, tato funkce generuje neplatnou výjimku parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **funkce EINVAL** a nastaví **errno** na **EINVAL**.

Tato funkce je ignorována při použití [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) ke kompilaci, protože clr (COMMON Language runtime) podporuje pouze výchozí přesnost s plovoucí desetinnou tázkem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Konstanty a hodnoty masky

Pro **masku _MCW_EM,** vymazáním nastaví výjimku, která umožňuje výjimku hardwaru; nastavení skryje výjimku. Pokud dojde k **_EM_UNDERFLOW** nebo **_EM_OVERFLOW,** není vyvolána žádná výjimka hardwaru, dokud není spuštěna další instrukce s plovoucí desetinnou desetinnou desetinnou thodem. Chcete-li vygenerovat výjimku hardwaru bezprostředně po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, zavolejte instrukce MASM FWAIT.

|Maska|Šestnáctková hodnota|Trvalé|Šestnáctková hodnota|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Denormální kontrola)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (maska výjimky přerušení)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (infinity ovládání)<br /><br /> (Není podporováno na platformách ARM nebo x64.)|0x000400000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x000400000<br /><br /> 0x00000000|
|**_MCW_RC** (řízení zaokrouhlení)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Přesné ovládání)<br /><br /> (Není podporováno na platformách ARM nebo x64.)|0x000300000|**_PC_24** (24 bitů)<br /><br /> **_PC_53** (53 bitů)<br /><br /> **_PC_64** (64 bitů)|0x00020000<br /><br /> 0x000100000<br /><br /> 0x00000000|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
