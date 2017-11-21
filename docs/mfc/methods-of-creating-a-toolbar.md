---
title: "Metody vytváření panelů nástrojů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f9c6347768075ebd382dce87d1933796644bf61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="methods-of-creating-a-toolbar"></a>Metody vytváření panelů nástrojů
Poskytuje dvě třídy vytvoření panelů nástrojů MFC: [ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (který zabalí běžné ovládacího prvku Windows rozhraní API). `CToolBar`obsahuje všechny funkce běžné ovládacího prvku panel nástrojů, a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktury pro vás; ale vaše Výsledný spustitelný soubor obvykle bude větší než vytvořené pomocí `CToolBarCtrl`.  
  
 `CToolBarCtrl`obvykle za následek menší spustitelný soubor a možná přednost `CToolBarCtrl` Pokud nemáte v úmyslu integrovat do architektury MFC panelu nástrojů. Pokud budete chtít použít `CToolBarCtrl` a integrovat panelu nástrojů do architektury MFC, je nutné provést další péči manipulace ovládacího prvku panel nástrojů s knihovnou MFC komunikovat. Tato komunikace není složité. je však další práci, kterou je potřeba, když používáte `CToolBar`.  
  
 Visual C++ nabízí dva způsoby, jak využít výhod běžného ovládacího prvku panel nástrojů.  
  
-   Vytvořte pomocí nástrojů `CToolBar`a pak zavolají [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) získat přístup k `CToolBarCtrl` členské funkce.  
  
-   Vytvořte pomocí nástrojů [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)pro konstruktor.  
  
 Buď metoda získáte přístup k členské funkce ovládacího panelu nástrojů. Při volání `CToolBar::GetToolBarCtrl`, vrátí odkaz na `CToolBarCtrl` objekt, můžete použít buď sadu členské funkce. V tématu [ctoolbar –](../mfc/reference/ctoolbar-class.md) informace o vytváření a vytváření nástrojů pomocí `CToolBar`.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

