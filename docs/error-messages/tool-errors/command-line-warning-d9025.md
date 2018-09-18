---
title: Upozornění příkazového řádku D9025 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9025
dev_langs:
- C++
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 822d1ac0cc1e6b3e728d43b816e7a0a15eee9958
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063690"
---
# <a name="command-line-warning-d9025"></a>Upozornění příkazového řádku D9025

přepsání "možnost1" s "možnost2.

*Možnost1* možnost byla zadána, ale pak se přepsat *možnost2*. *Možnost2* byla použita možnost.

Pokud dvě možnosti zadat direktivy odporuje nebo nekompatibilní, je použít direktiva určená nebo v možnost nejvíce vpravo na příkazovém řádku.

Je-li získat toto upozornění při kompilaci z vývojového prostředí a nejste jisti, odkud jsou konfliktní možnosti, zvažte následující:

- Možnost se dá nastavit v kódu nebo v nastavení projektu projekt. Když se podíváte na kompilátoru [stránky vlastností příkazového řádku](../../ide/command-line-property-pages.md) a pokud se zobrazí konfliktní možnosti v **všechny možnosti** pole a možnosti jsou nastaveny na stránkách vlastností projektu, jinak, možnosti jsou nastavené ve zdrojovém kódu.

     Pokud jsou možnosti v stránky vlastností projektu, podívejte se na stránku vlastností preprocesoru kompilátoru (s uzlem projektu vybraného v Průzkumníkovi řešení).  Pokud nevidíte možnost nastavit existuje, zkontrolujte nastavení stránky preprocesoru vlastnost pro každý soubor zdrojového kódu (v Průzkumníku řešení), ujistěte se, že tam není přidaný existuje.

     Možnosti jsou nastavené v kódu může být nastavena v kódu nebo v hlavičky systému windows.  Můžete vyzkoušet vytvoření předzpracovaného souboru ([/P](../../build/reference/p-preprocess-to-a-file.md)) a vyhledejte symbol.