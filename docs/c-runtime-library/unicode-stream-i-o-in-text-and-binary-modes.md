---
title: I/O proudu kódování Unicode v textovém a binárním režimu
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: c16d2f74856bb42dfd6ffc4e1af7306f6edd97fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745991"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>I/O proudu kódování Unicode v textovém a binárním režimu

Když Unicode Streamovat rutina vstupně-výstupních operací (například **fwprintf –**, **fwscanf –**, **fgetwc –**, **fputwc –**, **fgetws –**, nebo **fputws –**) funguje u souboru, který je otevřen v textovém režimu (výchozí), dva druhy znaků převody se konají:

- Převod kódování Unicode-znaková sada MBCS nebo znaková sada MBCS-Unicode. Pokud funguje funkce datového proudu vstupně-Unicode v textovém režimu, zdroj nebo cílový datový proud brán jako sekvence vícebajtových znaků. Proto se funkce vstupním datovým proudem sady Unicode převodu vícebajtových znaků na široké znaky (jako by volání **mbtowc** funkce). Ze stejného důvodu, převést funkce proudem sady Unicode široké znaky na vícebajtové znaky (jako by volání **wctomb –** funkce).

- Návrat vozíku - nový řádek (CR-LF) překlad. Tento překlad předchází MBCS - Unicode převod (pro funkce vstupního datového proudu Unicode) a po kódování Unicode - převodu znakové sady MBCS (pro funkce výstupního datového proudu Unicode). Při zadávání každý návrat vozíku - kombinaci znak odřádkování přeloženy do znak jeden znak odřádkování. Během výstup každý znak odřádkování přeloženy do návrat vozíku - kombinaci znak odřádkování.

Ale pokud pracuje funkce datového proudu vstupně-Unicode v binárním režimu, soubor je považován za kódování Unicode a převod překladu nebo znak CR-LF spadá vstup nebo výstup. Použít _setmode (_fileno (stdin), _O_BINARY); instrukce, aby bylo možné správně používat wcin na textového souboru UNICODE.

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
