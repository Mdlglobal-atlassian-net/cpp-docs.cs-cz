---
title: _matherr – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f8cba1887fe806c3a6cfa795437d3d60ed7f31e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402322"
---
# <a name="matherr"></a>_matherr

Zpracovává matematické chyby.

## <a name="syntax"></a>Syntaxe

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parametry

*S výjimkou*<br/>
Ukazatel na strukturu obsahující informace o chybě.

## <a name="return-value"></a>Návratová hodnota

**_matherr –** vrátí hodnotu 0 indikující chybu nebo nenulovou hodnotu, čímž indikuje úspěšné provedení. Pokud **_matherr –** vrátí hodnotu 0, chybovou zprávu lze zobrazit a **errno** je nastaven na hodnotu odpovídající chyby. Pokud **_matherr –** vrátí nenulovou hodnotu, žádná chybová zpráva se zobrazí a **errno** zůstává beze změny.

Další informace o návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Matherr –** funkce zpracovává chyby generované funkce plovoucí desetinné čárky matematické knihovny. Tyto funkce volání **_matherr –** když je zjištěna chyba.

Speciální při zpracování chyb, můžete zadat různé definice **_matherr –**. Pokud používáte dynamicky propojené verzi běhové knihovny jazyka C (CRT), můžete nahradit výchozí **_matherr –** rutiny v klientovi spustitelný soubor s verzí definovaný uživatelem. Však nelze nahradit výchozí **_matherr –** rutiny v klientovi knihovny DLL knihovny CRT DLL.

Když dojde k chybě v rutině matematické **_matherr –** je volán s ukazatel na **_exception –** zadejte struktury (definované v \<math.h >) jako argument. **_Exception –** struktura obsahuje následující prvky.

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

**Typ** člen Určuje typ matematické chyby. Jde o jeden z následujících hodnot, definované v \<math.h >:

|– Makro|Význam|
|-|-|
**_DOMAIN –**|Chyba argument domény
**–**|Argument singularity
**_OVERFLOW –**|Rozsah chybu přetečení
**_PLOSS –**|Částečné ztrátě násobek.
**_TLOSS –**|Celkový počet ztrátě násobek.
**_UNDERFLOW –**|Výsledkem je, a nelze je příliš malá. (Tento stav se aktuálně nepodporuje.)

Struktura člen **název** je ukazatel na obsahující název funkce, které chybu způsobilo řetězce ukončené hodnotou null. Členové struktury **arg1** a **arg2** zadejte hodnoty, které chybu způsobilo. Pokud jenom jeden argument je zadána, je uložen v **arg1**.

Vrátí výchozí hodnota pro danou chybu **retval**. Pokud změníte návratovou hodnotu, zadejte, zda ve skutečnosti došlo k chybě.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_matherr**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
