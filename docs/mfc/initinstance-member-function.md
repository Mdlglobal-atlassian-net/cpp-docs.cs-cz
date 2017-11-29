---
title: "InitInstance – členská funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: InitInstance
dev_langs: C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c33a058c126cea4dc6ce6d51fb2d4866ceb9218f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="initinstance-member-function"></a>InitInstance – členská funkce
Operační systém Windows umožňuje spuštění více kopií, nebo "instance" stejné aplikace. `WinMain`volání [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) pokaždé, když se spustí novou instanci třídy aplikace.  
  
 Standardní `InitInstance` implementace vytvořené průvodcem aplikací MFC provede následující úlohy:  
  
-   Jako jeho centrální akce vytvoří šablony dokumentů, které pak vytvářejí dokumenty, zobrazení a oken s rámečkem. Popis tohoto procesu naleznete v tématu [vytváření šablon dokumentů](../mfc/document-template-creation.md).  
  
-   Načte možnosti standardní souboru ze souboru INI nebo registru systému Windows, včetně názvů naposledy použitých souborů.  
  
-   Zaregistruje jednu nebo více šablon dokumentů.  
  
-   Pro aplikace MDI vytvoří okno rámce.  
  
-   Zpracuje příkazového řádku k otevření dokumentu zadat na příkazovém řádku nebo k otevření dokumentu nový, prázdný.  
  
 Můžete přidat vlastní kód inicializace nebo změnit kód napsaný v průvodci.  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Když zavoláte [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ve vaší `InitInstance` přepsat, zadejte `COINIT_APARTMENTTHREADED` (místo `COINIT_MULTITHREADED`). Další informace najdete v tématu PRB: MFC aplikace přestane reagovat při inicializaci aplikace jako a více vláken typu Apartment (828643) v [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)