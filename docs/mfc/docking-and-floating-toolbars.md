---
title: Ukotvitelné a plovoucí panely nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 317527d87c12a0c140c4a618ec4500dbe12bb003
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931886"
---
# <a name="docking-and-floating-toolbars"></a>Ukotvitelné a plovoucí panely nástrojů
Knihovny Microsoft Foundation Class podporuje lze ukotvit panely nástrojů. Lze ukotvit panelu nástrojů můžete připojit nebo ukotven na žádné straně nadřazené okno, nebo může být odpojený od, nebo obtékané v samostatném okně zkrácená rámce. Tento článek vysvětluje, jak používat lze ukotvit panely nástrojů ve svých aplikacích.  
  
 Pokud používáte Průvodce aplikace ke generování kostru aplikace, zobrazí se výzva zvolit, jestli chcete lze ukotvit panely nástrojů. Ve výchozím nastavení Průvodce aplikací generuje kód, který provádí tři akce, která je nutné umístit lze ukotvit panelu nástrojů v aplikaci:  
  
-   [Povolit ukotvení v okně s rámečkem](#_core_enabling_docking_in_a_frame_window).  
  
-   [Povolit ukotvení pro panel nástrojů](#_core_enabling_docking_for_a_toolbar).  
  
-   [Ukotvení panelu nástrojů (do okna s rámečkem)](#_core_docking_the_toolbar).  
  
 Pokud některé z těchto kroků chybí, aplikace se zobrazí standardním panelu nástrojů. Poslední dva kroky je potřeba provést pro každý lze ukotvit panelu nástrojů v aplikaci.  
  
 Další témata popsaná v tomto článku:  
  
-   [Plovoucí panelu nástrojů](#_core_floating_the_toolbar)  
  
-   [Dynamicky Změna velikosti panelu nástrojů](#_core_dynamically_resizing_the_toolbar)  
  
-   [Pozice wrap nastavení pro panel nástrojů – styl](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)  
  
 Viz ukázka MFC Obecné [DOCKTOOL](../visual-cpp-samples.md) příklady.  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> Povolení ukotvení v okně s rámečkem  
 Pokud chcete ukotvit panely nástrojů k okně s rámečkem, musí být oken s rámečkem (nebo cílové) povolený a umožňuje ukotvení. To se provádí pomocí [CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) funkce, která přebírá jeden *DWORD* parametr, který je sada styl bits, která určuje, které straně okna rámce přijímá ukotvení. Pokud panelu nástrojů je možné ukotvena a více stran, které by mohly být ukotvena se Postranní uvedené v parametru předaný `EnableDocking` se používají v následujícím pořadí: nahoře, dole, vlevo, vpravo. Pokud chcete mít možnost ukotvení ovládacího prvku panely odkudkoli, předat **cbrs_align_any –** k `EnableDocking`.  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> Povolení ukotvení pro panel nástrojů  
 Jakmile dokončíte přípravu cíl pro ukotvení, je nutné připravit panelu nástrojů (nebo zdroj) podobným způsobem. Volání [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) pro každý chcete ukotvení panelu nástrojů zadání cílové strany, na který by měl ukotvení panelu nástrojů. Pokud žádná z konce zadané ve volání `CControlBar::EnableDocking` postranní povolené pro ukotvení v rámci okna se shodují, nelze ukotvení panelu nástrojů – bude float. Jakmile byl obtékané, zůstane plovoucí panel nástrojů nelze ukotvit do okna s rámečkem.  
  
 Pokud chcete efekt je trvale plovoucí panel nástrojů, zavolejte `EnableDocking` s parametrem 0. Potom zavolejte [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Panelu nástrojů zůstává plovoucí, trvale nelze ukotvit kdekoli.  
  
##  <a name="_core_docking_the_toolbar"></a> Ukotvení panelu nástrojů  
 Volání framework [CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) když se uživatel pokusí o vyřadit na straně okna rámce, který umožňuje ukotvení panelu nástrojů.  
  
 Kromě toho můžete volat tuto funkci kdykoli ukotvení ovládací pruhy do rámce okna. To se obvykle provádí během inicializace. Více než jeden nástrojů můžete jej ukotven k okraji rámce okna.  
  
##  <a name="_core_floating_the_toolbar"></a> Plovoucí panelu nástrojů  
 Odpojování lze ukotvit panelu nástrojů v okně rámce se nazývá plovoucí panelu nástrojů. Volání [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) k tomu. Zadejte panelu nástrojů obtékání bodu, kde se má umístit a zarovnání styl, který určuje, zda je plovoucí panel nástrojů vodorovně nebo svisle.  
  
 Rozhraní framework volá tuto funkci, když uživatel nastavuje tažením panelu nástrojů vypnout místa ukotvení a zahodí v umístění, kde není povoleno ukotvení. To může být kdekoli uvnitř nebo vně rámce okna. Stejně jako u `DockControlBar`, můžete také volání této funkce během inicializace.  
  
 Implementace MFC lze ukotvit panely nástrojů neposkytuje některé rozšířené funkce některé aplikace, které podporují lze ukotvit panely nástrojů. Funkce, jako je přizpůsobitelné panely nástrojů nejsou zadány.  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> Dynamicky Změna velikosti panelu nástrojů  
 Od verze Visual C++ verze 4.0 můžete můžete umožnit uživatelům vaší aplikace ke změně velikosti plovoucí panely nástrojů dynamicky. Panel nástrojů má obvykle, dlouhé, lineární obrazce zobrazovat vodorovně. Ale můžete změnit orientaci panelu nástrojů a jeho tvaru. Například pokud uživatel ukotvené panelu nástrojů pro jeden z svislého strany rámce okna, tvar, který se změní na svislém rozložení. Také je možné změnit tvar panelu nástrojů do obdélníku s více řádky tlačítka.  
  
 Můžeš:  
  
-   Zadejte dynamické úpravy velikosti jako vlastnosti panelu nástrojů.  
  
-   Zadejte nastavení pevné velikosti jako vlastnosti panelu nástrojů.  
  
 K podpoře, existují dva nové styly nástrojů pro použití ve vašem volání [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) – členská funkce. Možnosti jsou následující:  
  
-   **Cbrs_size_dynamic –** ovládacích pruhů je dynamický.  
  
-   **Cbrs_size_fixed –** ovládacích pruhů vyřešen.  
  
 Styl dynamické velikost umožňuje změnit velikost panelu nástrojů, když je plovoucí, ale není při je ukotvena uživatelů. Panelu nástrojů "zabalí" tam, kde je potřeba změnit tvar jako uživatel nastavuje tažením jeho okraje.  
  
 Velikost pevné styl zachovává wrap stavy nástrojů opravě pozici tlačítek v každém sloupci. Vaše aplikace uživatel nemůže změnit obrazec panelu nástrojů. Zabalí panelu nástrojů na určené místech, jako je například umístění oddělovače mezi tlačítka. Zda je panel nástrojů ukotvený nebo plovoucí udržuje tento tvar. Efekt je pevné palety s více sloupci tlačítek.  
  
 Můžete také použít [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) k vrácení stavu a stylu pro tlačítka v panelech nástrojů. Určuje styl tlačítko vzhled tlačítka a odpovědí na vstup uživatele; Stav informuje, zda je tlačítko v zabalené stavu.  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Pozice Wrap nastavení pro panel nástrojů – styl  
 Panel nástrojů s velikostí pevné styl určete panelu nástrojů tlačítko indexy, na kterých budou zahrnovat panelu nástrojů. Následující kód ukazuje, jak to udělat v okně hlavního rámce `OnCreate` přepsání:  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]  
  
 Ukázka MFC Obecné [DOCKTOOL](../visual-cpp-samples.md) ukazuje způsob použití členské funkce tříd [ccontrolbar –](../mfc/reference/ccontrolbar-class.md) a [ctoolbar –](../mfc/reference/ctoolbar-class.md) ke správě dynamické rozložení panelu nástrojů. Naleznete v souboru EDITBAR. CPP v DOCKTOOL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Popisy tlačítek panelu nástrojů](../mfc/toolbar-tool-tips.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)

