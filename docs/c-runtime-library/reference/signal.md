---
title: "signál | Microsoft Docs"
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- signal
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
- signal
dev_langs:
- C++
helpviewer_keywords:
- signal function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23eae404bf5f8e2227d68189938defb2308f5e6b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="signal"></a>signal

Nastaví přerušení zpracování signál.

> [!IMPORTANT]
> Vypnout aplikaci pomocí Microsoft Store, s výjimkou testování nebo ladění scénáře nepoužívejte tuto metodu. Zavřete aplikaci ve Store způsoby programový nebo uživatelského rozhraní nejsou povolené podle požadavků [Microsoft Store zásady](http://go.microsoft.com/fwlink/?LinkId=865936). Další informace najdete v tématu [životní cyklus aplikace UWP](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Syntaxe

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry
_sig_  
Hodnota signál.

_Func_  
Druhý parametr je ukazatel na funkci spouštění. První parametr je hodnota signál a druhý parametr je dílčí kód, který lze použít při první parametr je sigfpe –.

## <a name="return-value"></a>Návratová hodnota

`signal` Vrátí předchozí hodnotu func, který je spojen s danou signál. Například pokud předchozí hodnotu _func_ byla `SIG_IGN`, vrácená hodnota je také `SIG_IGN`. Vrácená hodnota `SIG_ERR` označuje chybu; v takovém případě `errno` je nastaven na `EINVAL`.

V tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o návratové kódy.

## <a name="remarks"></a>Poznámky

`signal` Funkce umožňuje proces vyberte jednu z několik způsobů, jak zpracovat signál přerušení z operačního systému. _Sig_ argument je přerušení, ke kterému `signal` reaguje; musí mít jednu z následujících manifestu konstant, které jsou definovány v SIGNÁL. H.

|_SIG_ hodnota|Popis|
|-----------------|-----------------|
|`SIGABRT`|Abnormální ukončení|
|`SIGFPE`|Chyba s plovoucí desetinnou čárkou|
|`SIGILL`|Neplatná instrukce|
|`SIGINT`|CTRL + C signál|
|`SIGSEGV`|Přístup k úložišti neplatný|
|`SIGTERM`|Žádost o ukončení|

Pokud _sig_ není jedním z výše uvedené hodnoty, je vyvolána obslužná rutina neplatný parametr, jak jsou definovány v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `SIG_ERR`.

Ve výchozím nastavení `signal` ukončí volací program s ukončovacím kódem 3, bez ohledu na hodnotu _sig_.

> [!NOTE]
> `SIGINT` není podporován pro všechny aplikace typu Win32. Když dojde k přerušení CTRL + C, operační systémy Win32 generovat nové vlákno konkrétně zpracování této přerušení. To může způsobit jedním vláknem aplikaci, například ten, který v systému UNIX se stane s více vlákny a způsobit neočekávané chování.

_Func_ argument je adresu na signál obslužnou rutinu, která můžete psát, nebo na jednu z předdefinovaných konstanty `SIG_DFL` nebo `SIG_IGN`, která je definována v SIGNÁL. H. Pokud _func_ je funkce, je nainstalován jako obslužná rutina signál pro danou signál. Obslužná rutina signál prototypu vyžaduje jeden argument formální, _sig_, typu `int`. Operační systém poskytuje skutečné argument prostřednictvím _sig_ když dojde k přerušení; argument je signál, která generuje přerušení. Proto můžete šesti manifestu konstanty (uvedené v předchozí tabulce) ve vaší obslužné rutiny signál k určení které přerušení došlo k chybě a proveďte příslušnou akci. Například můžete volat `signal` na dvou různých signály přiřadit stejné obslužné rutiny a otestujte dvakrát _sig_ argument v rutině k provádění různých akcí podle signál přijata.

Pokud testujete výjimky s plovoucí desetinnou čárkou (`SIGFPE`), _func_ odkazuje na funkci, která přebírá volitelné druhý argument, který je jedním z několika manifestu konstanty – definované v FLOAT. H – formuláře `FPE_xxx`. Když `SIGFPE` signál dojde, můžete otestovat hodnotu druhý argument, abyste zjistili druh výjimek plovoucí desetinné čárky a proveďte příslušnou akci. Tento argument a jeho možné hodnoty jsou rozšíření Microsoft.

S plovoucí desetinnou čárkou výjimky, hodnota _func_ není resetovat, když je obdržena signál. Obnovit z s plovoucí desetinnou čárkou výjimky, zkuste použít / s výjimkou bodu klauzule k obklopit procedura operace. Je také možné obnovit pomocí [setjmp](../../c-runtime-library/reference/setjmp.md) s [longjmp](../../c-runtime-library/reference/longjmp.md). V obou případech volající proces obnoví spuštění a opustí s plovoucí desetinnou čárkou stav procesu není definovaná.

Pokud obslužná rutina signál vrátí, volající proces obnoví spuštění hned za bod, ve kterém přijala signál přerušení. To platí bez ohledu na druh signál nebo provozním režimu.

Před provedením zadaná funkce hodnotu _func_ je nastaven na `SIG_DFL`. Další signál přerušení považuje, jak je popsáno pro `SIG_DFL`, pokud uplynulého volat na `signal` neurčí jinak. Tato funkce slouží k resetování signály v volaná funkce.

Protože rutiny signál – obslužná rutina se obvykle říká asynchronně, když dojde přerušení, může funkce obslužných rutin signál k řízení při spuštění operace nekompletní a v neznámém stavu. Následující seznam shrnuje omezení, které určují, funkcích, které můžete použít v signál rutiny ovladače.

- To není problém nižší úrovně nebo STDIO. H vstupní a výstupní rutiny (například `printf` nebo `fread`).

- Nevolejte haldy rutiny nebo všechny rutiny, která používá rutiny haldy (například `malloc`, `_strdup`, nebo `_putenv`). V tématu [malloc –](../../c-runtime-library/reference/malloc.md) Další informace.

- Nepoužívejte všechny funkce, která generuje volání systému (například `_getcwd` nebo `time`).

- Nepoužívejte `longjmp` Pokud přerušení je způsobena výjimek plovoucí desetinné čárky (tedy _sig_ je `SIGFPE`). V takovém případě nejprve inicializovat balíček s plovoucí desetinnou čárkou s použitím volání `_fpreset`.

- Nepoužívejte všechny rutiny překrytí.

Program musí obsahovat s plovoucí desetinnou čárkou kódu, pokud je na depeše `SIGFPE` výjimky pomocí funkce. Pokud program nemá s plovoucí desetinnou čárkou kód a kód pro zpracování signál běhové knihovny vyžaduje, jenom deklarovat volatile dvojitou a provést jeho inicializaci na nulu:

`volatile double d = 0.0f;`

`SIGILL` a `SIGTERM` signály, které nejsou generované v rámci systému Windows. Jsou zahrnuté pro kompatibilitu ANSI. Proto můžete nastavit signál obslužné rutiny pro tyto signály pomocí `signal`, a také explicitně vygenerovat tyto signály voláním [vyvolat](../../c-runtime-library/reference/raise.md).

V vytvářený procesy, které jsou vytvořené pomocí volání nejsou zachována nastavení signál `_exec` nebo `_spawn` funkce. Signál nastavení se obnoví na výchozí hodnoty v nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`signal`|\<signal.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `signal` přidat některé vlastní chování `SIGABRT` signál. Další informace o chování přerušení najdete v tématu [_set_abort_behavior –](../../c-runtime-library/reference/set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[_fpreset](../../c-runtime-library/reference/fpreset.md)  
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)  
