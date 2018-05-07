---
title: 'Návod: Použití prostředí MFC nové prostředí Shell ovládací prvky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f19939a50b5bdbf98d087450b6301a923651a433
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Návod: Použití nových ovládacích prvků prostředí MFC
V tomto návodu vytvoříte aplikaci, která se podobá Průzkumníku souborů. Vytvoříte okno, které obsahuje dvě podokna. V levém podokně bude obsahovat [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objekt, který se zobrazuje v hierarchické zobrazení plochy. V pravém podokně bude obsahovat [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) který ukazuje soubory ve složce, který je vybraný v levém podokně.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento návod předpokládá, že jste nastavili [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] používat **obecné nastavení vývoj**. Pokud používáte jiný vývoj nastavení, některé [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] windows, které používáme v tomto názorném postupu nemusí být zobrazeny ve výchozím nastavení.  
  
### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Chcete-li vytvořit novou aplikaci MFC pomocí Průvodce aplikací MFC  
  
1.  Použití **Průvodce aplikací knihovny MFC** k vytvoření nové aplikace MFC. Spuštění průvodce, z **souboru** nabídky vyberte možnost **nový**a potom vyberte **projektu**. **Nový projekt** zobrazí se dialogové okno.  
  
2.  V **nový projekt** dialogové okno rozbalte položku **Visual C++** uzlu **typy projektů** panelu a vyberte **MFC**. Potom v **šablony** podokně, vyberte **aplikace knihovny MFC**. Zadejte název projektu, například `MFCShellControls` a klikněte na tlačítko **OK**. **Průvodce aplikací knihovny MFC** se zobrazí.  
  
3.  V **Průvodce aplikací knihovny MFC** dialogové okno, klikněte na tlačítko **Další**. **Typ aplikace** podokně se zobrazí.  
  
4.  Na **typ aplikace** podokně v části **typ aplikace**, zrušte **dokumenty na kartách** možnost. Potom vyberte **jednotlivý dokument** a vyberte **Document/View – architektura podporu**. V části **projektu styl**, vyberte **Visual Studio**a z **vizuálního stylu a barvy** rozevíracím seznamu vyberte **Office 2007 (motiv modrý)**. Nechte všech jiných možností, jak jsou. Klikněte na tlačítko **Další** zobrazíte **složené podporu dokumentu** podokně.  
  
5.  Na **složené podporu dokumentu** podokně, vyberte **žádné**. Klikněte na tlačítko **Další** zobrazíte **řetězce šablony dokumentu** podokně.  
  
6.  Neprovádějte žádné změny **řetězce šablony dokumentu** podokně. Klikněte na tlačítko **Další** zobrazíte **podpory databáze** podokně.  
  
7.  Na **podpory databáze** podokně, vyberte **žádné** protože této aplikace nepoužívá databázi. Klikněte na tlačítko **Další** zobrazíte **funkce uživatelského rozhraní** podokně.  
  
8.  Na **funkce uživatelského rozhraní** podokně, ujistěte se, že **použít řádku nabídek a panelů nástrojů** je vybraná možnost. Nechte všech jiných možností, jak jsou. Klikněte na tlačítko **Další** zobrazíte **upřesňující funkce** podokně.  
  
9. Na **upřesňující funkce** podokně v části **pokročilé funkce**, vyberte pouze **– ovládací prvky ActiveX** a **běžné ovládacího prvku manifestu**. V části **Rozšířené podokna rámce**, vyberte pouze **navigačním podokně** možnost. To způsobí, že průvodce pro vytvoření podokna na levé straně okna s `CMFCShellTreeCtrl` již vložených. Klikněte na tlačítko **Další** zobrazíte **generované třídy** podokně.  
  
10. Jsme nebudete provést jakékoli změny **generované třídy** podokně. Proto klikněte na tlačítko **Dokončit** k vytvoření nového projektu knihovny MFC.  
  
11. Ověřte, že aplikace byl úspěšně vytvořen vytváření a jeho spuštěním. K vytvoření aplikace, z **sestavení** nabídky vyberte možnost **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte aplikaci tak, že vyberete **spustit ladění** z **ladění** nabídky.  
  
     Průvodce automaticky vytvoří aplikaci, která obsahuje standardní řádek nabídek, standardním panelu nástrojů, standardní stavového řádku a panel aplikace Outlook na levé straně okna s **složky** zobrazení a **kalendáře** zobrazení .  
  
### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Přidání ovládacího prvku seznam prostředí do zobrazení dokumentu  
  
1.  V této části přidáte instanci `CMFCShellListCtrl` k zobrazení, které průvodce vytvořit. Otevřete soubor hlaviček zobrazení dvojitým kliknutím na soubor MFCShellControlsView.h v **Průzkumníku řešení**.  
  
     Vyhledejte `#pragma once` direktivy v horní části soubor hlaviček. Okamžitě pod ho přidat do zahrnout soubor hlaviček, pro tento kód `CMFCShellListCtrl`:  
  
 ```  
    #include <afxShellListCtrl.h>  
 ```  
  
     Nyní přidejte členské proměnné typu `CMFCShellListCtrl`. Nejdříve vyhledejte následující komentář v záhlaví souboru:  
  
 "' * / / Generované funkce mapy zpráv  
 ```  
  
     Immediately above that comment add this code:  
  
 ```  
    privátní: CMFCShellListCtrl m_wndList;  
 ```  
  
2.  The **MFC Application Wizard** already created a `CMFCShellTreeCtrl` object in the `CMainFrame` class, but it is a protected member. We will access this object later. Therefore, create an accessor for it now. Open the MainFrm.h header file by double-clicking it in the **Solution Explorer**. Locate the following comment:  
  
 ``` *// Attributes  
 ```  
  
     Bezprostředně pod, přidejte následující deklarace metody:  
  
 ```  
    public: 
    CMFCShellTreeCtrl& GetShellTreeCtrl();

 ```  
  
     V dalším kroku otevřít zdrojový soubor MainFrm.cpp poklepáním v **Průzkumníku řešení**. V dolní části tento soubor přidejte následující definici metody:  
  
 ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
 {  
    return m_wndTree;  
 }  
 ```  
  
3.  Nyní budeme aktualizovat `CMFCShellControlsView` třídy pro zpracování **WM_CREATE** zpráv systému windows. Otevřete soubor hlaviček MFCShellControlsView.h a klikněte na tento řádek kódu:  
  
 ```  
    class CMFCShellControlsView : public CView  
 ```  
  
     Vedle **vlastnosti** okně klikněte na tlačítko **zprávy** ikonu. Přejděte dolů na zjistíte **WM_CREATE** zprávy. Z rozevíracího seznamu vedle **WM_CREATE**, vyberte  **\<Přidat > OnCreate**. Tím se vytvoří obslužné rutiny zpráv pro nás a mapy zpráv knihovny MFC automaticky aktualizuje.  
  
     V `OnCreate` metoda Nyní vytvoříme naše `CMFCShellListCtrl` objektu. Najít `OnCreate` definici metody v MFCShellControlsView.cpp zdrojového souboru a jeho implementace nahraďte následujícím kódem:  
  
 ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
 {  
    if (CView::OnCreate(lpCreateStruct) == -1)  
    return -1;  
 
    CRect rectDummy (0,
    0,
    0,
    0);

    m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,  
    rectDummy,
    this,
    1);

 
    return 0;  
 }  
 ```  
  
4.  Opakujte předchozí krok, ale u **WM_SIZE** zprávy. To způsobí, že vaše aplikace zobrazení překreslit vždy, když uživatel změní velikost okna aplikace. Nahraďte definici `OnSize` metoda následujícím kódem:  
  
 ```  
    void CMFCShellControlsView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

    m_wndList.SetWindowPos(NULL, -1, -1,
    cx,
    cy,  
    SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);

 }  
 ```  
  
5.  Posledním krokem je pro připojení `CMFCShellTreeCtrl` a `CMFCShellListCtrl` objekty pomocí [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metoda. Po tuto metodu lze volat `CMFCShellListCtrl` se automaticky zobrazí obsah k položce vybrané `CMFCShellTreeCtrl`. Uděláme to `OnActivateView` metoda, která je přepsat z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).  
  
     V záhlaví souboru MFCShellControlsView.h uvnitř `CMFCShellControlsView` deklarace třídy, přidejte následující deklarace metody:  
  
 ```  
    protected: 
    virtual void OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);

 ```  
  
     V dalším kroku přidejte definici pro tuto metodu ke zdrojovému souboru MFCShellControlsView.cpp:  
  
 ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView)   
 {  
    if (bActivate&& AfxGetMainWnd() != NULL)  
 {  
 ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);

 }  
 
    CView::OnActivateView(bActivate,
    pActivateView,
    pDeactiveView);

 }  
 ```  
  
     Protože jsme se volání metod z `CMainFrame` třídu, musí přidáme `#include` direktivy v horní části MFCShellControlsView.cpp zdrojového souboru:  
  
 ```  
    #include "MainFrm.h"  
 ```  
  
