---
title: "Prvky rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5eead62c46bb9405a63bd523508142575a8ad93f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="interface-elements"></a>Prvky rozhraní
Tento dokument popisuje elementy rozhraní, které byly zavedeny v [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] SP1 a také popisuje rozdíly mezi starší verzi knihovny.  
  
 Následující obrázek znázorňuje aplikaci, která byla vytvořená pomocí nové prvky rozhraní.  
  
 ![Ukázková aplikace MFC Feature Pack](../mfc/media/mfc_featurepack.png "mfc_featurepack")  
  
## <a name="window-docking"></a>Okno ukotvení  
 Okno ukotvení funkce se podobá okno ukotvení, který [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] grafické uživatelské rozhraní využívá.  
  
## <a name="control-bars-are-now-panes"></a>Ovládací pruhy jsou nyní podokna  
 Ovládací pruhy jsou teď znáte jako podokna a jsou odvozené z [CBasePane třída](../mfc/reference/cbasepane-class.md). V dřívějších verzích MFC základní třídu ovládací pruhy byla `CControlBar`.  
  
 Obvykle představuje hlavního rámce okna aplikace [CFrameWndEx třída](../mfc/reference/cframewndex-class.md) nebo [CMDIFrameWndEx Class](../mfc/reference/cmdiframewndex-class.md). Je volána hlavního rámce *ukotvení lokality*. Podokna může mít jeden ze tří typů nadřazených prvků: ukotvení webu, ukotvení panelu nebo zkrácená rámce okna.  
  
 Existují dva typy podokna: bez umožňující změnu velikosti a s možností změny velikosti. Umožňující změnu velikosti podokna, jako je například stavové řádky a panelů nástrojů, můžete změnit pomocí příčky nebo posuvníky. Umožňující změnu velikosti podokna mohl vytvořit kontejnery (jeden podokně lze ukotvit do jiného podokna, vytváření rozdělovače mezi nimi). Ale umožňující změnu velikosti podokna nelze připojit (ukotven) ukotvení řádky.  
  
 Pokud vaše aplikace používá jiný umožňující změnu velikosti podokna, odvozena z [CPane třída](../mfc/reference/cpane-class.md).  Pokud vaše aplikace používá umožňující změnu velikosti podokna, odvozena z [CDockablePane – třída](../mfc/reference/cdockablepane-class.md)  
  
## <a name="dock-site"></a>Ukotvení lokality  
 Ukotvení lokality (nebo hlavního rámce okna) vlastní všechny podokna a okna s rámečkem zkrácená v aplikaci. Ukotvení lokalita obsahuje [CDockingManager](../mfc/reference/cdockingmanager-class.md) člen. Tento člen udržuje seznam všech podokna, které patří k webu ukotvení. Seznam tak, aby podokna vytvořený v částí webu ukotvení jsou umístěny na začátku seznamu. Když rozhraní ho překreslí webu ukotvení, cyklicky prochází přes tento seznam a upraví rozložení jednotlivých panelech zahrnout aktuální ohraničující obdélník webu ukotvení. Můžete volat `AdjustDockingLayout` nebo `RecalcLayout` když budete muset upravit ukotvení rozložení a rozhraní přesměruje volání správce ukotvení.  
  
## <a name="dock-bars"></a>Ukotvení pruhy  
 Každý hlavní rámec okna, můžete umístit *ukotvení řádky* podél jeho hranice. Ukotvení panelu je podokno, které patří [CDockSite třída](../mfc/reference/cdocksite-class.md). Ukotvení řádky může přijmout objekty, které jsou odvozené z [CPane](../mfc/reference/cpane-class.md), jako je například panely nástrojů. Chcete-li vytvořit panely ukotvení při inicializaci hlavního okna rámce, volejte `EnableDocking`. Chcete-li povolit automatické skrýt řádky, volejte `EnableAutoHideBars`. `EnableAutoHideBars`vytvoří [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) objekty a jejich umisťuje vedle jednotlivých ukotvení panelu.  
  
 Každý ukotvení panelu je rozdělena na řádky ukotvení. Ukotvení řádky jsou reprezentované pomocí [CDockingPanesRow třída](../mfc/reference/cdockingpanesrow-class.md). Každý řádek ukotvení obsahuje seznam panely nástrojů. Pokud uživatel ukotvené panelu nástrojů nebo Přesune panel nástrojů z jeden řádek do jiné v rámci stejné ukotvení panelu, rozhraní framework vytvoří nový řádek a odpovídajícím způsobem změní na ukotvení panelu, nebo ji umisťuje panelu nástrojů na stávající řádek.  
  
