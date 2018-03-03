---
title: "Oznámení z s formátováním ovládacích prvků pro úpravy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcfcb2e4fe333db1ed629489b405255d4ab050b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="notifications-from-a-rich-edit-control"></a>Oznámení z ovládacích prvků pro úpravy s formátováním
Sestava ovládacích prvků pro úpravy s formátováním ovlivňující událostí zprávy oznámení ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Jsou může zpracovat nadřazeného okna nebo pomocí reflexe zpráv pomocí bohaté upravit vlastní ovládací prvek. Ovládací prvky Rich edit podporovat všechny zprávy s oznámením použít s ovládacími prvky pro úpravy, jakož i několik dalších ty. Můžete určit, jaké zprávy s oznámením ovládacího prvku RichEdit odešle jeho nadřazeného okna nastavením "události maska."  
  
 Pokud chcete nastavit maska událostí pro ovládací prvek pro úpravy s formátováním, použijte [seteventmask –](../mfc/reference/cricheditctrl-class.md#seteventmask) – členská funkce. Můžete načíst aktuální masku událostí pro úpravy s formátováním ovládacího prvku s použitím [geteventmask –](../mfc/reference/cricheditctrl-class.md#geteventmask) – členská funkce.  
  
 V následujících odstavcích seznamu několik upozornění a jejich použití:  
  
-   **EN_MSGFILTER** zpracování **EN_MSGFILTER** oznámení umožňuje třídu, buď bohaté upravit ovládací prvek nebo jeho nadřazené okno, filtrovat všechny klávesnice a myši vstup do ovládacího prvku. Obslužná rutina může zabránit zpracovává zprávy klávesnici nebo myš nebo zprávu můžete změnit úpravou zadaný [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) struktury.  
  
-   **EN_PROTECTED** zpracování **EN_PROTECTED** oznámení zjistit, kdy se uživatel pokusí o chráněný textový upravit. Rozsah text označit jako chráněný, můžete nastavit účinek chráněné znak. Další informace najdete v tématu [formátování znaků v ovládacích prvcích upravit bohaté](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   **EN_DROPFILES** povolíte uživatelům vyřadit soubory v ovládacím prvku RichEdit zpracováním **EN_DROPFILES** oznámení. Zadaný [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) struktura obsahuje informace o souborech probíhá vyřazování.  
  
-   **EN_SELCHANGE** aplikace může rozpoznat, kdy aktuální výběr změní zpracováním **EN_SELCHANGE** oznámení. Určuje, oznámení [selchange –](http://msdn.microsoft.com/library/windows/desktop/bb787952) struktura obsahující informace o nový výběr.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

