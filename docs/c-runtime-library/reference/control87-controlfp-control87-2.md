---
title: _control87, _controlfp, __control87_2
ms.date: 04/05/2018
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: e2ebfdc80a451ebf02563f78a62dd08618f92bcd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505869"
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2

Získá a nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou. Bezpečnější verze **_controlfp** je k dispozici; viz [_controlfp_s –](controlfp-s.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>Parametry

*new*<br/>
Nové bitové hodnoty kontrolního slova.

*Maska*<br/>
Maska pro nové bity ovládacího slova, chcete-li nastavit.

*x86_cw*<br/>
Vyplněno řídicím slovem pro x87 jednotku s plovoucí desetinnou čárkou. Předejte 0 (**NULL**) Chcete-li nastavit pouze kontrolní slovo SSE2.

*sse2_cw*<br/>
Řídicí slovo jednotky SSE s plovoucí desetinnou čárkou. Předejte 0 (**NULL**) Chcete-li nastavit pouze x87 řídicí slovo.

## <a name="return-value"></a>Návratová hodnota

Pro **_control87** a **_controlfp**, vrátí bity v hodnotě označují stav ovládacího prvku s plovoucí desetinnou čárkou. Kompletní definici bitů, které jsou vrácené **_control87**, najdete v článku plovoucí desetinnou ČÁRKOU. H.

Pro **__control87_2**, vrácená hodnota je 1, což označuje úspěch.

## <a name="remarks"></a>Poznámky

**_Control87** funkce získá a nastaví slovo ovládacího prvku s plovoucí desetinnou čárkou. Slovo ovládacího prvku s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlení a režimy nekonečna matematickém s plovoucí desetinnou čárkou balíčku, v závislosti na platformě. Můžete také použít **_control87** k maskování nebo odmaskování výjimek s plovoucí desetinnou čárkou. Pokud hodnota *maska* se rovná 0, **_control87** získá slovo s plovoucí desetinnou čárkou ovládacího prvku. Pokud *maska* je nenulová, je nastavena nová hodnota pro řídicí slovo: pro všechny bity, který je na (to je rovno 1) v *maska*, odpovídající bit v *nové* slouží k aktualizaci ovládacího prvku aplikace Word. Jinými slovy **fpcntrl** = ((**fpcntrl** & ~*maska*) &#124; (*nové* & *maska*)) kde **fpcntrl** je slovo s plovoucí desetinnou čárkou ovládacího prvku.

> [!NOTE]
> Ve výchozím nastavení běhové knihovny maskují všechny výjimky s plovoucí desetinnou čárkou.

**_controlfp** je platformě nezávislá, přenosná verze **_control87**. Je téměř shodná **_control87** funkce na x86 x64 a ARM platformy. Pokud cílíte na platformy ARM, x64 nebo x86, použijte **_control87** nebo **_controlfp**.

Rozdíl mezi **_control87** a **_controlfp** je v tom, jak zachází s hodnotami DENORMAL. Pro x86 x64 a ARM platformy **_control87** nastavit a zrušit masku výjimka DENORMAL OPERAND. **_controlfp** neupraví masku výjimky DENORMAL OPERAND. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Možné hodnoty pro konstantu masky (*maska*) a nové hodnoty ovládacího prvku (*nové*) jsou uvedeny v následující tabulce šestnáctkových hodnot. Použijte přenosné konstanty uvedené níže (**_MCW_EM**, **_EM_INVALID**a tak dále) jako argumenty pro tyto funkce místo poskytování šestnáctkových hodnot explicitně.

X86 platformy odvozené od platformy Intel podporují DENORMAL vstupní a výstupní hodnoty v hardwaru. X86 chování je zachovat hodnoty DENORMAL. Platforma ARM a x64 podporu platformy, které mají SSE2 povolují operandy DENORMAL a výsledky se nebo na hodnotu nula. **_Controlfp** a **_control87** funkce poskytují masku ke změně tohoto chování. Následující příklad ukazuje použití této masky.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM **_control87** a **_controlfp** funkce se týkají registru FPSCR. Na x64 architektury, pouze kontrolní slovo SSE2, která je uložena v registru MXCSR je ovlivněno. Na x86 platformy, **_control87** a **_controlfp** ovlivňují řídicí slova pro x87 i SSE2, pokud jsou k dispozici. Funkce **__control87_2** umožňuje x87 a jednotek s plovoucí desetinnou čárkou SSE2 k společně nebo samostatně. Pokud chcete ovlivnit obě jednotky, předejte adresy dvou celých čísel na **x86_cw** a **sse2_cw**. Pokud chcete mít vliv na jednu jednotku, předejte adresu pro tento parametr, ale předejte 0 (**NULL**) pro ostatní. Je-li 0 předána pro jeden z těchto parametrů, funkce nemá žádný vliv na tuto jednotku s plovoucí desetinnou čárkou. Tato funkce může být užitečné v situacích, kdy část kódu používá x87 s plovoucí desetinnou čárkou jednotky a jiná část kódu používá jednotku s plovoucí desetinnou čárkou SSE2. Pokud používáte **__control87_2** v jedné části programu a nastavte různé hodnoty s plovoucí desetinnou čárkou řídicí slova a pak použít **_control87** nebo **_controlfp** pro další pracovat s řídicím slovem, pak **_control87** a **_controlfp** může být schopny vrátit jedno řídicí slovo představující stav obou jednotek s plovoucí desetinnou čárkou. V takovém případě tyto funkce nastaví **EM_AMBIGUOUS** příznak ve vrácené celočíselné hodnotě k označení, že existuje nekonzistence mezi dvěma řídicími slovy. Toto je upozornění, že vrácené řídicí slovo nemusí přesně reprezentovat stav obou slova s plovoucí desetinnou čárkou ovládacího prvku.

ARM a x64 architektury, změna režimu nekonečno ani přesnost s plovoucí desetinnou čárkou se nepodporuje. Pokud se maska ovládacího prvku přesnosti používá na x64 platformy, funkce vyvolá kontrolní výraz a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** není podporován ARM nebo x64 architektury. Pokud používáte **__control87_2** a zkompilujete program pro ARM nebo x64 architektury, kompilátor vygeneruje chybu.

Tyto funkce jsou ignorovány, pokud používáte [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) zkompilovat, protože modul CLR (CLR) podporuje pouze základní přesnost s plovoucí desetinnou čárkou.

**Šestnáctkové hodnoty**

Pro **_MCW_EM** maska zrušení masky nastaví výjimku, která povoluje výjimku hardwaru; nastavení masky skryje výjimku. Pokud **_EM_UNDERFLOW** nebo **_EM_OVERFLOW** dochází, není vyvolána žádná výjimka hardwaru, dokud je proveden další pokyn s plovoucí desetinnou čárkou. Chcete-li vygenerovat hardwarovou výjimku ihned po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, zavolejte **FWAIT** instrukci MASM.

|Maska|Šestnáctková hodnota|Konstanta|Šestnáctková hodnota|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (ovládací prvek denormal)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (přerušení masku výjimky)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (ovládací prvek nekonečno)<br /><br /> (Není podporováno na ARM nebo x64] platformy.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (ovládací prvek zaokrouhlení)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (ovládací prvek přesnost)<br /><br /> (Není podporován na ARM nebo x64 platformy.)|0x00030000|**_PC_24** (24 bitů)<br /><br /> **_PC_53** (53 bitů)<br /><br /> **_PC_64** (64 bitů)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_control87 –**, **_controlfp**, **_control87_2**|\<float.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cntrl87.c
// processor: x86
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87;

    // Show original x87 control word and do calculation.
    control_word_x87 = __control87_2(0, 0,
                                     &control_word_x87, 0);
    printf( "Original: 0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    control_word_x87 = __control87_2(_PC_24, MCW_PC,
                                     &control_word_x87, 0);
    printf( "24-bit:   0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,
                                     &control_word_x87, 0 );
    printf( "Default:  0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0001
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0x0001
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x0001
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
