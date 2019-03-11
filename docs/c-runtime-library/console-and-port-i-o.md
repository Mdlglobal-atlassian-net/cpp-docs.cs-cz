---
title: I/O konzoly a portu
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
ms.openlocfilehash: 55f97a70f2ce12f6363d234e9bbc9384d7ee9fe1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752373"
---
# <a name="console-and-port-io"></a>I/O konzoly a portu

Tyto rutiny čtení a zápis na konzole nebo na zadaný port. Vstupní a výstupní rutiny konzole nejsou kompatibilní s datový proud vstupně-výstupních operací nebo rutiny nízké úrovně knihoven vstupně-výstupních operací. Konzoly nebo port nemusí být otevřena nebo zavřena před prováděním vstupně-výstupních operací, takže v této kategorii nejsou žádné rutiny otevřít nebo zavřít. Výstup z těchto funkcí v operačních systémech Windows, vždy směrovala na konzole a nelze přesměrovat.

## <a name="console-and-port-io-routines"></a>Konzoly a portu vstupní a výstupní rutiny

|Rutina|Použití|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s, _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Přečtěte si řetězec z konzoly|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Zapište formátovaná data do konzoly|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|Zápis řetězců do konzoly|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Čtení formátovaných dat z konzoly|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Čtení znaků z konzoly|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Čtení znaků z konzoly a odezvu|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Jeden bajt četlo zadaný port vstupně-výstupních operací|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|Čtení double word ze zadaný port vstupně-výstupních operací|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|2bajtový slovo četlo zadaný port vstupně-výstupních operací|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Vyhledat stisk klávesy na konzole; použití před pokusem o čtení z konzoly|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|Zadaný port vstupně-výstupních operací zápisu jeden bajt|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|Zadaný port vstupně-výstupních operací zápisu double word|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Zápis do zadaný port vstupně-výstupních operací aplikace word|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Zápis znaků do konzoly|
|[_ungetch _ungetwch –](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|Čtení z konzoly, aby se stal další znak přečtený "Unget –" poslední znak|

## <a name="see-also"></a>Viz také:

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
