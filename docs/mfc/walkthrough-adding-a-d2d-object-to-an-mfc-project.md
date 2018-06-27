---
title: 'Návod: Přidání objektu D2D do projektu MFC | Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2018
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
ms.openlocfilehash: 87e1c696f3da374d7b71e1b24e3a8bd3ebfe41b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954868"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Návod: Přidání objektu D2D do projektu MFC

Tento názorný postup učí, jak přidat základní Direct2D (D2D) objektu pro aplikaci Visual C++, projektu Microsoft Foundation Class Library (MFC) a poté sestavení projektu do aplikace, která vytiskne "Hello, world" v přechodu pozadí.

Průvodce ukazuje, jak provést tyto úlohy:

- Vytvoření aplikace knihovny MFC.

- Vytvořte ucelený barevný štětec a štětce lineárního přechodu.

- Štětce přechodu upravte tak, aby se správně změní, když se změní velikost okna.

- Implementujte D2D kreslení obslužná rutina.

- Zkontrolujte výsledky.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

Pro dokončení tohoto návodu, musíte mít nainstalované s Visual Studio **vývoj aplikací s jazykem C++** zatížení a volitelné **Visual C++ MFC pro x86 a x64** součásti.

## <a name="to-create-an-mfc-application"></a>K vytvoření aplikace knihovny MFC

1. Na **soubor** nabídky, přejděte na příkaz **nový** a potom zvolte **projektu**.

2. V **nový projekt** dialogové okno, v levém podokně v části **nainstalovaných šablonách**, rozbalte položku **Visual C++** a pak vyberte **MFC**. V prostředním podokně vyberte **aplikace knihovny MFC**. V **název** zadejte *MFCD2DWalkthrough*. Zvolte **OK**.

3. V **Průvodce aplikací knihovny MFC**, zvolte **Dokončit** bez jakýchkoli změn nastavení.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Chcete-li vytvořit ucelený barevný štětec a štětce lineárního přechodu

1. V **Průzkumníku řešení**v **MFCD2DWalkthrough** v projektu **soubory hlaviček** složku, otevřete MFCD2DWalkthroughView.h. Přidejte tento kód, který `CMFCD2DWalkthroughView` třídy za účelem vytvoření tří proměnných dat:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Soubor uložte a zavřete ho.

2. V **zdrojové soubory** složku, otevřete MFCD2DWalkthroughView.cpp. V konstruktoru pro `CMFCD2DWalkthroughView` třídy, přidejte tento kód:

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Soubor uložte a zavřete ho.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Chcete-li upravit štětce přechodu tak, aby se správně změní, když se změní velikost okna

1. Na **projektu** nabídce zvolte **Průvodce třídou**.

2. V **Průvodce třídou MFC**v části **název třídy**, vyberte `CMFCD2DWalkthroughView`.

3. Na **zprávy** ve **zprávy** vyberte `WM_SIZE` a potom zvolte **přidat obslužnou rutinu**. Tato akce přidá `OnSize` popisovač zpráv se má `CMFCD2DWalkthroughView` třídy.

4. V **stávající obslužné rutiny** vyberte `OnSize`. Zvolte **upravit kód** zobrazíte `CMFCD2DWalkthroughView::OnSize` metoda. Na konci metodu přidejte následující kód.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Soubor uložte a zavřete ho.

## <a name="to-implement-a-d2d-drawing-handler"></a>K implementaci D2D kreslení obslužná rutina

1. Na **projektu** nabídce zvolte **Průvodce třídou**.

2. V **Průvodce třídou MFC**v části **název třídy**, vyberte `CMFCD2DWalkthroughView`.

3. Na **zprávy** , zvolte **přidat vlastní zprávu**.

4. V **přidat vlastní zprávu** dialogovém **vlastní zpráv systému Windows** zadejte *AFX_WM_DRAW2D*. V **název obslužné rutiny zpráv** zadejte *OnDraw2D*. Vyberte **zaregistrován zpráva** možnost a potom zvolte **OK**. Tato akce přidá obslužné rutiny zpráv pro zprávy AFX_WM_DRAW2D `CMFCD2DWalkthroughView` třídy.

5. V **stávající obslužné rutiny** vyberte `OnDraw2D`. Zvolte **upravit kód** zobrazíte `CMFCD2DWalkthroughView::OnDraw2D` metoda. Pomocí tohoto kódu pro `CMFCD2DWalkthroughView::OnDrawD2D` metoda:

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Soubor uložte a zavřete ho.

## <a name="to-verify-the-results"></a>Ověření výsledků

- Sestavte a spusťte aplikaci. Měl by mít barevného přechodu rámečku, která se změní při změně velikosti okna. "Hello, World!" má být zobrazena v centru rámečku.

## <a name="see-also"></a>Viz také:

- [Návody](../mfc/walkthroughs-mfc.md)
