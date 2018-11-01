---
title: _set_error_mode
ms.date: 11/04/2016
apiname:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 8c95ed45423b791a688f05ea30f48e188826a797
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502307"
---
# <a name="seterrormode"></a>_set_error_mode

Upraví **__error_mode** určit jiné než výchozí umístění, kde modul runtime jazyka C zapíše chybovou zprávu pro chybu, která může ukončit program.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Parametry

*mode_val*<br/>
Cíl chybové zprávy.

## <a name="return-value"></a>Návratová hodnota

Vrátí původní nastavení nebo -1, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Určuje výstupní jímky chyby tak, že nastavíte hodnotu **__error_mode**. Můžete například přesměrujte výstup do standardní chyby nebo použít **MessageBox** rozhraní API.

*Mode_val* parametr můžete nastavit na jedno z následujících hodnot.

|Parametr|Popis|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Chyba jímky se určuje podle **__app_type**.|
|**_OUT_TO_STDERR**|Chyba jímkou je standardní chyby.|
|**_OUT_TO_MSGBOX**|Chyba jímkou je okno se zprávou.|
|**_REPORT_ERRMODE**|Sestavy aktuální **__error_mode** hodnotu.|

Pokud je předána hodnota nejsou uvedeny, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_set_error_mode –** nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

Při použití s [vyhodnocení](assert-macro-assert-wassert.md), **_set_error_mode –** selhání příkazu se zobrazí v dialogovém okně a dá vám možnost výběru **Ignorovat** tlačítko, abyste mohli Pokračujte ke spuštění programu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>Příklad

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Viz také:

[assert Macro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
