---
title: Seznamy obrázků ovládacího prvku strom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef74b656cc85fbdcc29c7965b9398a5cbd2f44e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382190"
---
# <a name="tree-control-image-lists"></a>Seznamy obrázků v ovládacím prvku strom
Každá položka v ovládacím prvku strom ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) může mít pár rastrových obrázků s ním spojená. Bitové kopie se zobrazí na levé straně popisku položky. Jednu image se zobrazí, když je položka vybrána, a druhé se zobrazí, pokud není vybrána položka. Například může položky zobrazit, otevřít složku, pokud je vybrána a uzavřené složku Pokud není vybraná.  
  
 Pokud chcete použít obrázků položek, musíte vytvořit vytvořením seznamu obrázků [CImageList](../mfc/reference/cimagelist-class.md) objekt a pomocí [CImageList::Create](../mfc/reference/cimagelist-class.md#create) funkce k vytvoření seznamu přidruženou bitovou kopii. Pak přidejte do seznamu požadovanou rastrové obrázky a přidružit seznamu pomocí ovládacího prvku strom pomocí [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) – členská funkce. Ve výchozím nastavení umožňuje zobrazit všechny položky v seznamu obrázků pro vybrané a nevybrané stavy první obrázek. Výchozí chování pro konkrétní položku můžete změnit zadáním indexy obrázků na vybrané a nevybrané při přidávání položky do stromu ovládacího prvku pomocí [metody InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) – členská funkce. Indexy můžete změnit po přidání položky pomocí [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) – členská funkce.  
  
 Seznamy obrázků ovládacím prvku stromu může také obsahovat Image překrytí, které jsou určeny k překrývat obrázků položek. Určuje na základě jeden index bitové kopie překrytí nenulovou hodnotu v bitech 8 až 11 stav položky ovládacího prvku strom (0 znamená bez překrytí obrázek). Protože 4-bit, na základě jeden index je používán, překrytí obrázků musí být mezi první 15 obrázků v seznamech obrázků. Další informace o stavů položek ovládacího prvku strom najdete v tématu [přehled stavů položek ovládacího prvku strom](../mfc/tree-control-item-states-overview.md) výše v tomto tématu.  
  
 Pokud je zadán seznam stavu bitové kopie, ovládacím prvkem strom rezervy místa nalevo od ikony každé položky pro obrázek stavu. Aplikace můžete použít stav Image, jako jsou zaškrtnuté a nezaškrtnuté zaškrtávací políčka, k označení stavů položek definované aplikací. Nenulovou hodnotu v bitech 12 až 15 určuje na základě jeden index bitové kopie stavu (0 znamená žádný obrázek stavu).  
  
 Zadáním **I_IMAGECALLBACK** hodnotu namísto index bitové kopie, můžete počkat, zadání bitovou kopii vybrané nebo nevybrané, dokud položka je překreslit. **I_IMAGECALLBACK** přesměruje ovládací prvek stromu k dotazování aplikací pro index odesláním [TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) oznámení.  
  
 [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) – členská funkce načte popisovač seznamu obrázků ovládacím prvku stromu. Tato funkce je užitečná, pokud potřebujete přidat další Image do seznamu. Další informace o seznamech obrázků najdete v tématu [pomocí ovládacího prvku CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) v *odkaz knihovny MFC*, a [seznamy obrázků](http://msdn.microsoft.com/library/windows/desktop/bb761389) v Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

