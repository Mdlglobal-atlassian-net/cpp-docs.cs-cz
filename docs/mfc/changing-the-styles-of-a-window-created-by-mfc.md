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
ms.openlocfilehash: 0a002badf9c20ca7b2d1a129eca069e586893f3c
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344209"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Změna stylů okna vytvořeného rozhraním MFC

V jeho verzi `WinMain` funkce MFC registruje několik tříd standardní okno za vás. Protože nemusíte normálně upravit MFC `WinMain`, že funkce poskytuje žádnou možnost, chcete-li změnit výchozí styly okna knihovny MFC. Tento článek vysvětluje, jak změnit styly takové registrované třídy okna v existující aplikaci.

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Změna stylů v nové aplikaci knihovny MFC

Pokud používáte Visual C++ 2.0 nebo novější, můžete změnit výchozí styly oken v aplikaci průvodce při vytváření vaší aplikace. Na stránce funkce uživatelského rozhraní aplikace průvodce můžete změnit styly pro hlavní okno rámce a podřízených oken MDI. Pro oba typy okně můžete zadat jeho tloušťky rámce (silný nebo dynamicky) a žádný z následujících akcí:

- Určuje, zda má okno minimalizovat nebo maximalizovat ovládacích prvků.

- Určuje, zda se zobrazí okno zpočátku minimalizované maximalizované, nebo ani jedna.

Pro systém windows hlavního rámce můžete určit, zda má okno systémové nabídky. Pro podřízená okna MDI můžete určit, zda okno podporuje rozdělovač podokna.

##  <a name="_core_changing_styles_in_an_existing_application"></a> Změna stylů v existující aplikaci

Pokud chcete změnit okno atributů v existující aplikaci, postupujte podle pokynů ve zbývající části tohoto článku.

Chcete-li změnit výchozí atributy okno používá rozhraní framework aplikace vytvořené pomocí Průvodce aplikací, přepsat v okně [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) virtuální členskou funkci. `PreCreateWindow` umožňuje aplikaci získat přístup v procesu vytváření obvykle spravováno interně službou [CDocTemplate](../mfc/reference/cdoctemplate-class.md) třídy. Rámec volá `PreCreateWindow` pouze před vytvořením okna. Úpravou [soubor CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) předané do `PreCreateWindow`, vaše aplikace může změnit atributy použité k vytvoření okna. Například Ujistěte se, že okno nepoužívá titulek, použijte následující bitová operace:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[CTRLBARS](../overview/visual-cpp-samples.md) ukázkové aplikaci ukazuje tento postup pro změnu atributů okna. V závislosti na tom, co vaše aplikace změní v `PreCreateWindow`, může být nutné volat implementaci základní třídy funkce.

Následující diskuse zahrnuje případ SDI a [MDI případ](#_core_the_mdi_case).

##  <a name="_core_the_sdi_case"></a> Případ SDI

V aplikaci rozhraní (SDI) jeden dokument, výchozí styl oken v rámci je kombinací **WS_OVERLAPPEDWINDOW** a **FWS_ADDTOTITLE** styly. **FWS_ADDTOTITLE** je specifické pro knihovny MFC styl, který dává pokyn rozhraní přidat název dokumentu na titulek okna. Změna atributů okna v aplikaci SDI, přepsat `PreCreateWindow` funkce ve třídě odvozené z `CFrameWnd` (který názvy Průvodce aplikací `CMainFrame`). Příklad:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Tento kód vytvoří hlavní okno rámce bez tlačítka Minimalizovat a maximalizovat a proměnlivou velikostí ohraničení. V okně je zpočátku zarovnaný na střed na obrazovce.

##  <a name="_core_the_mdi_case"></a> Případ MDI

O něco více práce je potřeba změnit styl okna podřízeného okna v aplikaci (MDI interface) více dokumentů. Ve výchozím nastavení, aplikace vytvořená pomocí Průvodce aplikace MDI používá výchozí [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) třídy definované v knihovně MFC. Chcete-li změnit styl okna podřízené okno MDI, musíte odvodit novou třídu z `CMDIChildWnd` a nahradit všechny odkazy na `CMDIChildWnd` ve vašem projektu s odkazy na novou třídu. Největší pravděpodobností pouze odkaz na `CMDIChildWnd` v aplikaci je umístěný ve vaší aplikaci `InitInstance` členskou funkci.

Výchozí styl oken použijí v aplikaci MDI je kombinací **WS_CHILD**, **WS_OVERLAPPEDWINDOW**, a **FWS_ADDTOTITLE** styly. Změna atributů okna aplikace MDI podřízených oken, přepsat [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) funkce ve třídě odvozené z `CMDIChildWnd`. Příklad:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Tento kód vytvoří podřízený formulář MDI windows bez tlačítko Maximalizovat.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Styly Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)

- [Styly oken](/windows/desktop/winmsg/window-styles)

## <a name="see-also"></a>Viz také:

[Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)
