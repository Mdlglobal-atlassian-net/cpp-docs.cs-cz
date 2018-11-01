---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 11/04/2016
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
ms.openlocfilehash: e43d5caaeebb6303d209d870c804357117812985
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478361"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Tyto funkce používají běhové knihovny jazyka C pro zpracování neplatné parametry předané do funkce knihovny CRT. Váš kód může také použití těchto funkcí pro podporu výchozí nebo přizpůsobitelné manipulaci s neplatnými parametry.

## <a name="syntax"></a>Syntaxe

```C
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

## <a name="parameters"></a>Parametry

*Výraz*<br/>
Řetězec představující zdrojový kód parametr výraz, který není platný.

*Název_funkce*<br/>
Název funkce, která volá obslužná rutina.

*název_souboru*<br/>
Souboru zdrojového kódu, kde byla volána obslužnou rutinu.

*line_number*<br/>
Číslo řádku ve zdrojovém kódu, kde byla volána obslužnou rutinu.

*Rezervováno*<br/>
Nevyužité.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce nevrátí hodnotu. **_Invalid_parameter_noinfo_noreturn** a **_invoke_watson** funkce nevrací do volajícího a v některých případech **_invalid_parameter** a **_invalid_parameter_noinfo** nemusí vracet volajícímu.

## <a name="remarks"></a>Poznámky

Když funkce knihovny prostředí runtime jazyka C jsou předány neplatné parametry, knihovně funkce volání *obslužná rutina neplatného parametru*, funkce, která může být určeno programátorovi, aby provádět několik věcí. Například ji může nahlásit problém pro uživatele, zápis do protokolu, přerušení ladicího programu, ukončete program nebo nedělat nic vůbec. Pokud není zadána žádná funkce programátorem obslužnou rutinu výchozí **_invoke_watson**, je volána.

Ve výchozím nastavení, když není platná hodnota parametru je identifikován v ladění kódu, funkce knihovny CRT volat funkci **_invalid_parameter** pomocí podrobné parametrů. V kódu bez ladění **_invalid_parameter_noinfo** funkce je volána, který volá **_invalid_parameter** funkce pomocí prázdné parametry. Pokud funkce knihovny CRT bez ladění vyžaduje ukončení programu **_invalid_parameter_noinfo_noreturn** funkce je volána, který volá **_invalid_parameter** funkce pomocí prázdné parametry, za nímž následuje volání **_invoke_watson** funkci a vynuťte ukončení programu.

**_Invalid_parameter** funkce kontroly, zda byl nastaven uživatelem definované neplatný parametr obslužné rutiny a pokud ano, zavolá se. Například, pokud byl nastaven uživatelem definované obslužné rutiny místního vlákna voláním [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) v aktuálním vlákně, je volána, vrátí funkce. Jinak, pokud byl nastaven uživatelem definované globální neplatný parametr obslužné rutiny voláním [set_invalid_parameter_handler –](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), je volána, vrátí funkce. V opačném případě výchozí obslužnou rutinu **_invoke_watson** je volána. Výchozí chování **_invoke_watson** je ukončit program. Uživatelem definované obslužné rutiny může zrušit nebo vrátit. Doporučujeme vám, že uživatelem definované obslužné rutiny ukončete program, není-li obnovení některých.

Pokud výchozí obslužnou rutinu **_invoke_watson** je volána, pokud procesor podporuje [__fastfail](../../intrinsics/fastfail.md) operace, je vyvolán, pomocí parametru **FAST_FAIL_INVALID_ARG** a proces skončí. V opačném případě je vyvolána výjimka rychlé převzetí služeb při, což může být zachycena připojený ladicí program. Pokud proces může pokračovat, je ukončen voláním Windows **TerminateProcess** funkce pomocí stavem kód výjimky **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Ověřování parametrů](../../c-runtime-library/parameter-validation.md)<br/>
