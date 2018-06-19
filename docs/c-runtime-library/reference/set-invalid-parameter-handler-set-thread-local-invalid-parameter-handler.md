---
title: _set_invalid_parameter_handler –, _set_thread_local_invalid_parameter_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4808367c94ec6c869c7f3bcafd2965a317553a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407600"
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Nastaví funkci, která se má volat při CRT zjistí neplatný argument.

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
Ukazatel funkce na nový popisovač neplatný parametr.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na obslužnou rutinu neplatný parametr před voláním.

## <a name="remarks"></a>Poznámky

Mnoho funkcí jazyka C runtime kontrolu platnosti argumentů předaných na ně. Pokud není předán neplatný argument funkce můžete nastavit **errno** číslo chyby nebo return chybový kód. V takových případech se také nazývá obslužná rutina neplatný parametr. C runtime poskytuje globální neplatný parametr výchozí obslužnou rutinu, která ukončí program a zobrazí se chybová zpráva modulu runtime. Můžete použít **_set_invalid_parameter_handler –** nastavit vlastní funkce jako obslužná rutina globální neplatný parametr. C runtime také podporuje obslužná rutina specifická pro přístup z více vláken neplatný parametr. Pokud obslužná rutina specifická pro přístup z více vláken parametr nastavená v podprocesu pomocí **_set_thread_local_invalid_parameter_handler**, funkce C runtime volat z vlákna používat tuto obslužnou rutinu místo globální obslužná rutina. Jenom jednu funkci lze zadat jako obslužná rutina globální neplatný argument najednou. Jako obslužná rutina specifická pro přístup z více vláken neplatný argument na vlákno lze zadat pouze jednu funkci, ale různých vláknech může mít jiný místní obslužné rutiny. To vám umožní změnit obslužná rutina používá v jedné části kódu, aniž by to ovlivnilo chování jiná vlákna.

Když modul runtime volá funkci neplatný parametr, obvykle to znamená, že došlo k neobnovitelné chybě. Neplatný parametr obslužné rutiny, které zadáte měli uložit všechna data, může a pak k přerušení. Ovládací prvek je by neměla vrátit do hlavní funkce, pokud si nejste jisti, že je chyba použitelná pro obnovení.

Neplatný parametr obslužné rutiny musí mít následující prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

*Výraz* argument je široké řetězcovou reprezentaci argument výrazu, který vyvolal chybu. *Funkce* argument je název funkce CRT, který přijal neplatný argument. *Souboru* argument je název CRT zdrojový soubor, který obsahuje funkce. *Řádku* argument je číslo řádku v tomto souboru. Poslední argument je vyhrazena. Všechny parametry mají hodnotu **NULL** Pokud ladicí verze knihovny CRT se má použít.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_invalid_parameter_handler –**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h ><br /><br /> C++: \<cstdlib – > nebo \<stdlib.h >|

**_Set_invalid_parameter_handler –** a **_set_thread_local_invalid_parameter_handler** funkce se konkrétní společnosti Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

V následujícím příkladu se obslužná rutina neplatný parametr používá k vytištění funkce, která dostali CRT zdroje neplatný parametr a soubor a řádku. Při použití knihovny ladění CRT neplatný parametr chyby zároveň vyvolává kontrolní výrazy, který je zakázaný tento příklad pomocí [_crtsetreportmode –](crtsetreportmode.md).

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
[Verze funkcí CRT se zdokonaleným zabezpečením](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
