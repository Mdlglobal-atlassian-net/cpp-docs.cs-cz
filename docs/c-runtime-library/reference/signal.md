---
title: signál | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2018
ms.technology:
- cpp-standard-libraries
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
ms.workload:
- cplusplus
ms.openlocfilehash: a87978ec3b0840be6ab1779af86765208c80832c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416817"
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

*SIG*<br/>
Hodnota signál.

*Func*<br/>
Druhý parametr je ukazatel na funkci spouštění. První parametr je hodnota signál a druhý parametr je dílčí kód, který lze použít při první parametr je sigfpe –.

## <a name="return-value"></a>Návratová hodnota

**signál** vrátí předchozí hodnotu func, který je spojen s danou signál. Například pokud předchozí hodnotu *func* byla **sig_ign –**, vrácená hodnota je také **sig_ign –**. Vrácená hodnota **SIG_ERR** označuje chybu; v takovém případě **errno** je nastaven na **einval –**.

V tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o návratové kódy.

## <a name="remarks"></a>Poznámky

**Signál** funkce umožňuje proces vyberte jednu z několik způsobů, jak zpracovat signál přerušení z operačního systému. *Sig* argument je přerušení, ke kterému **signál** reaguje; musí mít jednu z následujících manifestu konstant, které jsou definovány v SIGNÁL. H.

|*SIG* hodnota|Popis|
|-----------------|-----------------|
|**SIGABRT –**|Abnormální ukončení|
|**SIGFPE –**|Chyba s plovoucí desetinnou čárkou|
|**SIGILL –**|Neplatná instrukce|
|**SIGINT –**|CTRL + C signál|
|**SIGSEGV –**|Přístup k úložišti neplatný|
|**SIGTERM –**|Žádost o ukončení|

Pokud *sig* není jedním z výše uvedené hodnoty, je vyvolána obslužná rutina neplatný parametr, jak jsou definovány v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **SIG_ERR**.

Ve výchozím nastavení **signál** ukončí volací program s ukončovacím kódem 3, bez ohledu na hodnotu *sig*.

> [!NOTE]
> **Sigint –** není podporován pro všechny aplikace typu Win32. Když dojde k přerušení CTRL + C, operační systémy Win32 generovat nové vlákno konkrétně zpracování této přerušení. To může způsobit jedním vláknem aplikaci, například ten, který v systému UNIX se stane s více vlákny a způsobit neočekávané chování.

*Func* argument je adresu na signál obslužnou rutinu, která můžete psát, nebo na jednu z předdefinovaných konstanty **sig_dfl –** nebo **sig_ign –**, která je definována v SIGNÁL. H. Pokud *func* je funkce, je nainstalován jako obslužná rutina signál pro danou signál. Obslužná rutina signál prototypu vyžaduje jeden argument formální, *sig*, typu **int**. Operační systém poskytuje skutečné argument prostřednictvím *sig* když dojde k přerušení; argument je signál, která generuje přerušení. Proto můžete šesti manifestu konstanty (uvedené v předchozí tabulce) ve vaší obslužné rutiny signál k určení které přerušení došlo k chybě a proveďte příslušnou akci. Například můžete volat **signál** na dvou různých signály přiřadit stejné obslužné rutiny a otestujte dvakrát *sig* argument v rutině k provádění různých akcí podle signál přijata.

Pokud testujete výjimky s plovoucí desetinnou čárkou (**sigfpe –**), *func* odkazuje na funkci, která přebírá volitelné druhý argument, který je jedním z několika manifestu konstanty definované v FLOAT. H formuláře **FPE_xxx**. Když **sigfpe –** signál dojde, můžete otestovat hodnotu druhý argument, abyste zjistili druh výjimek plovoucí desetinné čárky a proveďte příslušnou akci. Tento argument a jeho možné hodnoty jsou rozšíření Microsoft.

S plovoucí desetinnou čárkou výjimky, hodnota *func* není resetovat, když je obdržena signál. Obnovit z s plovoucí desetinnou čárkou výjimky, zkuste použít / s výjimkou bodu klauzule k obklopit procedura operace. Je také možné obnovit pomocí [setjmp](setjmp.md) s [longjmp](longjmp.md). V obou případech volající proces obnoví spuštění a opustí s plovoucí desetinnou čárkou stav procesu není definovaná.

Pokud obslužná rutina signál vrátí, volající proces obnoví spuštění hned za bod, ve kterém přijala signál přerušení. To platí bez ohledu na druh signál nebo provozním režimu.

Před provedením zadaná funkce hodnotu *func* je nastaven na **sig_dfl –**. Další signál přerušení považuje, jak je popsáno pro **sig_dfl –**, pokud uplynulého volat na **signál** neurčí jinak. Tato funkce slouží k resetování signály v volaná funkce.

Protože rutiny signál – obslužná rutina se obvykle říká asynchronně, když dojde přerušení, může funkce obslužných rutin signál k řízení při spuštění operace nekompletní a v neznámém stavu. Následující seznam shrnuje omezení, které určují, funkcích, které můžete použít v signál rutiny ovladače.

- To není problém nižší úrovně nebo STDIO. H vstupní a výstupní rutiny (například **printf** nebo **fread –**).

- Nevolejte haldy rutiny nebo všechny rutiny, která používá rutiny haldy (například **malloc –**, **_strdup –**, nebo **_putenv –**). V tématu [malloc –](malloc.md) Další informace.

- Nepoužívejte všechny funkce, která generuje volání systému (například **_getcwd –** nebo **čas**).

- Nepoužívejte **longjmp** Pokud přerušení je způsobena výjimek plovoucí desetinné čárky (tedy *sig* je **sigfpe –**). V takovém případě nejprve inicializovat balíček s plovoucí desetinnou čárkou s použitím volání **_fpreset –**.

- Nepoužívejte všechny rutiny překrytí.

Program musí obsahovat s plovoucí desetinnou čárkou kódu, pokud je na depeše **sigfpe –** výjimky pomocí funkce. Pokud program nemá s plovoucí desetinnou čárkou kód a kód pro zpracování signál běhové knihovny vyžaduje, jenom deklarovat volatile dvojitou a provést jeho inicializaci na nulu:

```C
volatile double d = 0.0f;
```

**Sigill –** a **SIGTERM –** signály, které nejsou generované v rámci systému Windows. Jsou zahrnuté pro kompatibilitu ANSI. Proto můžete nastavit signál obslužné rutiny pro tyto signály pomocí **signál**, a také explicitně vygenerovat tyto signály voláním [vyvolat](raise.md).

V vytvářený procesy, které jsou vytvořené pomocí volání nejsou zachována nastavení signál [_exec](../../c-runtime-library/exec-wexec-functions.md) nebo [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkce. Signál nastavení se obnoví na výchozí hodnoty v nový proces.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**signal**|\<signal.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat **signál** přidat některé vlastní chování **sigabrt –** signál. Další informace o chování přerušení najdete v tématu [_set_abort_behavior –](set-abort-behavior.md).

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

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
