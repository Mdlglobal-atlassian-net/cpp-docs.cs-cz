---
title: 'Návod: Přidání objektu D2D do projektu MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7985b36c0eeaa7adf5441a7a6fbb3314bac8353f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384017"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Návod: Přidání objektu D2D do projektu MFC
Tento názorný postup učí, jak přidat základní Direct2D (D2D) objektu pro aplikaci Visual C++, projektu Microsoft Foundation Class Library (MFC) a poté sestavení projektu do aplikace, která vytiskne "Hello, world" v přechodu pozadí.  
  
 Průvodce ukazuje, jak provést tyto úlohy:  
  
-   Vytvoření aplikace knihovny MFC.  
  
-   Vytvořte ucelený barevný štětec a štětce lineárního přechodu.  
  
-   Štětce přechodu upravte tak, aby se správně změní, když se změní velikost okna.  
  
-   Implementujte D2D kreslení obslužná rutina.  
  
-   Zkontrolujte výsledky.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Pro dokončení tohoto návodu, musíte mít Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>K vytvoření aplikace knihovny MFC  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogové okno, v levém podokně v části **nainstalovaných šablonách**, rozbalte položku **Visual C++** a pak vyberte **MFC**. V prostředním podokně vyberte **aplikace knihovny MFC**. V **název** zadejte `MFCD2DWalkthrough`. Click **OK**.  
  
3.  V **Průvodce aplikací knihovny MFC**, klikněte na tlačítko **Dokončit** bez jakýchkoli změn nastavení.  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Chcete-li vytvořit ucelený barevný štětec a štětce lineárního přechodu  
  
1.  V **Průzkumníku řešení**v **MFCD2DWalkthrough** v projektu **soubory hlaviček** složku, otevřete MFCD2DWalkthroughView.h. Přidejte následující kód, který `CMFCD2DWalkthroughView` třídy za účelem vytvoření tří proměnných data.  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     Soubor uložte a zavřete ho.  
  
2.  V **zdrojové soubory** složku, otevřete MFCD2DWalkthroughView.cpp. V konstruktoru pro `CMFCD2DWalkthroughView` třídy, přidejte následující kód.  
  
 "' * / / Enable D2D podporu pro toto okno:  
    EnableD2DSupport();

 * / / Inicializovat D2D prostředky:  
    m_pBlackBrush = nové CD2DSolidColorBrush(GetRenderTarget() D2D1::ColorF(D2D1::ColorF::Black));

 
    m_pTextFormat = nové CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50);

    m_pTextFormat -> Get() -> SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);

 m_pTextFormat -> Get() -> SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

 
    D2D1_GRADIENT_STOP gradientStops [2];  
 
    .color gradientStops [0] = D2D1::ColorF(D2D1::ColorF::White);

    .position gradientStops [0] = 0.f;  
    .color gradientStops [1] = D2D1::ColorF(D2D1::ColorF::Indigo);

    .position gradientStops [1] = 1.f;  
 
    m_pLinearGradientBrush = nové CD2DLinearGradientBrush(GetRenderTarget()   
    gradientStops, ARRAYSIZE(gradientStops),  
    D2D1::LinearGradientBrushProperties (D2D1::Point2F (0, 0), D2D1::Point2F (0, 0)));

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush -> SetEndPoint (CPoint (cx, cy));

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
 PRenderTarget CHwndRenderTarget * = (CHwndRenderTarget *) lParam;  
    ASSERT_VALID(pRenderTarget);

 
    Rect – CRect;  
    GetClientRect(rect);

 
    pRenderTarget -> FillRectangle (rect –, m_pLinearGradientBrush);

    pRenderTarget -> DrawText (_T ("Hello, World!"), Rect –, m_pBlackBrush m_pTextFormat);

 
    Vrátí hodnotu PRAVDA.  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

