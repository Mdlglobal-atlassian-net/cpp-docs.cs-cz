---
title: "Metody vytváření stavového řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f077c54902f69d181adbdfc8788f826f00239230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="methods-of-creating-a-status-bar"></a>Metody vytváření stavového řádku
Poskytuje dvě třídy Vytvoření stavové řádky MFC: [cstatusbar –](../mfc/reference/cstatusbar-class.md) a [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (který zabalí běžné ovládacího prvku Windows rozhraní API). `CStatusBar`obsahuje všechny funkce stavu panelu běžného ovládacího prvku, automaticky komunikuje se službou nabídek a panelů nástrojů a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktury pro vás; ale vaše Výsledný spustitelný soubor obvykle bude větší než vytvořené pomocí `CStatusBarCtrl`.  
  
 `CStatusBarCtrl`obvykle za následek menší spustitelný soubor a možná přednost `CStatusBarCtrl` Pokud nemáte v úmyslu integrovat do architektury MFC stavový řádek. Pokud budete chtít použít `CStatusBarCtrl` a integrovat stavový řádek do architektury MFC, je nutné provést další péči komunikovat řízení manipulace s knihovnou MFC řádek Stavový řádek. Tato komunikace není složité. je však další práci, kterou je potřeba, když používáte `CStatusBar`.  
  
 Visual C++ nabízí dva způsoby, jak využít výhod stav ovládacích prvků běžné panelu.  
  
-   Vytvořte na stavovém řádku pomocí `CStatusBar`a pak zavolají [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) získat přístup k `CStatusBarCtrl` členské funkce.  
  
-   Vytvořte na stavovém řádku pomocí [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)pro konstruktor.  
  
 Buď metoda získáte přístup k členské funkce ovládacího panelu stavu. Při volání `CStatusBar::GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objekt, můžete použít buď sadu členské funkce. V tématu [cstatusbar –](../mfc/reference/cstatusbar-class.md) informace o vytváření a vytváření stavovém řádku pomocí `CStatusBar`.  
  
## <a name="see-also"></a>Viz také  
 [Použití třídy CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
