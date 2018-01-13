---
title: "Unicode datového proudu I-O v textovém a binárním režimu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76e739ae95788448cc655ca18d32aaf1f8a5c90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>I/O proudu kódování Unicode v textovém a binárním režimu
Když typu Unicode stream rutiny vstupně-výstupní operace (například `fwprintf`, `fwscanf`, `fgetwc`, `fputwc`, `fgetws`, nebo `fputws`) funguje na soubor, který je otevřený v textovém režimu (výchozí), dva druhy znak převody proveďte místní:  
  
-   Převod Unicode MBCS nebo MBCS Unicode. Pokud funkce datového proudu I/O Unicode funguje v režimu text, zdroj nebo cílový datový proud předpokládá se, že posloupnosti vícebajtových znaků. Proto funkce vstupního datového proudu Unicode převést více-bajtové znaky na široké znaky (jako Pokud voláním `mbtowc` funkce). Ze stejného důvodu, funkce výstup datového proudu Unicode převést více-bajtové znaky široké znaky (jako Pokud voláním `wctomb` funkce).  
  
-   Návrat na začátek - překlad nový řádek (CR-LF). Tento překlad dojde před MBCS - převodu znakové sady Unicode (pro funkce vstupního datového proudu Unicode) a po kódování Unicode - převodu znakové sady MBCS (pro funkce výstupního datového proudu Unicode). Při vstupu je každý CR - konce řádku kombinaci přeložit na znak jednoho konce řádku. Během výstupu jednotlivé znaky konce řádku je přeložit na CR - kombinace konce řádku.  
  
 Ale když funkce datového proudu I/O Unicode působí v binárním režimu soubor předpokládá se, že kódování Unicode a žádný převod překlad nebo znak CR LF spadá vstup nebo výstup. Použít _setmode – (_fileno – (stdin –), _o_binary –); instrukce, aby bylo možné správně používat wcin na textového souboru UNICODE.  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [Vstup a výstup](../c-runtime-library/input-and-output.md)