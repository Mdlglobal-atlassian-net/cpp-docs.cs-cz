---
title: _controlfp_s
ms.date: 04/05/2018
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
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 0624cbfb4870ca87efebac01a8de682b588a4ca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335374"
---
# <a name="controlfps"></a>_controlfp_s

Získá a nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou. Tato verze [_control87 _controlfp, \__control87_2](control87-controlfp-control87-2.md) má rozšíření zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Aktuální hodnota řídicí slovo bit.

*newControl*<br/>
Nové bitové hodnoty kontrolního slova.

*Maska*<br/>
Maska pro nové bity ovládacího slova, chcete-li nastavit.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, nebo **errno** kód chyby hodnoty.

## <a name="remarks"></a>Poznámky

**_Controlfp_s –** funkce je nezávislá na platformě a bezpečnější verze **_control87**, který získá slovo ovládacího prvku s plovoucí desetinnou čárkou do adresy, která je uložena v  *currentControl* a nastavuje ho pomocí *newControl*. Bity v hodnotách označují stav ovládacího prvku s plovoucí desetinnou čárkou. Stav ovládacího prvku s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlení a režimy nekonečna matematickém s plovoucí desetinnou čárkou balíčku, v závislosti na platformě. Můžete také použít **_controlfp_s –** k maskování nebo odmaskování výjimek s plovoucí desetinnou čárkou.

Pokud hodnota *maska* se rovná 0, **_controlfp_s –** získá slovo s plovoucí desetinnou čárkou ovládací prvek a uloží získanou hodnotu v *currentControl*.

Pokud *maska* je nenulová, je nastavena nová hodnota pro řídicí slovo: Pro některé bit, který je nastaven (to je rovno 1) v *maska*, odpovídající bit v *nové* slouží k aktualizaci řídicího slova. Jinými slovy *fpcntrl* = ((*fpcntrl* & ~*maska*) &#124; (*newControl* & *masky* )) kde *fpcntrl* je slovo s plovoucí desetinnou čárkou ovládacího prvku. V tomto scénáři *currentControl* je nastavena na hodnotu po dokončení změny; nejde původní bitové hodnoty kontrolního slova.

> [!NOTE]
> Ve výchozím nastavení běhové knihovny maskují všechny výjimky s plovoucí desetinnou čárkou.

**_controlfp_s –** je téměř shodná **_control87** fungovat na Intel (x86) x64 a ARM platformy. Pokud cílíte na platformy ARM, x64 nebo x86, můžete použít **_control87** nebo **_controlfp_s –**.

Rozdíl mezi **_control87** a **_controlfp_s –** je v tom, jak zachází s hodnoty denormal. Pro Intel (x86), x 64 a ARM platformy **_control87** nastavit a zrušit masku výjimka DENORMAL OPERAND. **_controlfp_s –** neupraví masku výjimky DENORMAL OPERAND. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Možné hodnoty pro konstantu masky (*maska*) a nové hodnoty ovládacího prvku (*newControl*) jsou uvedeny v následující tabulce šestnáctkových hodnot. Použijte přenosné konstanty uvedené níže (**_MCW_EM**, **_EM_INVALID**, a tak dále) jako argumenty pro tyto funkce místo poskytování šestnáctkových hodnot explicitně.

(X86) platformy odvozené od platformy Intel podporují DENORMAL vstupní a výstupní hodnoty v hardwaru. X86 chování je zachovat hodnoty DENORMAL. Platforma ARM a x64 podporu platformy, které mají SSE2 povolují operandy DENORMAL a výsledky se nebo na hodnotu nula. **_Controlfp_s –**, **_controlfp**, a **_control87** funkce poskytují masku ke změně tohoto chování. Následující příklad demonstruje použití této masky:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM **_controlfp_s –** funkce se vztahuje na registru FPSCR. Na x64 architektury, pouze kontrolní slovo SSE2, která je uložena v registru MXCSR je ovlivněno. Na platformách Intel (x86) **_controlfp_s –** ovlivňuje řídicí slova pro x87 i SSE2, pokud jsou k dispozici. Je možné, dvěma řídicími slovy není konzistentní mezi sebou (z důvodu předchozího volání [__control87_2](control87-controlfp-control87-2.md), například), pokud existuje nekonzistence mezi dvěma řídicími slovy **_controlfp_s –** nastaví **EM_AMBIGUOUS** příznak v *currentControl*. Toto je upozornění, že vrácené řídicí slovo nemusí přesně reprezentovat stav obou slova s plovoucí desetinnou čárkou ovládacího prvku.

ARM a x64 architektury, změna režimu nekonečno ani přesnost s plovoucí desetinnou čárkou se nepodporuje. Pokud se maska ovládacího prvku přesnosti používá na x64 platformy, funkce vyvolá kontrolní výraz a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Pokud maska není nastavena správně, tato funkce generuje výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **EINVAL** a nastaví **errno** k **EINVAL**.

Tato funkce je ignorována, pokud použijete [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) zkompilovat, protože modul CLR (CLR) podporuje pouze základní přesnost s plovoucí desetinnou čárkou.

### <a name="mask-constants-and-values"></a>Maska konstanty a hodnoty

Pro **_MCW_EM** maska zrušení nastaví výjimku, která povoluje výjimku hardwaru; nastavení skryje výjimku. Pokud **_EM_UNDERFLOW** nebo **_EM_OVERFLOW** dochází, není vyvolána žádná výjimka hardwaru, dokud je proveden další pokyn s plovoucí desetinnou čárkou. Chcete-li vygenerovat hardwarovou výjimku ihned po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, zavolejte instrukci MASM FWAIT.

|Maska|Šestnáctková hodnota|Konstanta|Šestnáctková hodnota|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (ovládací prvek denormal)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (přerušení masku výjimky)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (ovládací prvek nekonečno)<br /><br /> (Není podporován na ARM nebo x64 platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (ovládací prvek zaokrouhlení)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (ovládací prvek přesnost)<br /><br /> (Není podporován na ARM nebo x64 platformy.)|0x00030000|**_PC_24** (24 bitů)<br /><br /> **_PC_53** (53 bitů)<br /><br /> **_PC_64** (64 bitů)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_controlfp_s**|\<float.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
