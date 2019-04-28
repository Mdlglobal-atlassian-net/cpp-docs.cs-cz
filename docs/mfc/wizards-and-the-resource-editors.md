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
ms.openlocfilehash: 41cbb86b4245bd78baecd222b5573ba5e877243a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338295"
---
# <a name="wizards-and-the-resource-editors"></a>Průvodci a editory prostředků

Visual C++ obsahuje několik průvodců pro použití v programování knihovny MFC, spolu s mnoha editory integrované prostředků. Pro programování a ovládací prvky ActiveX [Průvodce ovládacím prvkem ActiveX](../mfc/reference/mfc-activex-control-wizard.md) slouží k účelu, stejně jako u Průvodce aplikací knihovny MFC. Přestože můžete psát aplikace knihovny MFC bez většina těchto nástrojů, nástroje výrazně Zjednodušte a urychlete svou práci.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Vytvoření aplikace knihovny MFC pomocí Průvodce aplikací MFC

Použití [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) pro vytvoření projektu knihovny MFC v jazyce Visual C++, které můžete zahrnout OLE a podpora databáze. Obsahují soubory v projektu aplikace, dokumentu, zobrazení a třídy oken s rámečkem; standardní prostředky, včetně nabídek a volitelné nástrojů; Další požadované soubory Windows; a standardní témata nápovědy Windows, které můžete upravit a rozšířit k vytvoření souboru nápovědy váš program, který obsahuje soubory .rtf volitelné.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Zobrazení tříd používá Správa třídy a zpráv Windows

Třídy zobrazení pomáhá vytvářet funkce obslužné rutiny pro zprávy o Windows a příkazy, vytvářet a spravovat třídy, vytvořte proměnné člena třídy, vytvoření automatizace metody a vlastnosti, vytvoření databázové třídy a další.

> [!NOTE]
>  Zobrazení tříd také umožňuje přepsat virtuální funkce v třídách knihovny MFC. Vyberte třídu a virtuální funkce pro přepsání. Zbytek procesu je podobný zpracování zpráv, jak je popsáno v následujících odstavcích.

Aplikace běžící v rámci Windows jsou [zpráva řízené](../mfc/message-handling-and-mapping.md). Akce uživatele a další události, ke kterým dochází v běžící aplikaci způsobit, že Windows k odesílání zpráv do systému windows v programu. Například když uživatel klikne myší v okně, Windows odešle WM_LBUTTONDOWN zprávu, když se stiskne levé tlačítko myši a napište zprávu, WM_LBUTTONUP při uvolnění tlačítka. Windows rovněž odesílá wm_command – zprávy, když uživatel vybere příkazy na řádku nabídek.

V rámci MFC různé objekty, jako jsou dokumenty, zobrazení, oken s rámečkem, šablony dokumentů a objekt aplikace můžete "handle" zprávy. Takový objekt poskytuje "funkci obslužné rutiny" jako jeden z jeho členské funkce a rozhraní mapuje příchozí zprávy na její obslužná rutina.

Velkou část úlohou programování je výběr zpráv pro mapování na které objekty a pak implementace mapování. K tomu použijete zobrazení tříd a okně Vlastnosti.

V okně Vlastnosti vytvoří prázdný popisovač zpráv členské funkce a používat editor zdrojového kódu k implementaci těla obslužné rutiny. Můžete také vytvořit nebo upravit třídy (včetně třídy vlastní neodvozených ze třídy knihovny MFC) a jejich členy s zobrazení tříd. Další informace o použití zobrazení tříd a o Průvodci, který do projektu přidejte kód, naleznete v tématu [přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Editory prostředků můžete vytvořit a upravit prostředky

Použití jazyka Visual C++ [editory prostředků](../windows/resource-editors.md) vytvářet a upravovat nabídek, dialogová okna, vlastní ovládací prvky, klávesové zkratky, rastrové obrázky, ikony, kurzory, řetězce a verze zdroje. Od verze Visual C++ verze 4.0 editor panelu nástrojů jednodušší vytváření panelů nástrojů.

To vám pomůže i, poskytuje knihovny Microsoft Foundation Class soubor s názvem COMMON. RES, který obsahuje "klipart" prostředky, které můžete zkopírovat z běžné. RES a vložit do souboru prostředků. BĚŽNÉ. RES obsahuje tlačítka na panelu nástrojů, běžné kurzorů, ikony a další. Můžete použít, upravit a distribuovat tyto prostředky ve vaší aplikaci. Další informace o běžné. RES, najdete v článku [klipart ukázka](../overview/visual-cpp-samples.md).

Průvodce aplikací MFC, průvodců aplikace Visual C++, editory prostředků a rozhraní MFC dělat spoustu práce za vás a ujistěte se, správa kódu mnohem jednodušší. Hromadné kódu specifické pro aplikaci se dokument a zobrazení tříd.

## <a name="see-also"></a>Viz také:

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
