---
title: Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC | Microsoft Docs
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
ms.openlocfilehash: 17326bdb8fe01c9ad329db0a6c7e8178fdbb25e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864239"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC
Aplikace může zobrazit popisný text pro každou příkazů nabídky, které uživatel může vybrat. To uděláte tak, že každý pomocí příkazu nabídky přiřadíte textového řetězce **výzva** vlastnost v okně Vlastnosti. Pokud máte řetězec [tabulky řetězců](../windows/string-editor.md) jejíž ID je stejný jako příkaz, aplikace MFC se automaticky zobrazí tento řetězec prostředku ve stavovém řádku spuštěné aplikace při nastavení ukazatele myši položku nabídky.  
  
### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>Chcete-li přidružit příkazu v nabídce stavem panelu textového řetězce  
  
1.  V **nabídky** editor, vyberte příkaz nabídky.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), zadejte text přidružený stavového řádku v **výzva** pole.  
  

  
 **Požadavky**  
  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Přidání příkazů na nabídky](../windows/adding-commands-to-a-menu.md)   
 [Editor nabídek](../windows/menu-editor.md)