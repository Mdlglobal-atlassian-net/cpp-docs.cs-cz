---
title: Změna stylů okna vytvořeného rozhraním MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34ea35bd43e2bf4e96cbc1552ff169789c1068a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345726"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Změna stylů okna vytvořeného rozhraním MFC
V jeho verzi `WinMain` funkce MFC registruje několik tříd standardní okno za vás. Vzhledem k tomu, že nemáte normálně upravit na MFC `WinMain`, že funkce vám dává žádnou možnost, chcete-li změnit výchozí styly oken MFC. Tento článek vysvětluje, jak můžete změnit styly této preregistered okno třídy v existující aplikaci.  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Změna stylů v nové aplikace MFC  
 Pokud používáte Visual C++ 2.0 nebo novější, můžete změnit výchozí styly oken v Průvodci aplikace při vytváření aplikace. Na stránce funkce uživatelského rozhraní v Průvodce vytvořením aplikace můžete změnit styly oken s rámečkem hlavní a podřízených oken MDI. Oba typy okně můžete zadat jeho tloušťky rámce (silných nebo dynamické) a všechny z následujících akcí:  
  
-   Jestli má okna minimalizovat nebo maximalizovat ovládacích prvků.  
  
-   Určuje, zda okno zobrazí původně minimalizovaném okně Maximalizovaný, nebo žádný z nich.  
  
 Pro systém windows hlavního rámce můžete zadat, zda má okna nabídky systému. Pro podřízených oken MDI můžete určit, zda okno podporuje rozdělovače podokna.  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> Změna stylů v existující aplikaci  
 Pokud jste změna atributů okna v existující aplikaci, postupujte podle pokynů ve zbývající části tohoto článku.  
  
 Chcete-li změnit výchozí atributy okno používá framework aplikace vytvořené pomocí Průvodce aplikací, přepsání okna [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) člena virtuální funkce. `PreCreateWindow` umožňuje aplikaci přístup k procesu vytváření normálně spravuje interně [CDocTemplate](../mfc/reference/cdoctemplate-class.md) třídy. Volání framework `PreCreateWindow` těsně před vytvořením okna. Změnou [createstruct –](../mfc/reference/createstruct-structure.md) struktura předaný `PreCreateWindow`, vaše aplikace může změnit atributy použité k vytvoření okna. Například k zajištění, že okno nepoužívá popisek, použijte následující bitové operace:  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../visual-cpp-samples.md) ukázkovou aplikaci ukazuje tento postup pro změnu atributů okna. V závislosti na tom, jaké aplikace změny v `PreCreateWindow`, může být nutné volat základní třída implementace funkce.  
  
 Následující diskusi popisuje případ SDI a [MDI případ](#_core_the_mdi_case).  
  
##  <a name="_core_the_sdi_case"></a> Tento případ SDI  
 V aplikaci (SDI rozhraní) jednotlivý dokument, výchozí styl oken v rozhraní framework je kombinací **ws_overlappedwindow –** a **fws_addtotitle –** stylů. **Fws_addtotitle –** je MFC konkrétní styl, který instruuje framework přidat název dokumentu na záhlaví okna. Změna atributů okna v aplikaci SDI, přepsat `PreCreateWindow` funkce do vaší třídy odvozené od `CFrameWnd` (který názvy Průvodce vytvořením aplikace `CMainFrame`). Příklad:  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 Tento kód vytvoří okno rámce bez tlačítka Minimalizovat a maximalizovat a bez značné množství ohraničení. Okno původně na střed na obrazovce.  
  
##  <a name="_core_the_mdi_case"></a> Tento případ MDI  
 Chcete-li změnit styl okna podřízeného okna v aplikaci více rozhraní (MDI) dokumentu se vyžaduje trochu další práci. Ve výchozím nastavení, MDI aplikaci vytvořenou pomocí Průvodce aplikací používá výchozí [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) třídy definované v MFC. Chcete-li změnit styl okna podřízeného okna MDI, musí být odvozeny novou třídu z `CMDIChildWnd` a nahraďte všechny odkazy na `CMDIChildWnd` ve vašem projektu s odkazy na novou třídu. S největší pravděpodobností pouze odkaz na `CMDIChildWnd` v aplikaci se nachází ve vaší aplikaci `InitInstance` – členská funkce.  
  
 Výchozí styl oken použijí v aplikaci MDI je kombinací **ws_child –**, **ws_overlappedwindow –**, a **fws_addtotitle –** stylů. Změna atributů okna Windows podřízené aplikace MDI, přepsat [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) funkce do vaší třídy odvozené od `CMDIChildWnd`. Příklad:  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 Tento kód vytvoří podřízeného MDI windows bez tlačítko Maximalizovat.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Styly Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
-   [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)  
  
-   [Styly oken](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## <a name="see-also"></a>Viz také  
 [Styly oken s rámečkem](../mfc/frame-window-styles-cpp.md)

