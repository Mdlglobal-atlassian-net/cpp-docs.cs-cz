---
title: _matherr
ms.date: 04/05/2018
api_name:
- _matherr
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 340e3b8562e1f0f564810bc63cf6bd2e87ffdf63
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952760"
---
# <a name="_matherr"></a>_matherr

Zpracovává matematické chyby.

## <a name="syntax"></a>Syntaxe

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Parametry

*výjimk*<br/>
Ukazatel na strukturu obsahující informace o chybě.

## <a name="return-value"></a>Návratová hodnota

**_matherr** vrátí 0 pro indikaci chyby nebo nenulovou hodnotu pro indikaci úspěchu. Pokud **_matherr** vrátí hodnotu 0, může se zobrazit chybová zpráva a **errno** se nastaví na vhodnou chybovou hodnotu. Pokud **_matherr** vrátí nenulovou hodnotu, nezobrazí se žádná chybová zpráva a **errno** zůstane beze změny.

Další informace o návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_matherr** zpracovává chyby generované funkcemi plovoucí desetinné čárky v knihovně Math. Tyto funkce volají **_matherr** při zjištění chyby.

Pro zpracování speciálních chyb můžete zadat jinou definici **_matherr**. Použijete-li dynamicky propojenou verzi knihovny run-time jazyka C (CRT), můžete nahradit výchozí rutinu **_matherr** ve spustitelném souboru klienta pomocí uživatelem definované verze. Nemůžete však nahradit výchozí rutinu **_matherr** v klientovi knihovny DLL CRT.

Při výskytu chyby v matematické rutině je **_matherr** volána s ukazatelem na strukturu typu **_exception** (definovaná v \<Math. h >) jako argument. Struktura **_exception** obsahuje následující prvky.

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

Člen **typu** určuje typ matematické chyby. Je to jedna z následujících hodnot, která je definována \<v Math. h >:

|– Makro|Význam|
|-|-|
| **_DOMAIN** | Chyba domény argumentu |
| **_SING** | Argument v argumentu |
| **_OVERFLOW** | Chyba rozsahu přetečení |
| **_PLOSS** | Částečná ztráta významnosti |
| **_TLOSS** | Celková ztráta významnosti |
| **_UNDERFLOW** | Výsledek je příliš malý, aby jej bylo možné znázornit. (Tato podmínka se momentálně nepodporuje.) |

**Název** člena struktury je ukazatel na řetězec zakončený hodnotou null obsahující název funkce, která způsobila chybu. Struktury členů **arg1** a **arg2** určují hodnoty, které způsobily chybu. Je-li zadán pouze jeden argument, je uložen v **arg1**.

Výchozí návratová hodnota pro danou chybu je **retval**. Změníte-li návratovou hodnotu, je nutné určit, zda skutečně došlo k chybě.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_matherr**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
