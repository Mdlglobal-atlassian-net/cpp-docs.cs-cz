---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
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
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: 090eb43289313f12b900e671df61f74e7b464872
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948498"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Nastaví funkci, která bude volána, když CRT detekuje neplatný argument.

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

*pNew*<br/>
Ukazatel funkce na novou neplatnou obslužnou rutinu parametru.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na obslužnou rutinu neplatného parametru před voláním.

## <a name="remarks"></a>Poznámky

Mnoho funkcí modulu runtime jazyka C kontroluje platnost předaných argumentů. Pokud je předán neplatný argument, může funkce nastavit číslo chyby **errno** nebo vrátit kód chyby. V takových případech je volána také obslužná rutina neplatného parametru. Modul runtime jazyka C poskytuje výchozí globální obslužnou rutinu neplatného parametru, která ukončí program a zobrazí chybovou zprávu modulu runtime. Pomocí **_set_invalid_parameter_handler** můžete nastavit vlastní funkci jako globální obslužnou rutinu neplatného parametru. Modul runtime jazyka C také podporuje obslužnou rutinu neplatného místního vlákna. Pokud je obslužná rutina parametru místního vlákna nastavena ve vlákně pomocí **_set_thread_local_invalid_parameter_handler**, běhové funkce jazyka C volané z vlákna používají tento popisovač místo globální obslužné rutiny. Jako globální obslužnou rutinu neplatného argumentu se dá zadat jenom jedna funkce. Jako neplatnou obslužnou rutinu parametru Local vlákna je možné zadat jenom jednu funkci, ale různá vlákna můžou mít různé obslužné rutiny místního vlákna. To umožňuje změnit obslužnou rutinu použitou v jedné části kódu, aniž by to ovlivnilo chování jiných vláken.

Pokud modul runtime volá neplatnou funkci parametru, obvykle to znamená, že došlo k neopravitelné chybě. Neplatná obslužná rutina parametru, kterou zadáte, by měla ukládat všechna data, která může a pak přerušit. Nemělo by vracet řízení hlavní funkci, pokud si nejste jistí, že je chyba obnovitelná.

Neplatná funkce obslužné rutiny parametrů musí mít následující prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

Argument *výrazu* je celá řetězcová reprezentace výrazu argumentu, který vyvolal chybu. Argument *funkce* je název funkce CRT, která přijala neplatný argument. Argument *File* je název zdrojového souboru CRT, který obsahuje funkci. Argument *line* je číslo řádku v tomto souboru. Poslední argument je rezervován. Všechny parametry mají hodnotu **null** , pokud není použita ladicí verze knihovny CRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_invalid_parameter_handler**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib > nebo \<Stdlib. h >|

Funkce **_set_invalid_parameter_handler** a **_set_thread_local_invalid_parameter_handler** jsou specifické pro společnost Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V následujícím příkladu se k vytištění funkce, která obdržela neplatný parametr a souboru a řádku ve zdrojích CRT, používá neplatná obslužná rutina chyby parametru. Pokud je použita knihovna CRT ladění, neplatné chyby parametrů také vyvolají kontrolní výraz, který je v tomto příkladu zakázán pomocí [_CrtSetReportMode](crtsetreportmode.md).

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

## <a name="see-also"></a>Viz také:

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Verze funkcí CRT se zdokonaleným zabezpečením](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
