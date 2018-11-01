---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
apiname:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
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
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: 1df876d6df9327e817d5d2c401e0abe97ad7a548
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617032"
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Nastaví funkce, která se má volat při CRT zjistí neplatný argument.

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
Ukazatel funkce na novou obslužnou rutinu neplatného parametru.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na obslužnou rutinu neplatného parametru, před voláním.

## <a name="remarks"></a>Poznámky

Mnoho funkcí jazyka C runtime zkontroloval platnosti identifikátoru argumenty předané do nich. Pokud je předán neplatný argument, funkce lze nastavit **errno** číslo chyby nebo vrátí chybový kód. V takových případech se také nazývá obslužnou rutinu neplatného parametru. Modul runtime jazyka C poskytuje výchozí obslužná rutina globální neplatného parametru, který ukončí program a zobrazí chybovou zprávu modulu runtime. Můžete použít **_set_invalid_parameter_handler –** nastavit svoji vlastní funkci jako globální neplatný parametr obslužné rutiny. Modul runtime jazyka C podporuje také obslužnou rutinu neplatného parametru místního vlákna. Pokud je obslužná rutina parametru místního vlákna nastavení ve vlákně s použitím **_set_thread_local_invalid_parameter_handler**, místo globální obslužná rutina volat z vlákna funkce modulu runtime jazyka C použít tuto obslužnou rutinu. Pouze jedna funkce lze zadat jako obslužná rutina globální neplatný argument najednou. Pouze jedna funkce lze zadat jako místního vlákna neplatný argument obslužné rutiny na vlákno, ale různých vláken může mít jiné obslužné rutiny místního vlákna. To umožňuje změnit obslužnou rutinu použít v jedné části kódu, aniž by to ovlivnilo chování ostatních vláken.

Když modul runtime volá funkci neplatného parametru, obvykle to znamená, že došlo k neobnovitelné chybě. Neplatný parametr obslužné rutiny, které zadáte by měl uložte si veškerá data, můžete a potom zrušit. Pokud si nejste jisti, že je chyba obnovitelné ho by neměly vracet ovládacího prvku k funkci main.

Funkce obslužnou rutinu neplatného parametru, musíte mít následující prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

*Výraz* argument je široké řetězcové vyjádření výraz argumentu, který vyvolal chybu. *Funkce* argumentem je název funkce CRT, který přijal neplatný argument. *Souboru* argumentem je název zdrojového souboru CRT, který obsahuje funkci. *Řádku* argument je číslo řádku v tomto souboru. Poslední argument je vyhrazená. Všechny parametry mají hodnotu **NULL** jedině v případě používá ladicí verzi knihovny CRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_invalid_parameter_handler –**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h ><br /><br /> Jazyk C++: \<cstdlib – > nebo \<stdlib.h >|

**_Set_invalid_parameter_handler –** a **_set_thread_local_invalid_parameter_handler** funkce jsou specifické pro Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V následujícím příkladu obslužná rutina neplatného parametru chyby slouží k tisku, který přijal neplatný parametr a souboru a řádku ve zdrojích CRT funkce. Při použití ladicí CRT knihovny neplatný parametr chyby také vyvolat kontrolní výraz, který je zakázaný v tomto příkladu pomocí [_CrtSetReportMode](crtsetreportmode.md).

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
