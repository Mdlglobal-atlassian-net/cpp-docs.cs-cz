---
title: "Upozornění příkazového řádku D9025 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9025
dev_langs: C++
helpviewer_keywords: D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95c4c16b472f0e1b37a981df7f73ff573d06447
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9025"></a>Upozornění příkazového řádku D9025
přepsání možnost ' 1' s 'option2.  
  
 *Možnost 1* možnost byla zadána, ale pak se přepsat *option2*. *Option2* možnost byl použit.  
  
 Pokud dvě možnosti zadat direktivy odporuje nebo nekompatibilní, se používá direktiva určená nebo obsažená v možnost nejvíce vpravo na příkazovém řádku.  
  
 Je-li získat toto upozornění, když kompilujete z vývojového prostředí a nejste jisti, kde jsou konfliktní možnosti pocházejících z, zvažte následující:  
  
-   Možnost lze zadat v kódu nebo v nastavení projektu projektu. Pokud si prohlédnete kompilátoru [stránky vlastností příkazového řádku](../../ide/command-line-property-pages.md) a pokud se zobrazí na konfliktní možnosti v **všechny možnosti** pole možnosti jsou nastavena na stránkách vlastností projektu, jinak, možnosti jsou nastavené ve zdrojovém kódu.  
  
     Pokud možnosti jsou nastavené na stránkách vlastností projektu, podívejte se na stránce preprocesoru vlastnost kompilátoru (s uzel projektu vybraného v Průzkumníkovi řešení).  Pokud nevidíte možnost nastavit existuje, zkontrolujte nastavení stránky preprocesoru vlastnost pro každý soubor zdrojový kód (v Průzkumníkovi řešení), zajistěte, aby nebyla přidána existuje.  
  
     Pokud jsou nastavení v kódu může být nastavena v kódu nebo v záhlaví systému windows.  Mohou zkuste vytvořit soubor předběžně zpracované ([/P](../../build/reference/p-preprocess-to-a-file.md)) a vyhledejte symbolu.