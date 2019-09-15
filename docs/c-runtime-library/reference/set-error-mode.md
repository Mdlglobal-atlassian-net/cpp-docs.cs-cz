---
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 15a6d72a79f0498fb7d81094ed3595dea1cf444f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948566"
---
# <a name="_set_error_mode"></a>_set_error_mode

Upraví **__error_mode** pro určení nevýchozího umístění, kde modul runtime jazyka C zapíše chybovou zprávu pro chybu, která může ukončit program.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Parametry

*mode_val*<br/>
Cíl chybových zpráv

## <a name="return-value"></a>Návratová hodnota

Vrátí staré nastavení nebo-1, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Ovládá výstupní jímku chyby nastavením hodnoty **__error_mode**. Můžete například směrovat výstup na standardní chybu nebo použít rozhraní API **MessageBox** .

Parametr *mode_val* může být nastaven na jednu z následujících hodnot.

|Parametr|Popis|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Chybový jímka Určuje **__app_type**.|
|**_OUT_TO_STDERR**|Chybná jímka je standardní chyba.|
|**_OUT_TO_MSGBOX**|Chybná jímka je okno se zprávou.|
|**_REPORT_ERRMODE**|Vykázat aktuální hodnotu **__error_mode** .|

Pokud je předána jiná hodnota než uvedená, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **_set_error_mode** nastaví **errno** na **EINVAL** a vrátí-1.

Když se používá s [kontrolním](assert-macro-assert-wassert.md)výrazem, **_set_error_mode** zobrazí v dialogovém okně příkaz failed a nabídne vám možnost zvolit tlačítko **Ignorovat** , aby bylo možné pokračovat v běhu programu.

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
