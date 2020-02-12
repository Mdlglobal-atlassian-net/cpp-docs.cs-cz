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
ms.openlocfilehash: 04c7357d67dc1a5daee4b8b8135c9a54eda8504a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127826"
---
# <a name="special-cwinapp-services"></a>Speciální služby CWinApp

Kromě spuštění smyčky zpráv a poskytnutí možnosti k inicializaci aplikace a vyčištění po ní [CWinApp](../mfc/reference/cwinapp-class.md) poskytuje několik dalších služeb.

##  <a name="_core_shell_registration"></a>Registrace prostředí

Ve výchozím nastavení Průvodce aplikací knihovny MFC umožňuje uživateli otevřít datové soubory, které vaše aplikace vytvořila dvojitým kliknutím v Průzkumníkovi souborů nebo ve Správci souborů. Pokud je vaše aplikace aplikací MDI a zadáte rozšíření pro soubory, které vaše aplikace vytvoří, Průvodce aplikací knihovny MFC přidá volání členských funkcí [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) a [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen) z [CWinApp](../mfc/reference/cwinapp-class.md) do `InitInstance` přepsání, které za vás zapisuje.

`RegisterShellFileTypes` zaregistruje typy dokumentů vaší aplikace pomocí Průzkumníka souborů nebo správce souborů. Funkce přidá položky do registrační databáze, kterou systém Windows udržuje. Položky registrují jednotlivé typy dokumentů, přiřadí příponu souboru k typu souboru, určují příkazový řádek pro otevření aplikace a zadání příkazu DDE (Dynamic Data Exchange) pro otevření dokumentu tohoto typu.

`EnableShellOpen` dokončí proces tím, že aplikaci umožní přijímat příkazy DDE z Průzkumníka souborů nebo správce souborů, aby bylo možné otevřít soubor vybraný uživatelem.

Tato podpora automatických registrací v `CWinApp` eliminuje nutnost dodávat soubor. reg do vaší aplikace nebo provést speciální práci s instalací.

Pokud chcete inicializovat rozhraní GDI+ pro aplikaci (voláním [GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) ve funkci [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) ), je nutné potlačit vlákno na pozadí rozhraní GDI+.

To můžete provést nastavením `SuppressBackgroundThread` člena struktury [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) na **hodnotu true**. Při potlačení vlákna na pozadí rozhraní GDI+ by se měla provést volání `NotificationHook` a `NotificationUnhook` těsně před vstupem a ukončením smyčky zpráv aplikace. Další informace o těchto voláních naleznete v tématu [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Proto je vhodné místo volání `GdiplusStartup` a funkce oznámení o zapojování by byly v přepsání virtuální funkce [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run), jak je znázorněno níže:

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

Pokud potlačíte vlákno rozhraní GDI+ na pozadí, lze příkazy DDE předčasně vydávat aplikaci před vytvořením jeho hlavního okna. Příkazy DDE vyvolané prostředím lze předčasně přerušit, což vede k chybovým zprávám.

##  <a name="_core_file_manager_drag_and_drop"></a>Správce souborů – přetažení

Soubory lze přetáhnout z okna zobrazení souboru ve Správci souborů nebo v Průzkumníku souborů do okna v aplikaci. Můžete například povolit přetažení jednoho nebo více souborů do hlavního okna aplikace MDI, kde aplikace by mohla načíst názvy souborů a otevřít podřízená okna MDI pro tyto soubory.

Chcete-li povolit přetahování souborů v aplikaci, Průvodce aplikací knihovny MFC zapíše volání členské funkce [CWnd](../mfc/reference/cwnd-class.md) [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) pro hlavní okno rámce v `InitInstance`. Toto volání můžete odebrat, pokud nechcete implementovat funkci přetažení.

> [!NOTE]
>  Můžete také implementovat obecnější možnosti přetahování – přetahování dat mezi dokumenty nebo v nich – pomocí technologie OLE. Informace najdete v článku [přetažení OLE](../mfc/drag-and-drop-ole.md).

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>Udržování přehledu o naposledy použitých dokumentech

Když uživatel otevře a zavře soubory, objekt aplikace udržuje přehled o čtyřech naposledy použitých souborech. Názvy těchto souborů se přidají do nabídky soubor a při změně se aktualizují. Rozhraní ukládá tyto názvy souborů buď v registru, nebo v souboru. ini se stejným názvem, jako má váš projekt, a čte je ze souboru při spuštění aplikace. `InitInstance` přepíše, že Průvodce aplikací knihovny MFC vytvoří pro vás volání členské funkce [CWinApp](../mfc/reference/cwinapp-class.md) [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), která načte informace ze souboru registru nebo ini, včetně naposledy použitých názvů souborů.

Tyto položky jsou uloženy následujícím způsobem:

- V systémech Windows NT, Windows 2000 a novějších se hodnota ukládá do klíče registru.

- Ve Windows 3. x je hodnota uložená v souboru WIN. Soubor INI.

- Ve Windows 95 a novější hodnotě se hodnota ukládá ve verzi WIN uložené v mezipaměti. Užívaný.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
