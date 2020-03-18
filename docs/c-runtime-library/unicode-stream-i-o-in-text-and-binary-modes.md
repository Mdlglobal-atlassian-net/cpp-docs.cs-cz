---
title: I/O proudu kódování Unicode v textovém a binárním režimu
ms.date: 11/04/2016
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: b41818bbb625a8c875771e86e3d82b74f4291e9f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444503"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>I/O proudu kódování Unicode v textovém a binárním režimu

V případě, že rutina vstupu/výstupu datového proudu sady Unicode (například **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws**nebo **fputws**) pracuje na souboru otevřeném v textovém režimu (výchozí), jsou dva druhy převodu znaků provedeny:

- Konverze Unicode na znakovou sadu MBCS nebo znakové sady MBCS na kódování Unicode. Pokud funkce vstupně-výstupních streamů v kódování Unicode funguje v textovém režimu, předpokládá se, že zdrojový nebo cílový Stream je sekvence vícebajtových znaků. Proto funkce vstupního streamu Unicode převádí vícebajtové znaky na velké znaky (jako by bylo volání funkce **mbtowc** ). Ze stejného důvodu funkce výstupní datové proudy Unicode převádějí velké znaky na vícebajtové znaky (jako při volání funkce **wctomb** ).

- Překlad návratového kanálu návratového řádku (CR-LF). K tomuto překladu dochází před převodem znakové sady MBCS-Unicode (pro vstupní funkce streamu Unicode) a po převodu Unicode-MBCS (pro výstupní funkce streamu Unicode). Během vstupu se každá kombinace kanálů pro návrat do řádku vrátí do jednoduchého znaku pro čárové kanály. Během výstupu se každý znak kanálu řádku převede na kombinaci pro návratovou čáru na řádku.

Pokud však funkce vstupně-výstupních datových proudů v kódování Unicode funguje v binárním režimu, předpokládá se, že se jedná o soubor Unicode a při vstupu nebo výstupu nedochází k převodu znaků CR-LF. Použijte instrukci `_setmode( _fileno( stdin ), _O_BINARY );`, aby bylo možné správně použít `wcin` v textovém souboru s kódováním UNICODE.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
