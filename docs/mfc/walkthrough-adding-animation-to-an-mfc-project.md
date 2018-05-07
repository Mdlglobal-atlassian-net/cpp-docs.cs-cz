---
title: 'Návod: Přidání animace do projektu MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8ae7496daf6827a6be7769d60af10bca45f7a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Návod: Přidání animace do projektu MFC
Tento názorný postup učí, jak přidat základní animovaný objekt pro aplikaci Visual C++, projektu Microsoft Foundation Class Library (MFC).  
  
 Průvodce ukazuje, jak provést tyto úlohy:  
  
-   Vytvoření aplikace knihovny MFC.  
  
-   Přidat nabídku a pak přidejte příkazů pro spuštění a zastavení animace.  
  
-   Vytvoření obslužné rutiny pro příkazy zahájení a ukončení.  
  
-   Animovaný objekt přidejte do projektu.  
  
-   Animovaný objekt v okně centra softwaru.  
  
-   Zkontrolujte výsledky.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Pro dokončení tohoto návodu, musíte mít Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>K vytvoření aplikace knihovny MFC  
  
1.  Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.  
  
2.  V **nový projekt** dialogové okno, v levém podokně v části **nainstalovaných šablonách**, rozbalte položku **Visual C++** a pak vyberte **MFC**. V prostředním podokně vyberte **aplikace knihovny MFC**. V **název** zadejte `MFCAnimationWalkthrough`. Click **OK**.  
  
3.  V **Průvodce aplikací knihovny MFC** dialogové okno ověřte, zda **typ aplikace** je **více dokumentů**, **styl projektu** je  **Visual Studio**a **Document/View – architektura podporu** je vybraná možnost. Klikněte na tlačítko **Dokončit**.  
  
### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Přidat nabídku a pak přidat příkazů pro spuštění a zastavení animace  
  
1.  Na **zobrazení** nabídky, přejděte na příkaz **ostatní okna** a pak klikněte na **zobrazení prostředků**.  
  
2.  V **zobrazení prostředků**, přejděte na **nabídky** složky a otevřete ji. Dvakrát klikněte `IDR_MFCAnimationWalTYPE` prostředků otevřít pro úpravy.  
  
3.  V řádku nabídek v **zde typ** zadejte `A&nimation` k vytvoření nabídky animace.  
  
4.  V části **animace**v **zde typ** zadejte `Start &Forward` k vytvoření příkazu Start dál.  
  
5.  V části **spustit dál**v **zde typ** zadejte `Start &Backward`.  
  
6.  V části **spustit zpětné**v **zde typ** zadejte `S&top` vytvořit příkaz Stop.  
  
7.  MFCAnimationWalkthrough.rc uložte a zavřete ji.  
  
8.  V **Průzkumníku**, dvakrát klikněte na MainFrm.cpp otevřete pro úpravy. V `CMainFrame::OnCreate` metoda, vyhledejte oddíl, který má několik volání `lstBasicCommands.AddTail`. Bezprostředně za tuto část přidejte následující kód.  
  
 ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);

 lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);

    lstBasicCommands.AddTail(ID_ANIMATION_STOP);

 ```  
  
9. Soubor uložte a zavřete ho.  
  
### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>K vytvoření obslužné rutiny pro spuštění a zastavení příkazy  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídou**.  
  
2.  V **Průvodce třídou MFC**v části **název třídy**, vyberte `CMFCAnimationWalkthroughView`.  
  
3.  Na **příkazy** ve **ID objektů** vyberte `ID_ANIMATION_STARTFORWARD`a potom v **zprávy** vyberte `COMMAND`. Klikněte na tlačítko **přidejte obslužnou rutinu**.  
  
4.  V **přidat – členská funkce** dialogové okno, klikněte na tlačítko **OK**.  
  
5.  V **ID objektů** vyberte `ID_ANIMATION_STARTBACKWARD`a potom v **zprávy** vyberte `COMMAND`. Klikněte na tlačítko **přidejte obslužnou rutinu**.  
  
6.  V **přidat – členská funkce** dialogové okno, klikněte na tlačítko **OK**.  
  
7.  V **ID objektů** vyberte `ID_ANIMATION_STOP`a potom v **zprávy** vyberte `COMMAND`. Klikněte na tlačítko **přidat obslužnou rutinu** a pak klikněte na **OK**.  
  
8.  V **přidat – členská funkce** dialogové okno, klikněte na tlačítko **OK**.  
  
9. V **Průvodce třídou MFC**, klikněte na tlačítko **OK**.  
  
10. Uložit MFCAnimationWalkthroughView.cpp, což je otevřen v editoru, ale není ho zavřete.  
  
### <a name="to-add-an-animated-object-to-the-project"></a>Chcete-li přidat animovaného objektu do projektu  
  
1.  V Průzkumníku řešení klikněte dvakrát na MFCAnimationWalkthroughView.h otevřete pro úpravy. Těsně před definice `CMFCAnimationWalkthroughView` třídy, přidejte následující kód k vytvoření vlastní animace kontroler, který bude zpracovávat plánování je v konfliktu s objekt animace.  
  
 ```  
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
  
