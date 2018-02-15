---
title: "_control87, _controlfp, __control87_2 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2405b569c7e7accb828ba7052a9ea9fae125f0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2
Získá a nastaví s plovoucí desetinnou čárkou řídicího slova. Bezpečnější verzi `_controlfp` je k dispozici, najdete v části [_controlfp_s –](../../c-runtime-library/reference/controlfp-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `new`  
 Nové hodnoty bit řídicího slova.  
  
 `mask`  
 Maska pro novou službu bits řídicího slova nastavit.  
  
 `x86_cw`  
 Zadá řídicího slova pro x87 jednotku s plovoucí desetinnou čárkou. Předejte 0 (`NULL`) nastavit jenom SSE2 řídicího slova.  
  
 `sse2_cw`  
 Řízení aplikace word pro jednotku SSE s plovoucí desetinnou čárkou. Předejte 0 (`NULL`) Chcete-li nastavit pouze x87 řízení aplikace word.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pro `_control87` a `_controlfp`, bity v hodnotě vrátil znamenat s plovoucí desetinnou čárkou řízení stavu. Pro dokončení definice bitů, které se vrátí pomocí `_control87`, najdete v části FLOAT. H.  
  
 Pro `__control87_2`, návratová hodnota je 1, která označuje úspěch.  
  
## <a name="remarks"></a>Poznámky  
 `_control87` Funkce získá a nastaví s plovoucí desetinnou čárkou řídicího slova. S plovoucí desetinnou čárkou řídicího slova umožňuje program, který chcete změnit přesnost, zaokrouhlení a infinity režimy v balíčku s plovoucí desetinnou čárkou matematické, v závislosti na platformu. Můžete také použít `_control87` maskování nebo odmaskujte s plovoucí desetinnou čárkou výjimky. Pokud hodnota `mask` rovná 0, `_control87` získá s plovoucí desetinnou čárkou řídicího slova. Pokud `mask` je nenulové hodnoty, nastavena novou hodnotu řídicího slova: pro všechny verze, který je na (který je rovno 1) v `mask`, příslušné bity `new` se používá k aktualizaci řídicího slova. Jinými slovy `fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`)) kde `fpcntrl` je s plovoucí desetinnou čárkou řídicího slova.  
  
> [!NOTE]
>  Ve výchozím nastavení masku běhové knihovny všechny výjimky s plovoucí desetinnou čárkou.  
  
 `_controlfp` je nezávislé na platformě, přenosné verze `_control87`. Je téměř shodná `_control87` funkce na Intel (x86), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]a platformy ARM. Pokud cílíte x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], nebo ARM platformy, použijte `_control87` nebo `_controlfp`.  
  
 Rozdíl mezi `_control87` a `_controlfp` je v tom, jak se považovat DENORMAL hodnoty. Pro technologii Intel (x86) [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]a platformy ARM `_control87` můžete nastavit a vymazat maska DENORMAL OPERAND výjimka. `_controlfp` Maska výjimka DENORMAL OPERAND nelze změnit. Tento příklad ukazuje rozdíl:  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 Možné hodnoty pro maska konstanta (`mask`) a nové hodnoty ovládacího prvku (`new`) jsou uvedené v následující tabulce šestnáctkové hodnoty. Pomocí přenosného konstanty uvedené níže (`_MCW_EM`, `_EM_INVALID`, a tak dále) jako argumenty pro tyto funkce místo zadávání hexadecimální hodnoty explicitně.  
  
 Intel (x86) odvozené platformy podporují DENORMAL vstupní a výstupní hodnoty v hardwaru. X86 chování je zachování DENORMAL hodnoty. Platforma ARM a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy, které mají podporu SSE2 povolit DENORMAL operandy a výsledky vyprázdněny, nebo na nulu. `_controlfp` a `_control87` funkce zadejte masku toto chování změnit. Následující příklad ukazuje použití tuto masku.  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 Na platformách ARM `_control87` a `_controlfp` funkce se týkají FPSCR registrace. Na [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, pouze řídicího slova SSE2, která je uložená v MXCSR registrace vliv. Na platformách Intel (x86) `_control87` a `_controlfp` ovlivnit slova ovládacího prvku x87 a SSE2, pokud je k dispozici. Funkce `__control87_2` umožňuje x87 a SSE2 s plovoucí desetinnou čárkou jednotky pro řízení společně nebo samostatně. Pokud chcete mít vliv na obou jednotky, předejte adresy dvou celých čísel na `x86_cw` a `sse2_cw`. Pokud chcete mít vliv na jednu jednotku, předat adresu pro tento parametr, ale předat 0 (nula) pro druhý. Pokud pro jeden z těchto parametrů je předán 0, funkce nemá žádný vliv na této jednotce, s plovoucí desetinnou čárkou. Tato funkce může být užitečné v situacích, kde součástí s plovoucí desetinnou čárkou jednotka používá x87 kódu a další část kód používá SSE2 jednotka s plovoucí desetinnou čárkou. Pokud používáte `__control87_2` v jedné části programu a nastavit různé hodnoty pro ovládací prvek s plovoucí desetinnou čárkou slova a pak použijte `_control87` nebo `_controlfp` další pak manipulace s řídicího slova `_control87` a `_controlfp` může nelze vrátit jeden ovládací prvek slovo představující stav obou jednotek s plovoucí desetinnou čárkou. V takovém případě nastavte tyto funkce `EM_AMBIGUOUS` příznak ve vrácené celočíselnou hodnotu indikující, že existuje nekonzistence mezi slovy dvě řízení. Toto je upozornění, že vrácený řídicího slova nemusí přesně vyjadřovat stav obou slova plovoucí desetinné čárky ovládacího prvku.  
  
 Na ARM a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, změna režimu infinity nebo s plovoucí desetinnou čárkou přesnost není podporován. Pokud se používá maska přesnost ovládacího prvku na [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy, funkce vyvolá kontrolní výrazy a volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
> [!NOTE]
>  `__control87_2` nepodporuje ARM nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury. Pokud používáte `__control87_2` a kompilaci vašeho programu pro RAMENEM nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, kompilátor, vygeneruje se chyba.  
  
 Tyto funkce jsou ignorovány, při použití [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) kompilovat, protože modul CLR (CLR) podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.  
  
 **Hexadecimální hodnoty**  
  
 Pro `_MCW_EM` maska, vymazání maska nastaví výjimku, která umožňuje výjimky hardwaru; nastavení masky skryje výjimku. Pokud `_EM_UNDERFLOW` nebo `_EM_OVERFLOW` dojde, je vyvolána výjimka žádný hardware, dokud se spustí další instrukce s plovoucí desetinnou čárkou. Ke generování výjimek hardwaru ihned po `_EM_UNDERFLOW` nebo `_EM_OVERFLOW`, volání `FWAIT` MASM instrukcí.  
  
|Maska|Šestnáctkové hodnoty|Konstanta|Šestnáctkové hodnoty|  
|----------|---------------|--------------|---------------|  
|`_MCW_DN` (Denormal řízení)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` (Přerušení maska výjimka)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` (Infinity řízení)<br /><br /> (Není podporováno v ARM nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy.)|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` (Zaokrouhlení řízení)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` (Přesností řízení)<br /><br /> (Není podporováno v ARM nebo [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy.)|0x00030000|`_PC_24` (24 bits)<br /><br /> `_PC_53` (53 bits)<br /><br /> `_PC_64` (64bitová verze)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_control87`, `_controlfp`, `_control87_2`|\<float.h – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_clear87, _clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87, _statusfp, _statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)