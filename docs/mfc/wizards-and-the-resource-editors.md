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
ms.openlocfilehash: fb1a523ca82cd8e1a4256da657efe9702517beda
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907355"
---
# <a name="wizards-and-the-resource-editors"></a>Průvodci a editory prostředků

Vizuál C++ obsahuje několik průvodců pro použití v programování MFC spolu s mnoha integrovanými editory prostředků. Pro programování ovládacích prvků ActiveX slouží [Průvodce ovládacím prvkem ActiveX](../mfc/reference/mfc-activex-control-wizard.md) jako takový, podobně jako v Průvodci aplikací knihovny MFC. I když můžete psát aplikace MFC bez většiny těchto nástrojů, nástroje značně zjednodušují a urychlují práci.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>Použití Průvodce aplikací knihovny MFC k vytvoření aplikace MFC

Použijte [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) k vytvoření projektu MFC v jazyce Visual C++, který může zahrnovat podporu technologie OLE a databáze. Soubory v projektu obsahují aplikace, dokumenty, zobrazení a třídy oken s rámečkem; standardní prostředky, včetně nabídek a volitelného panelu nástrojů; Další požadované soubory Windows; a volitelné soubory. RTF obsahující standardní témata nápovědy systému Windows, která můžete revidovat a rozšířit a vytvořit tak soubor nápovědy programu.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Použití Zobrazení tříd ke správě tříd a zpráv Windows

Zobrazení tříd pomáhá vytvářet obslužné rutiny pro zprávy a příkazy systému Windows, vytvářet a spravovat třídy, vytvářet členské proměnné třídy, vytvářet metody a vlastnosti automatizace, vytvářet databázové třídy a další.

> [!NOTE]
>  Zobrazení tříd také pomůže přepsat virtuální funkce v třídách MFC. Vyberte třídu a virtuální funkci, kterou chcete přepsat. Zbytek procesu je podobný zpracování zpráv, jak je popsáno v následujících odstavcích.

Aplikace spuštěné v systému Windows jsou [řízeny zprávou](../mfc/message-handling-and-mapping.md). Akce uživatele a další události, ke kterým dojde v běžícím programu, způsobí, že systém Windows odesílá zprávy do oken v programu. Pokud uživatel například klikne na myš v okně, systém Windows pošle zprávu WM_LBUTTONDOWN při stisknutí levého tlačítka myši a zprávu WM_LBUTTONUP při uvolnění tlačítka. Systém Windows odesílá také zprávy WM_COMMAND, když uživatel vybere příkazy z řádku nabídek.

V rozhraní knihovny MFC mohou různé objekty, jako jsou například dokumenty, zobrazení, okna s rámečkem, šablony dokumentů a objekt aplikace, sloužit ke zpracování zpráv. Takový objekt poskytuje "funkci obslužné rutiny" jako jednu z jejích členských funkcí a rozhraní mapuje příchozí zprávu na její obslužnou rutinu.

Velkou součástí úlohy programování je výběr zpráv, které mají být namapovány na které objekty a následně implementují toto mapování. K tomu slouží Zobrazení tříd a [Průvodce třídou](reference/mfc-class-wizard.md).

[Průvodce třídou](reference/mfc-class-wizard.md) vytvoří prázdné členské funkce obslužných rutin zpráv a použijete Editor zdrojového kódu k implementaci těla obslužné rutiny. Můžete také vytvořit nebo upravit třídy (včetně tříd, které vlastní, nejsou odvozeny z tříd knihovny MFC) a jejich členy pomocí Zobrazení tříd. Další informace o použití Zobrazení tříd a o průvodcích, které přidávají kód do projektu, naleznete v tématu [Přidání funkcionality pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Vytváření a upravování prostředků pomocí editorů prostředků

Pomocí C++ [editorů](../windows/resource-editors.md) vizuálních prostředků můžete vytvářet a upravovat nabídky, dialogová okna, vlastní ovládací prvky, klávesové zkratky, rastrové obrázky, ikony, kurzory, řetězce a verze prostředků. Od verze Visual C++ 4,0 je editor panelů nástrojů mnohem jednodušší vytvářet panely nástrojů.

Abychom vám pomohli ještě víc, knihovna Microsoft Foundation Class poskytuje soubor s názvem COMMON. RES, která obsahuje prostředky "kliparty", které můžete kopírovat ze společného. RES a vložte do vlastního souboru prostředků. Obecný. RES obsahuje tlačítka panelu nástrojů, běžné kurzory, ikony a další. Tyto prostředky můžete v aplikaci použít, upravit a znovu distribuovat. Další informace o COMMON. RES, viz [Ukázka klipartu](../overview/visual-cpp-samples.md).

Průvodce aplikací knihovny MFC, vizuálními C++ průvodci, editory prostředků a rozhraním MFC můžete pro vás využít spoustu práce a zjednodušit správu kódu. Hromadný kód specifický pro aplikaci je ve vašem dokumentu a třídách zobrazení.

## <a name="see-also"></a>Viz také:

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
