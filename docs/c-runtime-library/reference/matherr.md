---
title: _matherr
ms.date: 04/05/2018
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
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: b830dc940fa2abb131f70130033d27b057412137
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156905"
---
# <a name="matherr"></a>_matherr

Matematické chyby zpracovává.

## <a name="syntax"></a>Syntaxe

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parametry

*S výjimkou*<br/>
Ukazatel na strukturu obsahující informace o chybě.

## <a name="return-value"></a>Návratová hodnota

**_matherr** vrátí hodnotu 0 označující chybu nebo nenulovou hodnotu, čímž indikuje úspěšné provedení. Pokud **_matherr** vrátí hodnotu 0, chybová zpráva je možné zobrazit a **errno** je nastavena na hodnotu odpovídající chyba. Pokud **_matherr** vrátí nenulovou hodnotu, žádná chybová zpráva se zobrazí a **errno** zůstane beze změny.

Další informace o návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Matherr** funkce zpracovává chyby generované funkce s plovoucí desetinnou čárkou matematické knihovny. Volání těchto funkcí **_matherr** při rozpoznání chyby.

Pro zpracování chyb speciální, můžete zadat jinou definici **_matherr**. Pokud používáte verzi dynamicky propojené knihovny run-time jazyka C (CRT), můžete nahradit výchozí **_matherr** rutiny v spustitelného souboru pomocí uživatelem definované verze klienta. Však nelze nahradit výchozí **_matherr** rutiny v klientovi knihovny DLL CRT knihovny DLL.

Když dojde k chybě v rutině matematické, **_matherr** je volána pomocí ukazatele na **_snímky** strukturu typu (definované v \<math.h >) jako argument. **_Snímky** struktura obsahuje následující prvky.

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

**Typ** člen Určuje typ matematické chyby. Představuje jednu z následujících hodnot podle \<math.h >:

|– Makro|Význam|
|-|-|
| **_DOMAIN** | Chyba argumentu domény |
| **_SING** | Argument singularity |
| **_OVERFLOW** | Chyba přetečení rozsahu |
| **_PLOSS** | Částečné ztrátě významu |
| **_TLOSS** | Celkový počet ke ztrátě významu |
| **_UNDERFLOW** | Výsledek je příliš malá, aby se dala vyjádřit. (Tento stav se aktuálně nepodporuje.) |

Člen struktury **název** je ukazatel na řetězec zakončený hodnotou null obsahující název funkce, která způsobila chybu. Členové struktury **arg1** a **arg2** zadejte hodnoty, které způsobily chybu. Pokud pouze jeden argument je zadána, je uložena v **arg1**.

Výchozí návratová hodnota pro danou chybu **retval**. Pokud změníte návratovou hodnotu, musí určovat, zda skutečně došlo k chybě.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_matherr**|\<math.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
