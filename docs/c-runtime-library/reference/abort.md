---
title: "Abort – | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- abort
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
- Abort
dev_langs:
- C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02e8c81ef539dc2f078a3b120ca673a0ef612779
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="abort"></a>abort

Zruší aktuální proces a vrátí kód chyby.

> [!NOTE]
> Nepoužívejte tuto metodu a ukončí se na aplikaci Microsoft Store nebo aplikace pro univerzální platformu Windows (UWP), s výjimkou testování nebo ladění scénáře. Zavřete aplikaci ve Store způsoby programový nebo uživatelského rozhraní nejsou povolené podle požadavků [Microsoft Store zásady](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```c
void abort( void );
```

## <a name="return-value"></a>Návratová hodnota

`abort` nevrátí volající proces řízení. Ve výchozím nastavení, vyhledává signál obslužné rutiny přerušení a vyvolá `SIGABRT` je-li nastavena. Potom `abort` ukončí aktuální proces a vrátí ukončovací kód nadřazeného procesu.

## <a name="remarks"></a>Poznámky

**Microsoft Specific**

Ve výchozím nastavení, pokud je aplikace vytvořené s nástroji knihovně spuštění ladění `abort` rutiny zobrazí chybovou zprávu před `SIGABRT` je vyvolána. Pro aplikace konzoly, spuštěna v režimu konzoly, je zpráva odeslána na `STDERR`. Desktopové aplikace systému Windows a konzole aplikace běžící v režimu zobrazení v okně zobrazení zprávy v okně se zprávou. K potlačení zprávy, použijte [_set_abort_behavior –](../../c-runtime-library/reference/set-abort-behavior.md) zrušte `_WRITE_ABORT_MSG` příznak. Zpráva zobrazí závisí na verzi modulu runtime prostředí použít. Pro aplikace vytvořené pomocí nejnovější verze aplikace Visual C++ zpráva vypadá takto:

> Byla volána R6010 - abort()

Tato zpráva zobrazila v předchozích verzích běhové knihovny jazyka C:

> Tato aplikace vyžaduje modul Runtime ukončen neobvyklým způsobem. Další informace získáte tým podpory aplikace.

Když program kompiluje v režimu ladění, zobrazí se v možnosti **Abort**, **opakujte**, nebo **Ignorovat**. Pokud se uživatel rozhodne **Abort**, program okamžitě ukončí a vrátí ukončovací kód 3. Pokud se uživatel rozhodne **opakujte**, ladicí program je volána pro ladění za běhu, pokud je k dispozici. Pokud se uživatel rozhodne **Ignorovat**, `abort` pokračuje normálním zpracování.

V sestavení pro ladění a prodejní `abort` zkontroluje, zda je nastaven obslužné rutiny přerušení signál. Pokud obslužná rutina signál jiné než výchozí nastavená, `abort` volání `raise(SIGABRT)`. Použití [signál](../../c-runtime-library/reference/signal.md) funkce pro přidružení přerušení signál obslužné rutiny funkce s `SIGABRT` signál. Můžete provést vlastní akce – například vyčištění prostředků nebo protokolování informací – a ukončete aplikaci pomocí vlastní kód chyby v obslužné rutiny. Pokud je definována žádná obslužná rutina vlastní signál, `abort` nevyvolá `SIGABRT` signál.

Ve výchozím nastavení v sestavení bez ladění aplikací, plocha nebo konzoly `abort` poté vyvolá mechanismus Windows Error Reporting Service (dříve označované jako zotavení po havárii. Watson) do sestav chyb společnosti Microsoft. Toto chování můžete povolit nebo zakázat voláním `_set_abort_behavior` a nastavení nebo maskování `_CALL_REPORTFAULT` příznak. Když je nastavený příznak, systém Windows zobrazí okno se zprávou, která má text něco jako "Problém způsobil, že program přestane fungovat správně." Uživatel může vybrat, má být vyvolán ladicí program s **ladění** tlačítko, nebo zvolte **ukončení programu** tlačítko Ukončit aplikaci s kódem chyby, která je definována v operačním systému.

Pokud není vyvolána o chybách systému Windows obslužná rutina, pak `abort` volání [_exit –](../../c-runtime-library/reference/exit-exit-exit.md) ukončit proces řízení 3 a vrátí kód ukončení nadřazeného procesu nebo operačního systému. `_exit` Vyprázdní vyrovnávací paměti datového proudu nebo provést `atexit` / `_onexit` zpracování.

Další informace o ladění CRT najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

**Konkrétní Microsoft end**

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`abort`|\<Process.h > nebo \<stdlib.h >|

## <a name="example"></a>Příklad

Následující program pokusí otevřít soubor a zruší, pokud se nezdaří pokus.

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

[Použití funkce abort](../../cpp/using-abort.md)  
[abort – funkce](../../c-language/abort-function-c.md)  
[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)  
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)  
[raise](../../c-runtime-library/reference/raise.md)  
[signal](../../c-runtime-library/reference/signal.md)  
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)  
[_DEBUG](../../c-runtime-library/debug.md)  
[_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md)  

