---
title: Prvky rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8cb2a8f3ccb36f3fa1ed2bf3f81087691ce988
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404407"
---
# <a name="interface-elements"></a>Prvky rozhraní

Tento dokument popisuje prvky rozhraní, které byly zavedeny v systému Visual Studio 2008 SP1 a také rozdíly v dřívější verzi knihovny.

Následující obrázek znázorňuje aplikaci, která byla vytvořena pomocí nové prvky rozhraní.

![Ukázková aplikace knihovny MFC Feature Pack](../mfc/media/mfc_featurepack.png "mfc_featurepack")

## <a name="window-docking"></a>Okno ukotvení

Okno ukotvení, používá grafické uživatelské rozhraní sady Visual Studio se podobá funkci ukotvení oken.

## <a name="control-bars-are-now-panes"></a>Ovládací pruhy jsou nyní podokna

Ovládací pruhy se souhrnně označují jako podokna a jsou odvozeny z [cbasepane – třída](../mfc/reference/cbasepane-class.md). V dřívějších verzích MFC se základní třídy ovládacích pruhů `CControlBar`.

Aplikace hlavní okno rámce je obvykle reprezentováno [cframewndex – třída](../mfc/reference/cframewndex-class.md) nebo [CMDIFrameWndEx – třída](../mfc/reference/cmdiframewndex-class.md). Je volána hlavního rámce *ukotvit lokality*. Podokna může mít jeden ze tří typů nadřazených objektů: dokovacím místě, ukotvení panelu nebo okno s minirámcem.

Existují dva typy podoken: bez možností změny velikosti a umožňující změnu velikosti. Můžete změnit velikost umožňující změnu velikosti podoken, jako je například stavové řádky a panely nástrojů, pomocí příčky nebo posuvníky. Umožňující změnu velikosti podoken mohl vytvořit kontejnery (jedno podokno lze ukotvit do jiného podokna vytváření rozdělovač mezi nimi). Ale umožňující změnu velikosti podoken nelze připojit (ukotven) ukotvení pruhy.

Pokud vaše aplikace používá bez možností změny velikosti podoken, jsou odvozeny z [cpane – třída](../mfc/reference/cpane-class.md).  Pokud vaše aplikace používá umožňující změnu velikosti podoken, jsou odvozeny z [CDockablePane – třída](../mfc/reference/cdockablepane-class.md)

## <a name="dock-site"></a>Dokovacího webu

Dokovacím místě (nebo okna hlavního rámce) vlastní všechny podokna a okna s minirámcem objektů Window v aplikaci. Obsahuje dokovacím místě [cdockingmanager –](../mfc/reference/cdockingmanager-class.md) člena. Tento člen udržuje seznam všech podoken, které patří do dokovacího webu. Seznam je seřazen tak, aby podokna vytvořil vnější hrany dokovacím místě jsou umístěny na začátku seznamu. Když rozhraní překreslí dokovacím místě, smyčky v tomto seznamu a upraví rozložení jednotlivých panelech zahrnout aktuální ohraničující obdélník dokovacího webu. Můžete volat `AdjustDockingLayout` nebo `RecalcLayout` když budete muset upravit dokovací rozložení a rozhraní přesměruje volání na dokovací manager.

## <a name="dock-bars"></a>Ukotvit pruhy

Každé okno hlavního rámce lze umístit *ukotvěte panely* podél jeho okrajů. Ukotvení panelu je podokno, které patří [cdocksite – třída](../mfc/reference/cdocksite-class.md). Ukotvit pruhy může přijmout objektů odvozených od [cpane –](../mfc/reference/cpane-class.md), jako je například panely nástrojů. Chcete-li vytvořit panely ukotvení při inicializaci oknem hlavního rámce, zavolejte `EnableDocking`. Chcete-li povolit automatické skrývání pruhy, zavolejte `EnableAutoHideBars`. `EnableAutoHideBars` vytvoří [cautohidedocksite –](../mfc/reference/cautohidedocksite-class.md) objekty a umisťuje vedle každého ukotvení panelu.

Každý ukotvit panel je rozdělen do docku řádků. Ukotvit řádky jsou reprezentovány [cdockingpanesrow – třída](../mfc/reference/cdockingpanesrow-class.md). Každý řádek dock obsahuje seznam panely nástrojů. Pokud uživatel ukotvené panelu nástrojů nebo Přesune panel nástrojů z jeden řádek do jiného v rámci stejné ukotvení panelu, rozhraní vytvoří nový řádek a změní velikost panelu ukotvení odpovídajícím způsobem, nebo ho pozic panelu nástrojů na stávající řádek.

## <a name="mini-frame-windows"></a>Okna s minirámcem Windows

