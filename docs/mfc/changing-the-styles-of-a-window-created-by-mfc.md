---
title: Změna stylů okna vytvořeného rozhraním MFC
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374597"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Změna stylů okna vytvořeného rozhraním MFC

Ve své verzi `WinMain` funkce knihovna MFC zaregistruje několik standardních tříd oken. Vzhledem k tomu, že obvykle `WinMain`neupravujete knihovnu MFC , tato funkce neposkytuje žádnou příležitost ke změně výchozích stylů oken knihovny MFC. Tento článek vysvětluje, jak můžete změnit styly takové předregistrované třídy okna v existující aplikaci.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Změna stylů v nové aplikaci knihovny MFC

Pokud používáte Visual C++ 2.0 nebo novější, můžete při vytváření aplikace změnit výchozí styly oken v Průvodci aplikací. Na stránce Funkce uživatelského rozhraní Průvodce aplikací můžete změnit styly pro okno hlavního rámce a podřízená okna MDI. Pro libovolný typ okna můžete určit jeho tloušťku rámečku (tlustou nebo tenkou) a některou z následujících možností:

- Zda má okno minimalizovat nebo maximalizovat ovládací prvky.

- Určuje, zda se okno zobrazí zpočátku minimalizované, maximalizované nebo ani jedno.

U oken hlavních rámců můžete také určit, zda má okno systémovou nabídku. Pro podřízená okna MDI můžete určit, zda okno podporuje podokna rozdělovače.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Změna stylů v existující aplikaci

Pokud měníte atributy okna v existující aplikaci, postupujte podle pokynů ve zbývající části tohoto článku.

Chcete-li změnit výchozí atributy okna používané aplikací framework vytvořené pomocí Průvodce aplikací, přepište virtuální člennou funkci [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) v okně. `PreCreateWindow`umožňuje aplikaci přístup k procesu vytváření, který je obvykle spravován interně třídou [CDocTemplate.](../mfc/reference/cdoctemplate-class.md) Rozhraní framework `PreCreateWindow` volání těsně před vytvořením okna. Úpravou struktury [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) předané aplikaci `PreCreateWindow`může aplikace změnit atributy použité k vytvoření okna. Chcete-li například zajistit, aby okno nepoužívalo titulek, použijte následující bitovou operaci:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Ukázková aplikace [CTRLBARS](../overview/visual-cpp-samples.md) ukazuje tuto techniku pro změnu atributů okna. V závislosti na tom, co se změní aplikace v `PreCreateWindow`aplikaci , může být nutné volat implementaci základní třídy funkce.

Následující diskuse se týká případu SDI a [případu MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>Případ SDI

V aplikaci rozhraní jednoho dokumentu (SDI) je výchozí styl okna v rámci kombinací **WS_OVERLAPPEDWINDOW** a **FWS_ADDTOTITLE** stylů. **FWS_ADDTOTITLE** je styl specifický pro knihovnu MFC, který instruuje rozhraní pro přidání názvu dokumentu do titulku okna. Chcete-li změnit atributy okna v aplikaci `PreCreateWindow` SDI, přepište `CFrameWnd` funkci ve třídě `CMainFrame`odvozenou z (kterou pojmenuje Průvodce aplikací ). Příklad:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Tento kód vytvoří okno hlavního rámce bez tlačítek Minimalizovat a Maximalizovat a bez značného ohraničení. Okno je zpočátku vystředěno na obrazovce.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>Případ MDI

Trochu více práce je nutné změnit styl okna podřízeného okna v aplikaci rozhraní více dokumentů (MDI). Ve výchozím nastavení používá aplikace MDI vytvořená pomocí Průvodce aplikací výchozí třídu [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) definovanou v knihovně MFC. Chcete-li změnit styl okna podřízeného okna MDI, `CMDIChildWnd` musíte odvodit novou třídu z a nahradit všechny odkazy `CMDIChildWnd` v projektu odkazy na novou třídu. S největší pravděpodobností `CMDIChildWnd` pouze odkaz v aplikaci je `InitInstance` umístěn v členské funkce vaší aplikace.

Výchozí styl okna použitý v aplikaci MDI je kombinací stylů **WS_CHILD**, **WS_OVERLAPPEDWINDOW**a **FWS_ADDTOTITLE.** Chcete-li změnit atributy okna podřízených oken aplikace MDI, přepište funkci [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) ve třídě odvozené z aplikace `CMDIChildWnd`. Příklad:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Tento kód vytvoří podřízená okna MDI bez tlačítka Maximalizovat.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Styly systému Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Styly rám-okno](../mfc/frame-window-styles-cpp.md)

- [Styly oken](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Viz také

[Styly rám-okno](../mfc/frame-window-styles-cpp.md)
