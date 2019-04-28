---
title: signal
ms.date: 04/12/2018
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
helpviewer_keywords:
- signal function
ms.openlocfilehash: 351bdbe1d787fc5e5d741460adfe415df7fda756
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356287"
---
# <a name="signal"></a>signal

Nastavuje zpracování signálu přerušení.

> [!IMPORTANT]
> Nepoužívejte tuto metodu k vypnutí aplikace Microsoft Store, s výjimkou testování nebo ladění scénářů. Zavření aplikace pro Store způsoby programátorské nebo uživatelské rozhraní nejsou povoleny podle [zásady Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Hodnota signálu.

*Func*<br/>
Druhý parametr je ukazatel na funkci, která má být proveden. První parametr je hodnota signálu a druhý parametr je dílčí kód, který se dá použít při první parametr sigfpe.

## <a name="return-value"></a>Návratová hodnota

**signál** vrátí předchozí hodnotu funkce, která je přidružená zadanému signálu. Například pokud předchozí hodnotu *func* byl **SIG_IGN**, vrácená hodnota je také **SIG_IGN**. Vrácená hodnota **SIG_ERR** označuje chybu; v takovém případě **errno** je nastavena na **EINVAL**.

Zobrazit [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o návratových kódech.

## <a name="remarks"></a>Poznámky

**Signál** funkce umožňuje procesu zvolit jeden z několika způsobů zpracování signálu přerušení z operačního systému. *Sig* argument je přerušení, kterému **signál** odpovídá; musí být jedna z následujících konstant manifestu, které jsou definovány v SIGNÁLU. H.

|*SIG* hodnota|Popis|
|-----------------|-----------------|
|**SIGABRT**|Abnormální ukončení|
|**SIGFPE**|Chyba plovoucí desetinné čárky|
|**SIGILL**|Neplatná instrukce|
|**SIGINT**|CTRL + C signál|
|**SIGSEGV**|Neplatný přístup k úložišti|
|**SIGTERM**|Žádost o ukončení|

Pokud *sig* není jednou z výše uvedených hodnot, je vyvolána obslužná rutina neplatného parametru, jak jsou definovány v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **SIG_ERR**.

Ve výchozím nastavení **signál** ukončí volající program s ukončovacím kódem 3, bez ohledu na hodnotu *sig*.

> [!NOTE]
> **SIGINT** není podporováno pro žádnou aplikaci Win32. Pokud dojde k přerušení CTRL + C, operační systémy Win32 vygenerují nové vlákno, které konkrétně zpracuje toto přerušení. To může způsobit aplikace jedním vláknem, jako jsou například v systému UNIX, se stane s více vlákny a způsobí neočekávané chování.

*Func* argument je adresa popisovače signálu, který napíšete, nebo na jednu z předdefinovaných konstant **SIG_DFL** nebo **SIG_IGN**, které jsou také definovány v SIGNÁLU. H. Pokud *func* je funkce, je nainstalována jako obslužná rutina signálu pro daný signál. Prototyp obslužné rutiny signálu vyžaduje jeden formální argument *sig*, typu **int**. Operační systém poskytuje skutečný argument prostřednictvím *sig* když dojde k přerušení; argument je signál, který je vygenerován přerušením. Proto můžete šest konstant manifestu (uvedených v předchozí tabulce) v obslužné rutině signálu k určení kterému přerušení došlo a přijmout vhodná opatření. Například můžete volat **signál** na přiřadit stejnou obslužnou rutinu dvěma různým signálům a poté otestujte dvakrát *sig* argument v obslužné rutině, aby provedl různé akce podle přijatého signálu.

Pokud testujete výjimky s plovoucí desetinnou čárkou (**SIGFPE**), *func* odkazuje na funkci, která přebírá volitelný druhý argument, který je jedním z několika konstant manifestu definovaných v typu FLOAT. H formuláře **FPE_xxx**. Když **SIGFPE** dojde k signálu, můžete testovat hodnotu druhého argumentu pro určení druhu výjimky s plovoucí desetinnou čárkou a poté přijmout vhodná opatření. Tento argument a jeho možné hodnoty jsou rozšíření společnosti Microsoft.

Pro výjimky s plovoucí desetinnou čárkou, hodnota *func* není resetována při příjmu signálu. K zotavení z výjimek s plovoucí desetinnou čárkou, použít try / except bodu klauzule ohraničit plovoucí operace. Je také možné obnovit pomocí [setjmp](setjmp.md) s [longjmp](longjmp.md). V obou případech volající proces pokračuje v provádění a ponechá stav s plovoucí desetinnou čárkou procesu nedefinovaný.

Pokud se vrátí obslužná rutina signálu, volající proces pokračuje v provádění bezprostředně bodu, kdy obdržel signál přerušení. To platí bez ohledu na druh signálu nebo provozní režim.

Před provedením zadané funkce je hodnota *func* je nastavena na **SIG_DFL**. Další signál přerušení je považován, jak je popsáno pro **SIG_DFL**, pokud intervenující volání **signál** neurčí jinak. Tuto funkci můžete použít k obnovení signálů ve volané funkci.

Protože rutiny popisovače signálu jsou obvykle volány asynchronně, když dojde k přerušení, funkce popisovače signálu může převzít kontrolu, když operace spuštění je neúplná a v neznámém stavu. Následující seznam obsahuje souhrn omezení, které určují, jaké funkce můžete používat ve vaší obslužné rutině signálu.

- To není problém nízké úrovně nebo STDIO. Rutiny H vstupně-výstupních operací (například **printf** nebo **fread –**).

- Nevolejte rutiny haldy nebo jakékoli rutiny, které používají rutiny haldy (například **malloc**, **_strdup –**, nebo **_putenv**). Zobrazit [malloc](malloc.md) Další informace.

- Nepoužívejte žádné funkce, které generují volání systému (například **_getcwd** nebo **čas**).

- Nepoužívejte **longjmp** Pokud přerušení není způsobeno výjimkou plovoucí desetinné čárky (to znamená *sig* je **SIGFPE**). V takovém případě nejprve znovu inicializujte balíček s plovoucí desetinnou čárkou pomocí volání **_fpreset –**.

- Nepoužívejte žádné překrytí rutin.

Program musí obsahovat kód s plovoucí desetinnou čárkou, pokud má zachytit **SIGFPE** výjimek pomocí funkce. Pokud program nemá kód s plovoucí desetinnou čárkou a vyžaduje kód pro zpracování signálu knihovny run-time, stačí deklarovat volatile double a inicializovat je na nulu:

```C
volatile double d = 0.0f;
```

**SIGILL** a **SIGTERM** signály nejsou generovány v Windows. Jsou zahrnuty z důvodu kompatibility ANSI. Proto lze nastavit obslužné rutiny signálu pro tyto signály pomocí **signál**, a tyto signály můžete vygenerovat také explicitně voláním [vyvolat](raise.md).

Není zachováno nastavení signálu ve vytvářených procesech, které jsou vytvořeny pomocí volání [_exec](../../c-runtime-library/exec-wexec-functions.md) nebo [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkce. Nastavení signálu je obnoveno na výchozí hodnoty v novém procesu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**signal**|\<signal.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat **signál** přidání některého vlastního chování **SIGABRT** signálu. Další informace o chování rušení naleznete v tématu [_set_abort_behavior](set-abort-behavior.md).

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

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
