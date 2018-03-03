---
title: "Aktualizace textu panelu stavového řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0fb0f9bdaa032340256eee4781bfd775767f62ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualizace textu na panelu stavového řádku
Tento článek vysvětluje, jak změnit text, který se zobrazí v podokně panelu aplikace MFC stavu. Stavový řádek – objektem okna třídy [cstatusbar –](../mfc/reference/cstatusbar-class.md) – obsahuje několik "podokna." Každý podokno je obdélníkovou oblast stavový řádek, který můžete použít k zobrazení informací. Například mnoho aplikace se zobrazí stav klávesy CAPS LOCK NUMLOCK a jiných klíčů ve nejvíce vpravo podokna. Aplikace se zobrazí také často informativní text v krajní levé podokno (0), někdy označuje jako "podokno zpráva". Například výchozí MFC stavového řádku používá v podokně zpráv pro zobrazení řetězec vysvětlením tlačítko nabídky aktuálně vybrané položky nebo na panelu nástrojů. Na obrázku v [stavové řádky](../mfc/status-bar-implementation-in-mfc.md) zobrazuje indikátor stavu z aplikace vytvořené – Průvodce aplikací knihovny MFC.  
  
 Ve výchozím nastavení, nepovolí MFC `CStatusBar` podokně, když vytváří v podokně. Pokud chcete aktivovat podokno, musíte použít `ON_UPDATE_COMMAND_UI` makro pro každý podokně Stav panel a aktualizujte podokna. Protože podokna Neodesílat **wm_command –** zprávy (nejsou jako tlačítka panelu nástrojů), musíte ručně zadat kód.  
  
 Předpokládejme například, jeden podokno má `ID_INDICATOR_PAGE` jako jeho identifikátoru příkazu a který obsahuje aktuální číslo stránky v dokumentu. Následující postup popisuje, jak vytvořit nové podokno ve stavovém řádku.  
  
### <a name="to-make-a-new-pane"></a>Aby se nové podokno  
  
1.  Zadejte ID v podokně příkazu.  
  
     Na **zobrazení** nabídky, klikněte na tlačítko **zobrazení prostředků**. Klikněte pravým tlačítkem na zdroj projektu a klikněte na tlačítko **symboly prostředků**. V dialogovém okně symboly prostředků, klikněte na tlačítko `New`. Zadejte název příkazu ID: například `ID_INDICATOR_PAGE`. Zadejte hodnotu pro ID, nebo přijměte hodnota navrhovaná službou dialogové okno symboly prostředků. Například pro `ID_INDICATOR_PAGE`, přijměte výchozí hodnotu. Symboly prostředků dialogové okno zavřete.  
  
2.  Definujte výchozí řetězec k zobrazení v podokně.  
  
     K zobrazení prostředků otevřený, klikněte dvakrát na **řetězec tabulky** v okně, které jsou uvedeny typy prostředků pro vaši aplikaci. S **tabulky řetězců** editoru otevřete, zvolte **nový řetězec** z **vložit** nabídky. V okně Vlastnosti řetězce, vyberte ID do podokna příkazu (například `ID_INDICATOR_PAGE`) a zadejte výchozí hodnotu řetězce, jako je například "Stránka". Zavřete editor řetězce. (Potřebujete výchozí řetězec, aby se zabránilo chybě kompilátoru.)  
  
3.  Přidat podokno **indikátory** pole.  
  
     V souboru MAINFRM. CPP, vyhledejte **indikátory** pole. Toto pole obsahuje ID příkazu pro všechny indikátory stavového řádku v pořadí zleva doprava. V odpovídajícím bodě v poli, zadejte do podokna příkazu ID, jak je vidět tady pro `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 Doporučený způsob zobrazení textu v podokno je volání **SetText –** funkce člena třídy `CCmdUI` v obslužná rutina funkci aktualizace pro podokně. Například můžete chtít nastavit proměnná typu integer `m_nPage` obsahující aktuální číslo stránky a použijte **SetText –** nastavení textu v podokně na řetězec verzi toto číslo.  
  
> [!NOTE]
>  **SetText –** se doporučuje přístup. Je možné provést tuto úlohu na mírně nižší úrovni voláním `CStatusBar` – členská funkce `SetPaneText`. I tak je stále nutné obslužnou rutinu aktualizace. Bez takové obslužnou rutinu pro podokně MFC automaticky zakáže podokně mazání jeho obsah.  
  
 Následující postup ukazuje, jak používat funkci obslužné rutiny aktualizace zobrazení textu v podokně.  
  
#### <a name="to-make-a-pane-display-text"></a>Chcete-li do podokna zobrazení textu  
  
1.  Přidejte obslužnou rutinu aktualizace příkazu pro příkaz.  
  
     Ručně přidejte prototypu pro obslužnou rutinu, jak je vidět tady pro `ID_INDICATOR_PAGE` (v MAINFRM. H):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  Do odpovídajícího. CPP soubor, přidejte obslužné rutiny definice, jak je vidět tady pro `ID_INDICATOR_PAGE` (v MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     Poslední tři řádky této rutiny se kód, který zobrazí text.  
  
3.  V příslušnou zprávu mapy, přidejte `ON_UPDATE_COMMAND_UI` makro, jak je vidět tady pro `ID_INDICATOR_PAGE` (v MAINFRM. CPP):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 Jakmile definujete hodnotu `m_nPage` členské proměnné (třídy `CMainFrame`), tento postup způsobí, že se objeví v podokně během zpracování při nečinnosti stejným způsobem, že aplikace aktualizuje další indikátory číslo stránky. Pokud `m_nPage` změn, změny zobrazení během další nečinné smyčky.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Aktualizace objektů uživatelského rozhraní (postup aktualizace tlačítka panelu nástrojů a položek nabídky jako změnu podmínky programu)](../mfc/how-to-update-user-interface-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace stavového řádku v prostředí MFC](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar – třída](../mfc/reference/cstatusbar-class.md)
