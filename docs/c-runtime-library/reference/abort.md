---
title: přerušit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
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
ms.workload:
- cplusplus
ms.openlocfilehash: bc7aefdac322ca8b34bccd2e377534ed1eca47e8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402709"
---
# <a name="abort"></a>abort

Přeruší aktuální proces a vrátí kód chyby.

> [!NOTE]
> Nepoužívejte tuto metodu k vypnutí aplikace Microsoft Store nebo aplikace pro univerzální platformu Windows (UPW), s výjimkou testování nebo ladění scénářů. Zavření aplikace pro Store způsoby programátorské nebo uživatelské rozhraní nejsou povoleny podle [zásady Microsoft Store](/legal/windows/agreements/store-policies). Další informace najdete v tématu [životní cyklus aplikace UPW](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void abort( void );
```

## <a name="return-value"></a>Návratová hodnota

**přerušit** nevrátí ovládací prvek do volajícího procesu. Ve výchozím nastavení, zkontroluje obslužné rutiny přerušení signálu a vyvolá `SIGABRT` je-li nastavena. Potom **přerušit** ukončí aktuální proces a vrátí kód ukončení nadřazenému procesu.

## <a name="remarks"></a>Poznámky

**Specifické pro Microsoft**

Ve výchozím nastavení, když je aplikace sestavena s běhovou ladicí knihovnou **přerušit** rutina zobrazí chybovou zprávu před `SIGABRT` je vyvolána. Pro aplikace konzoly spuštěné v režimu konzoly, je zpráva odeslána `STDERR`. Aplikace klasické pracovní plochy Windows a aplikace konzoly spuštěné v režimu zobrazení v okně zobrazí zpráva v okně se zprávou. Chcete-li potlačit tuto zprávu, použijte [_set_abort_behavior](set-abort-behavior.md) zrušte `_WRITE_ABORT_MSG` příznak. Zobrazená zpráva závisí na verzi běhového prostředí. Pro aplikace vytvořené pomocí nejnovější verze aplikace Visual C++ zpráva vypadá takto:

> Byla volána R6010 - abort()

V předchozích verzích běhové knihovny jazyka C byla zobrazena tato zpráva:

> Tato aplikace vydala požadavek modulu Runtime, aby ji ukončil neobvyklým způsobem. Kontaktujte prosím tým podpory vaší aplikace pro další informace.

Při kompilaci programu v režimu ladění, okno se zprávou zobrazí možnosti pro **přerušit**, **opakujte**, nebo **Ignorovat**. Pokud uživatel zvolí **přerušit**, program okamžitě ukončí a vrátí kód ukončení 3. Pokud uživatel zvolí **opakujte**, ladicí program je vyvolán pro ladění just-in-time, pokud je k dispozici. Pokud uživatel zvolí **Ignorovat**, **přerušit** pokračuje v normálním zpracování.

V maloobchodních a ladicích sestaveních **přerušit** zkontroluje, zda je nastavena obslužná rutina přerušení signálu. Pokud je nastavena obslužná rutina signálu než výchozí, **přerušit** volání `raise(SIGABRT)`. Použití [signál](signal.md) funkce pro přidružení přerušení signálu rutinu s `SIGABRT` signálu. Můžete provést vlastní akce – například vyčištění prostředků nebo protokolování informací – a ukončit aplikaci s vlastním kódem chyby ve funkci obslužné rutiny. Pokud není definován žádný popisovač vlastního signálu, **přerušit** nevyvolá `SIGABRT` signálu.

Ve výchozím nastavení v sestaveních bez ladění aplikací konzoly nebo stolního počítače **přerušit** pak vyvolá mechanismus Windows Error Reporting Service (dříve označovaný jako zotavení po havárii. Watson) na zprávy o selhání společnosti Microsoft. Toto chování může být povoleno nebo zakázáno voláním `_set_abort_behavior` a nastavením nebo maskováním `_CALL_REPORTFAULT` příznak. Když je příznak nastaven, Windows zobrazí okno se zprávou s textem typu "Problém způsobil, že program přestal správně fungovat." Uživatel může rozhodnout pro vyvolání ladicího programu pomocí **ladění** tlačítko, nebo zvolte **ukončit program** tlačítko Ukončit aplikaci s chybovým kódem, který je definován v operačním systému.

Pokud není vyvolána obslužná rutina hlášení chyb Windows, pak **přerušit** volání [_exit](exit-exit-exit.md) k ukončení procesu s ukončovací kód 3 a vrátí kontrolu nadřazenému procesu nebo operačního systému. `_exit` Vyprázdní vyrovnávací paměť datového proudu nebo proveďte `atexit` / `_onexit` zpracování.

Další informace o ladění CRT naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

**Specifické pro end Microsoft**

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**abort**|\<Process.h > nebo \<stdlib.h >|

## <a name="example"></a>Příklad

Následující program pokusí otevřít soubor a přeruší se, pokud se pokus nezdaří.

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

## <a name="see-also"></a>Viz také:

[Použití funkce abort](../../cpp/using-abort.md)  
[abort – funkce](../../c-language/abort-function-c.md)  
[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)  
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)  
[exit, _Exit, _exit](exit-exit-exit.md)  
[raise](raise.md)  
[signal](signal.md)  
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)  
[_DEBUG](../../c-runtime-library/debug.md)  
[_set_abort_behavior](set-abort-behavior.md)  