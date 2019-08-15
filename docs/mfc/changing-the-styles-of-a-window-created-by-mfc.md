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
ms.openlocfilehash: ef79fc88604d565a942fdb0ae07d5fc5a2e0ebeb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509009"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Změna stylů okna vytvořeného rozhraním MFC

Ve verzi `WinMain` funkce MFC registruje několik standardních tříd okna za vás. Vzhledem k tomu, že nebudete normálně upravovat knihovnu MFC `WinMain`, tato funkce vám neumožňuje změnit výchozí styly oken knihovny MFC. Tento článek vysvětluje, jak můžete změnit styly takové předdefinované třídy okna v existující aplikaci.

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a>Změna stylů v nové aplikaci knihovny MFC

Pokud používáte Visual C++ 2,0 nebo novější, můžete změnit výchozí styly oken v Průvodci aplikací při vytváření aplikace. Na stránce funkce uživatelského rozhraní Průvodce aplikací můžete změnit styly pro hlavní okno rámce a podřízená okna MDI. Pro libovolný typ okna můžete zadat jeho tloušťku snímku (silný nebo tenký) a jednu z následujících možností:

- Určuje, zda má okno minimalizovat nebo maximalizovat ovládací prvky.

- Určuje, zda se okno zobrazuje na začátku minimalizovaného, maximalizovaného nebo žádného.

V případě oken hlavního rámce můžete také určit, zda má okno systémovou nabídku. V případě podřízených oken MDI můžete určit, zda okno podporuje rozdělovače.

##  <a name="_core_changing_styles_in_an_existing_application"></a>Změna stylů v existující aplikaci

Pokud měníte atributy okna v existující aplikaci, postupujte místo toho podle pokynů ve zbývající části tohoto článku.

Chcete-li změnit výchozí atributy okna používané aplikací architektury vytvořenými pomocí Průvodce aplikací, přepište virtuální členskou funkci [](../mfc/reference/cwnd-class.md#precreatewindow) předmoci okna. `PreCreateWindow`umožňuje aplikaci přístup k procesu vytváření, který je obvykle spravován interně třídou [CDocTemplate –](../mfc/reference/cdoctemplate-class.md) . Rozhraní volá `PreCreateWindow` těsně před vytvořením okna. Změnou struktury [CREATESTRUCT –](/windows/win32/api/winuser/ns-winuser-createstructw) předané na `PreCreateWindow`, může aplikace změnit atributy používané k vytvoření okna. Například, chcete-li zajistit, že okno nepoužívá titulek, použijte následující bitovou operaci:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Ukázková aplikace [CTRLBARS](../overview/visual-cpp-samples.md) ukazuje tuto techniku pro změnu atributů okna. V závislosti na tom, co vaše aplikace `PreCreateWindow`v nástroji změní, může být nutné volat implementaci základní třídy funkce.

Následující diskuze se týká případu SDI a [případu MDI](#_core_the_mdi_case).

##  <a name="_core_the_sdi_case"></a>Případ SDI

V aplikaci s jedním dokumentovým rozhraním (SDI) je výchozí styl okna v rozhraní kombinací stylů **WS_OVERLAPPEDWINDOW** a **FWS_ADDTOTITLE** . **FWS_ADDTOTITLE** je styl specifický pro knihovnu MFC, který instruuje rozhraní, aby přidalo název dokumentu do titulku okna. Chcete-li změnit atributy okna v aplikaci SDI, přepište `PreCreateWindow` funkci ve třídě odvozené z `CFrameWnd` (kterou průvodce aplikací názvů `CMainFrame`). Příklad:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Tento kód vytvoří hlavní okno rámce bez minimalizace a maximalizace tlačítek a bez ohraničení s proměnlivými proměnnými. Okno se zpočátku nacentruje na obrazovce.

##  <a name="_core_the_mdi_case"></a>Případ MDI

Ke změně stylu okna podřízeného okna v aplikaci MDI (Multiple Document Interface) je potřeba trochu více práce. Ve výchozím nastavení používá aplikace MDI vytvořené pomocí Průvodce aplikací výchozí třídu [CMDIChildWnd –](../mfc/reference/cmdichildwnd-class.md) definovanou v knihovně MFC. Chcete-li změnit styl okna podřízeného okna MDI, je nutné odvodit novou třídu z `CMDIChildWnd` a nahradit všechny odkazy na `CMDIChildWnd` v projektu odkazy na novou třídu. Nejpravděpodobnější je, že jediný odkaz `CMDIChildWnd` na aplikaci je umístěný v `InitInstance` členské funkci aplikace.

Výchozím stylem okna použitým v aplikaci MDI je kombinace stylů **WS_CHILD**, **WS_OVERLAPPEDWINDOW**a **FWS_ADDTOTITLE** . Chcete-li změnit atributy okna podřízených oken aplikace MDI, přepište funkci [](../mfc/reference/cwnd-class.md#precreatewindow) předpracovat ve třídě odvozené z `CMDIChildWnd`. Příklad:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Tento kód vytváří podřízená okna MDI bez tlačítka maximalizovat.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Styly Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)

- [Styly oken](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Viz také:

[Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)
