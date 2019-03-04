---
title: Speciální služby CWinApp
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
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
ms.openlocfilehash: 910660253c9d306b13294a710021a6bbd36c1952
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258083"
---
# <a name="special-cwinapp-services"></a>Speciální služby CWinApp

Kromě spouštění smyčky zpráv a díky tomu získáte příležitost k inicializaci aplikace a vyčištění po něm, [CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik dalších služeb.

##  <a name="_core_shell_registration"></a> Registrace prostředí

Ve výchozím nastavení Průvodce aplikací MFC umožňuje uživateli otevřít datových souborů, které vaše aplikace má vytvořit na ně poklikáte v Průzkumníku souborů nebo správce souborového. Pokud vaše aplikace je aplikace MDI a zadat rozšíření pro soubory vytváří vaše aplikace, Průvodce aplikací MFC přidá volání [registershellfiletypes –](../mfc/reference/cwinapp-class.md#registershellfiletypes) a [enableshellopen –](../mfc/reference/cwinapp-class.md#enableshellopen)členské funkce [CWinApp](../mfc/reference/cwinapp-class.md) k `InitInstance` přepsání, které se zapíše za vás.

`RegisterShellFileTypes` zaregistruje typů dokumentů aplikace pomocí Průzkumníka souborů nebo Správce souborů. Funkce přidá položky do registrační databázi, která udržuje Windows. Položky zaregistrovat každý typ dokumentu, příponu souboru přidružení typu souboru, zadejte příkazového řádku k otevření aplikace a zadat dynamických dat systému exchange (DDE) příkaz pro otevření dokumentu daného typu.

`EnableShellOpen` dokončení procesu tím, že vaše aplikace pro příjem DDE příkazy z Průzkumníka souborů nebo Správce souborů otevřete soubor uživatelem.

Tato podpora automatické registrace v `CWinApp` se eliminuje potřeba k odeslání souboru .reg pomocí aplikace nebo speciální instalační práci.

Pokud chcete inicializovat rozhraní GDI + pro vaši aplikaci (voláním [GdiplusStartup](/windows/desktop/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) ve vaší [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) funkce), budete muset potlačit vlákna na pozadí rozhraní GDI +.

Můžete to provést tak, že nastavíte `SuppressBackgroundThread` člena [GdiplusStartupInput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) struktury na **TRUE**. Při potlačení rozhraní GDI + na pozadí vlákna, `NotificationHook` a `NotificationUnhook` volání by měl pouze předchozí zadání a ukončení smyčky zpráv aplikace. Další informace o těchto volání, naleznete v tématu [GdiplusStartupOutput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Proto vhodné místo pro volání `GdiplusStartup` a funkce háku oznámení by měly být v přepsání virtuální funkce [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak je znázorněno níže:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Pokud jste nepotlačujte rozhraní GDI + vlákno na pozadí, DDE příkazy můžete předčasně vydaném pro aplikaci předtím, než byla vytvořena její hlavní okno. DDE příkazy vydané prostředí můžete předčasně přeruší, což vede k chybě.

##  <a name="_core_file_manager_drag_and_drop"></a> Správce souborů přetažení

Soubory lze přetáhnout z okna zobrazení souboru v souboru správce nebo Průzkumníka souborů do okna ve vaší aplikaci. Například může povolit jeden nebo více souborů přetáhnout hlavního okna aplikace MDI, kde aplikace může načíst názvy souborů a otevřete podřízených oken MDI těchto souborů.

Chcete-li povolit souboru přetažení ve vaší aplikaci, Průvodce aplikací MFC zapíše volání [CWnd](../mfc/reference/cwnd-class.md) členskou funkci [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) okna hlavního rámce v vaše `InitInstance`. Pokud nechcete k implementaci funkcí přetahování myší, můžete odebrat toto volání.

> [!NOTE]
>  Můžete také implementovat další obecné možnosti přetahování myší – přetažení dat mezi nebo v rámci dokumentů – technologií OLE. Informace najdete v článku [oblast pro přetažení přetažení (OLE)](../mfc/drag-and-drop-ole.md).

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> Udržování přehledu o nejčastěji naposledy použité dokumenty

Když uživatel otevře a zavře soubory, daný aplikační objekt uchovává informace o čtyři naposledy použitých souborů. Názvy těchto souborů se přidají do nabídky soubor a při změnách. Rozhraní framework uloží tyto názvy souborů, buď v registru nebo v souboru INI se stejným názvem jako váš projekt a přečte ze souboru při spuštění aplikace. `InitInstance` Přepsat, Průvodce aplikací MFC vytvoří pro vás spravujeme volání [CWinApp](../mfc/reference/cwinapp-class.md) členskou funkci [loadstdprofilesettings –](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), což způsobí načtení informací z registru nebo INI soubor, včetně použít názvy souborů.

Tyto položky jsou uloženy následujícím způsobem:

- V systému Windows NT, Windows 2000 nebo novější, je hodnota uložena do klíče registru.

- Ve Windows 3.x, hodnota je uložena v VÍTĚZSTVÍ. Soubor INI.

- Ve Windows 95 a později hodnota je uložena v mezipaměti verzi systému Windows. INI.

## <a name="see-also"></a>Viz také:

[CWinApp Třída aplikace](../mfc/cwinapp-the-application-class.md)
