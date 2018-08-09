---
title: Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d868c9270e23e2ee1fa0dcdc1845d9762cefb16c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649398"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC
Aplikace může zobrazit popisný text pro všechny příkazy nabídek, které může uživatel vybrat. To provedete tak, že přiřadíte textový řetězec pro každý pomocí příkazu nabídky **výzvy** vlastnost **vlastnosti** okna. Pokud máte řetězci [tabulka řetězců](../windows/string-editor.md) jehož ID je stejný jako příkaz, aplikace knihovny MFC, automaticky zobrazí tento prostředek řetězce ve stavovém řádku běžící aplikaci. když uživatel najede myší položku nabídky.  
  
### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Chcete přidružit k příkazu nabídky stavového řádku textový řetězec  
  
1.  V **nabídky** editoru, vyberte příkaz nabídky.  
  
2.  V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte text přidružený stavového řádku v **výzvy** pole.  
  
## <a name="requirements"></a>Požadavky  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Přidání příkazů do nabídky](../windows/adding-commands-to-a-menu.md)   
 [Editor nabídek](../windows/menu-editor.md)