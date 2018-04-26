---
title: I/O konzoly a portu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5532b35e915f69927699ce9678d5bd5ffb5579
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="console-and-port-io"></a>I/O konzoly a portu

Tyto rutiny čtení a zápis na konzole nebo na zadaný port. Vstupní a výstupní rutiny konzoly nejsou kompatibilní s vstupně-výstupní datový proud nebo nízké úrovně vstupní a výstupní rutiny knihovny. V konzole nebo portu nemá chcete otevřít nebo zavřel před provádí vstupně-výstupních operací, proto nejsou žádné otevřené nebo zavřít rutiny v této kategorii. V operačních systémech Windows výstup z těchto funkcí je vždy směrovala ke konzole a nemůže být přesměrována.

## <a name="console-and-port-io-routines"></a>Vstupní a výstupní rutiny konzoly a portu

|Rutina|Použití|
|-------------|---------|
|[_cgets –, _cgetws –](../c-runtime-library/cgets-cgetws.md), [_cgets_s –, _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Řetězec pro čtení z konzoly|
|[_cprintf –, _cwprintf –](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s –, _cprintf_s_l –, _cwprintf_s –, _cwprintf_s_l –](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Zápis formátovaných dat do konzoly|
|[_cputs –](../c-runtime-library/reference/cputs-cputws.md)|Zápis řetězců do konzoly|
|[_cscanf –, _cwscanf –](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s –, _cscanf_s_l –, _cwscanf_s –, _cwscanf_s_l –](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Čtení formátovaných dat z konzoly|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Čtení znaků z konzoly|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Čtení znaků z konzoly a odezvu|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Přečtěte si jeden bajt z zadaný port vstupně-výstupních operací|
|[_inpd –](../c-runtime-library/inp-inpw-inpd.md)|Čtení z zadaný vstupně-výstupní port double aplikace word|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Čtení 2bajtová word z zadaný port vstupně-výstupních operací|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Zkontrolujte klávesu v konzole; Před pokusem o použít ke čtení z konzoly|
|[_outp –](../c-runtime-library/outp-outpw-outpd.md)|Zadaný port vstupně-výstupní operace zápisu jeden bajt|
|[_outpd –](../c-runtime-library/outp-outpw-outpd.md)|Zadaný port vstupně-výstupních operací zápisu double aplikace word|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Zadaný port vstupně-výstupních operací zápisu aplikace word|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Zápis znaků do konzoly|
|[_ungetch –, _ungetwch –](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|"Unget –" číst z konzoly, bude další znak, přečtěte si poslední znak.|

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
 [Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>