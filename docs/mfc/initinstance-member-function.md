---
title: InitInstance – členská funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: d026665a48d038092031bf4b632b7ef676124196
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198172"
---
# <a name="initinstance-member-function"></a>InitInstance – členská funkce
Operační systém Windows umožňuje spustit více než jednu kopii nebo "instance" stejné aplikace. `WinMain` volání [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) pokaždé, když se spustí novou instanci aplikace.  
  
 Standardní `InitInstance` implementace vytvořené průvodcem aplikací MFC provádí následující úlohy:  
  
-   Jako centrální akcí vytvoří šablony dokumentů, které pak vytvářejí dokumenty, zobrazení a oken s rámečkem. Popis tohoto procesu najdete v tématu [vytváření šablon dokumentů](../mfc/document-template-creation.md).  
  
-   Načte možnosti standardní soubor ze souboru INI nebo registru Windows, včetně názvů naposledy použitých souborů.  
  
-   Zaregistruje jednu nebo více šablon dokumentů.  
  
-   Pro aplikace MDI vytvoří hlavní okno rámce.  
  
-   Zpracování příkazového řádku k otevření dokumentu zadané na příkazovém řádku nebo chcete-li otevřít nový prázdný dokument.  
  
 Můžete přidat kód inicializace nebo upravit kód napsaný v průvodci.  
  
> [!NOTE]
>  Aplikace MFC musí být inicializovány jako jednovláknový objekt apartment (STA). Při volání [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) ve vašich `InitInstance` přepsání, určete COINIT_APARTMENTTHREADED (spíše než COINIT_MULTITHREADED). Další informace najdete v tématu PRB: aplikace MFC přestane reagovat při inicializaci aplikace jako a s více vlákny typu Apartment (828643) na [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
