---
title: _fpieee_flt
ms.date: 04/05/2018
apiname:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 9a49ec403b1cb95407b0a366accf1d9374d9cb22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458614"
---
# <a name="fpieeeflt"></a>_fpieee_flt

Vyvolá uživatelem definované obslužné rutiny pro výjimky s plovoucí desetinnou čárkou IEEE.

## <a name="syntax"></a>Syntaxe

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Parametry

*excCode*<br/>
Kód výjimky.

*excInfo*<br/>
Ukazatel na strukturu informace výjimky Windows NT.

*Obslužná rutina*<br/>
Ukazatel na uživatele IEEE depeše obslužné rutině.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota **_fpieee_flt** je hodnoty vrácené *obslužná rutina*. V důsledku toho rutina IEEE filtru sloužící k s výjimkou klauzulí mechanismus strukturovaného zpracování výjimek (SEH).

## <a name="remarks"></a>Poznámky

**_Fpieee_flt** funkce vyvolá uživatelem definované obslužné rutiny pro výjimky s plovoucí desetinnou čárkou IEEE a poskytuje všechny relevantní informace. Tato rutina slouží jako filtr výjimek v SEH mechanismus, který vyvolá vlastní IEEE obslužná rutina výjimky v případě potřeby.

**_Fpieee_record –** struktury definované v Fpieee.h, obsahuje informace týkající se výjimky s plovoucí desetinnou čárkou IEEE. Tato struktura je předán do uživatelem definované obslužné rutiny ve **_fpieee_flt**.

|_Fpieee_record – pole|Popis|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Přesnost**|Tyto **bez znaménka** **int** pole obsahují informace o prostředí s plovoucí desetinnou čárkou v době došlo k výjimce.|
|**Operace**|To **bez znaménka** **int** pole určuje typ operace, která způsobila depeše. Pokud je typ porovnání (**_FpCodeCompare**), můžete zadat jednu zvláštní **_FPIEEE_COMPARE_RESULT** hodnoty (jak jsou definovány v Fpieee.h) v **Result.Value** pole. Typ převodu (**_FpCodeConvert**) označuje, že depeše došlo k chybě během operace s plovoucí desetinnou čárkou převodu. Můžete si prohlédnout **Operand1** a **výsledek** typy určit typ převodu Probíhá pokus o.|
|**Operand1**<br/>**Operand2**<br/>**výsledek**|Tyto **_FPIEEE_VALUE** struktury určit typy a hodnoty navrhované výsledek a operandů. Každá struktura obsahuje tato pole:<br /><br /> **OperandValid** – příznak označující, zda odpovídá hodnota je platná.<br />**Formát** – datový typ odpovídající hodnoty. Typ formátu může být vrácena, i v případě, že odpovídající hodnota není platná.<br />**Hodnota** – výsledek nebo operand hodnotu data.|
|**Příčina**<br/>**Enable**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** obsahuje jeden bitové pole za typ s plovoucí desetinnou čárkou bodu výjimku. Neexistuje shoda mezi tato pole a jsou argumenty použity k maskování výjimky zadaný pro [_controlfp](control87-controlfp-control87-2.md). Přesné význam každý bit závisí na kontextu:<br /><br /> **Příčina** – každá nastaveného bitu indikuje konkrétní výjimky, ke které došlo.<br />**Povolit** – každá nastaveného bitu indikuje, že je aktuálně odmaskovaná konkrétní výjimce.<br />**Stav** – každá nastaveného bitu indikuje, že konkrétní výjimce čeká na vyřízení. Jedná se o výjimky, které dosud bylo vyvoláno, protože byly maskovaná **_controlfp**.|

Čekajících výjimkách, které jsou zakázány jsou vyvolány, když je povolit. To může způsobit nedefinované chování při použití **_fpieee_flt** jako filtr výjimek. Vždy volat [_clearfp –](clear87-clearfp.md) před povolením výjimky s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_control87 – _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
