---
title: Řízení procesů a prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c314decf15886f8d99ed8be3b7bafe4fff3e36b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085755"
---
# <a name="process-and-environment-control"></a>Řízení procesů a prostředí

Pomocí rutiny řízení procesů ke spuštění, zastavení a spravovat procesy v rámci programu. Rutiny řízení prostředí využít k získání a změnit informace o prostředí operačního systému.

## <a name="process-and-environment-control-functions"></a>Proces a funkce ovládacího prvku prostředí

|Rutina|Použití|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Přerušit proces bez vyprázdnění vyrovnávacích pamětí nebo volání funkcí registrovaných **atexit** a **_onexit**|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Test pro došlo k logické chybě|
|[_ASSERT, _asserte –](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobně jako **vyhodnocení**, ale k dispozici pouze v ladicích verzí knihoven runtime|
|[atexit](../c-runtime-library/reference/atexit.md)|Rutiny plánu pro spuštění při ukončení programu|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Vytvořit nové vlákno v procesu operačního systému Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Provedení **ukončit** postupy ukončení (jako je vyprazdňování vyrovnávací paměti), pak se vraťte ovládací prvek do volajícího programu bez ukončení procesu|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Provedení **_exit** postupy ukončení, vrátíte se ovládací prvek do volajícího programu bez ukončení procesu|
|[_cwait](../c-runtime-library/reference/cwait.md)|Počkejte, až do doby ukončení jiný proces|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Ukončení vlákna operačního systému Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Spuštění nového procesu se seznam argumentů.|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Spuštění nového procesu se seznam argumentů a mají prostředí|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Spuštění nového procesu pomocí **cesta** seznamu proměnných a argumentů|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Spuštění nového procesu pomocí **cesta** proměnné prostředí a seznam argumentů.|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Spuštění nového procesu s pole argumentů|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Spuštění nového procesu s argumentem pole a mají prostředí|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Spuštění nového procesu pomocí **cesta** proměnných a argumentů pole|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Spuštění nového procesu pomocí **cesta** proměnné prostředí a pole argumentů|
|[ukončení](../c-runtime-library/reference/exit-exit-exit.md)|Volání funkcí registrovaných **atexit** a **_onexit**, vyprázdní všechny vyrovnávací paměti, zavřete všechny otevřít soubory a ukončit proces|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Ukončí proces okamžitě, bez volání **atexit** nebo **_onexit** nebo vyprazdňování vyrovnávací paměti|
|[GETENV _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s – _wgetenv_s –](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Získat hodnotu proměnné prostředí|
|[_getpid](../c-runtime-library/reference/getpid.md)|Získat číslo ID procesu|[System::Diagnostics::Process::ID](https://msdn.microsoft.com/library/system.diagnostics.process.id.aspx)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Obnovení uložit prostředí zásobníku; použít ke spuštění nejsou místní **goto**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Rutiny plánu pro spuštění při ukončení programu; použijte pro kompatibilitu s Microsoft C/C++ version 7.0 a starší|
|[_pclose](../c-runtime-library/reference/pclose.md)|Počkejte nový příkazový procesor a zavřete datový proud na přidruženého kanálu|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Tisk chybová zpráva|
|[_pipe](../c-runtime-library/reference/pipe.md)|Vytvořit kanál pro čtení a zápis|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Vytvoření kanálu a spusťte příkaz|
|[_putenv _wputenv](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s _wputenv_s –](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Přidat nebo změnit hodnotu proměnné prostředí|
|[raise](../c-runtime-library/reference/raise.md)|Odesílání signálu do volajícího procesu|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Uložit prostředí zásobníku použít ke spuštění jiných místní **goto**|
|[signal](../c-runtime-library/reference/signal.md)|Zpracování signálu přerušení|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Vytvoření a spuštění nového procesu s určený seznam argumentů|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Vytvoření a spuštění nového procesu s určený seznam argumentů a prostředí|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Vytvoření a spuštění nového procesu pomocí **cesta** proměnné a zadaný seznam argumentů|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Vytvoření a spuštění nového procesu pomocí **cesta** proměnná, zadaný prostředí a seznam argumentů.|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Vytvoření a spuštění nového procesu s poli zadaného argumentu|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Vytvoření a spuštění nového procesu pomocí zadaného prostředí a pole argumentů|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Vytvoření a spuštění nového procesu pomocí **cesta** proměnná a pole zadaného argumentu|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Vytvoření a spuštění nového procesu pomocí **cesta** proměnná, zadaný prostředí a pole argumentů|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Spusťte příkaz operačního systému|

V operačním systému Windows je ekvivalentní trdliště proces spuštěný proces. Můžete použít jakýkoli proces **_cwait** čekání na jiný proces, pro který se označuje ID procesu.

Rozdíl mezi **_exec** a **_spawn** rodiny je, že **_spawn** funkce může vrátit ovládací prvek z nového procesu do volajícího procesu. V **_spawn** funkce volajícího procesu a nový proces se nacházejí v paměti není-li **_P_OVERLAY** určena. V **_exec** funkce, nový proces překrytí zpracovat volání ovládacího prvku nelze vrátit do volajícího procesu, pokud dojde k chybě při pokusu o spuštění nového procesu.

Rozdíly mezi funkcemi v **_exec** řady, jakož i z těch, které v **_spawn** řady, zahrnují metodu vyhledání soubor, který má být proveden, protože nový proces, formulář v nástrojích pro které argumenty jsou předány do nového procesu a způsob nastavení prostředí, jak je znázorněno v následující tabulce. Použijte funkci, která předá seznam argumentů, když počet argumentů je konstantní nebo známý v době kompilace. Použijte funkci, která předává ukazatel na pole obsahující argumenty, pokud je počet argumentů, které má být stanovena v době běhu. Informace v následující tabulce platí taky pro protějšky širokého znaku **_spawn** a **_exec** funkce.

### <a name="spawn-and-exec-function-families"></a>_spawn a _exec rodiny – funkce

|Funkce|Použít proměnnou cesty k souboru|Konvence předávání argumentů|Nastavení prostředí|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl**, **_spawnl**|Ne|Seznam|Zděděno z volající proces.|
|**_execle –**, **_spawnle**|Ne|Seznam|Ukazatel na tabulce prostředí pro nový proces, předá jako poslední argument|
|**_execlp –**, **_spawnlp –**|Ano|Seznam|Zděděno z volající proces.|
|**_execvpe**, **_spawnvpe**|Ano|Pole|Ukazatel na tabulce prostředí pro nový proces, předá jako poslední argument|
|**_execlpe –**, **_spawnlpe –**|Ano|Seznam|Ukazatel na tabulce prostředí pro nový proces, předá jako poslední argument|
|**_execv**, **_spawnv**|Ne|Pole|Zděděno z volající proces.|
|**_execve**, **_spawnve –**|Ne|Pole|Ukazatel na tabulce prostředí pro nový proces, předá jako poslední argument|
|**_execvp –**, **_spawnvp**|Ano|Pole|Zděděno z volající proces.|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
