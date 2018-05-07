---
title: InitInstance – členská funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda38c7173feeccf878ee7befc3d27c0061ddb1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="initinstance-member-function"></a>InitInstance – členská funkce
Operační systém Windows umožňuje spuštění více kopií, nebo "instance" stejné aplikace. `WinMain` volání [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) pokaždé, když se spustí novou instanci třídy aplikace.  
  
 Standardní `InitInstance` implementace vytvořené průvodcem aplikací MFC provede následující úlohy:  
  
-   Jako jeho centrální akce vytvoří šablony dokumentů, které pak vytvářejí dokumenty, zobrazení a oken s rámečkem. Popis tohoto procesu naleznete v tématu [vytváření šablon dokumentů](../mfc/document-template-creation.md).  
  
-   Načte možnosti standardní souboru ze souboru INI nebo registru systému Windows, včetně názvů naposledy použitých souborů.  
  
-   Zaregistruje jednu nebo více šablon dokumentů.  
  
-   Pro aplikace MDI vytvoří okno rámce.  
  
-   Zpracuje příkazového řádku k otevření dokumentu zadat na příkazovém řádku nebo k otevření dokumentu nový, prázdný.  
  
 Můžete přidat vlastní kód inicializace nebo změnit kód napsaný v průvodci.  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Když zavoláte [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ve vaší `InitInstance` přepsat, zadejte `COINIT_APARTMENTTHREADED` (místo `COINIT_MULTITHREADED`). Další informace najdete v tématu PRB: MFC aplikace přestane reagovat při inicializaci aplikace jako a více vláken typu Apartment (828643) v [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
