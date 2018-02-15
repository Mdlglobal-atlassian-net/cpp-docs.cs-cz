---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 258d3e3aa9f005c76b5e4f2b3739ee588cde3f0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
Tyto funkce jsou používány běhové knihovny jazyka C pro zpracování neplatné parametry předané do funkce knihovny CRT. Váš kód také mohou používat tyto funkce pro podporu výchozí nebo přizpůsobitelné zpracování neplatné parametry.

## <a name="syntax"></a>Syntaxe
```
extern "C" void __cdecl 
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);  

extern "C" void __cdecl 
_invalid_parameter_noinfo(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invalid_parameter_noinfo_noreturn(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invoke_watson(  
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="return-value"></a>Návratová hodnota
Tyto funkce nevrátí hodnotu. `_invalid_parameter_noinfo_noreturn` a `_invoke_watson` funkce nevrátí volajícímu a v některých případech `_invalid_parameter` a `_invalid_parameter_noinfo` nemusí vracet volajícímu.

## <a name="parameters"></a>Parametry
`expression`  
Řetězec představující výraz parametr zdrojový kód, který není platný.

`function_name`  
Název funkce, která volána obslužná rutina.

`file_name`  
Souboru zdrojového kódu, kde byla volána obslužná rutina.

`line_number`  
Číslo řádku ve zdrojovém kódu, kde byla volána obslužná rutina.

`reserved`  
Nepoužívá se.

## <a name="remarks"></a>Poznámky
Když funkce knihovny za běhu C jsou předány neplatné parametry, knihovny funkce volání *neplatná obslužná rutina parametru*, funkci, která může být určena programátorů lze provádět několik věcí. Například je může ohlaste daný problém pro uživatele, zapisovat do protokolu, proniknout ladicí program, ukončení programu nebo vůbec nic nestane. Pokud je zadána žádná funkce programátory, výchozí obslužnou rutinu, `_invoke_watson`, je volána.

Ve výchozím nastavení, když není platná hodnota parametru se v ladění kódu identifikuje funkce knihovny CRT volání funkce `_invalid_parameter` pomocí podrobné parametrů. V jiných ladění kódu `_invalid_parameter_noinfo` funkce je volána, který volá `_invalid_parameter` funkce pomocí prázdné parametry. Pokud funkce knihovny CRT bez ladění vyžaduje ukončení programu `_invalid_parameter_noinfo_noreturn` funkce je volána, který volá `_invalid_parameter` funkce pomocí prázdné parametry, za nímž následuje volání `_invoke_watson` funkce vynutit ukončení programu.

`_invalid_parameter` Funkce kontroly, zda byl nastaven neplatný parametr uživatelem definované obslužné rutiny a pokud ano, zavolá ho. Například, pokud byl nastaven uživatelem definované obslužné rutiny místní voláním [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) v aktuální vlákno je volána, potom funkce vrátí hodnotu. Jinak, pokud obslužná rutina uživatelem definované globální neplatný parametr byl nastaven voláním [set_invalid_parameter_handler –](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), se označuje jako a pak funkce vrátí hodnotu. Jinak výchozí obslužnou rutinu `_invoke_watson` je volána. Výchozí chování `_invoke_watson` je program ukončit. Uživatelem definované obslužné rutiny ukončit nebo vrátit. Doporučujeme vám, že uživatelem definované obslužné rutiny ukončení programu, pokud obnovení není určité. 

Při výchozí obslužnou rutinu `_invoke_watson` je volána, pokud procesor podporuje [__fastfail](../../intrinsics/fastfail.md) operace, je vyvolána, pomocí parametr `FAST_FAIL_INVALID_ARG` a proces se ukončuje. Jinak je vyvolána výjimka rychlé selhání, který může být zachycen připojené ladicí program. Pokud tento proces může pokračovat, je ukončen voláním Windows `TerminateProcess` funkce pomocí stavu kód výjimky `STATUS_INVALID_CRUNTIME_PARAMETER`. 

## <a name="requirements"></a>Požadavky  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [Ověřování parametrů](../../c-runtime-library/parameter-validation.md)