## <a name="mini-frame-windows"></a>Okna s rámečkem zkrácená  
 Plovoucí podokno se nachází v okně s rámečkem zkrácená. Okna s rámečkem zkrácená jsou reprezentované pomocí dvou tříd: [CMDITabInfo třída](../mfc/reference/cmditabinfo-class.md) (která může obsahovat jenom jeden podokně) a [CMultiPaneFrameWnd třída](../mfc/reference/cmultipaneframewnd-class.md) (která může obsahovat několik podokna). Chcete-li uvolnit podokno ve vašem kódu, volejte [CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane). Po jako plovoucí podokno, systém automaticky vytvoří zkrácená rámce okna a stane se okno zkrácená rámce plovoucí podokně nadřazené. Když plovoucí podokno ukotvené, rozhraní obnoví jeho nadřazený objekt a podokně plovoucí stane ukotvení panelu (pro panely nástrojů) nebo web ukotvení (pro umožňující změnu velikosti podokna).  
  
## <a name="pane-dividers"></a>Podokno oddělovačů  
 Podokno oddělovače (nazývaná také posuvníky nebo příčky) jsou reprezentované pomocí [CPaneDivider třída](../mfc/reference/cpanedivider-class.md). Když uživatel ukotvené podokno, vytvoří rozhraní podokně oddělovače, bez ohledu na to, jestli je v podokně ukotven na ukotvení lokality nebo na jinou podokně. Podokno ukotvené k webu ukotvení, se nazývá dělicí podokně *výchozí podokně dělicí*. Grafika podokně výchozí je zodpovědná za rozložení všechny ukotvení podokna v lokalitě ukotvení. Správce ukotvení udržuje seznam výchozí podokně rozdělení a seznam podokna. Ukotvení správci jsou zodpovědní za rozložení ukotvení podokna.  
  
## <a name="containers"></a>Kontejnery  
 Všechny umožňující změnu velikosti podokna, pokud jej ukotven k sobě navzájem, se udržují v kontejnerech. Kontejnery jsou reprezentované pomocí [CPaneContainer třída](../mfc/reference/cpanecontainer-class.md). Každý kontejner obsahuje odkazy na jeho levém podokně, pravém podokně, levé dílčí kontejneru, správném dílčí kontejneru a rozdělovače mezi levé a pravé části. (*Doleva* a *správné* neodkazují na fyzické strany, ale spíš identifikovat větve stromovou strukturu.) Tímto způsobem jsme vytvoření stromu podokna a příčky a proto dosáhnout komplexní rozložení podokny, která může být po změně velikosti společně. `CPaneContainer` Třída udržuje stromu kontejnerů; také udržuje dva seznamy podokna a jezdce, které se nacházejí v tomto stromu. Správci kontejneru podokně jsou obvykle vkládat do výchozí posuvníky a okna s rámečkem malý, které zajišťují více podoken.  
  
## <a name="auto-hide-control-bars"></a>Automaticky skrýt ovládací pruhy  
 Ve výchozím nastavení každý `CDockablePane` podporuje funkci automaticky skrýt. Když uživatel klikne na tlačítko PIN kód na titulek `CDockablePane`, v podokně rozhraní se přepne do režimu automaticky skrýt. Pro zpracování kliknutím na možnost, vytvoří rozhraní [CMFCAutoHideBar – třída](../mfc/reference/cmfcautohidebar-class.md) a [CMFCAutoHideButton třída](../mfc/reference/cmfcautohidebutton-class.md) přidružené `CMFCAutoHideBar` objektu. Rozhraní framework vloží novou `CMFCAutoHideBar` na [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md). Rozhraní framework také připojí `CMFCAutoHideButton` na panelu nástrojů. [CDockingManager třída](../mfc/reference/cdockingmanager-class.md) udržuje `CDockablePane`.  
  
## <a name="tabbed-control-bars-and-outlook-bars"></a>Ovládací pruhy s kartami a Outlook řádky  
 [CMFCBaseTabCtrl třída](../mfc/reference/cmfcbasetabctrl-class.md) implementuje základní funkce okno s kartami odpojitelných karty. Použít `CMFCBaseTabCtrl` objektu, inicializovat [CBaseTabbedPane třída](../mfc/reference/cbasetabbedpane-class.md) ve vaší aplikaci. `CBaseTabbedPane`je odvozený od `CDockablePane` a uchovává ukazatel `CMFCBaseTabCtrl` objektu. `CBaseTabbedPane` Umožňuje uživatelům ukotvení a změňte velikost záložkách ovládací pruhy. Použití [CDockablePane::AttachToTabWnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd) vytvořit dynamicky ovládací pruhy, které jsou ukotvena a na kartách.  
  
 Ovládací prvek panelu aplikace Outlook je také založená na záložkách řádky. [CMFCOutlookBar Class](../mfc/reference/cmfcoutlookbar-class.md) je odvozený od `CBaseTabbedPane`. Další informace o tom, jak pomocí Outlooku panelu najdete v tématu [CMFCOutlookBar Class](../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)

