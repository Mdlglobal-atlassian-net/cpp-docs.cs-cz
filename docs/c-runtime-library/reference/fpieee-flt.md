---
title: "_fpieee_flt – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88d05d4d8c7f403cc2702c5a0ec3b2af840bd320
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fpieeeflt"></a>_fpieee_flt
Vyvolá obslužnou rutinu depeše uživatelem definované výjimky plovoucí desetinné čárky IEEE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fpieee_flt(   
   unsigned long excCode,  
   struct _EXCEPTION_POINTERS *excInfo,  
   int handler(_FPIEEE_RECORD *)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `excCode`  
 Kód výjimky.  
  
 `excInfo`  
 Ukazatel na strukturu systému Windows NT výjimka informace.  
  
 `handler`  
 Ukazatel na rutiny obslužných rutin depeše IEEE uživatele.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota `_fpieee_flt` je hodnoty vrácené `handler`. Jako takový rutiny filtru IEEE může být používány kromě klauzule mechanismus strukturované zpracování výjimek (SEH).  
  
## <a name="remarks"></a>Poznámky  
 `_fpieee_flt` Funkce vyvolá obslužnou rutinu depeše uživatelem definované výjimky plovoucí desetinné čárky IEEE a poskytuje všechny potřebné informace. Tato rutina slouží jako filtr výjimek v SEH mechanismus, který vyvolá vlastní IEEE obslužná rutina výjimky Pokud je to nezbytné.  
  
 `_FPIEEE_RECORD` Struktuře, které jsou definované v Fpieee.h, obsahuje informace týkající se výjimku IEEE s plovoucí desetinnou čárkou. Tato struktura je předán obslužná rutina uživatelem definované depeše podle `_fpieee_flt`.  
  
|_Fpieee_record – pole|Popis|  
|----------------------------|-----------------|  
|`unsigned int RoundingMode`, `unsigned int Precision`|Tato pole obsahují informace o prostředí s plovoucí desetinnou čárkou v době, že se vyskytla výjimka.|  
|`unsigned int Operation`|Určuje typ operace, která způsobila, že depeše. Pokud je typ porovnání (`_FpCodeCompare`), můžete zadat jednu z speciální `_FPIEEE_COMPARE_RESULT` hodnoty (podle definice v Fpieee.h) ve `Result.Value` pole. Typ převodu (`_FpCodeConvert`) označuje, že depeše došlo k chybě během operace převody plovoucí desetinné čárky. Můžete si prohlédnout `Operand1` a `Result` typy určit typ převodu Probíhá pokus o provedení.|  
|`_FPIEEE_VALUE Operand1`, `_FPIEEE_VALUE Operand2`, `_FPIEEE_VALUE Result`|Tyto struktury znamenat typy a hodnoty navrhované výsledek a operandy:<br /><br /> `OperandValid` Příznak určující, zda je hodnota odpovídá platný.<br /><br /> `Format` Datový typ s odpovídající hodnotou. Typ formátu může být vrácena, i když odpovídající hodnota není platná.<br /><br /> `Value` Výsledek nebo operand hodnota data.|  
|`_FPIEEE_EXCEPTION_FLAGS Cause`, `_FPIEEE_EXCEPTION_FLAGS Enable`, `_FPIEEE_EXCEPTION_FLAGS Status`|_FPIEEE_EXCEPTION_FLAGS obsahuje jeden bit pole na každý typ plovoucí bodu výjimky.<br /><br /> Je korespondence mezi těmito poli a argumenty použít k maskování výjimky zadaný do [_controlfp –](../../c-runtime-library/reference/control87-controlfp-control87-2.md).<br /><br /> Přesný význam každý bit záviset na kontextu:<br /><br /> `Cause` Každá nastavit chvíli indikuje konkrétní výjimku, která byla vyvolána.<br /><br /> `Enable` Každé nastavení chvíli označuje, že je aktuálně odmaskovaná určité výjimky.<br /><br /> `Status` Každý nastavit chvíli označuje, že konkrétní výjimka je momentálně neprobíhá. To zahrnuje výjimky, které nebyly bylo vyvoláno, protože byly maskovat pomocí `_controlfp`.|  
  
 Čekající na vyřízení výjimky, které jsou zakázány se vyvolá, když je povolit. To může vést k nedefinované chování při použití `_fpieee_flt` jako filtr výjimek. Vždy volat [_clearfp –](../../c-runtime-library/reference/clear87-clearfp.md) před povolením plovoucí bodu výjimky.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fpieee_flt`|\<fpieee.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)