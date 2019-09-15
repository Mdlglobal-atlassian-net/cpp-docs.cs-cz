---
title: _controlfp_s
ms.date: 04/05/2018
api_name:
- _controlfp_s
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
ms.openlocfilehash: 0d12c139f305a3c66419a4e27905ac9f73345f4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942885"
---
# <a name="_controlfp_s"></a>_controlfp_s

Získá a nastaví řídicí slovo s plovoucí desetinnou čárkou. Tato verze [_control87, _controlfp a \__control87_2](control87-controlfp-control87-2.md) má vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Aktuální bitová hodnota řídicího slova.

*newControl*<br/>
Nové bitové hodnoty řídicího slova.

*zrušit*<br/>
Maska pro nové bity řídicího slova, které se mají nastavit

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo kód chyby **errno** hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **_controlfp_s** je nezávislý na platformě a bezpečnější verze **_control87**, která získá kontrolní slovo s plovoucí desetinnou čárkou na adresu uloženou v *CurrentControl* a nastaví ji pomocí *newControl*. Bity v hodnotách označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav ovládacího prvku s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlování a režimy nekonečno v matematickém balíčku s plovoucí desetinnou čárkou v závislosti na platformě. **_Controlfp_s** můžete použít také k maskování nebo zrušení maskování výjimek s plovoucí desetinnou čárkou.

Pokud je hodnota *masky* rovna 0, **_controlfp_s** získá řídicí slovo s plovoucí desetinnou čárkou a uloží načtenou hodnotu v *currentControl*.

Pokud je *Maska* nenulová, je nastavena nová hodnota pro řídicí slovo: Pro každý bit, který je nastaven na *masce*(tj. roven 1), se k aktualizaci řídicího slova používá odpovídající bit v *New* . Jinými slovy *fpcntrl* = ((*fpcntrl* & ~*Mask*) &#124; (*Maska* *newControl* & )), kde *fpcntrl* je řídicí slovo s plovoucí desetinnou čárkou. V tomto scénáři je *currentControl* nastaveno na hodnotu po dokončení změny; Nejedná se o starou bitovou hodnotu řídicího slova.

> [!NOTE]
> Ve výchozím nastavení maskují knihovny run-time všechny výjimky s plovoucí desetinnou čárkou.

**_controlfp_s** je téměř totožná s funkcí **_control87** na platformách Intel (x86), x64 a ARM. Pokud cílíte na platformy x86, x64 nebo ARM, můžete použít **_control87** nebo **_controlfp_s**.

Rozdíl mezi **_control87** a **_controlfp_s** je ve způsobu, jakým zpracovává destandardní hodnoty. Pro platformy Intel (x86), x64 a ARM může **_control87** nastavit a vymazat masku výjimky denormálního operandu. **_controlfp_s** neupravuje masku výjimky denormálního operandu. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Možné hodnoty pro konstantu masky (*Maska*) a nové hodnoty ovládacího prvku (*newControl*) jsou uvedeny v následující tabulce hexadecimálních hodnot. Použijte přenosné konstanty uvedené níže ( **_MCW_EM**, **_EM_INVALID**a tak dále) jako argumenty pro tyto funkce místo toho, aby explicitně poskytovaly hexadecimální hodnoty.

Platformy Intel (x86) – odvozené platformy podporují denormální vstupní a výstupní hodnoty v hardwaru. Chování x86 je zachovat hodnoty destandardní. Platforma ARM a platformy x64, které mají podporu SSE2, umožňují vyprázdnit normální operandy a výsledky, které mají být vyprázdněny, nebo musí být vynucené nula. Funkce **_controlfp_s**, **_controlfp**a **_control87** poskytují masku pro změnu tohoto chování. Následující příklad demonstruje použití této masky:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM se funkce **_controlfp_s** vztahuje na registr FPSCR. V architekturách x64 je ovlivněno pouze řídicí slovo SSE2, které je uloženo v registru MXCSR. Na platformách Intel (x86) **_controlfp_s** ovlivňuje řídicí slova pro X87 i SSE2, pokud je k dispozici. Je možné, že dvě řídicí slova budou vzájemně nekonzistentní (například kvůli předchozímu volání [__control87_2](control87-controlfp-control87-2.md)); Pokud existuje nekonzistence mezi dvěma řídicími slovy, **_controlfp_s** nastaví příznak **EM_AMBIGUOUS** v *currentControl*. Toto je upozornění, že vrácené řídicí slovo nemusí přesně reprezentovat stav obou slov ovládacího prvku s plovoucí desetinnou čárkou.

V architekturách ARM a x64 se změna režimu nekonečna nebo přesnost s plovoucí desetinnou čárkou nepodporuje. Pokud se na platformě x64 používá maska ovládacího prvku Precision, funkce vyvolá kontrolní výraz a vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Pokud maska není nastavena správně, tato funkce vygeneruje výjimku neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tato funkce **EINVAL** a nastaví **errno** na **EINVAL**.

Tato funkce se ignoruje, pokud použijete funkci [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) ke kompilaci, protože modul CLR (Common Language Runtime) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

### <a name="mask-constants-and-values"></a>Konstanty a hodnoty masky

V případě masky **_MCW_EM** se zrušením nastaví výjimka, která umožňuje hardwarovou výjimku. jeho nastavením skryje výjimku. Pokud dojde k **_EM_UNDERFLOW** nebo **_EM_OVERFLOW** , není vyvolána žádná výjimka hardwaru, dokud nebude provedena další instrukce s plovoucí desetinnou čárkou. Chcete-li vygenerovat hardwarovou výjimku hned po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, zavolejte instrukci FWAIT MASM.

|Zrušit|Šestnáctková hodnota|Konstanta|Šestnáctková hodnota|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Nestandardní ovládací prvek)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Maska výjimky přerušení)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Ovládací prvek nekonečno)<br /><br /> (Nepodporuje se na platformách ARM nebo x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Ovládací prvek zaokrouhlení)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Řízení přesnosti)<br /><br /> (Nepodporuje se na platformách ARM nebo x64.)|0x00030000|**_PC_24** (24 bitů)<br /><br /> **_PC_53** (53 bitů)<br /><br /> **_PC_64** (64 bitů)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_controlfp_s**|\<float. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
