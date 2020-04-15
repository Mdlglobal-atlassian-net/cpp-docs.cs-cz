---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343945"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Tyto funkce jsou používány knihovnou runtime C ke zpracování neplatných parametrů předaných funkcím knihovny CRT. Váš kód může také použít tyto funkce pro podporu výchozí nebo přizpůsobitelné zpracování neplatných parametrů.

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
Řetězec představující výraz parametru zdrojového kódu, který není platný.

*function_name*<br/>
Název funkce, která volala obslužnou rutinu.

*Název_souboru*<br/>
Soubor zdrojového kódu, kde byla volána obslužná rutina.

*line_number*<br/>
Číslo řádku ve zdrojovém kódu, kde byla volána obslužná rutina.

*Vyhrazena*<br/>
Nepoužívá se.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce nevracejí hodnotu. Funkce **_invalid_parameter_noinfo_noreturn** a **_invoke_watson** se volajícímu nevrátí a v některých případech **se _invalid_parameter** a **_invalid_parameter_noinfo** nemusí volajícímu vrátit.

## <a name="remarks"></a>Poznámky

Když jsou funkce knihovny runtime C předány neplatným parametrům, funkce knihovny volají *neplatnou obslužnou rutinu parametru*, funkci, kterou může programátor určit k provádění některé z několika věcí. Může například nahlásit problém uživateli, zapsat do protokolu, přerušit ladicí program, ukončit program nebo neprovádět vůbec žádné akce. Pokud programátor nezadal žádnou funkci, je volána výchozí obslužná rutina **_invoke_watson**.

Ve výchozím nastavení, pokud je v ladicím kódu identifikován neplatný parametr, funkce knihovny CRT volají funkci **_invalid_parameter** pomocí podrobných parametrů. V kódu bez ladění je volána funkce **_invalid_parameter_noinfo,** která volá **funkci _invalid_parameter** pomocí prázdných parametrů. Pokud funkce knihovny CRT bez ladění vyžaduje ukončení programu, je volána **funkce _invalid_parameter_noinfo_noreturn,** která volá funkci **_invalid_parameter** pomocí prázdných parametrů, následovanou voláním **_invoke_watson** funkce k vynucení ukončení programu.

Funkce **_invalid_parameter** zkontroluje, zda byla nastavena uživatelem definovaná obslužná rutina neplatného parametru, a pokud ano, volá ji. Například pokud uživatelem definované obslužné rutiny místní vlákno byla nastavena volání [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) v aktuálním vlákně, je volána, pak funkce vrátí. V opačném případě, pokud uživatelem definované globální neplatná obslužná rutina parametru byla nastavena volání [mset_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), je volána, vrátí funkce. V opačném případě se nazývá výchozí obslužná rutina **_invoke_watson.** Výchozí chování **_invoke_watson** je ukončit program. Uživatelem definované obslužné rutiny mohou ukončit nebo vrátit. Doporučujeme, aby uživatelem definované obslužné rutiny ukončily program, pokud není jisté obnovení.

Pokud je volána výchozí obslužná rutina **_invoke_watson,** pokud procesor podporuje [operaci __fastfail,](../../intrinsics/fastfail.md) je vyvolánpomocí parametru **FAST_FAIL_INVALID_ARG** a proces se ukončí. V opačném případě je vyvolána výjimka rychlé selhání, která může být zachycena připojeným ladicím programem. Pokud je povoleno pokračovat v procesu, je ukončen voláním funkce **Windows TerminateProcess** pomocí stavu kódu výjimky **STATUS_INVALID_CRUNTIME_PARAMETER**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn** **_invoke_watson**|\<corecrt.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Ověření parametru](../../c-runtime-library/parameter-validation.md)<br/>
