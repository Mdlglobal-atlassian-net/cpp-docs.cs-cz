---
title: Upozornění příkazového řádku D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: e7090dda72868ad7ee4d5f8e4f1ba6a0ad121c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214092"
---
# <a name="command-line-warning-d9025"></a>Upozornění příkazového řádku D9025

přepsání "možnost1" s "možnost2.

*Možnost1* možnost byla zadána, ale pak se přepsat *možnost2*. *Možnost2* byla použita možnost.

Pokud dvě možnosti zadat direktivy odporuje nebo nekompatibilní, je použít direktiva určená nebo v možnost nejvíce vpravo na příkazovém řádku.

Je-li získat toto upozornění při kompilaci z vývojového prostředí a nejste jisti, odkud jsou konfliktní možnosti, zvažte následující:

- Možnost se dá nastavit v kódu nebo v nastavení projektu projekt. Když se podíváte na kompilátoru [stránky vlastností příkazového řádku](../../build/reference/command-line-property-pages.md) a pokud se zobrazí konfliktní možnosti v **všechny možnosti** pole a možnosti jsou nastaveny na stránkách vlastností projektu, jinak, možnosti jsou nastavené ve zdrojovém kódu.

   Pokud jsou možnosti v stránky vlastností projektu, podívejte se na stránku vlastností preprocesoru kompilátoru (s uzlem projektu vybraného v Průzkumníkovi řešení).  Pokud nevidíte možnost nastavit existuje, zkontrolujte nastavení stránky preprocesoru vlastnost pro každý soubor zdrojového kódu (v Průzkumníku řešení), ujistěte se, že tam není přidaný existuje.

   Možnosti jsou nastavené v kódu může být nastavena v kódu nebo v hlavičky systému windows.  Můžete vyzkoušet vytvoření předzpracovaného souboru ([/P](../../build/reference/p-preprocess-to-a-file.md)) a vyhledejte symbol.