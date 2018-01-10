---
title: "Přepisování virtuální funkce (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.virtualfunc.override
dev_langs: C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98e77579d511f4c78f0f7835c0b3c1dcea632734
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-a-virtual-function-visual-c"></a>Přepisování virtuální funkce (Visual C++)
Můžete přepsat virtuálních funkcí definovaných v základní třídě ze sady Visual Studio [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>Chcete-li přepsat virtuální funkce v okně vlastností  
  
1.  V zobrazení tříd klikněte na třídu.  
  
2.  V okně vlastností klikněte **přepsání** tlačítko.  
  
    > [!NOTE]
    >  **Přepsání** tlačítko je k dispozici, když vyberete název třídy v zobrazení tříd nebo když kliknete na okno zdrojového kódu.  
  
     V levém sloupci uvádí virtuální funkce. Pokud se název virtuální funkce se také zobrazí v pravém sloupci, pak přepsání již byl implementován.  
  
3.  Pokud funkce má žádné potlačení, klikněte na buňku v pravém sloupci v okně vlastností zobrazíte navrhovaný název funkce přepsat jako \<Přidat >*%{FuncName/*.  
  
4.  Klikněte na tlačítko Přidat se zakázaným inzerováním kódu pro funkce navrhovaný název.  
  
5.  Chcete-li upravit přepsání funkce, dvakrát klikněte na název funkce v zobrazení tříd a úpravy kódu v okně zdroje.  
  
 Chcete-li odebrat přepsání, klikněte na název funkce přepsání v pravém sloupci a vyberte \<odstranit >*%{FuncName/*. Kód funkce je označeno jako komentář.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)