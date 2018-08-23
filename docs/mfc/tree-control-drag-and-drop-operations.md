---
title: Operace a přetažení u ovládacího prvku strom | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e1c642642f94c021001ae67d2dcc3fd87f4f287
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589082"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operace přetažení u ovládacího prvku strom
Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle oznámení, když uživatel spustí přetáhněte položku. Ovládací prvek odešle [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) zprávy oznámení, když uživatel zahájí přetahování položky s levým tlačítkem myši a [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) zprávy oznámení, když uživatel zahájí přetahování s pravým tlačítkem. Ovládací prvek stromu můžete zabránit zadáním do ovládacího prvku stromu styl TVS_DISABLEDRAGDROP posílání těchto oznámení.  
  
 Získat obrázek, který se zobrazí během operace přetažení voláním [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) členskou funkci. Do ovládacího prvku stromu vytvoří přetahování rastrového obrázku na základě štítku položky právě přetáhli. Pak do ovládacího prvku stromu vytvoří seznam obrázků, přidá rastrového obrázku nastaven na ni a vrací ukazatel na [atributu CImageList](../mfc/reference/cimagelist-class.md) objektu.  
  
 Je nutné zadat kód, který ve skutečnosti přetáhne položku. To obvykle zahrnuje pomocí přetahování možností funkce seznam obrázků a zpracování [wm_mousemove a](http://msdn.microsoft.com/library/windows/desktop/ms645616) a [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (nebo [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) zprávy odeslané po zahájení operace přetažení. Další informace o funkcích seznamu image, najdete v části [atributu CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [seznamy obrázků](http://msdn.microsoft.com/library/windows/desktop/bb761389) v sadě Windows SDK. Další informace o přetahování položky ovládacího prvku stromu, naleznete v tématu [přetažením položka stromového zobrazení](http://msdn.microsoft.com/library/windows/desktop/bb760017), také v sadě Windows SDK.  
  
 Pokud jsou položky v ovládacím prvku strom cíli operace přetažení myší, musíte vědět, kdy je ukazatel myši na cílovou položku. Můžete zjistit pomocí volání [hitTest –](../mfc/reference/ctreectrl-class.md#hittest) členskou funkci. Zadejte bod a celé číslo nebo adresu [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) strukturu, která obsahuje aktuální souřadnic ukazatele myši. Po návratu funkce celé číslo nebo struktura obsahuje příznak označující umístění ukazatele myši relativně vzhledem k stromové struktury. Pokud je kurzor na položku v ovládacím prvku stromu, struktura obsahuje popisovač předmětu také.  
  
 Můžete určit, že položka je cíl operace přetažení myší pomocí volání [SetItem](../mfc/reference/ctreectrl-class.md#setitem) členskou funkci pro nastavení stavu `TVIS_DROPHILITED` hodnotu. Položka, která má být tento stav je vykreslena ve stylu slouží k určení cíle přetažení myší.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

