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
ms.openlocfilehash: 1f5abcdab3eda1304879b122acc8072951a0e6c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363908"
---
# <a name="special-cwinapp-services"></a>Speciální služby CWinApp

Kromě spuštění smyčky zpráv a dává vám možnost inicializovat aplikaci a vyčistit po ní, [CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik dalších služeb.

## <a name="shell-registration"></a><a name="_core_shell_registration"></a>Registrace prostředí

Ve výchozím nastavení umožňuje Průvodce aplikací knihovny MFC uživateli otevřít datové soubory, které vaše aplikace vytvořila, poklepáním v Průzkumníku souborů nebo Správci souborů. Pokud je vaše aplikace aplikace MDI a zadáte příponu pro soubory, které aplikace vytvoří, Průvodce aplikací knihovny MFC přidá `InitInstance` volání [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) a [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) členské funkce [CWinApp](../mfc/reference/cwinapp-class.md) přepsat, že zapíše za vás.

`RegisterShellFileTypes`zaregistruje typy dokumentů aplikace pomocí Průzkumníka souborů nebo Správce souborů. Funkce přidá položky do registrační databáze, kterou systém Windows udržuje. Položky registrují každý typ dokumentu, přidružují příponu souboru k typu souboru, určují příkazový řádek pro otevření aplikace a zadejte příkaz dynamické výměny dat (DDE) pro otevření dokumentu tohoto typu.

`EnableShellOpen`dokončí proces tím, že aplikace umožňuje přijímat příkazy DDE z Průzkumníka souborů nebo Správce souborů otevřít soubor zvolený uživatelem.

Tato automatická podpora `CWinApp` registrace v eliminuje potřebu doložky souboru REG s vaší aplikací nebo provedení speciálních instalačních prací.

Pokud chcete inicializovat GDI+ pro vaši aplikaci (voláním [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) ve funkci [InitInstance),](../mfc/reference/cwinapp-class.md#initinstance) musíte potlačit vlákno na pozadí GDI+.

Můžete to provést nastavením `SuppressBackgroundThread` člena [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) struktury na **TRUE**. Při potlačení podprocesu na pozadí `NotificationHook` GDI + a `NotificationUnhook` volání by měla být provedena těsně před zadáním a ukončení minstí aplikace. Další informace o těchto voláních naleznete v [tématu GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Proto dobré místo pro `GdiplusStartup` volání a háček oznámení funkce by se v přepsání virtuální funkce [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), jak je znázorněno níže:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Pokud nepotlačíte vlákno GDI+ na pozadí, mohou být příkazy DDE předčasně vydány aplikaci před vytvořením hlavního okna. Příkazy DDE vydané prostředímůže být předčasně přerušena, výsledkem jsou chybové zprávy.

## <a name="file-manager-drag-and-drop"></a><a name="_core_file_manager_drag_and_drop"></a>Přetáhnout správce souborů

Soubory lze přetáhnout z okna zobrazení souborů ve Správci souborů nebo Průzkumníku souborů do okna v aplikaci. Můžete například povolit jeden nebo více souborů, které mají být přetaženy do hlavního okna aplikace MDI, kde aplikace může načíst názvy souborů a otevřít podřízená okna MDI pro tyto soubory.

Chcete-li povolit přetažení souborů v aplikaci, Průvodce aplikací knihovny MFC zapíše volání do `InitInstance`členské funkce [CWnd](../mfc/reference/cwnd-class.md) [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) pro okno hlavního rámce ve vašem . Toto volání můžete odebrat, pokud nechcete implementovat funkci přetažení.

> [!NOTE]
> Můžete také implementovat obecnější možnosti přetažení – přetahování dat mezi dokumenty nebo v rámci dokumentů – s OLE. Další informace naleznete v článku [OLE přetažení .](../mfc/drag-and-drop-ole.md)

## <a name="keeping-track-of-the-most-recently-used-documents"></a><a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Sledování naposledy použitých dokumentů

Když uživatel otevírá a zavírá soubory, objekt aplikace sleduje čtyři naposledy použité soubory. Názvy těchto souborů jsou přidány do nabídky Soubor a aktualizovány při jejich změně. Rozhraní Framework ukládá tyto názvy souborů v registru nebo v souboru INI se stejným názvem jako projekt a čte je ze souboru při spuštění aplikace. Přepsání, `InitInstance` které pro vás vytvoří Průvodce aplikací knihovny MFC, zahrnuje volání členské funkce [CWinApp](../mfc/reference/cwinapp-class.md) [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), která načte informace z registru nebo souboru INI, včetně naposledy použitých názvů souborů.

Tyto položky jsou uloženy takto:

- V systémech Windows NT, Windows 2000 a novějších je hodnota uložena do klíče registru.

- V systému Windows 3.x je hodnota uložena ve win. INI.

- V systému Windows 95 a novějších je hodnota uložena ve verzi win uložené v mezipaměti. Ini.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
