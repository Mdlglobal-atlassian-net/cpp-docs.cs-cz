---
title: Strom – styly ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a448d76236c3467228b2aa57cd71284274687ac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200428"
---
# <a name="tree-control-styles"></a>Styly ovládacího prvku strom
Ovládací prvek stromu ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) Styly určují různé aspekty vzhledu ovládacího prvku stromu. Při vytváření ovládacího prvku stromu je nastavíte počáteční styly. Můžete načíst a měnit styly po vytvoření ovládacího prvku stromu pomocí [GetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633584) a [SetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633591) funkce Windows a určení **GWL_STYLE** pro *nIndex* parametru. Úplný seznam stylů, najdete v části [styly oken ovládací prvek zobrazení stromové struktury](/windows/desktop/Controls/tree-view-control-window-styles) v sadě Windows SDK.  
  
 **TVS_HASLINES** styl vylepšuje grafické znázornění ovládací prvek stromu hierarchie a kreslení čar, které jsou propojeny podřízených položek na jejich odpovídající nadřazené položky. Tento styl neobsahuje odkazy na položky v kořenovém adresáři hierarchie. Uděláte to tak, budete muset zkombinovat **TVS_HASLINES** a **TVS_LINESATROOT** styly.  
  
 Uživatel můžete rozbalit nebo sbalit nadřazená položka seznamu podřízených položek na něj poklikejte nadřazené položky. Ovládací prvek stromu, který má **TVS_SINGLEEXPAND** styl způsobí, že se položka výběru rozbalte a probíhá sbalit nevybrané položky. Pokud ukazatel myši se používá pro vybranou položku jedním kliknutím a zavření danou položku, bude rozšířena. Pokud vybrané položky je jedním kliknuto, když je otevřen, se sbalil.  
  
 Ovládací prvek stromu, který má **TVS_HASBUTTONS** styl přidá tlačítko na levé straně každé nadřazené položky. Kliknutí na tlačítko pro rozbalení a sbalení podřízené položky jako alternativu k poklepání nadřazené položky. **TVS_HASBUTTONS** nedojde k přidání tlačítek do položek v kořeni hierarchie. Uděláte to tak, je nutné zkombinovat **TVS_HASLINES**, **TVS_LINESATROOT**, a **TVS_HASBUTTONS**.  
  
 **TVS_EDITLABELS** style umožňuje uživateli upravit popisky položek ovládacího prvku stromu. Další informace o úpravě popisků naleznete v tématu [úpravy štítků ovládací prvek stromu](../mfc/tree-control-label-editing.md) dále v tomto tématu.  
  
 **TVS_NOTOOLTIPS** styl zakáže funkci Automatické nástroj tip ovládací prvky zobrazení stromu. Tato funkce automaticky zobrazí popis obsahující název položky pod kurzorem myši, pokud není aktuálně viditelné celý název.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

