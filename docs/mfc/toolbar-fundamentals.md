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
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373469"
---
# <a name="toolbar-fundamentals"></a>Principy panelů nástrojů

Tento článek popisuje základní implementaci knihovny MFC, která umožňuje přidat do aplikace výchozí panel nástrojů výběrem možnosti v Průvodci aplikací. Probíraná témata zahrnují:

- [Panel nástrojů Průvodce aplikací, volba](#_core_the_appwizard_toolbar_option)

- [Panel nástrojů v kódu](#_core_the_toolbar_in_code)

- [Úprava prostředku panelu nástrojů](#_core_editing_the_toolbar_resource)

- [Více panelů nástrojů](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>Možnost panelu nástrojů Průvodce aplikací

Chcete-li získat jeden panel nástrojů s výchozími tlačítky, vyberte na stránce s popiskem Funkce uživatelského rozhraní možnost Standardní ukotvení. Tím přidáte do aplikace kód, který:

- Vytvoří objekt panelu nástrojů.

- Spravuje panel nástrojů, včetně jeho schopnosti ukotvit nebo plavat.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>Panel nástrojů v kódu

Panel nástrojů je [ctoolbar](../mfc/reference/ctoolbar-class.md) objekt deklarován jako `CMainFrame` datový člen třídy vaší aplikace. Jinými slovy, objekt panelu nástrojů je vložen do objektu okna hlavního rámečku. To znamená, že knihovna MFC vytvoří panel nástrojů při vytváření okna rámce a zničí panel nástrojů, když zničí okno rámce. Následující deklarace částečné třídy pro aplikaci rozhraní více dokumentů (MDI) zobrazuje datové členy pro vložený panel nástrojů a vložený stavový řádek. Zobrazuje také přepsání `OnCreate` členské funkce.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

K vytvoření panelu `CMainFrame::OnCreate`nástrojů dochází v . Knihovna MFC volá [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po vytvoření okna pro rámec, ale před tím, než se stane viditelným. Výchozí `OnCreate` nastavení, které Generuje Průvodce aplikací, provádí následující úkoly na panelu nástrojů:

1. Volá `CToolBar` členská funkce [Create](../mfc/reference/ctoolbar-class.md#create) objektu k vytvoření podkladového objektu [CToolBarCtrl.](../mfc/reference/ctoolbarctrl-class.md)

1. Volá [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) načíst informace o prostředku panelu nástrojů.

1. Volá funkce pro povolení dokování, plovoucí a tipy nástrojů. Podrobnosti o těchto hovorech naleznete v článku [Ukotvení a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
> Ukázka knihovny MFC General [DOCKTOOL](../overview/visual-cpp-samples.md) obsahuje ilustrace starých i nových panelů nástrojů knihovny MFC. Panely nástrojů, `COldToolbar` které používají vyžadují `LoadBitmap` volání v `LoadToolBar`kroku `SetButtons`2 na (nikoli ) a . Nové panely nástrojů vyžadují `LoadToolBar`volání .

Volání tipů pro ukotvení, plovoucí a nástroje jsou volitelné. Pokud chcete, můžete `OnCreate` tyto řádky odebrat. Výsledkem je panel nástrojů, který zůstává pevný, nemůže se uvolnit nebo znovu ukotvit a nemůže zobrazit tipy nástrojů.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>Úprava prostředku panelu nástrojů

Výchozí panel nástrojů, který získáte pomocí Průvodce aplikací, je založen na **vlastním prostředku RT_TOOLBAR** zavedeném ve verzi 4.0 knihovny MFC. Tento prostředek můžete upravit pomocí [editoru panelu nástrojů](../windows/toolbar-editor.md). Editor umožňuje snadno přidávat, odstraňovat a měnit uspořádání tlačítek. Obsahuje grafický editor tlačítek, který je velmi podobný obecnému grafickému editoru v jazyce Visual C++. Pokud jste upravili panely nástrojů v předchozích verzích visual c++, najdete úkol mnohem jednodušší nyní.

Chcete-li k příkazu připojit tlačítko panelu nástrojů, přiřazujte tlačítku ID příkazu, například `ID_MYCOMMAND`. Zadejte ID příkazu na stránce vlastností tlačítka v editoru panelu nástrojů. Potom vytvořte funkci obslužné rutiny pro příkaz (další informace naleznete v [tématu Mapování zpráv na funkce).](../mfc/reference/mapping-messages-to-functions.md)

Nové členské funkce [CToolBar](../mfc/reference/ctoolbar-class.md) pracují s **RT_TOOLBAR** zdrojem. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) nyní přebírá místo [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) pro načtení bitmapy obrazů tlačítka panelu nástrojů a [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) pro nastavení stylů tlačítek a připojení tlačítek s bitmapovými obrazy.

Podrobnosti o používání editoru panelů nástrojů naleznete v [editoru panelů nástrojů](../windows/toolbar-editor.md).

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>Více panelů nástrojů

Průvodce aplikací poskytuje jeden výchozí panel nástrojů. Pokud potřebujete více než jeden panel nástrojů v aplikaci, můžete modelovat kód pro další panely nástrojů na základě kódu generovaného průvodcem pro výchozí panel nástrojů.

Pokud chcete zobrazit panel nástrojů jako výsledek příkazu, budete muset:

- Vytvořte nový prostředek panelu nástrojů pomocí editoru panelu nástrojů a načtěte `OnCreate` jej pomocí členské funkce [LoadToolbar.](../mfc/reference/ctoolbar-class.md#loadtoolbar)

- Vložte nový objekt [CToolBar](../mfc/reference/ctoolbar-class.md) do třídy okna hlavního rámce.

- Proveďte příslušná `OnCreate` volání funkcí pro ukotvení nebo plovoucí panel nástrojů, nastavte jeho styly a tak dále.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Implementace panelu nástrojů knihovny MFC (přehled informací o panelech nástrojů)](../mfc/mfc-toolbar-implementation.md)

- [Dokovací a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)

- [Tipy nástrojů panelu nástrojů](../mfc/toolbar-tool-tips.md)

- [Třídy CToolBar](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Práce s ovládacím prvkem panelu nástrojů](../mfc/working-with-the-toolbar-control.md)

- [Používání starých panelů nástrojů](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Viz také

[Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)
