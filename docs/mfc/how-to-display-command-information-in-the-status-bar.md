---
title: 'Postupy: zobrazení informací o příkazu ve stavovém řádku | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 440e550e6e1ba5a82cac3f35dcb3c76b346b5343
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346042"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Postupy: Zobrazení informací o příkazu ve stavovém řádku
Když spustíte Průvodce aplikace vytvořit kostru aplikace, může podporovat panelu nástrojů a stavového řádku. Právě jednou z možností v Průvodci aplikace podporuje obě. Když se nachází stavového řádku, aplikace automaticky poskytuje užitečné zpětnou vazbu přesunutí ukazatele myši položky v nabídkách. Aplikace automaticky zobrazí výzva řetězec ve stavovém řádku, když je označený položky nabídky. Například při přesunutí ukazatele myši **Vyjmout** příkaz na **upravit** nabídce Stavový řádek může zobrazit "Vyjme výběr a umístí jej do schránky" v oblasti zpráv stavového řádku. Na řádku pomáhá pochopit účel položky nabídky uživatele. Tento postup funguje i když uživatel klikne tlačítko panelu nástrojů.  
  
 Můžete přidat do této nápovědy stavového řádku definováním výzva řetězce pro položky nabídky, které přidáte do programu. K tomu, poskytnout výzva řetězce, když upravujete vlastnosti položky nabídky v editoru nabídky. Řetězce, které definujete jsou uloženy v souboru prostředků aplikace. mají stejné ID jako příkazy, které jsou zde popsány.  
  
 Ve výchozím nastavení, Průvodce aplikací přidá `AFX_IDS_IDLEMESSAGE`, ID pro standardní "Připravena" zprávy, která se zobrazí, když program čeká nové zprávy. Pokud zadáte možnost Context-Sensitive Help v Průvodci aplikací, zpráva se změní na "Nápovědy, stiskněte F1."  
  
## <a name="see-also"></a>Viz také  
 [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

