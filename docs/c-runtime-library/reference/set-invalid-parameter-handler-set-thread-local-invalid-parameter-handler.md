---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
- _o__set_invalid_parameter_handler
- _o__set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: 0637937d4596d28875c40efec62f79a32f533dcf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337672"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Nastaví funkci, která má být volána, když CRT zjistí neplatný argument.

## <a name="syntax"></a>Syntaxe

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>Parametry

*pNový*<br/>
Ukazatel funkce na novou obslužnou rutinu neplatného parametru.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na neplatnou obslužnou rutinu parametru před voláním.

## <a name="remarks"></a>Poznámky

Mnoho funkcí runtime C zkontrolovat platnost argumentů, které jim byly předány. Pokud je předán neplatný argument, funkce můžete nastavit číslo **chyby errno** nebo vrátit kód chyby. V takových případech je také volána obslužná rutina neplatného parametru. Zaběhu C poskytuje výchozí globální neplatná obslužná rutina parametru, která ukončí program a zobrazí chybovou zprávu za běhu. **Pomocí _set_invalid_parameter_handler** můžete nastavit vlastní funkci jako globální obslužnou rutinu neplatného parametru. C runtime také podporuje obslužnou rutinu neplatný parametr místní vlákno. Pokud je obslužná rutina parametru místního vlákna nastavena ve vlákně pomocí **_set_thread_local_invalid_parameter_handler**, funkce runtime C volané z vlákna používají tuto obslužnou rutinu namísto globální obslužné rutiny. Jako globální neplatná obslužná rutina argumentů lze současně zadat pouze jednu funkci. Pouze jedna funkce může být zadána jako místní obslužná rutina argumentu na vlákno, ale různá vlákna mohou mít různé obslužné rutiny místního vlákna. To umožňuje změnit obslužnou rutinu použitou v jedné části kódu bez ovlivnění chování jiných vláken.

Když runtime volá funkci neplatného parametru, obvykle to znamená, že došlo k neopravitelné chybě. Neplatná funkce obslužné rutiny parametru, kterou zadáte, by měla uložit všechna data, která může, a poté přerušit. Neměl by vrátit řízení do hlavní funkce, pokud si nejste jisti, že chyba je obnovitelná.

Funkce obslužné rutiny neplatného parametru musí mít následující prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

Argument *výrazu* je široký řetězec reprezentace výraz argument, který vyvolal chybu. Argument *funkce* je název funkce CRT, která obdržela neplatný argument. Argument *souboru* je název zdrojového souboru CRT, který obsahuje funkci. Argument *řádku* je číslo řádku v tomto souboru. Poslední argument je vyhrazen. Všechny parametry mají hodnotu **NULL,** pokud není použita ladicí verze knihovny CRT.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_invalid_parameter_handler**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib \<> nebo stdlib.h>|

Funkce **_set_invalid_parameter_handler** a **_set_thread_local_invalid_parameter_handler** jsou specifické pro společnost Microsoft. Informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V následujícím příkladu se k tisku funkce, která obdržela neplatný parametr, používá neplatná obslužná rutina chyby parametru a soubor a řádek ve zdrojích CRT. Při použití knihovny ladění CRT, neplatné chyby parametrů také vyvolat kontrolní výraz, který je zakázán v tomto příkladu pomocí [_CrtSetReportMode](crtsetreportmode.md).

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>Viz také

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Bezpečnostní verze funkcí CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
