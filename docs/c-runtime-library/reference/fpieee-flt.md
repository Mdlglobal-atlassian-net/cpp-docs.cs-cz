---
title: _fpieee_flt – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 412eef6e3999c18901792643fa7a57ce18d19520
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403362"
---
# <a name="fpieeeflt"></a>_fpieee_flt

Vyvolá obslužnou rutinu depeše uživatelem definované výjimky plovoucí desetinné čárky IEEE.

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
Ukazatel na strukturu systému Windows NT výjimka informace.

*obslužné rutiny*<br/>
Ukazatel na rutiny obslužných rutin depeše IEEE uživatele.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota **_fpieee_flt –** je hodnoty vrácené *obslužná rutina*. Jako takový rutiny filtru IEEE může být používány kromě klauzule mechanismus strukturované zpracování výjimek (SEH).

## <a name="remarks"></a>Poznámky

**_Fpieee_flt –** funkce vyvolá obslužnou rutinu depeše uživatelem definované výjimky plovoucí desetinné čárky IEEE a poskytuje všechny potřebné informace. Tato rutina slouží jako filtr výjimek v SEH mechanismus, který vyvolá vlastní IEEE obslužná rutina výjimky Pokud je to nezbytné.

**_Fpieee_record –** struktuře, které jsou definované v Fpieee.h, obsahuje informace týkající se výjimku IEEE s plovoucí desetinnou čárkou. Tato struktura je předán obslužná rutina uživatelem definované depeše podle **_fpieee_flt –**.

|_Fpieee_record – pole|Popis|
|----------------------------|-----------------|
|**RoundingMode**<br/>**přesnost**|Tyto **nepodepsané** **int** obsahují informace o prostředí s plovoucí desetinnou čárkou v době se vyskytla výjimka.|
|**operace**|To **nepodepsané** **int** pole určuje typ operace, která způsobila, že depeše. Pokud je typ porovnání (**_FpCodeCompare**), můžete zadat jednu z speciální **_FPIEEE_COMPARE_RESULT** hodnoty (podle definice v Fpieee.h) ve **Result.Value** pole. Typ převodu (**_FpCodeConvert**) označuje, že depeše došlo k chybě během operace převody plovoucí desetinné čárky. Můžete si prohlédnout **Operand1** a **výsledek** typy určit typ převodu Probíhá pokus o provedení.|
|**operand1**<br/>**operand2**<br/>**výsledek**|Tyto **_FPIEEE_VALUE** struktury znamenat typy a hodnoty navrhované výsledek a operandy. Každá struktura obsahuje tato pole:<br /><br /> **OperandValid** – příznak označující, zda odpovídá hodnota je platná.<br />**Formát** – datový typ s odpovídající hodnotou. Typ formátu může být vrácena, i když odpovídající hodnota není platná.<br />**Hodnota** -výsledek nebo operand hodnotu data.|
|**Příčina**<br/>**Povolit**<br/>**Status**|**_FPIEEE_EXCEPTION_FLAGS** obsahuje jeden bit pole na každý typ plovoucí bodu výjimka. Je korespondence mezi těmito poli a argumenty použít k maskování výjimky zadaný do [_controlfp –](control87-controlfp-control87-2.md). Přesný význam každý bit záviset na kontextu:<br /><br /> **Příčina** – každá nastavit chvíli indikuje konkrétní výjimku, která byla vyvolána.<br />**Povolit** -každé chvíli nastavit označuje, že je aktuálně odmaskovaná určité výjimky.<br />**Stav** -každé chvíli nastavit označuje, že konkrétní výjimka je momentálně neprobíhá. To zahrnuje výjimky, které nebyly bylo vyvoláno, protože byly maskovat pomocí **_controlfp –**.|

Čekající na vyřízení výjimky, které jsou zakázány se vyvolá, když je povolit. To může vést k nedefinované chování při použití **_fpieee_flt –** jako filtr výjimek. Vždy volat [_clearfp –](clear87-clearfp.md) před povolením plovoucí bodu výjimky.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
