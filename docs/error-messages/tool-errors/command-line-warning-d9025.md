---
title: Upozornění příkazového řádku D9025 | Microsoft Docs
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
ms.openlocfilehash: 3875a2cbd065fd5ad887267bcc80748fa9845d0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298847"
---
# <a name="command-line-warning-d9025"></a>Upozornění příkazového řádku D9025
přepsání možnost ' 1' s 'option2.  
  
 *Možnost 1* možnost byla zadána, ale pak se přepsat *option2*. *Option2* možnost byl použit.  
  
 Pokud dvě možnosti zadat direktivy odporuje nebo nekompatibilní, se používá direktiva určená nebo obsažená v možnost nejvíce vpravo na příkazovém řádku.  
  
 Je-li získat toto upozornění, když kompilujete z vývojového prostředí a nejste jisti, kde jsou konfliktní možnosti pocházejících z, zvažte následující:  
  
-   Možnost lze zadat v kódu nebo v nastavení projektu projektu. Pokud si prohlédnete kompilátoru [stránky vlastností příkazového řádku](../../ide/command-line-property-pages.md) a pokud se zobrazí na konfliktní možnosti v **všechny možnosti** pole možnosti jsou nastavena na stránkách vlastností projektu, jinak, možnosti jsou nastavené ve zdrojovém kódu.  
  
     Pokud možnosti jsou nastavené na stránkách vlastností projektu, podívejte se na stránce preprocesoru vlastnost kompilátoru (s uzel projektu vybraného v Průzkumníkovi řešení).  Pokud nevidíte možnost nastavit existuje, zkontrolujte nastavení stránky preprocesoru vlastnost pro každý soubor zdrojový kód (v Průzkumníkovi řešení), zajistěte, aby nebyla přidána existuje.  
  
     Pokud jsou nastavení v kódu může být nastavena v kódu nebo v záhlaví systému windows.  Mohou zkuste vytvořit soubor předběžně zpracované ([/P](../../build/reference/p-preprocess-to-a-file.md)) a vyhledejte symbolu.