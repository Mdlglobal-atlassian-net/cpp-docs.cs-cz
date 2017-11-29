---
title: "Speciální služby CWinApp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs: C++
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bcc050c834d6c070b85e1f4494fd1888b3fc2ad6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="special-cwinapp-services"></a>Speciální služby CWinApp
Kromě toho spuštěn zpráva smyčky a budete moci inicializace aplikace a vyčištění po, [CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik dalších služeb.  
  
##  <a name="_core_shell_registration"></a>Registrace prostředí  
 Ve výchozím nastavení Průvodce aplikací MFC umožňuje uživateli otevřít datové soubory, které vaše aplikace vytvořena poklepáním na tyto v Průzkumníkovi souborů nebo správce souborového. Pokud vaše aplikace je aplikace MDI a zadáte rozšíření pro soubory, které vytváří vaše aplikace, Průvodce aplikací MFC přidá volání [registershellfiletypes –](../mfc/reference/cwinapp-class.md#registershellfiletypes) a [enableshellopen –](../mfc/reference/cwinapp-class.md#enableshellopen)členské funkce [CWinApp](../mfc/reference/cwinapp-class.md) k `InitInstance` přepsání, které se zapíše za vás.  
  
 `RegisterShellFileTypes`zaregistruje typů dokumentů aplikace pomocí Průzkumníka souborů nebo Správce souborů. Funkce přidá položky do databáze registrace, která udržuje systému Windows. Položky zaregistrovat každý typ dokumentu, příponu souboru přidružení typu souboru, zadejte příkazového řádku k otevření aplikace a zadat příkaz exchange (DDE), dynamická data o otevření dokumentu daného typu.  
  
 `EnableShellOpen`dokončení procesu tím, že aplikace na příjem DDE příkazy z Průzkumníka souborů nebo správce souborového k otevření souboru volená uživatelem.  
  
 Tato podpora automatickou registraci v `CWinApp` se eliminuje potřeba pro odeslání soubor REG s vaší aplikací nebo k provedení práce speciální instalaci.  
  
 Pokud budete chtít inicializace GDI + pro vaši aplikaci (voláním [GdiplusStartup]--brokenlink--(_gdiplus_FUNC_GdiplusStartup_token_input_output_) ve vaší [InitInstance –](../mfc/reference/cwinapp-class.md#initinstance) funkce), budete muset potlačíte GDI + vlákně na pozadí.  
  
 To provedete nastavením **SuppressBackgroundThread** členem [k strukturu GdiplusStartupInput]--brokenlink--(_gdiplus_STRUC_GdiplusStartupInput) **TRUE**. Při potlačení GDI + pozadí přístup z více vláken, **NotificationHook** a **NotificationUnhook** volání (viz [GdiplusStartupOutput]--brokenlink--(_gdiplus_STRUC_GdiplusStartupOutput)) by měl provést těsně před vstupující do a vystupující smyčku zpráva aplikace. Proto místo pro volání **GdiplusStartup** a funkce háku oznámení by v přepsání virtuální funkce [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak je uvedeno níže:  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 Pokud není potlačit GDI + vlákna na pozadí, příkazy DDE předčasně vystavit do aplikace před jeho hlavní okno. Příkazy DDE vystavený prostředí můžete předčasně ukončeno, výsledkem chybové zprávy.  
  
##  <a name="_core_file_manager_drag_and_drop"></a>Správce souborů – přetažení  
 Soubory můžete přetáhnout z okna zobrazení souborů v souboru Manager nebo v Průzkumníku souborů do okna ve vaší aplikaci. Například může povolit jeden nebo více souborů přetáhnout pro aplikace MDI hlavní okno, kde aplikace může načíst názvy souborů a otevřete podřízených oken MDI pro tyto soubory.  
  
 Pokud chcete povolit přetáhněte soubor a vyřadit ve vaší aplikaci, Průvodce aplikací MFC zapíše volání [CWnd](../mfc/reference/cwnd-class.md) – členská funkce [dragacceptfiles –](../mfc/reference/cwnd-class.md#dragacceptfiles) hlavního rámce okna ve vaší `InitInstance`. Toto volání může odebrat, pokud nechcete implementovat funkci přetažení myší.  
  
> [!NOTE]
>  Můžete taky implementovat další obecné možnosti přetahování myší – přetahování data mezi nebo v rámci dokumenty – s OLE. Informace najdete v článku [přetažení a Drop (OLE)](../mfc/drag-and-drop-ole.md).  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Udržování přehledu o nejvíc naposledy použité dokumenty  
 Když uživatel otevře a zavře soubory, uchovává informace o čtyři naposledy použitých souborů objekt aplikace. Názvy těchto souborů se přidají do nabídky soubor a při jejich změně. Rozhraní framework uloží tyto názvy souborů, buď v registru nebo v souboru .ini, se stejným názvem jako projektu a čtení ze souboru při spuštění aplikace. `InitInstance` Přepsat, Průvodce aplikací MFC vytvoří pro obsahuje volání [CWinApp](../mfc/reference/cwinapp-class.md) – členská funkce [loadstdprofilesettings –](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), který načte informace z registru nebo souboru INI soubor, včetně použít názvy souborů.  
  
 Tyto položky jsou uloženy následujícím způsobem:  
  
-   V systému Windows NT, Windows 2000 nebo novější, je hodnota uložena do klíče registru.  
  
-   V systému Windows 3.x, hodnota je uložena v WIN. Soubor INI.  
  
-   V systému Windows 95 a novější hodnota je uložena v mezipaměti verzi WIN. INI.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)