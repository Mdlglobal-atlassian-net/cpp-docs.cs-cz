---
title: Oznámení z s formátováním ovládacích prvků pro úpravy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 928728093ff6e2150578c4ba48f2d8081620a48d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931141"
---
# <a name="notifications-from-a-rich-edit-control"></a>Oznámení z ovládacích prvků pro úpravy s formátováním
Sestava ovládacích prvků pro úpravy s formátováním ovlivňující událostí zprávy oznámení ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Jsou může zpracovat nadřazeného okna nebo pomocí reflexe zpráv pomocí bohaté upravit vlastní ovládací prvek. Ovládací prvky Rich edit podporovat všechny zprávy s oznámením použít s ovládacími prvky pro úpravy, jakož i několik dalších ty. Můžete určit, jaké zprávy s oznámením ovládacího prvku RichEdit odešle jeho nadřazeného okna nastavením "události maska."  
  
 Pokud chcete nastavit maska událostí pro ovládací prvek pro úpravy s formátováním, použijte [seteventmask –](../mfc/reference/cricheditctrl-class.md#seteventmask) – členská funkce. Můžete načíst aktuální masku událostí pro úpravy s formátováním ovládacího prvku s použitím [geteventmask –](../mfc/reference/cricheditctrl-class.md#geteventmask) – členská funkce.  
  
 V následujících odstavcích seznamu několik upozornění a jejich použití:  
  
-   Zpracování oznámení EN_MSGFILTER EN_MSGFILTER umožňuje třídu, buď prvku RichEdit nebo jeho nadřazené okno, filtrovat všechny klávesnici a myš vstupu pro ovládací prvek. Obslužná rutina může zabránit zpracovává zprávy klávesnici nebo myš nebo zprávu můžete změnit úpravou zadaný [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) struktury.  
  
-   EN_PROTECTED zpracování zpráv oznámení EN_PROTECTED zjistit, kdy se uživatel pokusí o chráněný textový upravit. Rozsah text označit jako chráněný, můžete nastavit účinek chráněné znak. Další informace najdete v tématu [formátování znaků v ovládacích prvcích upravit bohaté](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   EN_DROPFILES můžete povolit uživatelům vyřadit soubory v ovládacím prvku RichEdit zpracováním EN_DROPFILES oznámení. Zadaný [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) struktura obsahuje informace o souborech probíhá vyřazování.  
  
-   EN_SELCHANGE aplikace může rozpoznat, kdy aktuální výběr změní zpracováním EN_SELCHANGE oznámení. Určuje, oznámení [selchange –](http://msdn.microsoft.com/library/windows/desktop/bb787952) struktura obsahující informace o nový výběr.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