6.  Ověřte, že aplikace byl úspěšně vytvořen vytváření a jeho spuštěním. K vytvoření aplikace, z **sestavení** nabídky vyberte možnost **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte ji tak, že vyberete **spustit ladění** z **ladění** nabídky.  
  
     Teď byste měli vidět podrobnosti pro vybranou položku v `CMFCShellTreeCtrl` v podokně zobrazení. Po kliknutí uzel v `CMFCShellTreeCtrl`, `CMFCShellListCtrl` budou automaticky aktualizovány. Podobně pokud dvakrát kliknete na složku, do `CMFCShellListCtrl`, `CMFCShellTreeCtrl` by měl být automaticky aktualizován.  
  
     Klikněte pravým tlačítkem libovolnou položku v ovládacím prvku stromu nebo v ovládacím prvku seznamu. Všimněte si, získat stejné kontextové nabídky, jak je, pokud jste používali skutečné Průzkumníka souborů.  
  
## <a name="next-steps"></a>Další kroky  
  
-   Průvodce Vytvořit panel aplikace Outlook s oběma **složky** podokně a **kalendáře** podokně. Je pravděpodobně nemá smysl mít **kalendáře** podokně v okně Průzkumníka. Proto že podokně nyní odeberte.  
  
-   `CMFCShellListCtrl` Podporuje zobrazení souborů, jako v různých režimech **ikony. velké ikony**, **ikony. Malé ikony**, **seznamu**, a **podrobnosti**. Aktualizujte aplikaci, abyste tuto funkci implementovat. Nápověda: najdete v části [Visual C++ – ukázky](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody](../mfc/walkthroughs-mfc.md)

