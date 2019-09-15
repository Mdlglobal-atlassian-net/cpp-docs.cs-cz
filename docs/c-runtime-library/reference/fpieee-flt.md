---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 8835a3184300f1c56f1123a09aa48cd34a387c87
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957031"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

Vyvolá uživatelsky definovanou obslužnou rutinu depeše pro výjimky s plovoucí desetinnou čárkou standardu IEEE.

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
Ukazatel na strukturu informací o výjimce systému Windows NT.

*handler*<br/>
Ukazatel na rutinu IEEE depeše v uživatelském rozhraní.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota **_fpieee_flt** je hodnota vrácená *obslužným rutinou*. V takovém případě může být rutina filtru IEEE použita v klauzuli Except mechanismu strukturovaného zpracování výjimek (SEH).

## <a name="remarks"></a>Poznámky

Funkce **_fpieee_flt** vyvolá uživatelsky definovanou obslužnou rutinu depeše pro výjimky s plovoucí desetinnou ČÁRKou standardu IEEE a poskytne jí všechny relevantní informace. Tato rutina slouží jako filtr výjimek v mechanismu SEH, který v případě potřeby vyvolá vlastní obslužnou rutinu výjimky IEEE.

Struktura **_FPIEEE_RECORD** definovaná v FPIEEE. h obsahuje informace týkající se výjimky s plovoucí desetinnou čárkou IEEE. Tato struktura je předána uživatelsky definované obslužné rutině depeše od **_fpieee_flt**.

|Pole _FPIEEE_RECORD|Popis|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Číslic**|Tato pole **bez znaménka** **int** obsahují informace o prostředí s plovoucí desetinnou čárkou v době, kdy došlo k výjimce.|
|**Operace**|Toto pole s **nepodepsaným** **int** označuje typ operace, která způsobila depeši. Pokud je typ porovnání ( **_FpCodeCompare**), můžete zadat jednu ze zvláštních hodnot **_FPIEEE_COMPARE_RESULT** (jak je definováno v FPIEEE. h) v poli **výsledek. Value** . Typ převodu ( **_FpCodeConvert**) označuje, že během operace převodu s plovoucí desetinnou čárkou došlo k depeši. Můžete se podívat na **Operand1** a typy **výsledků** a určit typ převodu, který se pokouší.|
|**Operand1**<br/>**Operand2**<br/>**výsledek**|Tyto struktury **_FPIEEE_VALUE** označují typy a hodnoty navrhovaného výsledku a operandů. Každá struktura obsahuje tato pole:<br /><br /> **OperandValid** – příznak označující, zda je hodnota reakce platná.<br />**Formát** – datový typ odpovídající hodnoty. Typ formátu může být vrácen i v případě, že odpovídající hodnota není platná.<br />**Hodnota dat** výsledku nebo operandu.|
|**Způsobit**<br/>**Enable**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** obsahuje jedno bitové pole na typ výjimky s plovoucí desetinnou čárkou. Mezi těmito poli a argumenty, které slouží k maskování výjimek dodaných do [_controlfp](control87-controlfp-control87-2.md), existuje shoda. Přesný význam každého bitu závisí na kontextu:<br /><br /> **Příčina** – každý bit nastavení označuje konkrétní vyvolanou výjimku.<br />**Enable** – každý nastavený bit označuje, že konkrétní výjimka je aktuálně odmaskována.<br />**Stav** – každý bit nastavení znamená, že konkrétní výjimka aktuálně čeká na vyřízení. To zahrnuje výjimky, které nebyly vyvolány, protože byly maskovány pomocí **_controlfp**.|

Zakázané výjimky jsou vyvolány, když je povolíte. To může mít za následek nedefinované chování při použití **_fpieee_flt** jako filtru výjimky. Před povolením výjimek s plovoucí desetinnou čárkou vždy volejte [_clearfp](clear87-clearfp.md) .

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
