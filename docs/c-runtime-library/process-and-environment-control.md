---
title: Řízení procesů a prostředí | Microsoft Docs
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
ms.openlocfilehash: e52284db986ec642724f97aae75a9af004339b40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="process-and-environment-control"></a>Řízení procesů a prostředí

Pomocí rutiny řízení procesů spuštění, zastavení a spravovat procesy z v rámci programu. Rutiny řízení prostředí použijte k získání a změnit informace o prostředí operačního systému.

## <a name="process-and-environment-control-functions"></a>Proces a funkce ovládacího prvku prostředí

|Rutina|Použití|
|-------------|---------|
|[abort](../c-runtime-library/reference/abort.md)|Proces přerušit bez vyprázdnění vyrovnávací paměti nebo volání funkcí registrovaných **atexit** a **_onexit –**|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|Test pro logická chyba|
|[_ASSERT, _asserte –](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobně jako **assert**, ale k dispozici pouze ve verzích ladicí běhové knihovny|
|[atexit](../c-runtime-library/reference/atexit.md)|Rutiny plán pro spouštění v ukončení programu|
|[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|Vytvořit nové vlákno u procesu operačního systému Windows|
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|Provedení **ukončete** ukončení procedur (například vyprázdnění vyrovnávací paměti), pak se vraťte ovládacího prvku do volací program bez proces se ukončuje|
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|Provedení **_exit –** ukončení postupy, pak se vraťte ovládacího prvku do volací program bez proces se ukončuje|
|[_cwait](../c-runtime-library/reference/cwait.md)|Počkejte, dokud jiný proces se ukončuje|
|[_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|Ukončení vlákna operačního systému Windows|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|Spustit nový proces s seznam argumentů|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|Spustit nový proces s seznam argumentů a vzhledem k tomu prostředí|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|Spuštění nové procesů pomocí **cesta** proměnné a argument seznamu|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|Spuštění nové procesů pomocí **cesta** dané prostředí a seznam argumentů proměnných|
|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|Spustit nový proces s pole argumentů|
|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|Spustit nový proces s polem argument a vzhledem k tomu prostředí|
|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|Spuštění nové procesů pomocí **cesta** proměnné a argument pole|
|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|Spuštění nové procesů pomocí **cesta** dané prostředí a pole argumentů proměnných|
|[Ukončení](../c-runtime-library/reference/exit-exit-exit.md)|Volání funkce registrovaných **atexit** a **_onexit –**, vyprázdnit všechny vyrovnávací paměti, zavřete všechny otevřené soubory a ukončení procesu|
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|Ukončit proces okamžitě bez volání **atexit** nebo **_onexit –** nebo abyste vyprázdnili vyrovnávací paměti|
|[GETENV –, _wgetenv –](../c-runtime-library/reference/getenv-wgetenv.md), [getenv_s –, _wgetenv_s –](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Získá hodnotu proměnné prostředí|
|[_getpid](../c-runtime-library/reference/getpid.md)|Získat číslo ID procesu|[System::Diagnostics::Process::ID](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|Obnovení uložit zásobníku prostředí; použít k provedení nejsou místní **goto – příkaz**|
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|Rutiny plán pro spouštění v ukončení programu; použijte pro kompatibilitu s Microsoft C/C++ version 7.0 a starší|
|[_pclose](../c-runtime-library/reference/pclose.md)|Počkejte nové procesor příkazů a zavřít datový proud v přidružené kanálu|
|[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)|Tisk – chybová zpráva|
|[_pipe](../c-runtime-library/reference/pipe.md)|Vytvoření kanálu pro čtení a zápis|
|[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)|Vytvoření kanálu a spusťte příkaz|
|[_putenv –, _wputenv –](../c-runtime-library/reference/putenv-wputenv.md), [_putenv_s –, _wputenv_s –](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Přidat nebo změnit hodnotu proměnné prostředí|
|[raise](../c-runtime-library/reference/raise.md)|Odesílat signál volající proces|
|[setjmp](../c-runtime-library/reference/setjmp.md)|Uložit zásobníku prostředí; použít k provedení bez místní **goto – příkaz**|
|[signal](../c-runtime-library/reference/signal.md)|Popisovač přerušení signál|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|Vytvoření a provedení nový proces s zadaného argumentu seznamu|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|Vytvoření a provedení nový proces s zadaného argumentu seznamu a prostředí|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|Vytvoření a spuštění nové procesů pomocí **cesta** proměnnou a zadaného argumentu seznamu|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|Vytvoření a spuštění nové procesů pomocí **cesta** proměnné, zadaný prostředí a seznam argumentů|
|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|Vytvoření a provedení nový proces s polem zadaného argumentu|
|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|Vytvoření a provedení nový proces pomocí zadaného prostředí a pole argumentů|
|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|Vytvoření a spuštění nové procesů pomocí **cesta** proměnnou a zadaného argumentu pole|
|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|Vytvoření a spuštění nové procesů pomocí **cesta** proměnné, zadaný prostředí a pole argumentů|
|[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)|Provedení příkazu operačního systému|

 V operačním systému Windows je proces spuštěný ekvivalentní trdliště proces. Můžete použít jakýkoli proces **_cwait –** čekání na jiný proces, pro který se označuje Identifikátor procesu.

 Rozdíl mezi **_exec** a **_spawn** rodiny je, že **_spawn** funkce může vrátit ovládací prvek z nový proces pro proces volání. V **_spawn** fungovat, volající proces a nový proces jsou k dispozici v paměti Pokud **_p_overlay –** je zadán. V **_exec** funkce, nový proces překrytí volání zpracovat, takže ovládacího prvku nelze vrátit k volání proces, pokud dojde k chybě při pokusu o spuštění provádění nový proces.

 Rozdíly mezi funkcí v **_exec** rodiny, jakož i z těch, které v **_spawn** rodiny, zahrnují způsob nasazení souboru spuštěny jako nový proces formuláře v které argumenty jsou předány nový proces a metodu, nastavení prostředí, jak je znázorněno v následující tabulce. Použijte funkci, která předá seznam argumentů, když počet argumentů je konstantní nebo známý v době kompilace. Použijte funkci, která předá ukazatele na pole obsahující argumenty, pokud počet argumentů je možné určit v době běhu. Informace v následující tabulce platí taky pro svými protějšky široká charakterová z **_spawn** a **_exec** funkce.

### <a name="spawn-and-exec-function-families"></a>Rodiny _spawn a _exec – funkce

|Funkce|Pomocí proměnné PATH vyhledejte soubor|Konvence předávání argumentů|Nastavení prostředí|
|---------------|--------------------------------------|----------------------------------|--------------------------|
|**_execl –**, **_spawnl –**|Ne|Seznam|Zděděno z volání procesu|
|**_execle –**, **_spawnle –**|Ne|Seznam|Ukazatel na tabulku prostředí pro nový proces jako poslední argument předaná|
|**_execlp –**, **_spawnlp –**|Ano|Seznam|Zděděno z volání procesu|
|**_execvpe –**, **_spawnvpe –**|Ano|Pole|Ukazatel na tabulku prostředí pro nový proces jako poslední argument předaná|
|**_execlpe –**, **_spawnlpe –**|Ano|Seznam|Ukazatel na tabulku prostředí pro nový proces jako poslední argument předaná|
|**_execv –**, **_spawnv –**|Ne|Pole|Zděděno z volání procesu|
|**_execve –**, **_spawnve –**|Ne|Pole|Ukazatel na tabulku prostředí pro nový proces jako poslední argument předaná|
|**_execvp –**, **_spawnvp –**|Ano|Pole|Zděděno z volání procesu|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
