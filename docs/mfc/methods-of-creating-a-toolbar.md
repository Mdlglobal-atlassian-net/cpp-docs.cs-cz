---
title: Metody vytváření panelů nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052f1578386746f9a4d9892576f09b3b61547289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348632"
---
# <a name="methods-of-creating-a-toolbar"></a>Metody vytváření panelů nástrojů
Poskytuje dvě třídy vytvoření panelů nástrojů MFC: [ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (který zabalí běžné ovládacího prvku Windows rozhraní API). `CToolBar` obsahuje všechny funkce běžné ovládacího prvku panel nástrojů, a zpracovává mnoho vyžaduje obecná nastavení ovládacího prvku a struktury pro vás; ale vaše Výsledný spustitelný soubor obvykle bude větší než vytvořené pomocí `CToolBarCtrl`.  
  
 `CToolBarCtrl` obvykle za následek menší spustitelný soubor a možná přednost `CToolBarCtrl` Pokud nemáte v úmyslu integrovat do architektury MFC panelu nástrojů. Pokud budete chtít použít `CToolBarCtrl` a integrovat panelu nástrojů do architektury MFC, je nutné provést další péči manipulace ovládacího prvku panel nástrojů s knihovnou MFC komunikovat. Tato komunikace není složité. je však další práci, kterou je potřeba, když používáte `CToolBar`.  
  
 Visual C++ nabízí dva způsoby, jak využít výhod běžného ovládacího prvku panel nástrojů.  
  
-   Vytvořte pomocí nástrojů `CToolBar`a pak zavolají [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) získat přístup k `CToolBarCtrl` členské funkce.  
  
-   Vytvořte pomocí nástrojů [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)pro konstruktor.  
  
 Buď metoda získáte přístup k členské funkce ovládacího panelu nástrojů. Při volání `CToolBar::GetToolBarCtrl`, vrátí odkaz na `CToolBarCtrl` objekt, můžete použít buď sadu členské funkce. V tématu [ctoolbar –](../mfc/reference/ctoolbar-class.md) informace o vytváření a vytváření nástrojů pomocí `CToolBar`.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

