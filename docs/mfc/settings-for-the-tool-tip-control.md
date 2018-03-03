---
title: "Nastavení nástroje pro ovládací prvek tlačítka | Microsoft Docs"
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
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 406e35b6ab694ca972d4cd6add0dcca7586e5005
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-tool-tip-control"></a>Nastavení pro ovládací prvek popis tlačítka
Můžete nastavit ovládacím prvkem popis tlačítka ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) Chcete-li být aktivní nebo neaktivní. Když nastavíte ji jako aktivní, ovládacím prvkem popis tlačítka se zobrazí, pokud se ukazatel na nástroj. Když nastavíte ho do neaktivního stavu, ovládacím prvkem popis tlačítka nezobrazí, i když na nástroj se nachází kurzor. Volání [aktivovat](../mfc/reference/ctooltipctrl-class.md#activate) aktivovat nebo deaktivovat prvkem popis tlačítka.  
  
 Můžete nastavit active Popis zobrazený popis tlačítka, pokud se ukazatel na nástroj, zda okno vlastníka prvkem popis tlačítka je aktivní nebo neaktivní, pomocí **TTS_ALWAYSTIP** stylu. Pokud nepoužijete tento styl, ovládacím prvkem popis tlačítka se zobrazí, když je aktivní okno nástroje vlastníka, ale ne v případě, že je neaktivní.  
  
 Většina aplikací obsahovat panely nástrojů s nástroji, které odpovídají příkazy nabídky. Tyto nástroje je vhodné pro ovládacím prvkem popis tlačítka pro zobrazení textu stejné jako odpovídající položky nabídky. Systém automaticky odstraní ampersand (&) akcelerátoru znaky z všechny řetězce předaný prvkem popis tlačítka, pokud má ovládací prvek **TTS_NOPREFIX** stylu.  
  
## <a name="see-also"></a>Viz také  
 [Použití objektu CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

