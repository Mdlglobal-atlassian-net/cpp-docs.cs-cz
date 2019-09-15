---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 11/04/2016
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b2714c140a2396d88c700689244c6ec04e12169c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954609"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Tyto funkce používá běhová knihovna jazyka C ke zpracování neplatných parametrů předaných funkcím knihovny CRT. Váš kód může také používat tyto funkce k podpoře výchozího nebo přizpůsobitelného zpracování neplatných parametrů.

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

*vyjádření*<br/>
Řetězec představující výraz parametru zdrojového kódu, který není platný.

*function_name*<br/>
Název funkce, která se nazývá obslužná rutina.

*název_souboru*<br/>
Soubor zdrojového kódu, kde byla obslužná rutina volána.

*line_number*<br/>
Číslo řádku ve zdrojovém kódu, kde byla obslužná rutina volána.

*rezervovaný*<br/>
Nepoužívané.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce nevracejí hodnotu. Funkce **_invalid_parameter_noinfo_noreturn** a **_invoke_watson** se nevrátí volajícímu a v některých případech se **_invalid_parameter** a **_invalid_parameter_noinfo** nemusí vrátit volajícímu.

## <a name="remarks"></a>Poznámky

Když jsou funkce běhové knihovny jazyka C předány neplatným parametrům, funkce knihovny volá *neplatnou obslužnou rutinu parametru*, funkci, která může být určena programátorem k provedení některé z několika věcí. Může například nahlásit problém uživateli, zapsat do protokolu, přerušit ladicí program, ukončit program nebo neprovádět žádné akce. Pokud programátor nezadá žádnou funkci, zavolá se výchozí obslužná rutina **_invoke_watson**.

Ve výchozím nastavení, pokud je v kódu ladění identifikován neplatný parametr, funkce knihovny CRT volá funkci **_invalid_parameter** pomocí podrobných parametrů. V kódu bez ladění je volána funkce **_invalid_parameter_noinfo** , která volá funkci **_invalid_parameter** s použitím prázdných parametrů. Pokud funkce knihovny CRT bez ladění vyžaduje ukončení programu, je volána funkce **_invalid_parameter_noinfo_noreturn** , která volá funkci **_invalid_parameter** pomocí prázdných parametrů následovaných voláním **_invoke_ funkce Watson** pro vynucení ukončení programu.

Funkce **_invalid_parameter** ověřuje, zda byla nastavena uživatelsky definovaný neplatný parametr obslužné rutiny, a pokud ano, zavolá ji. Například pokud uživatelem definovaná obslužná rutina místního vlákna byla nastavena voláním [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) v aktuálním vlákně, je volána, poté funkce vrátí. V opačném případě, pokud byla uživatelem definovaná obslužná rutina globálního neplatného parametru nastavena voláním [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), je volána, funkce vrátí. V opačném případě je volána výchozí obslužná rutina **_invoke_watson** . Výchozím chováním **_invoke_watson** je ukončení programu. Může skončit nebo vracet uživatelsky definované obslužné rutiny. Doporučujeme, aby uživatelsky definované obslužné rutiny ukončily program, pokud není jisté obnovení.

Pokud je volána výchozí obslužná rutina **_invoke_watson** , pokud procesor podporuje operaci [__fastfail](../../intrinsics/fastfail.md) , je vyvolána pomocí parametru **FAST_FAIL_INVALID_ARG** a proces je ukončen. V opačném případě je vyvolána rychlá výjimka selhání, která může být zachycena připojeným ladicím programem. Pokud může proces pokračovat, je ukončen voláním funkce Windows **TerminateProcess** pomocí stavu kódu výjimky **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Ověřování parametrů](../../c-runtime-library/parameter-validation.md)<br/>
