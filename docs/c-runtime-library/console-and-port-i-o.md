---
title: I/O konzoly a portu
ms.date: 11/04/2016
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
ms.openlocfilehash: 5b4dc2a081ea11bd84d932f55b5b247de81f296a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443444"
---
# <a name="console-and-port-io"></a>I/O konzoly a portu

Tyto rutiny čtou a zapisují na konzolu nebo na určeném portu. Rutiny v/v konzoly nejsou kompatibilní s rutinami v/v streamu nebo v/v knihovny pro vstupně-výstupní operace s nízkou úrovní. Před provedením vstupu/výstupu není nutné otevřít ani zavřít konzolu nebo port, takže v této kategorii nejsou žádné otevřené ani zavřené rutiny. V operačních systémech Windows je výstup z těchto funkcí vždy směrován do konzoly a nelze jej přesměrovat.

## <a name="console-and-port-io-routines"></a>Rutiny I/O konzoly a portu

|Rutina|Použití|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Přečíst řetězec z konzoly|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md) _cwprintf_s_l|Zápis formátovaných dat do konzoly|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|Zapsat řetězec do konzoly|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md) _cwscanf_s_l|Čtení formátovaných dat z konzoly|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Přečíst znak z konzoly|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Načíst znak z konzoly a zobrazit jeho odezvu|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Načte jeden bajt ze zadaného vstupně-výstupního portu.|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|Číst dvojité slovo ze zadaného vstupně-výstupního portu|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Číst ze zadaného vstupně-výstupního portu slovo 2-Byte|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Vyhledat klávesovou zkratku v konzole; použijte před tím, než se pokusíte přečíst z konzoly.|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|Zápis jednoho bajtu do určeného vstupně-výstupního portu|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|Zapsat dvojité slovo do zadaného vstupně-výstupního portu|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Zapsat slovo do zadaného vstupně-výstupního portu|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Zapsat znak do konzoly|
|[_ungetch _ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|Poslední přečtený znak "unget" z konzoly, aby se staly dalším znakem|

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
