---
title: Principy panelů nástrojů
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: 9c784db2e1a482b313147e6837d6bbbd16d0ecb4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775488"
---
# <a name="toolbar-fundamentals"></a>Principy panelů nástrojů

Tento článek popisuje základní implementace MFC, která umožňuje přidat výchozí panel nástrojů do vaší aplikace tak, že vyberete možnost v Průvodci aplikací. Probíraná témata zahrnují:

- [Možnosti nástrojů Průvodce aplikací](#_core_the_appwizard_toolbar_option)

- [Panel nástrojů v kódu](#_core_the_toolbar_in_code)

- [Úpravy prostředek panelu nástrojů](#_core_editing_the_toolbar_resource)

- [Více panelů nástrojů](#_core_multiple_toolbars)

##  <a name="_core_the_appwizard_toolbar_option"></a> Možnost nástrojů Průvodce aplikací

Chcete-li získat jeden panel nástrojů s výchozí tlačítka, vyberte možnost Standard ukotvení panelu nástrojů na stránce s názvem funkce uživatelského rozhraní. Tím přidáte kód do vaší aplikace, které:

- Vytvoří objekt panelu nástrojů.

- Spravuje panelu nástrojů, včetně schopnosti ukotvit nebo uvolnit.

##  <a name="_core_the_toolbar_in_code"></a> Panel nástrojů v kódu

Panel nástrojů [ctoolbar –](../mfc/reference/ctoolbar-class.md) objekt deklarován jako datový člen vaší aplikace `CMainFrame` třídy. Jinými slovy objekt nástrojů se vloží do objekt okna hlavního rámce. To znamená, že MFC vytvoří panel nástrojů, když se vytvoří okno rámce a odstraní panelu nástrojů při odstraní okno rámce. Následující deklarace částečné třídy pro několik aplikačních dokumentu (MDI interface) ukazuje datových členů pro integrovaném panelu nástrojů a vložené stavový řádek. Také ukazuje přepsání `OnCreate` členskou funkci.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

Dojde k vytvoření panelu nástrojů v `CMainFrame::OnCreate`. Volání knihovny MFC [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po vytvoření okna pro snímek, ale předtím, než se stane viditelnou. Výchozí hodnota `OnCreate` , Průvodce aplikací generuje provede následující úlohy nástrojů:

1. Volání `CToolBar` objektu [vytvořit](../mfc/reference/ctoolbar-class.md#create) členskou funkci pro vytvoření základní [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu.

1. Volání [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) načíst informace o prostředku panelu nástrojů.

1. Volání funkce umožňující ukotvení s plovoucí desetinnou čárkou a popisy tlačítek. Podrobnosti o těchto volání, najdete v článku [ukotvení a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
>  Ukázky knihovny MFC Obecné [DOCKTOOL](../overview/visual-cpp-samples.md) zahrnuje obrázky starých i nových panelů nástrojů MFC. Panely nástrojů, které používají `COldToolbar` vyžadují volání v kroku 2 `LoadBitmap` (spíše než `LoadToolBar`) a `SetButtons`. Nových panelů nástrojů vyžaduje volání `LoadToolBar`.

Ukotvení s plovoucí desetinnou čárkou a tipy k volání nástroje jsou volitelné. Můžete odebrat tyto řádky z `OnCreate` Pokud dáváte přednost. Výsledkem je zůstane pevný, nelze plovoucí desetinnou čárkou nebo redock a nedá se zobrazit popisy tlačítek panelu nástrojů.

##  <a name="_core_editing_the_toolbar_resource"></a> Úpravy prostředek panelu nástrojů

Podle výchozích nástrojů, získáte pomocí Průvodce aplikací **rt_toolbar –** vlastní prostředek, zavedená v prostředí MFC verze 4.0. Můžete upravit tento prostředek se [panelu nástrojů editoru](../windows/toolbar-editor.md). Editor umožňuje snadno přidat, odstranit a změna uspořádání tlačítek. Obsahuje grafický editor pro tlačítka, který je velmi podobný editor obecné grafiky v aplikaci Visual C++. Pokud jste upravili panelů nástrojů v předchozích verzích Visual C++, najdete úlohy mnohem jednodušší, nyní.

Pro tlačítka panelu nástrojů připojte k příkazu, dáváte tlačítko ID příkazu, například `ID_MYCOMMAND`. ID příkazu zadejte na stránce vlastností tlačítka panelu nástrojů editoru. Vytvořte obslužnou rutinu pro příkaz (viz [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md) Další informace).

Nové [ctoolbar –](../mfc/reference/ctoolbar-class.md) členské funkce pracovat **rt_toolbar –** prostředků. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) nyní zaujímá místo [loadbitmap –](../mfc/reference/ctoolbar-class.md#loadbitmap) načíst bitmapu obrázky tlačítek panelu nástrojů a [setbuttons –](../mfc/reference/ctoolbar-class.md#setbuttons) nastavit styly tlačítek a spojte se s rastrové obrázky tlačítka.

Podrobnosti o použití editoru panelu nástrojů najdete v tématu [panelu nástrojů editoru](../windows/toolbar-editor.md).

##  <a name="_core_multiple_toolbars"></a> Více panelů nástrojů

Průvodce aplikací poskytuje jeden výchozí panel nástrojů. Pokud potřebujete více než jednoho panelu nástrojů v aplikaci, můžete modelovat se může váš kód pro další panely nástrojů, na základě kódu generované v průvodci pro výchozí panel nástrojů.

Pokud chcete zobrazit panel nástrojů jako výsledek příkazu, bude potřeba:

- Vytvořit nový prostředek panelu nástrojů pomocí panelu nástrojů editoru a načtěte ho v `OnCreate` s [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) členskou funkci.

- Vložit nový [ctoolbar –](../mfc/reference/ctoolbar-class.md) objekt ve své třídě okna hlavního rámce.

- Ujistěte se volá příslušnou funkci v `OnCreate` ukotvit nebo plovoucí panel nástrojů, nastavení jeho stylů a tak dále.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Implementace panelu nástrojů v prostředí MFC (Přehled informací na panely nástrojů)](../mfc/mfc-toolbar-implementation.md)

- [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Popisy tlačítek na panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy

- [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také:

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
