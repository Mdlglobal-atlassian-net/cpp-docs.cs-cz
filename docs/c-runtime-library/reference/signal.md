---
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 232bf7bc518907db8744fbb85e0f3a33c9296006
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625856"
---
# <a name="signal"></a>signal

Nastaví zpracování signálu přerušení.

> [!IMPORTANT]
> Nepoužívejte tuto metodu k ukončení aplikace Microsoft Store, s výjimkou scénářů testování nebo ladění. Programové a uživatelské možnosti pro zavření aplikace ze Storu nejsou povolené podle [zásad Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Parametry

*SIG*<br/>
Hodnota signálu

*func*<br/>
Druhý parametr je ukazatel na funkci, která má být provedena. První parametr je hodnota signálu a druhý parametr je dílčí kód, který lze použít, pokud je první parametr SIGFPE.

## <a name="return-value"></a>Návratová hodnota

**signál** vrací předchozí hodnotu Func, která je přidružena k dané signalizaci. Například pokud byla předchozí hodnota *Func* **SIG_IGN**, návratová hodnota je také **SIG_IGN**. Návratová hodnota **SIG_ERR** označuje chybu. v takovém případě je **errno** nastaveno na **EINVAL**.

Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Funkce **signálu** umožňuje procesu zvolit jeden z několika způsobů, jak zpracovat signál přerušení z operačního systému. Argument *SIG* je přerušení, ke kterému se **signál** odpoví; musí to být jedna z následujících konstant manifestu, které jsou definovány v signálu. Y.

|hodnota *SIG*|Popis|
|-----------------|-----------------|
|**SIGABRT**|Abnormální ukončení|
|**SIGFPE**|Chyba s plovoucí desetinnou čárkou|
|**SIGILL**|Neplatná instrukce|
|**SIGINT**|Signál CTRL + C|
|**SIGSEGV**|Neplatný přístup k úložišti|
|**SIGTERM**|Žádost o ukončení|

Pokud *SIG* není jedna z výše uvedených hodnot, je vyvolána obslužná rutina neplatného parametru, jak je definováno v [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **SIG_ERR**.

Ve výchozím nastavení **signál** ukončí volající program s ukončovacím kódem 3 bez ohledu na hodnotu *SIG*.

> [!NOTE]
> **SIGINT** se nepodporuje pro žádnou aplikaci Win32. Pokud dojde k přerušení CTRL + C, operační systémy Win32 vygenerují nové vlákno, aby se toto přerušení zpracovalo zvlášť. To může způsobit, že aplikace s jedním vláknem, jako je například jedna v systému UNIX, bude mít multithreading a způsobit neočekávané chování.

Argument *Func* je adresa pro obslužnou rutinu signálu, kterou zapisujete, nebo na jednu z předdefinovaných konstant **SIG_DFL** nebo **SIG_IGN**, která jsou také definována v signálu. Y. Pokud *Func* je funkce, je nainstalována jako obslužná rutina signálu pro daný signál. Prototyp obslužné rutiny signálu vyžaduje jeden formální argument *SIG*typu **int**. Pokud dojde k přerušení, operační systém poskytne skutečný argument pomocí *SIG* . argument je signál, který vygeneroval přerušení. Proto můžete použít šest konstant manifestu (uvedených v předchozí tabulce) v obslužné rutině signálu k určení toho, ke kterému přerušení došlo, a provést odpovídající akci. Například **můžete zavolat dvakrát** pro přiřazení stejné obslužné rutiny dvěma různým signálům a potom otestovat argument *SIG* v obslužné rutině, aby se v závislosti na přijatém signálu převzaly různé akce.

Pokud testujete výjimky s plovoucí desetinnou čárkou (**SIGFPE**), funkce *Func* odkazuje na funkci, která přebírá volitelný druhý argument, který je jednou z několika konstant MANIFESTŮ definovaných v typu float. H, ve tvaru **FPE_xxx**. Když dojde k signálu **SIGFPE** , můžete otestovat hodnotu druhého argumentu a určit tak druh výjimky s plovoucí desetinnou čárkou a následně provést příslušné akce. Tento argument a jeho možné hodnoty jsou rozšíření společnosti Microsoft.

U výjimek s plovoucí desetinnou čárkou se hodnota *Func* neresetuje, když je signál přijat. Chcete-li provést obnovení z výjimek s plovoucí desetinnou čárkou, použijte klauzule try/except pro ohraničení operací s plovoucí desetinnou čárkou. Je také možné provést obnovení pomocí [setjmp](setjmp.md) s [longjmp](longjmp.md). V obou případech volající proces pokračuje v provádění a opustí stav s plovoucí desetinnou čárkou procesu, který není definován.

Pokud se obslužná rutina signálu vrátí, volající proces pokračuje v provádění hned za bodem, ve kterém přijal signál přerušení. To platí bez ohledu na druh signálu nebo provozní režim.

Před provedením zadané funkce je hodnota *Func* nastavena na **SIG_DFL**. Další signál přerušení je považován za popsaný pro **SIG_DFL**, pokud v případě volání **návěstí** neurčí jiné. Tuto funkci můžete použít k resetování signálů ve volané funkci.

Vzhledem k tomu, že rutiny obslužné rutiny jsou obvykle volány asynchronně, když dojde k přerušení, funkce obslužné rutiny signálu může získat řízení, když je běhová operace nekompletní a je v neznámém stavu. Následující seznam shrnuje omezení, která určují funkce, které můžete použít v rutině obslužných rutin signálu.

- Neprovádějte vystavení nízké úrovně nebo STDIO. Rutiny H v/v (například **printf** nebo **fread**).

- Nevolejte rutiny haldy ani žádné rutiny, které používají rutiny haldy (například " **_strdup** **",** nebo **_putenv**). Další [informace najdete v tématu.](malloc.md)

- Nepoužívejte žádné funkce, které generují systémové volání (například **_getcwd** nebo **Time**).

- Nepoužívejte **longjmp** , pokud není přerušení způsobeno výjimkou plovoucí desetinné čárky (to znamená, že *SIG* je **SIGFPE**). V takovém případě nejprve znovu inicializujte balíček s plovoucí desetinnou čárkou pomocí volání **_fpreset**.

- Nepoužívejte žádné rutiny překryvných operací.

Program musí obsahovat kód s plovoucí desetinnou čárkou, pokud je třeba zachytit výjimku **SIGFPE** pomocí funkce. Pokud váš program nemá kód s plovoucí desetinnou čárkou a vyžaduje kód pro zpracování signálu v běhové knihovně, stačí deklarovat nestálou dvojitou hodnotu a inicializovat ji na nulu:

```C
volatile double d = 0.0f;
```

Signály **SIGILL** a **SIGTERM** nejsou vygenerovány v systému Windows. Jsou součástí kompatibility ANSI. Proto můžete nastavit obslužné rutiny signálu pro tyto signály pomocí **signálu**a také můžete tyto signály explicitně generovat voláním metody [vyvolat](raise.md).

Nastavení signálu se nezachovají v sedefinovaných procesech, které jsou vytvořené voláními funkcí [_exec](../../c-runtime-library/exec-wexec-functions.md) nebo [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) . Nastavení signálu se obnoví na výchozí hodnoty nového procesu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**signal**|\<Signal. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít **signál** k přidání nějakého vlastního chování do signálu **SIGABRT** . Další informace o chování přerušování najdete v tématu [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>

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

Výstup závisí na používané verzi modulu runtime, zda je aplikace Konzolová aplikace nebo aplikace systému Windows a nastavení registru systému Windows. V případě konzolové aplikace může být do stderr odesílána například následující zpráva:

```Output
Debug Error!

Program: c:\Projects\crt_signal\Debug\crt_signal.exe

R6010

- abort() has been called
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
