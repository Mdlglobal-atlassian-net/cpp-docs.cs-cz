---
title: Upozornění příkazového řádku D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196713"
---
# <a name="command-line-warning-d9025"></a>Upozornění příkazového řádku D9025

Přepisuje se ' možnost1 ' pomocí ' možnost2 '

Možnost *možnost1* byla zadána, ale byla přepsána *možnost2*. Byla použita možnost *možnost2* .

Pokud dvě možnosti určují protichůdné nebo nekompatibilní direktivy, použije se direktiva zadaná nebo odvozená v možnosti nejvíce vpravo na příkazovém řádku.

Pokud se zobrazí toto upozornění při kompilování z vývojového prostředí a nejste si jisti, kde jsou z něj konfliktní možnosti, zvažte následující:

- Možnost lze zadat buď v kódu, nebo v nastavení projektu projektu. Pokud se podíváte na [stránky vlastností příkazového řádku](../../build/reference/command-line-property-pages.md) kompilátoru a pokud se zobrazí konfliktní možnosti v poli **všechny možnosti** , pak se možnosti nastaví na stránkách vlastností projektu, jinak se možnosti nastavují ve zdrojovém kódu.

   Pokud jsou možnosti nastaveny na stránkách vlastností projektu, podívejte se na stránku vlastností preprocesoru kompilátoru (s uzlem projektu vybraným v Průzkumník řešení).  Pokud nevidíte tuto možnost, zkontrolujte nastavení stránky vlastností preprocesoru pro každý soubor zdrojového kódu (v Průzkumník řešení), abyste se ujistili, že tam není přidané.

   Pokud jsou možnosti nastaveny v kódu, může být nastaven buď v kódu, nebo v hlavičkách systému Windows.  Můžete zkusit vytvořit předzpracovaný soubor ([/p](../../build/reference/p-preprocess-to-a-file.md)) a vyhledat ho pro symbol.
