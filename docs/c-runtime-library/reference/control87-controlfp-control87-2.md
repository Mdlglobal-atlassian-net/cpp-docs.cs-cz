---
title: _control87, _controlfp, __control87_2
ms.date: 08/29/2019
api_name:
- _control87
- _controlfp
- __control87_2
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
ms.openlocfilehash: 15700a5dabfbc3f8915e251bd8b9270f8f9c1a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942908"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87, _controlfp, __control87_2

Získá a nastaví řídicí slovo s plovoucí desetinnou čárkou. K dispozici je bezpečnější verze **_controlfp** ; viz [_controlfp_s](controlfp-s.md).

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

*New*\
Nové bitové hodnoty řídicího slova.

*zrušit*\
Maska pro nové bity řídicího slova, které se mají nastavit

*x86_cw*\
Vyplněno pomocí řídicího slova pro jednotku s plovoucí desetinnou čárkou x87. Chcete-li nastavit pouze řídicí slovo SSE2, předejte 0 (**null**).

*sse2_cw*\
Řídicí slovo pro jednotku s plovoucí desetinnou čárkou SSE Chcete-li nastavit pouze řídicí slovo x87, předejte 0 (**null**).

## <a name="return-value"></a>Návratová hodnota

V případě **_control87** a **_controlfp**určuje počet vrácených bitů v hodnotě stav ovládacího prvku s plovoucí desetinnou čárkou. Úplnou definici bitů, které jsou vráceny nástrojem **_control87**, naleznete v tématu float. Y.

Pro **__control87_2**je návratová hodnota 1, což indikuje úspěch.

## <a name="remarks"></a>Poznámky

Funkce **_control87** získá a nastaví řídicí slovo s plovoucí desetinnou čárkou. Řídicí slovo s plovoucí desetinnou čárkou umožňuje programu změnit přesnost, zaokrouhlování a režimy nekonečno v závislosti na platformě. **_Control87** můžete použít také k maskování nebo zrušení maskování výjimek s plovoucí desetinnou čárkou. Pokud je hodnota *masky* rovna 0, **_control87** získá řídicí slovo s plovoucí desetinnou čárkou. Pokud je *Maska* nenulová, je nastavena nová hodnota pro řídicí slovo: Pro každý bit, který je zapnut (tj. je rovno 1) v *masce*, se k aktualizaci řídicího slova používá odpovídající bit v *New* . Jinými slovy **fpcntrl** = ((**fpcntrl** & ~*Mask*) &#124; (*Nová* & *Maska*)), kde **fpcntrl** je řídicí slovo s plovoucí desetinnou čárkou.

> [!NOTE]
> Ve výchozím nastavení maskují knihovny run-time všechny výjimky s plovoucí desetinnou čárkou.

**_controlfp** je přenosná verze **_control87** nezávislá na platformě, která je téměř totožná s funkcí **_control87** . Pokud je váš kód cílen na více než jednu platformu, použijte **_controlfp** nebo **_controlfp_s**. Rozdíl mezi **_control87** a **_controlfp** je ve způsobu, jakým zpracovává destandardní hodnoty. Pro platformy x86, x64, ARM a ARM64 může **_control87** nastavit a vymazat masku výjimky denormálního operandu. **_controlfp** neupravuje masku výjimky denormálního operandu. Tento příklad ukazuje rozdíl:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Možné hodnoty pro konstantu masky (*Maska*) a nové hodnoty ovládacího prvku (*nové*) jsou uvedeny v tabulce řídicích a hodnotových slov. Použijte přenosné konstanty uvedené níže ( **_MCW_EM**, **_EM_INVALID**a tak dále) jako argumenty pro tyto funkce místo toho, aby explicitně poskytovaly hexadecimální hodnoty.

Platformy Intel x86 podporují denormální vstupní a výstupní hodnoty v hardwaru. Chování x86 je zachovat hodnoty destandardní. Platformy ARM a ARM64 a platformy x64, které mají podporu SSE2, umožňují povolit vyprázdnit normální operandy a výsledky, které mají být vyprázdněny, nebo vynuceně nula. Funkce **_controlfp** a **_control87** poskytují masku pro změnu tohoto chování. Následující příklad demonstruje použití této masky.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Na platformách ARM a ARM64 se funkce **_control87** a **_controlfp** vztahují na registraci FPSCR. Na platformách x64 je ovlivněno pouze řídicí slovo SSE2, které je uloženo v registru MXCSR. Na platformách x86 **_control87** a **_controlfp** ovlivňují řídicí slova pro x87 i SSE2, pokud jsou k dispozici.

Funkce **__control87_2** umožňuje, aby byly jednotky s plovoucí desetinnou čárkou X87 a SSE2 řízeny společně nebo samostatně. Aby bylo možné ovlivnit oba jednotky, předejte adresy dvou celých čísel do **x86_cw** a **sse2_cw**. Pokud chcete mít vliv pouze na jednu jednotku, předejte adresu pro tento parametr, ale předejte 0 (**null**) pro druhý. Je-li hodnota 0 předána pro jeden z těchto parametrů, funkce nemá žádný vliv na tuto jednotku s plovoucí desetinnou čárkou. Je užitečná v případě, že část kódu používá jednotku s plovoucí desetinnou čárkou x87 a jiná část používá jednotku s plovoucí desetinnou čárkou SSE2.

Použijete-li **__control87_2** k nastavení různých hodnot pro kontrolní slova s plovoucí desetinnou čárkou, pak **_control87** nebo **_controlfp** nemusí být schopni vrátit jedno řídicí slovo, které představuje stav obou jednotek s plovoucí desetinnou čárkou. V takovém případě tyto funkce nastaví příznak **EM_AMBIGUOUS** v vrácené celočíselné hodnotě tak, aby označoval nekonzistenci mezi dvěma řídicími slovy. Příznak **EM_AMBIGUOUS** je upozornění, že vrácené řídicí slovo nemusí přesně reprezentovat stav obou slov ovládacího prvku s plovoucí desetinnou čárkou.

Na platformách ARM, ARM64 a x64 se změna režimu nekonečna nebo přesnost s plovoucí desetinnou čárkou nepodporuje. Pokud je na platformě x64 použita maska ovládacího prvku Precision, funkce vyvolá kontrolní výraz a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** se nepodporuje na platformách ARM, ARM64 a x64. Pokud používáte **__control87_2** a zkompilujete program pro platformy ARM, ARM64 nebo x64, kompilátor vygeneruje chybu.

Tyto funkce jsou ignorovány při použití možnosti [/CLR (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) ke kompilaci. Modul CLR (Common Language Runtime) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.

### <a name="control-word-masks-and-values"></a>Řídicí masky a hodnoty slov

V případě masky **_MCW_EM** je zrušením masky nastavena výjimka, která umožňuje výjimku hardwaru; nastavení masky skrývá výjimku. Pokud dojde k **_EM_UNDERFLOW** nebo **_EM_OVERFLOW** , není vyvolána žádná výjimka hardwaru, dokud nebude provedena další instrukce s plovoucí desetinnou čárkou. Chcete-li vygenerovat hardwarovou výjimku hned po **_EM_UNDERFLOW** nebo **_EM_OVERFLOW**, zavolejte instrukci **FWAIT** MASM.

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
|**_control87**, **_controlfp**, **_control87_2**|\<float. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)\
[_clear87, _clearfp](clear87-clearfp.md)\
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
