---
title: "Formátovaní výstupu vlastního kroku sestavení nebo události sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 189f18f5d8944fc61635b5aa83522e5a89a3a100
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Formátovaní výstupu vlastního kroku sestavení nebo události sestavení
Pokud správně naformátován výstupu vlastního kroku sestavení nebo události sestavení, uživatelé získat následující výhody:  
  
-   Upozornění a chyby počítají **výstup** okno.  
  
-   Zobrazí se výstup v **seznam úkolů** okno.  
  
-   Kliknutím na výstup v **výstup** okno se zobrazí odpovídající téma.  
  
-   Jsou povolené operace klávesy F1 **seznam úkolů** okno nebo **výstup** okno.  
  
 Formát výstupu by měl být:  
  
 {*filename* (*řádku #* [, *sloupec #*]) &#124; *název nástroje*} **:**  
  
 [*jakýkoli text*] {**chyba** &#124; **upozornění**} *kód ###***:***lokalizovatelný řetězec*  
  
 [ *jakýkoli text* ]  
  
 Kde:  
  
-   {*a* &#124; *b*} je volbou buď *a* nebo *b*.  
  
-   [`ccc`] je volitelný řetězec nebo parametr.  
  
 Příklad:  
  
 C:\\*sourcefile.cpp*(134): chyba C2143: Chyba syntaxe: chybějící ';' než '}'  
  
 ODKAZ: závažná chyba LNK1104: Nelze otevřít soubor "*somelib.lib*.  
  
## <a name="see-also"></a>Viz také  
 [Seznámení s kroky vlastního sestavení a událostí sestavení](../ide/understanding-custom-build-steps-and-build-events.md)