2.  Na konci `CMFCAnimationWalkthroughView` třídy, přidejte následující kód.  
  
 ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
 ```  
  
3.  Po `DECLARE_MESSAGE_MAP()` řádek, přidejte následující kód.  
  
 ```  
    void Animate(BOOL bDirection);

 ```  
  
4.  Soubor uložte a zavřete ho.  
  
5.  V MFCAnimationWalkthroughView.cpp v horní části souboru po `#include` příkazy ale předtím, než všechny třídy metody, přidejte následující kód.  
  
 ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
 ```  
  
6.  Na konci v konstruktoru pro `CMFCAnimationWalkthroughView`, přidejte následující kód.  
  
 ```  
    m_animationController.EnableAnimationTimerEventHandler();
m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);

 
    m_animationColor = RGB(255,
    255,
    255);

    m_animationRect = CRect(0,
    0,
    0,
    0);

 
    m_animationColor.SetID(-1,
    nAnimationGroup);

    m_animationRect.SetID(-1,
    nAnimationGroup);

 
    m_animationController.AddAnimationObject(&m_animationColor);

 m_animationController.AddAnimationObject(&m_animationRect);

 ```  
  
7.  Vyhledejte `CAnimationWalthroughView::PreCreateWindow` metodu a nahraďte ji následujícím kódem.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
 { *// TODO: Modify the Window class or styles here by modifying *//  the CREATESTRUCT cs  
 
    m_animationController.SetRelatedWnd(this);

 return CView::PreCreateWindow(cs);

 }  
 ```  
  
8.  Vyhledejte `CAnimationWalkthroughView::OnDraw` metodu a nahraďte ji následujícím kódem.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
 {  
    CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
ASSERT_VALID(pDoc);

 if (!pDoc)  
    return; 
 *// TODO: add draw code for native data here  
    CMemDC dcMem(*pDC,
    this);

    CDC& dc = dcMem.GetDC();

 
    CRect rect;  
    GetClientRect(rect);

 
    dc.FillSolidRect(rect,
    GetSysColor(COLOR_WINDOW));

 
    CString strRGB;  
    strRGB.Format(_T("Fill Color is: %d; %d; %d"),
    GetRValue(m_animationColor),
    GetGValue(m_animationColor),
    GetBValue(m_animationColor));

 
    dc.DrawText(strRGB,
    rect,
    DT_CENTER);

    rect.top += nInfoAreaHeight;  
 
    CBrush br;  
 
    br.CreateSolidBrush(m_animationColor);

 CBrush* pBrushOld = dc.SelectObject(&br);

 
    dc.Rectangle((CRect)m_animationRect);

 dc.SelectObject(pBrushOld);

 }  
 ```  
  
9. Na konci souboru přidejte následující kód.  
  
 ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
 {  
    static UI_ANIMATION_SECONDS duration = 3;  
    static DOUBLE dblSpeed = 35.;  
    static BYTE nStartColor = 50;  
    static BYTE nEndColor = 255;  
 
    BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;  
 
    CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

    CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

    CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

 
    m_animationColor.AddTransition(pRedTransition,
    pGreenTransition,
    pBlueTransition);

 
    CRect rectClient;  
    GetClientRect(rectClient);

 rectClient.top += nInfoAreaHeight;  
 
    int nLeftFinal = bDirection  rectClient.left : rectClient.CenterPoint().x;  
    int nTopFinal = bDirection  rectClient.top : rectClient.CenterPoint().y;  
    int nRightFinal = bDirection  rectClient.right : rectClient.CenterPoint().x;  
    int nBottomFinal = bDirection  rectClient.bottom : rectClient.CenterPoint().y;  
 
    CLinearTransition* pLeftTransition = new CLinearTransition(duration,
    nLeftFinal);

    CLinearTransition* pTopTransition = new CLinearTransition(duration,
    nTopFinal);

    CLinearTransition* pRightTransition = new CLinearTransition(duration,
    nRightFinal);

    CLinearTransition* pBottomTransition = new CLinearTransition(duration,
    nBottomFinal);

 
    m_animationRect.AddTransition(pLeftTransition,
    pTopTransition,
    pRightTransition,
    pBottomTransition);

 
    CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();
CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup,
    pBlueTransition);

 
    pLeftTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pTopTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pRightTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pBottomTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

 
    m_animationController.AnimateGroup(nAnimationGroup);

 }  
 ```  
  
10. Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídou**.  
  
11. V **Průvodce třídou MFC**v části **název třídy**, vyberte `CMFCAnimationWalkthroughView`.  
  
12. Na **zprávy** ve **zprávy** vyberte `WM_ERASEBKGND`, klikněte na tlačítko **přidat obslužnou rutinu**a potom klikněte na **OK**.  
  
13. V MFCAnimationWalkthroughView.cpp, nahraďte implementace `OnEraseBkgnd` ke snížení blikání v animovaný objektu, když bude překreslen následujícím kódem.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
 {  
    return TRUE;  
 }  
 ```  
  
14. Nahraďte implementace `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, a `CMFCAnimationWalkthroughView::OnAnimationStop` následujícím kódem.  
  
 ```  
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
  
15. Soubor uložte a zavřete ho.  
  
### <a name="to-center-the-animated-object-in-the-window"></a>Na střed animovaný objekt v okně  
  
1.  V **Průzkumníku**, dvakrát klikněte na MFCAnimationWalkthroughView.h otevřete pro úpravy. Na konci `CMFCAnimationWalkthroughView` třída právě po definování `m_animationRect`, přidejte následující kód.  
  
 ```  
    BOOL m_bCurrentDirection;  
 ```  
  
2.  Soubor uložte a zavřete ho.  
  
3.  Na **projektu** nabídky, klikněte na tlačítko **Průvodce třídou**.  
  
4.  V **Průvodce třídou MFC**v části **název třídy**, vyberte `CMFCAnimationWalkthroughView`.  
  
5.  Na **zprávy** ve **zprávy** vyberte `WM_SIZE`, klikněte na tlačítko **přidat obslužnou rutinu**a potom klikněte na **OK**.  
  
6.  V MFCAnimationWalkthroughView.cpp, nahraďte kód pro `CMFCAnimationWalkthroughView::OnSize` následujícím kódem.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

 
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
  
7.  Na začátku v konstruktoru pro `CMFCAnimationWalkthroughView`, přidejte následující kód.  
  
 ```  
    m_bCurrentDirection = TRUE;  
 ```  
  
8.  Na začátku `CMFCAnimationWalkthroughView::Animate` metoda, přidejte následující kód.  
  
 ```  
    m_bCurrentDirection = bDirection;  
 ```  
  
9. Soubor uložte a zavřete ho.  
  
### <a name="to-verify-the-results"></a>Ověření výsledků  
  
1.  Sestavte a spusťte aplikaci. Na **animace** nabídky, klikněte na tlačítko **spustit dál**. Obdélník by měl zobrazit a pak zadejte oblasti center. Když kliknete na tlačítko **spustit zpětné**, by měl reverse animace a když kliknete na tlačítko **Zastavit**, by se měla zastavit. Barva výplně rámečku by se měl změnit v průběhu animace a aktuální barva má být zobrazen v horní části okna animace.  
  
## <a name="see-also"></a>Viz také  
 [Návody](../mfc/walkthroughs-mfc.md)

