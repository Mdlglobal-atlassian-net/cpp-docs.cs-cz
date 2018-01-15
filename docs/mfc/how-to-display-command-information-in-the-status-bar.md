---
title: "Postupy: zobrazení informací o příkazu ve stavovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da836f48592d97b3526c568eb9d9a830428f53a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Postupy: Zobrazení informací o příkazu ve stavovém řádku
Když spustíte Průvodce aplikace vytvořit kostru aplikace, může podporovat panelu nástrojů a stavového řádku. Právě jednou z možností v Průvodci aplikace podporuje obě. Když se nachází stavového řádku, aplikace automaticky poskytuje užitečné zpětnou vazbu přesunutí ukazatele myši položky v nabídkách. Aplikace automaticky zobrazí výzva řetězec ve stavovém řádku, když je označený položky nabídky. Například při přesunutí ukazatele myši **Vyjmout** příkaz na **upravit** nabídce Stavový řádek může zobrazit "Vyjme výběr a umístí jej do schránky" v oblasti zpráv stavového řádku. Na řádku pomáhá pochopit účel položky nabídky uživatele. Tento postup funguje i když uživatel klikne tlačítko panelu nástrojů.  
  
 Můžete přidat do této nápovědy stavového řádku definováním výzva řetězce pro položky nabídky, které přidáte do programu. K tomu, poskytnout výzva řetězce, když upravujete vlastnosti položky nabídky v editoru nabídky. Řetězce, které definujete jsou uloženy v souboru prostředků aplikace. mají stejné ID jako příkazy, které jsou zde popsány.  
  
 Ve výchozím nastavení, Průvodce aplikací přidá `AFX_IDS_IDLEMESSAGE`, ID pro standardní "Připravena" zprávy, která se zobrazí, když program čeká nové zprávy. Pokud zadáte možnost Context-Sensitive Help v Průvodci aplikací, zpráva se změní na "Nápovědy, stiskněte F1."  
  
## <a name="see-also"></a>Viz také  
 [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

