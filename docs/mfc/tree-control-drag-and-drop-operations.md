---
title: "Strom operací přetažení myší řízení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 978c577a01b2f574009c601ca594a235e0712d71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-drag-and-drop-operations"></a>Operace přetažení u ovládacího prvku strom
Ovládacím prvkem strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) odešle oznámení, když uživatel spustí přetáhněte položku. Odešle ovládacího prvku [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) oznámení, když uživatel zahájí přetahování položky s levým tlačítkem myši a [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) oznámení, když uživatel zahájí přetahování s pravým tlačítkem. Můžete zabránit v ovládacím prvku stromu odesílání tato oznámení tím, že ovládací prvek stromu **TVS_DISABLEDRAGDROP** stylu.  
  
 Získat bitovou kopii k zobrazení během operace přetažení ve volání [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) – členská funkce. Ovládací prvek stromu vytvoří přetahování rastrový obrázek podle popisku položky přetažen. Ovládací prvek stromu vytvoří seznamu obrázků, přidá do něj bitovou mapu a vrací ukazatel na [CImageList](../mfc/reference/cimagelist-class.md) objektu.  
  
 Je nutné zadat kód, který ve skutečnosti nastavuje tažením položky. To obvykle zahrnuje pomocí přetahování možností funkce seznamu bitové kopie a zpracování [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) a [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (nebo [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) zprávy odeslané po zahájení operace přetažení. Další informace o funkcích seznamu bitové kopie najdete v tématu [CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC* a [seznamy obrázků](http://msdn.microsoft.com/library/windows/desktop/bb761389) ve Windows SDK. Další informace o při přetažení ovládací prvek stromu najdete v tématu [přetáhnete položky zobrazení stromu](http://msdn.microsoft.com/library/windows/desktop/bb760017)také v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Pokud položky v ovládacím prvku stromu jsou cíle operace přetahování myší, budete muset vědět, pokud se ukazatel myši na cílová položka. Můžete zjistit pomocí volání [hitTest –](../mfc/reference/ctreectrl-class.md#hittest) – členská funkce. Zadejte bod a celé číslo nebo adresu [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) struktura, která obsahuje aktuální souřadnice myší. Když funkce vrátí hodnotu, celé číslo nebo struktura obsahuje příznak, který udává umístění ukazatele myši relativně k ovládacím prvku stromu. Pokud je kurzor na položku v ovládacím prvku stromu, obsahuje strukturu popisovač také položky.  
  
 Můžete určit, že položku je cílem operací přetažení myší pomocí volání [SetItem](../mfc/reference/ctreectrl-class.md#setitem) – členská funkce pro nastavení stavu `TVIS_DROPHILITED` hodnotu. Položku, která obsahuje tento stav se vykresluje v styl slouží k určení cíle přetažení a přetažení.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

