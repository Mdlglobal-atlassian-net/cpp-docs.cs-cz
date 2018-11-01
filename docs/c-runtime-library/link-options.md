---
title: Možnosti odkazů
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
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
ms.openlocfilehash: 8cd5513acd2617e784b2ec9fa203614b752e6076
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661822"
---
# <a name="link-options"></a>Možnosti odkazů

Adresáři lib CRT obsahuje několik souborů malých objektů, které umožňují specifické funkce CRT, bez jakékoli změny kódu. Nazývají se "možnosti odkaz" a protože stačí je přidat do příkazového řádku linkeru pro jejich použití.

Režim čisté verze CLR tyto objekty jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Použijte regulární verze pro kód nativní a/CLR.

|Nativní a/CLR|Režim čisté|Popis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Nastaví výchozí režim překladu souboru do binárního souboru. Zobrazit [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|není k dispozici|Poskytuje podporu kontrolou zásobníku a alloca bez použití CRT.|
|commode.obj|pcommode.obj|Nastaví globální příznak "Potvrdit". Zobrazit [fopen _wfopen –](../c-runtime-library/reference/fopen-wfopen.md) a [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|není k dispozici|Inicializuje objekt apartment MTA během spouštění EXE, což umožňuje použití objektů COM v globální inteligentní ukazatele. Protože tato možnost nevracení Postrádáte odkaz na objekt apartment MTA během vypínání, nepoužívejte ho pro knihovny DLL. Odkazování na to je ekvivalentní včetně combase.h a definování _EXE_INITIALIZE_MTA. |
|fp10.obj|není k dispozici|Výchozí přesnost ovládací prvek se změní na 64 bitů. Zobrazit [podpora plovoucí desetinné čárky](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Nastaví výchozí obslužná rutina neplatného parametru, který nemá žádný účinek, což znamená, že neplatné parametry předány do funkcí CRT se právě errno nastavení a vracení chybného výsledku.|
|loosefpmath.obj|není k dispozici|Zajišťuje, že číslo s plovoucí čárkou bod kódu toleruje hodnoty denormal.|
|newmode.obj|pnewmode.obj|Způsobí, že [malloc](../c-runtime-library/reference/malloc.md) novou obslužnou rutinu volání při selhání. Zobrazit [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md), a [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Zakáže zpracování argc a argv.|
|nochkclr.obj|není k dispozici|Neprovádí žádnou akci. Odeberte z projektu.|
|noenv.obj|pnoenv.obj|Zakazuje vytváření prostředí uložené v mezipaměti pro CRT.|
|nothrownew.obj|pnothrownew.obj|Umožňuje non-throwing. verze ve CRT. Zobrazit [nové a odstranit operátory](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Umožňuje rozšíření zástupného znaku argument příkazového řádku. Zobrazit [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Umožňuje vlákno národní prostředí pro všechna nová vlákna ve výchozím nastavení.|
|wsetargv.obj|pwsetargv.obj|Umožňuje rozšíření zástupného znaku argument příkazového řádku. Zobrazit [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Viz také:

- [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
