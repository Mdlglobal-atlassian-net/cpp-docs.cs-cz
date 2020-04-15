---
title: Možnosti odkazů
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: ea71faab639a8c0a09d6e332618dd7e09159a4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351103"
---
# <a name="link-options"></a>Možnosti odkazů

Adresář CRT lib obsahuje řadu souborů s malými objekty, které umožňují specifické funkce CRT bez jakékoli změny kódu. Ty se nazývají "možnosti propojení", protože stačí je přidat do příkazového řádku linkeru, abyste je mohli používat.

Clr čistý režim verze těchto objektů jsou zastaralé v Sadě Visual Studio 2015 a nepodporované v Sadě Visual Studio 2017. Použijte běžné verze pro nativní a /clr kód.

|Nativní a /clr|Čistý režim|Popis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Nastaví výchozí režim překladu souborů na binární. Viz [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|neuvedeno|Poskytuje kontrolu zásobníku a alloca podporu při nepoužití CRT.|
|commode.obj|pcommode.obj|Nastaví příznak globálního potvrzení na "commit". Viz [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) a [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|neuvedeno|Inicializuje mta apartment během spuštění EXE, což umožňuje použití objektů COM v globálníinteligentní ukazatele. Vzhledem k tomu, že tato možnost nevrací odkaz na byt MTA během vypnutí, nepoužívejte jej pro knihovny DLL. Propojení s tímto je ekvivalentní včetně combase.h a definování _EXE_INITIALIZE_MTA. |
|fp10.obj|neuvedeno|Změní výchozí řízení přesnosti na 64 bitů. Viz [Podpora s plovoucí desetinnou tálicí](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Nastaví výchozí neplatnou obslužnou rutinu parametru, která neprovede žádnou akci, což znamená, že neplatné parametry předané funkcím CRT pouze nastaví chybovo a vrátí výsledek chyby.|
|legacy_stdio_float_rounding.obj|neuvedeno|Tisk hodnot s plovoucí desetinnou táž (například při použití [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)) s Windows 10 19041 Universal C Runtime byla stanovena. Nyní správně zaokrouhluje přesně reprezentovatelná čísla s plovoucí desetinnou desetinnou tágo a respektuje zaokrouhlení s plovoucí desetinnou desetinnou nebo druhou požadovanou [společností fesetenv](../c-runtime-library/reference/fesetenv1.md). Tato aktualizace chování je k dispozici ve Visual Studiu 2019 verze 16.2 a novější. Starší verze chování se používá v dřívějších verzích sady Visual Studio nebo poskytnutím této možnosti odkazu.|
|loosefpmath.obj|neuvedeno|Zajišťuje, že kód s plovoucí desetinnou čárou toleruje denormální hodnoty.|
|newmode.obj|pnewmode.obj|Způsobí, [že malloc](../c-runtime-library/reference/malloc.md) volat novou obslužnou rutinu na selhání. Viz [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md)a [relokace](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Zakáže veškeré zpracování argc a argv.|
|nochkclr.obj|neuvedeno|Neprovádí žádnou akci. Odebrat z projektu.|
|noenv.obj|pnoenv.obj|Zakáže vytváření prostředí uloženého v mezipaměti pro CRT.|
|nothrownew.obj|pnothrownew.obj|Umožňuje non-throwing verze new v CRT. Viz [nové a odstranit operátory](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Povolí rozšíření zástupných míst argumentů příkazového řádku. Viz [Rozbalení argumentů se zástupnými znaky](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Ve výchozím nastavení povolí národní prostředí pro všechna nová vlákna.|
|wsetargv.obj|pwsetargv.obj|Povolí rozšíření zástupných míst argumentů příkazového řádku. Viz [Rozbalení argumentů se zástupnými znaky](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Viz také

- [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
