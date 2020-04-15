---
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350916"
---
# <a name="abort"></a>abort

Přeruší aktuální proces a vrátí kód chyby.

> [!NOTE]
> Tuto metodu nepoužívejte k vypnutí aplikace pro Microsoft Store nebo univerzální platformy Windows (UPW), s výjimkou scénářů testování nebo ladění. Programové nebo způsoby, jak zavřít aplikaci store, nejsou povoleny v souladu se [zásadami Microsoft Storu](/legal/windows/agreements/store-policies). Další informace naleznete v [tématu Životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void abort( void );
```

## <a name="return-value"></a>Návratová hodnota

**abort** nevrátí řízení volajícímu procesu. Ve výchozím nastavení kontroluje obslužnou rutinu signálu přerušení a zvyšuje, `SIGABRT` pokud je nastavena. Potom **abort** ukončí aktuální proces a vrátí ukončovací kód nadřazenému procesu.

## <a name="remarks"></a>Poznámky

**Specifické pro Microsoft**

Ve výchozím nastavení, když je aplikace vytvořena s **abort** knihovnou ladění za `SIGABRT` běhu, rutina přerušení zobrazí chybovou zprávu před je aktivována. U konzolových aplikací spuštěné v režimu konzoly je zpráva odeslána společnosti `STDERR`. Aplikace klasické pracovní plochy a konzolové aplikace windows spuštěné v režimu s okny zobrazují zprávu v okně. Chcete-li zprávu [_set_abort_behavior](set-abort-behavior.md) potlačit, použijte `_WRITE_ABORT_MSG` _set_abort_behavior k vymazání příznaku. Zobrazená zpráva závisí na verzi použitého prostředí runtime. Pro aplikace vytvořené pomocí nejnovějších verzí visual c++ se zpráva podobá tomuto:

> R6010 - abort() byl volán

V předchozích verzích knihovny runtime C byla tato zpráva zobrazena:

> Tato aplikace požádala runtime ukončit neobvyklým způsobem. Další informace získáte od týmu podpory aplikace.

Když je program kompilován v režimu ladění, zobrazí se v okně se zprávou **možnosti Přerušit**, **Opakovat**nebo **Ignorovat**. Pokud uživatel zvolí **Abort**, program okamžitě ukončí a vrátí ukončovací kód 3. Pokud uživatel zvolí **Opakovat**, ladicí program je vyvolánpro just-in-time ladění, pokud je k dispozici. Pokud uživatel zvolí **Ignore**, **přerušení** pokračuje normální zpracování.

V maloobchodních i ladicích sestaveních **abort** a následnékontrole, zda je nastavena obslužná rutina signálu přerušení. Pokud je nastavena obslužná `raise(SIGABRT)`rutina signálu, která není výchozí, **přerušte** volání . Pomocí funkce [signálu](signal.md) přidružte k `SIGABRT` funkci obslužné rutiny signálu přerušení se signálem. Můžete provádět vlastní akce – například vyčistit prostředky nebo informace protokolu – a ukončit aplikaci s vlastním kódem chyby ve funkci obslužné rutiny. Pokud není definována žádná **abort** vlastní obslužná rutina signálu, `SIGABRT` abort nevyvolá signál.

Ve výchozím nastavení v neladicích sestaveních aplikací klasické pracovní plochy nebo konzoly **se přeruší** a potom vyvolá mechanismus služby zasílání zpráv o chybách systému Windows (dříve označovaný jako Dr. Watson), aby společnosti Microsoft nahlásil chyby. Toto chování lze povolit `_set_abort_behavior` nebo zakázat `_CALL_REPORTFAULT` voláním a nastavením nebo maskováním příznaku. Je-li příznak nastaven, systém Windows zobrazí okno se zprávou, které má text přibližně "Problém způsobil, že program přestal pracovat správně." Uživatel se může rozhodnout vyvolat ladicí program s tlačítkem **Ladění** nebo zvolit tlačítko **Zavřít program** pro ukončení aplikace s kódem chyby, který je definován operačním systémem.

Pokud není vyvolána obslužná rutina zasílání zpráv o chybách systému Windows, **potom přerušit** volání [_exit](exit-exit-exit.md) ukončit proces s ukončovacíkód 3 a vrátí řízení nadřazenému procesu nebo operačnímu systému. `_exit`nevyprázdní vyrovnávací `atexit` / `_onexit` paměti datového proudu nebo provést zpracování.

Další informace o ladění CRT naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

**Ukončit microsoft specifické**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Přerušení**|\<process.h> \<nebo stdlib.h>|

## <a name="example"></a>Příklad

Následující program se pokusí otevřít soubor a přeruší, pokud se pokus nezdaří.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>Viz také

[Používání příkazu abort](../../cpp/using-abort.md)<br/>
[přerušit funkci](../../c-language/abort-function-c.md)<br/>
[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
