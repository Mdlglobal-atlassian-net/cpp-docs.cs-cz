---
title: "Přiřazení příkazů nabídky k textu stavového řádku v aplikacích MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 16bf93390538a5f2abebb2bf327970dbec1d2a8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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