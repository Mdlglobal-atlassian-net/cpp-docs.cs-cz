---
title: 'Návod: Přidání objektu D2D do projektu MFC'
ms.date: 09/20/2018
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 0793511f09be9dcb37732c4c16bfd2b3038a6cf4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567255"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Návod: Přidání objektu D2D do projektu MFC

Tento návod vás naučí, jak přidat základní Direct2D (D2D) objektů jazyka Visual C++, projekt třídy knihovny MFC (Microsoft Foundation) a následné sestavení projektu do aplikace, která zobrazí "text Hello, world" na barevného přechodu pozadí.

Návodu ukazuje, jak provádět tyto úlohy:

- Vytvoření aplikace knihovny MFC.

- Vytvořte štětec plnými barvami a štětec lineárního přechodu.

- Štětec přechodu upravte tak, aby se správně změní, když je velikost okna.

- Implementujte obslužnou rutinu výkresu D2D.

- Zkontrolujte výsledky.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu, musíte mít nainstalované s Visual Studio **vývoj desktopových aplikací pomocí C++** pracovního vytížení a volitelné **Visual C++ MFC pro x86 a x64** komponenty.

## <a name="to-create-an-mfc-application"></a>Vytvoření aplikace MFC

1. Na **souboru** nabídky, přejděte k **nový** a klikněte na tlačítko **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně v části **nainstalované šablony**, rozbalte **Visual C++** a pak vyberte **MFC**. V prostředním podokně vyberte **aplikace knihovny MFC**. V **název** zadejte *MFCD2DWalkthrough*. Zvolte **OK**.

1. V **Průvodce aplikací knihovny MFC**, zvolte **Dokončit** bez jakýchkoli změn nastavení.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Chcete-li vytvořit štětec plnými barvami a štětec lineárního přechodu

1. V **Průzkumníka řešení**v **MFCD2DWalkthrough** v projektu **hlavičkové soubory** složku, otevřete MFCD2DWalkthroughView.h. Přidejte tento kód `CMFCD2DWalkthroughView` třídy za účelem vytvoření tří datových proměnných:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Soubor uložte a zavřete ho.

1. V **zdrojové soubory** složku, otevřete MFCD2DWalkthroughView.cpp. V konstruktoru pro `CMFCD2DWalkthroughView` třídy, přidejte tento kód:

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

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Chcete-li změnit štětce přechodu tak, aby se správně změní, když je velikost okna

1. Na **projektu** nabídce zvolte **Průvodce třídami**.

1. V **Průvodce třídami MFC**v části **název třídy**vyberte `CMFCD2DWalkthroughView`.

1. Na **zprávy** kartě **zprávy** vyberte `WM_SIZE` a klikněte na tlačítko **přidat obslužnou rutinu**. Tato akce přidá `OnSize` obslužná rutina zprávy `CMFCD2DWalkthroughView` třídy.

1. V **existující obslužné rutiny** vyberte `OnSize`. Zvolte **upravit kód** zobrazíte `CMFCD2DWalkthroughView::OnSize` metody. Na konci metody přidejte následující kód.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Soubor uložte a zavřete ho.

## <a name="to-implement-a-d2d-drawing-handler"></a>K implementaci obslužné rutiny vykreslení D2D

1. Na **projektu** nabídce zvolte **Průvodce třídami**.

1. V **Průvodce třídami MFC**v části **název třídy**vyberte `CMFCD2DWalkthroughView`.

1. Na **zprávy** kartě **přidat vlastní zprávu**.

1. V **přidat vlastní zprávu** v dialogu **vlastní zpráva Windows** zadejte *AFX_WM_DRAW2D*. V **název obslužné rutiny** zadejte *OnDraw2D*. Vyberte **registrovanou zprávu** možnost a klikněte na tlačítko **OK**. Tato akce přidá obslužné rutiny zpráv pro zprávy AFX_WM_DRAW2D `CMFCD2DWalkthroughView` třídy.

1. V **existující obslužné rutiny** vyberte `OnDraw2D`. Zvolte **upravit kód** zobrazíte `CMFCD2DWalkthroughView::OnDraw2D` metody. Pomocí tohoto kódu pro `CMFCD2DWalkthroughView::OnDrawD2D` metody:

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

## <a name="to-verify-the-results"></a>Chcete-li ověřit výsledky

Sestavte a spusťte aplikaci. Měl by mít přechodu obdélníku, která se mění při změně velikosti okna. "Hello World!" má být zobrazena ve středu obdélníku.

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
