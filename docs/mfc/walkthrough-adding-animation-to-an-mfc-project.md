---
title: 'Návod: Přidání animace do projektu MFC'
ms.date: 09/20/2018
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
ms.openlocfilehash: 25e29654f1e192e03a078e4a963f27abeea6056d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358601"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Návod: Přidání animace do projektu MFC

Tento návod vás naučí přidání základní animovaný objekt do jazyka Visual C++, projekt třídy knihovny MFC (Microsoft Foundation).

Návodu ukazuje, jak provádět tyto úlohy:

- Vytvoření aplikace knihovny MFC.

- Přidání nabídky a pak přidejte příkazy ke spuštění a zastavení animace.

- Vytváření obslužných rutin pro spouštění a zastavování příkazy.

- Animovaný objektu přidáte do projektu.

- Animovaný objekt v okně centra.

- Zkontrolujte výsledky.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu, musíte mít Visual Studio.

### <a name="to-create-an-mfc-application"></a>Vytvoření aplikace MFC

1. Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně v části **nainstalované šablony**, rozbalte **Visual C++** a pak vyberte **MFC**. V prostředním podokně vyberte **aplikace knihovny MFC**. V **název** zadejte *MFCAnimationWalkthrough*. Klikněte na **OK**.

1. V **Průvodce aplikací knihovny MFC** dialogovém okně ověřte, zda **typ aplikace** je **více dokumentů**, **styl projektu** je  **Visual Studio**a **podpora architektury Document/View** je vybraná možnost. Klikněte na tlačítko **Dokončit**.

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Přidání nabídky a pak přidejte příkazy ke spuštění a zastavení animace

1. Na **zobrazení** nabídky, přejděte k **ostatní Windows** a potom klikněte na tlačítko **zobrazení prostředků**.

1. V **zobrazení prostředků**, přejděte **nabídky** složky a otevřete ho. Dvakrát klikněte **IDR_MFCAnimationWalkthroughTYPE** prostředků otevřete pro úpravy.

1. Na panelu nabídek v **typu tady** zadejte *A & nalizaci* k vytvoření nabídky animace.

1. V části **animace**v **typu tady** zadejte *Start & vpřed* vytvoření příkazu Start vpřed.

1. V části **Start vpřed**v **typu tady** zadejte *oddíl Start & zpětně*.

1. V části **Start zpětně**v **typu tady** zadejte *zas & tavit* vytvoření příkazu Stop.

1. MFCAnimationWalkthrough.rc uložte a zavřete ho.

1. V **Průzkumníka řešení**, dvakrát klikněte na panel MainFrm.cpp otevřete pro úpravy. V `CMainFrame::OnCreate` metoda, vyhledejte oddíl, který má několik volání `lstBasicCommands.AddTail`. Bezprostředně po této části přidejte následující kód.

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. Soubor uložte a zavřete ho.

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Vytváření obslužných rutin pro spuštění a zastavení příkazy

1. Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídami**.

1. V **Průvodce třídami MFC**v části **název třídy**vyberte **CMFCAnimationWalkthroughView**.

1. Na **příkazy** kartě **ID objektů** vyberte **ID_ANIMATION_STARTFORWARD**a pak v **zprávy** vyberte  **PŘÍKAZ**. Klikněte na tlačítko **přidat obslužnou rutinu**.

1. V **přidat členskou funkci** dialogové okno, klikněte na tlačítko **OK**.

1. V **ID objektů** vyberte **ID_ANIMATION_STARTBACKWARD**a pak v **zprávy** vyberte **příkaz**. Klikněte na tlačítko **přidat obslužnou rutinu**.

1. V **přidat členskou funkci** dialogové okno, klikněte na tlačítko **OK**.

1. V **ID objektů** vyberte **ID_ANIMATION_STOP**a pak v **zprávy** vyberte **příkaz**. Klikněte na tlačítko **přidat obslužnou rutinu** a potom klikněte na tlačítko **OK**.

1. V **přidat členskou funkci** dialogové okno, klikněte na tlačítko **OK**.

1. V **Průvodce třídami MFC**, klikněte na tlačítko **OK**.

1. Uložit MFCAnimationWalkthroughView.cpp, což je otevřen v editoru, ale nechejte ho.

### <a name="to-add-an-animated-object-to-the-project"></a>Chcete-li přidat do projektu animovaný objekt

