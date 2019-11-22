---
title: 'Návod: Přidání objektu D2D do projektu MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304297"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Návod: Přidání objektu D2D do projektu MFC

Tento návod popisuje, jak přidat objekt základní Direct2D (D2D) do projektu Visual C++, knihovna Microsoft Foundation Class (MFC) a potom sestavit projekt do aplikace, která tiskne "Hello, World!". na pozadí přechodu.

V tomto návodu se dozvíte, jak provádět tyto úlohy:

- Vytvořte aplikaci knihovny MFC.

- Vytvoření štětce s plnými barvami a štětce s lineárním přechodem

- Upravte štětec přechodu tak, aby se při změně velikosti okna vhodně změnil.

- Implementujte obslužnou rutinu vykreslování D2D.

- Ověřte výsledky.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu musíte mít nainstalovanou aplikaci Visual Studio s funkcí **vývoj pro C++ Desktop s** úlohou a volitelnou **Visual C++ MFC pro součásti x86 a x64** .

## <a name="to-create-an-mfc-application"></a>Vytvoření aplikace MFC

1. Použijte **Průvodce aplikací knihovny MFC** k vytvoření aplikace MFC. Pokyny k otevření Průvodce pro vaši verzi sady Visual Studio najdete v tématu [Návod: použití nových ovládacích prvků prostředí MFC](walkthrough-using-the-new-mfc-shell-controls.md) .

1. Do pole **název** zadejte *MFCD2DWalkthrough*. Zvolte **OK**.

1. V **Průvodci aplikací knihovny MFC**zvolte možnost **Dokončit** beze změny nastavení.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Vytvoření štětce s plnými barvami a štětce s lineárním přechodem

1. V **Průzkumník řešení**v projektu **MFCD2DWalkthrough** ve složce **soubory hlaviček** otevřete MFCD2DWalkthroughView. h. Přidejte tento kód do třídy `CMFCD2DWalkthroughView` pro vytvoření tří datových proměnných:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Uložte soubor a zavřete ho.

1. Ve složce **zdrojové soubory** otevřete MFCD2DWalkthroughView. cpp. V konstruktoru pro třídu `CMFCD2DWalkthroughView` přidejte tento kód:

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

   Uložte soubor a zavřete ho.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Úprava štětce přechodu tak, aby se při změně velikosti okna vhodně změnil

1. V nabídce **projekt** klikněte na příkaz **Průvodce třídami**.

1. V **Průvodci třídou MFC**vyberte v části **název třídy**možnost `CMFCD2DWalkthroughView`.

1. Na kartě **zprávy** v poli **zprávy** vyberte možnost `WM_SIZE` a pak zvolte možnost **Přidat obslužnou rutinu**. Tato akce přidá do třídy `CMFCD2DWalkthroughView` obslužnou rutinu zprávy `OnSize`.

1. V poli **existující obslužné rutiny** vyberte `OnSize`. Chcete-li zobrazit metodu `CMFCD2DWalkthroughView::OnSize`, vyberte možnost **Upravit kód** . Na konci metody přidejte následující kód.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Uložte soubor a zavřete ho.

## <a name="to-implement-a-d2d-drawing-handler"></a>Implementace obslužné rutiny vykreslování D2D

1. V nabídce **projekt** klikněte na příkaz **Průvodce třídami**.

1. V **Průvodci třídou MFC**vyberte v části **název třídy**možnost `CMFCD2DWalkthroughView`.

1. Na kartě **zprávy** vyberte **Přidat vlastní zprávu**.

1. V dialogovém okně **Přidat vlastní zprávu** zadejte do pole **zpráva ve vlastním systému Windows** *AFX_WM_DRAW2D*. Do pole **název obslužné rutiny zpráv** zadejte *OnDraw2D*. Vyberte možnost **registrovaná zpráva** a klikněte na **tlačítko OK**. Tato akce přidá do `CMFCD2DWalkthroughView` třídy obslužnou rutinu zprávy pro AFX_WM_DRAW2Dovou zprávu.

1. V poli **existující obslužné rutiny** vyberte `OnDraw2D`. Chcete-li zobrazit metodu `CMFCD2DWalkthroughView::OnDraw2D`, vyberte možnost **Upravit kód** . Použijte tento kód pro metodu `CMFCD2DWalkthroughView::OnDrawD2D`:

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

   Uložte soubor a zavřete ho.

## <a name="to-verify-the-results"></a>Ověření výsledků

Sestavte a spusťte aplikaci. Měla by mít obdélník přechodu, který se změní při změně velikosti okna. "Hello World!" by měla být zobrazena uprostřed obdélníku.

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
