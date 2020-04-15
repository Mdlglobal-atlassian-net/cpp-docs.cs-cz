---
title: Průvodci a editory prostředků
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365268"
---
# <a name="wizards-and-the-resource-editors"></a>Průvodci a editory prostředků

Visual C++ obsahuje několik průvodců pro použití v programování knihovny MFC, spolu s mnoha integrovanými editory prostředků. Pro programování ovládacích prvků ActiveX slouží [Průvodce ovládacím prvkem ActiveX](../mfc/reference/mfc-activex-control-wizard.md) účelu podobně jako U Průvodce aplikací knihovny MFC. Zatímco aplikace MFC můžete psát bez většiny těchto nástrojů, nástroje výrazně zjednodušují a urychlují vaši práci.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>Vytvoření aplikace knihovny MFC pomocí Průvodce aplikací knihovny MFC

Pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) vytvořte projekt knihovny MFC v jazyce Visual C++, který může zahrnovat podporu OLE a databáze. Soubory v projektu obsahují třídy aplikace, dokumentu, zobrazení a okna rámce; standardní zdroje, včetně nabídek a volitelného panelu nástrojů; další požadované soubory systému Windows; a volitelné soubory RTF obsahující standardní témata nápovědy systému Windows, které můžete revidovat a rozšířit a vytvořit soubor nápovědy programu.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Správa tříd a zpráv systému Windows pomocí zobrazení tříd

Zobrazení tříd pomáhá vytvářet funkce obslužné rutiny pro zprávy a příkazy systému Windows, vytvářet a spravovat třídy, vytvářet proměnné členů tříd, vytvářet metody a vlastnosti automatizace, vytvářet třídy databáze a další.

> [!NOTE]
> Zobrazení tříd také pomáhá přepsat virtuální funkce ve třídách knihovny MFC. Vyberte třídu a virtuální funkci, kterou chcete přepsat. Zbytek procesu je podobný zpracování zpráv, jak je popsáno v následujících odstavcích.

Aplikace spuštěné v systému Windows jsou [řízeny zprávami](../mfc/message-handling-and-mapping.md). Akce uživatele a další události, ke kterým dochází v spuštěném programu, způsobí, že systém Windows odesílá zprávy do oken programu. Pokud například uživatel klepne myší v okně, systém Windows odešle zprávu WM_LBUTTONDOWN při stisknutí levého tlačítka myši a WM_LBUTTONUP zprávu při uvolnění tlačítka. Systém Windows také odesílá WM_COMMAND zprávy, když uživatel vybere příkazy z panelu nabídek.

V rámci knihovny MFC mohou různé objekty, jako jsou dokumenty, zobrazení, okna rámců, šablony dokumentů a aplikační objekt, "zpracovávat" zprávy. Takový objekt poskytuje "obslužnou rutinu" jako jednu ze svých členských funkcí a rozhraní framework mapuje příchozí zprávu na jeho obslužnou rutinu.

Velká část programovací úlohy je výběr zpráv, které mají být mapovány na které objekty, a poté implementovat toto mapování. Chcete-li tak učinit, použijte zobrazení třídy a [Průvodce třídou](reference/mfc-class-wizard.md).

[Průvodce třídou](reference/mfc-class-wizard.md) vytvoří prázdné členské funkce obslužné rutiny zpráv a pomocí editoru zdrojového kódu implementujete tělo obslužné rutiny. Můžete také vytvořit nebo upravit třídy (včetně vlastních tříd, které nejsou odvozeny z tříd knihovny MFC) a jejich členy pomocí zobrazení tříd. Další informace o používání zobrazení tříd a průvodců, kteří přidávají kód do projektu, naleznete v [tématu Přidání funkcí pomocí Průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Použití editorů prostředků k vytváření a úpravám prostředků

Pomocí [editorů prostředků](../windows/resource-editors.md) Visual C++ můžete vytvářet a upravovat nabídky, dialogová okna, vlastní ovládací prvky, klávesy akcelerátoru, bitmapy, ikony, kurzory, řetězce a prostředky verze. Od verze Visual C++ verze 4.0 umožňuje editor panelů nástrojů vytváření panelů nástrojů mnohem jednodušší.

Aby vám knihovna tříd Microsoft Foundation pomohla ještě více, poskytuje soubor s názvem COMMON. RES, který obsahuje "klipart" prostředky, které můžete kopírovat z COMMON. RES a vložte do vlastního souboru prostředků. Společné. Res obsahuje tlačítka panelu nástrojů, běžné kurzory, ikony a další. Tyto prostředky můžete použít, upravit a dále distribuovat v aplikaci. Další informace o COMMON. RES, viz [ukázka clipartu](../overview/visual-cpp-samples.md).

Průvodce aplikací knihovny MFC, průvodci visual c++, editory prostředků a rozhraní MFC dělají spoustu práce za vás a usnadňují správu kódu. Převážná část kódu specifické pro aplikaci je ve vašem dokumentu a zobrazení třídy.

## <a name="see-also"></a>Viz také

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