Plovoucí podokno se nachází v okno s minirámcem. Okna s minirámcem windows jsou reprezentované pomocí dvou tříd: [cmditabinfo – třída](../mfc/reference/cmditabinfo-class.md) (která může obsahovat pouze jedno podokno) a [cmultipaneframewnd – třída](../mfc/reference/cmultipaneframewnd-class.md) (která může obsahovat několik podokna). Chcete-li uvolnit podokno ve vašem kódu, zavolejte [CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane). Po podokno čísel s plovoucí čárkou, rozhraní automaticky vytvoří okno s minirámcem a okna s minirámcem okno stane plovoucí podokno nadřazené. Po ukotvené podokno s plovoucí desetinnou čárkou, rozhraní restartuje svého nadřazeného objektu a podokna s plovoucí desetinnou čárkou se stane ukotvení panelu (pro panely nástrojů) nebo dokovacího webu (pro umožňující změnu velikosti podoken).

## <a name="pane-dividers"></a>Podokno oddělovače

Podokno oddělovače (nazývaná také posuvník nebo příčky) jsou reprezentovány [cpanedivider – třída](../mfc/reference/cpanedivider-class.md). Když uživatel ukotvené podokno, vytvoří rozhraní podokně oddělovače, bez ohledu na to, určuje, zda je v podokně ukotveno na dokovacím místě nebo jiného podokna. Když na dokovacím místě ukotvené podokno, se nazývá rozdělovač podokna *výchozí rozdělovač podokna*. Oddělovač podokna výchozí zodpovídá za rozložení všech dokovací podoken v dokovacím místě. Správce dock udržuje seznam oddělovačů podokně výchozí a seznam podoken. Ukotvit správci zodpovídají za rozložení ukotvitelných podoken.

## <a name="containers"></a>Kontejnery

Všech možností změny velikosti podoken, pokud jej ukotven k sobě navzájem, jsou zachovány v kontejnerech. Kontejnery jsou reprezentovány [cpanecontainer – třída](../mfc/reference/cpanecontainer-class.md). Každý kontejner obsahuje odkazy na jeho levé, pravé, levý dílčí kontejneru, správné dílčím kontejneru a příčky mezi částmi vlevo a vpravo. (*Vlevo* a *správné* neodkazují na fyzické strany, ale místo určení větví, stromové struktury.) Tímto způsobem můžeme vytvářet větve z podokna a příčky a proto dosáhnout složitá rozložení podoken, která se dá změnit společně. `CPaneContainer` Třída udržuje strom kontejnerů; udržuje také dva seznamy podokna a jezdce, které se nacházejí v této struktuře. Správci kontejneru podokně jsou obvykle součástí výchozí posuvníky a okna s minirámcem windows, které mají více podoken.

## <a name="auto-hide-control-bars"></a>Automaticky skrýt ovládací pruhy

Ve výchozím nastavení každý `CDockablePane` podporuje funkce automatického skrytí. Když uživatel klikne na tlačítko pro titulek Připnutí `CDockablePane`, rozhraní se přepne do režimu automatického skrytí podokna. Kliknutím na zpracování, vytvoří rozhraní [cmfcautohidebar – třída](../mfc/reference/cmfcautohidebar-class.md) a [cmfcautohidebutton – třída](../mfc/reference/cmfcautohidebutton-class.md) spojené s `CMFCAutoHideBar` objektu. Vloží nové rozhraní `CMFCAutoHideBar` na [cautohidedocksite –](../mfc/reference/cautohidedocksite-class.md). Také připojí rozhraní `CMFCAutoHideButton` na panelu nástrojů. [Cdockingmanager – třída](../mfc/reference/cdockingmanager-class.md) udržuje `CDockablePane`.

## <a name="tabbed-control-bars-and-outlook-bars"></a>Na kartách ovládacích pruhů a panely aplikace Outlook

[Cmfcbasetabctrl – třída](../mfc/reference/cmfcbasetabctrl-class.md) implementuje základní funkce pro okno s kartami s odnímatelnými kartami. Použití `CMFCBaseTabCtrl` objektu, inicializovat [cbasetabbedpane – třída](../mfc/reference/cbasetabbedpane-class.md) ve vaší aplikaci. `CBaseTabbedPane` je odvozen z `CDockablePane` a uchovává ukazatel `CMFCBaseTabCtrl` objektu. `CBaseTabbedPane` Umožňuje uživatelům ukotvení a změňte jeho velikost na kartách ovládacích panelů. Použití [CDockablePane::AttachToTabWnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd) dynamicky se vytvářejí ovládací panely, které jsou ukotvena a oddělené tabulátory.

Ovládací prvek panel aplikace Outlook se odvíjí také s kartami pruhy. [CMFCOutlookBar – třída](../mfc/reference/cmfcoutlookbar-class.md) je odvozen z `CBaseTabbedPane`. Další informace o tom, jak použít panel aplikace Outlook, naleznete v tématu [CMFCOutlookBar – třída](../mfc/reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)

