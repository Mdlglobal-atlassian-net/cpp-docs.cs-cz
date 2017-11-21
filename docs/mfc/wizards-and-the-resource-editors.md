---
title: "Průvodci a editory prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c91ba5c74ebda12df4bc912ac8bd760263364345
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wizards-and-the-resource-editors"></a>Průvodci a editory prostředků
Visual C++ obsahuje několik průvodců pro použití v MFC – programování, společně s mnoha editory integrované prostředků. Pro programování, ovládací prvky ActiveX [Průvodce ovládacím prvkem ActiveX](../mfc/reference/mfc-activex-control-wizard.md) slouží k účelu, podobně jako u Průvodce aplikací MFC. Při můžete psát aplikace MFC bez většinu těchto nástrojů, nástroje výrazně zjednodušit a urychlit práci.  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>Vytvoření aplikace knihovny MFC pomocí Průvodce aplikací MFC  
 Použití [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) k vytvoření projektu knihovny MFC v jazyce Visual C++, což může zahrnovat OLE a podpora databáze. Soubory v projektu obsahují aplikace, dokumentu, zobrazení a oken s rámečkem třídy; standardní prostředky, včetně nabídky a volitelné nástrojů; Další požadované soubory Windows; a volitelné .rtf soubory obsahující standardní témata nápovědy pro Windows, která můžete revidovat a posílení k vytvoření souboru nápovědy vašeho programu.  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Zobrazení tříd použijte ke správě třídy a zpráv systému Windows  
 Třídy zobrazení pomáhá vytvářet funkce obslužných rutin zpráv systému Windows a příkazy, vytvořit a spravovat třídy, vytvořit člen třídy proměnné, vytvoření automatizace metody a vlastnosti, vytvoření databázové třídy a další.  
  
> [!NOTE]
>  Zobrazení tříd také pomáhá přepsání virtuální funkce do tříd MFC. Vyberte třídu a virtuální funkce pro přepsání. Zbytek procesu je podobná zpracování zpráv, jak je popsáno v následujících odstavcích.  
  
 Aplikace běžící v systému Windows jsou [zpráva řízené](../mfc/message-handling-and-mapping.md). Akcemi uživatelů a dalších událostí, ke kterým došlo v programu spuštěný systém Windows k odesílání zpráv do systému windows v programu. Například pokud uživatel klikne na tlačítko myši v okně, systém Windows odešle `WM_LBUTTONDOWN` při stisknutí levým tlačítkem myši a zpráv `WM_LBUTTONUP` zprávy při vydání tlačítko. Systém Windows odešle také **wm_command –** zprávy, když uživatel vybere příkazy z řádku nabídek.  
  
 V rozhraní MFC framework různé objekty, jako jsou dokumenty, zobrazení, okna s rámečkem, šablony dokumentů a objekt aplikace může "zpracovávat" zprávy. Takového objektu poskytuje "obslužné rutiny funkce" jako jeden z jeho členských funkcí a rozhraní mapuje příchozí zpráva její obslužnou rutinu.  
  
 Velkou část programovací úkolu je výběr zprávy k mapování na které objekty a pak implementace mapování. Uděláte to tak, použijte zobrazení tříd a okně Vlastnosti.  
  
 Okno vlastností vytvoří prázdný popisovač zpráv členské funkce a pomocí editoru zdrojového kódu pro implementaci text obslužné rutiny. Můžete také vytvořit nebo upravit třídy (třídy vlastní není odvozen od třídy MFC včetně) a jejich členové s zobrazení tříd. Další informace o používání zobrazení tříd a o Průvodci, který přidá do projektu kódu najdete v tématu [přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Editory prostředků slouží k vytvoření a úpravě prostředků  
 Pomocí Visual C++ [editory prostředků](../windows/resource-editors.md) můžete vytvářet a upravovat nabídky, dialogová okna, vlastní ovládací prvky, klávesy akcelerátoru, rastrové obrázky, ikony, kurzory, řetězce a verze prostředky. Od verze Visual C++ verze 4.0 editor panelu nástrojů jednodušší vytváření panelů nástrojů.  
  
 Můžete i další, poskytuje knihovny Microsoft Foundation Class do souboru s názvem běžné. RES, který obsahuje "clip art" prostředky, které můžete zkopírovat z běžné. RES a vložte do souboru prostředků. BĚŽNÉ. RES zahrnuje tlačítka panelu nástrojů, běžné kurzory, ikony a další. Můžete použít, upravit a znovu distribuovat tyto prostředky ve vaší aplikaci. Další informace o běžné. RES, najdete v článku [Clipart ukázka](../visual-cpp-samples.md).  
  
 Průvodce aplikací MFC, průvodci Visual C++, editory prostředků a rozhraní MFC framework velké množství pracovních to pro vás a ujistěte se, správa kódu mnohem jednodušší. Třídy dokumentů a zobrazení se hromadným kódu pro konkrétní aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