1. V **Průzkumníka řešení**, dvakrát klikněte na panel MFCAnimationWalkthroughView.h otevřete pro úpravy. Těsně před definici `CMFCAnimationWalkthroughView` třídy, přidejte následující kód k vytvoření vlastní animace kontroler, který bude zpracovávat plánování je v konfliktu s objektem animace.

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. Na konci `CMFCAnimationWalkthroughView` třídy, přidejte následující kód.

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. Po `DECLARE_MESSAGE_MAP()` řádek, přidejte následující kód.

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. Soubor uložte a zavřete ho.

1. V MFCAnimationWalkthroughView.cpp v horní části souboru po `#include` příkazy ale předtím, než se jakékoli třídy, metody, přidejte následující kód.

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. Na konci konstruktor pro `CMFCAnimationWalkthroughView`, přidejte následující kód.

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. Vyhledejte `CAnimationWalthroughView::PreCreateWindow` metodu a nahraďte ho následujícím kódem.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. Vyhledejte `CAnimationWalkthroughView::OnDraw` metodu a nahraďte ho následujícím kódem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)
    {
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
        ASSERT_VALID(pDoc);
        if (!pDoc)
            return;

        // TODO: add draw code for native data here
        CMemDC dcMem(*pDC, this);
        CDC& dc = dcMem.GetDC();
        CRect rect;
        GetClientRect(rect);

        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));

        CString strRGB;
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. Na konci souboru přidejte následující kód.

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídami**.

1. V **Průvodce třídami MFC**v části **název třídy**vyberte **CMFCAnimationWalkthroughView**.

1. Na **zprávy** kartě **zprávy** vyberte **WM_ERASEBKGND**, klikněte na tlačítko **přidat obslužnou rutinu**a potom klikněte na tlačítko **OK** .

1. V MFCAnimationWalkthroughView.cpp, nahraďte provádění `OnEraseBkgnd` s následující kód pro omezení blikání v animovaný objekt, když se měl překreslit.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. Nahraďte implementace `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, a `CMFCAnimationWalkthroughView::OnAnimationStop` následujícím kódem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()
    {
        Animate(TRUE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()
    {
        Animate(FALSE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStop()
    {
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
        if (pManager != NULL)
        {
            pManager->AbandonAllStoryboards();

        }
    }
    ```

1. Soubor uložte a zavřete ho.

### <a name="to-center-the-animated-object-in-the-window"></a>Zarovnat na střed animovaný objekt v okně

1. V **Průzkumníka řešení**, dvakrát klikněte na panel MFCAnimationWalkthroughView.h otevřete pro úpravy. Na konci `CMFCAnimationWalkthroughView` třídy ihned za definici `m_animationRect`, přidejte následující kód.

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. Soubor uložte a zavřete ho.

1. Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídami**.

1. V **Průvodce třídami MFC**v části **název třídy**vyberte **CMFCAnimationWalkthroughView**.

1. Na **zprávy** kartě **zprávy** vyberte **WM_SIZE**, klikněte na tlačítko **přidat obslužnou rutinu**a potom klikněte na tlačítko **OK**.

1. V MFCAnimationWalkthroughView.cpp, nahraďte kód `CMFCAnimationWalkthroughView::OnSize` následujícím kódem.

    ```cpp
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);
        CRect rect;
        GetClientRect(rect);

        rect.top += nInfoAreaHeight;

        CRect rectAnim = m_animationRect;
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,
        rect.CenterPoint().y - rectAnim.Height() / 2),
        rectAnim.Size());

        if (m_animationController.IsAnimationInProgress())
        {
            Animate(m_bCurrentDirection);
        }
    }
    ```

1. Na začátku konstruktor pro `CMFCAnimationWalkthroughView`, přidejte následující kód.

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. Na začátku `CMFCAnimationWalkthroughView::Animate` metodu, přidejte následující kód.

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. Soubor uložte a zavřete ho.

### <a name="to-verify-the-results"></a>Chcete-li ověřit výsledky

1. Sestavte a spusťte aplikaci. Na **animace** nabídky, klikněte na tlačítko **Start vpřed**. Obdélník by měla objevit a potom vyplňte oblasti System center. Po kliknutí na **Start zpětně**, by měla odvolat animace a po kliknutí na **Zastavit**, by se měla zastavit. Barva výplně rámečku měli měnit v průběhu animace a aktuální barva má být zobrazena v horní části okna animace.

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
