---
title: "Styly ovládacího prvku strom | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c141a2b0db673f8d3c5f2c116de5b5d2ec81a8ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-styles"></a>Styly ovládacího prvku strom
Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) styly řídí aspektů vzhled ovládacího prvku strom. Při vytváření ovládacího prvku strom nastavte počáteční stylů. Můžete načíst a změnit po vytvoření ovládacího prvku strom pomocí stylů [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) a [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) funkce systému Windows, zadání **GWL_STYLE** pro `nIndex` parametr. Úplný seznam styly, najdete v části [styly okno zobrazení ovládacího prvku strom](http://msdn.microsoft.com/library/windows/desktop/bb760013) ve Windows SDK.  
  
 **TVS_HASLINES** styl vylepšuje grafické reprezentace ovládacího prvku stromu hierarchie a kreslení čar, které odkazují na jejich odpovídající nadřazené položky podřízené položky. Tento styl neobsahuje odkazy na položky v kořenovém adresáři hierarchie. To pokud chcete udělat, je nutné sloučit **TVS_HASLINES** a **TVS_LINESATROOT** stylů.  
  
 Uživatele můžete rozbalit nebo sbalit seznam nadřazené položky podřízené položky poklepáním na nadřazené položky. Ovládací prvek stromu, který má **TVS_SINGLEEXPAND** styl způsobí, že položka Vybrat rozšíření a položka se zrušit na Sbalit. Pokud myš slouží k vybrané položce jedním kliknutím a že položky uzavřené, bude rozšířena. Vybrané položky je po jednom klepnutí když je otevřený, bude sbalené.  
  
 Ovládací prvek stromu, který má **TVS_HASBUTTONS** styl přidá tlačítko na levé straně každé nadřazené položky. Uživatele můžete kliknutím na tlačítko Rozbalit nebo sbalit podřízené položky jako alternativu k dvakrát kliknete na soubor nadřazené položky. **TVS_HASBUTTONS** nepřidá tlačítka pro položky v kořenovém adresáři hierarchie. Chcete-li to provést, je nutné zkombinovat **TVS_HASLINES**, **TVS_LINESATROOT**, a **TVS_HASBUTTONS**.  
  
 **TVS_EDITLABELS** styl umožňuje uživateli upravit popisky položek ovládacího prvku strom. Další informace o úpravách popisky najdete v tématu [úpravy štítků ovládací prvek stromu](../mfc/tree-control-label-editing.md) dál v tomto tématu.  
  
 **TVS_NOTOOLTIPS** styl zakáže funkci Automatické nástroj tip ovládací prvky zobrazení stromu. Tato funkce se automaticky zobrazí popis tlačítka, obsahující název položky v části myší, pokud celý název není aktuálně viditelná.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

