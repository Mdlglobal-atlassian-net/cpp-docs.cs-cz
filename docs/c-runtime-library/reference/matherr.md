---
title: "_matherr – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _matherr
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
apitype: DLLExport
f1_keywords:
- _matherr
- matherr
dev_langs:
- C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 843cfbbcac39af23aa6a3daaf70a786e8fa6866d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="matherr"></a>_matherr
Zpracovává matematické chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *except*  
 Ukazatel na strukturu obsahující informace o chybě.  
  
## <a name="return-value"></a>Návratová hodnota  
 _**matherr –** vrátí hodnotu 0 indikující chybu nebo nenulovou hodnotu, čímž indikuje úspěšné provedení. Pokud \_ **matherr –** vrátí hodnotu 0, chybovou zprávu lze zobrazit a `errno` je nastaven na hodnotu odpovídající chyby. Pokud \_ **matherr –** vrátí nenulovou hodnotu, žádná chybová zpráva se zobrazí a `errno` zůstává beze změny.  
  
 Další informace o návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 _**Matherr –** funkce zpracovává chyby generované funkce plovoucí desetinné čárky matematické knihovny. Tyto funkce volání \_ **matherr –** když je zjištěna chyba.  
  
 Speciální při zpracování chyb, můžete zadat různé definice _**matherr –**. Pokud používáte dynamicky propojené verzi běhové knihovny jazyka C (Msvcr90.dll), můžete nahradit výchozí \_ **matherr –** rutiny v klientovi spustitelný soubor s verzí definovaný uživatelem. Však nelze nahradit výchozí `_matherr` rutiny v klientovi knihovny DLL z Msvcr90.dll.  
  
 Když dojde k chybě v rutině matematické, _**matherr –** je volán s odkazy **_exception –** struktury (definovanou v Math.h) zadejte jako argument. **_Exception –** struktura obsahuje následující prvky.  
  
 **int – typ**  
 Typ výjimky.  
  
 **Char \*název**  
 Název funkce, kde došlo k chybě.  
  
 **dvojité arg1**, **arg2**  
 První a druhý (pokud existuje) argumenty funkce.  
  
 **dvojité retval**  
 Hodnota má být vráceným funkcí.  
  
 **Typ** Určuje typ matematické chyby. Jednu z následujících hodnot, které jsou definované v Math.h je.  
  
 `_DOMAIN`  
 Argument domény došlo k chybě.  
  
 `_SING`  
 Argument singularity.  
  
 `_OVERFLOW`  
 Rozsah chyby přetečení.  
  
 `_PLOSS`  
 Částečné ztrátě násobek.  
  
 `_TLOSS`  
 Celkový počet ztrátě násobek.  
  
 `_UNDERFLOW`  
 Výsledkem je, a nelze je příliš malá. (Tento stav se aktuálně nepodporuje.)  
  
 Struktura člen **název** je ukazatel na obsahující název funkce, které chybu způsobilo řetězce ukončené hodnotou null. Členové struktury **arg1** a **arg2** zadejte hodnoty, které chybu způsobilo. (Pokud jenom jeden argument je zadána, je uložen v **arg1**.)  
  
 Vrátí výchozí hodnota pro danou chybu **retval**. Pokud změníte návratovou hodnotu, zadejte, zda ve skutečnosti došlo k chybě.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_matherr`|\<math.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_matherr.c  
/* illustrates writing an error routine for math   
 * functions. The error function must be:  
 *      _matherr  
 */  
  
#include <math.h>  
#include <string.h>  
#include <stdio.h>  
  
int main()  
{  
    /* Do several math operations that cause errors. The _matherr  
     * routine handles _DOMAIN errors, but lets the system handle  
     * other errors normally.  
     */  
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );  
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );  
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );  
}  
  
/* Handle several math errors caused by passing a negative argument  
 * to log or log10 (_DOMAIN errors). When this happens, _matherr  
 * returns the natural or base-10 logarithm of the absolute value  
 * of the argument and suppresses the usual error message.  
 */  
int _matherr( struct _exception *except )  
{  
    /* Handle _DOMAIN errors for log or log10. */  
    if( except->type == _DOMAIN )  
    {  
        if( strcmp( except->name, "log" ) == 0 )  
        {  
            except->retval = log( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
        else if( strcmp( except->name, "log10" ) == 0 )  
        {  
            except->retval = log10( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
    }  
    printf( "Normal: " );  
    return 0;    /* Else use the default actions */  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   