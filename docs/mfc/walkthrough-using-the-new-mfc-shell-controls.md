---
title: 'Návod: Použití nových ovládacích prvků prostředí MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360216"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Návod: Použití nových ovládacích prvků prostředí MFC

V tomto návodu vytvoříte aplikaci, která se podobá Průzkumníku souborů. Vytvoříte okno, které má dvě podokna. V levém podokně bude obsahovat objekt [CMFCShellTreeCtrl,](../mfc/reference/cmfcshelltreectrl-class.md) který zobrazuje plochu v hierarchickém zobrazení. V pravém podokně bude obsahovat [cmfcShellListCtrl,](../mfc/reference/cmfcshelllistctrl-class.md) který zobrazuje soubory ve složce, která je vybrána v levém podokně.

## <a name="prerequisites"></a>Požadavky

- V sadě Visual Studio 2017 a novější je podpora knihovny MFC volitelnou součástí. Chcete-li ji nainstalovat, otevřete instalační službu sady Visual Studio z nabídky Start systému Windows. Najděte verzi sady Visual Studio, kterou používáte, a zvolte tlačítko **Změnit.** Ujistěte se, že je zaškrtnutá dlaždice **Vývoj plochy s C++.** V části **Volitelné součásti**zaškrtněte tlačítko Podpora **knihovny MFC.**

- Tento návod předpokládá, že jste nastavili Visual Studio používat **obecné nastavení vývoje**. Pokud používáte jiné nastavení vývoje, některá okna sady Visual Studio, která používáme v tomto návodu, se nemusí ve výchozím nastavení zobrazit.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Vytvoření nové aplikace knihovny MFC pomocí Průvodce aplikací knihovny MFC

Tyto kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Vytvoření projektu knihovny MFC v sadě Visual Studio 2019

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. Do vyhledávacího pole v horní části zadejte **knihovnu MFC** a ze seznamu výsledků zvolte **aplikaci knihovny MFC.**

1. Klikněte na **Další**. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

   Po zobrazení **Průvodce aplikací knihovny MFC** použijte následující možnosti:

   1. Vlevo zvolte **Typ aplikace.** Pak vyberte **Jeden dokument** a vyberte podporu **architektury Document/View**. V části **Styl projektu**vyberte **Visual Studio**a v rozevíracím seznamu Vizuální styl a **barvy** vyberte **Office 2007 (modrý motiv).**

   1. V podokně **Podpora složených dokumentů** vyberte **možnost Žádný**.

   1. V podokně **Vlastnosti šablony dokumentu** neprovázte žádné změny.

   1. V podokně **Funkce uživatelského rozhraní** zkontrolujte, zda je vybraná volba **Použít řádek nabídek a panel nástrojů.** Nechte všechny ostatní možnosti tak, jak jsou.

   1. V podokně **Upřesnit funkce** vyberte **ovládací prvky ActiveX**, **Společný manifest ovládacího prvku**a navigační **podokno.** Všechno ostatní nechte tak, jak to je. Možnost **Navigační podokno** způsobí, že průvodce vytvoří podokno nalevo od okna s již vloženým. `CMFCShellTreeCtrl`

   1. V podokně **Generované třídy** neprovedeme žádné změny, takže kliknutím na **Dokončit** vytvořte nový projekt knihovny MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Vytvoření projektu knihovny MFC v sadě Visual Studio 2017 nebo starší

1. Pomocí **Průvodce aplikací knihovny MFC** vytvořte novou aplikaci knihovny MFC. Chcete-li průvodce spustit, vyberte v nabídce **Soubor** **položku Nový**a pak vyberte **možnost Projekt**. Zobrazí se dialogové okno **Nový projekt.**

1. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C++** v podokně **Typy projektu** a vyberte **knihovnu MFC**. Potom v podokně Šablony vyberte **položku Aplikace knihovny MFC**. **Templates** Zadejte název projektu, například `MFCShellControls` a klepněte na tlačítko **OK**.

   Po zobrazení **Průvodce aplikací knihovny MFC** použijte následující možnosti:

   1. V podokně **Typ aplikace** v části **Typ aplikace**zrušte zaškrtnutí možnosti Dokumenty **s kartami.** Dále vyberte **Jeden dokument** a vyberte **podporu architektury Document/View**. V části **Styl projektu**vyberte **Visual Studio**a v rozevíracím seznamu Vizuální styl a **barvy** vyberte **Office 2007 (modrý motiv).**

   1. V podokně **Podpora složených dokumentů** vyberte **možnost Žádný**.

   1. V podokně **Řetězce šablon dokumentu** neprovázte žádné změny.

   1. V podokně **Podpora databáze** (Visual Studio 2015 a starší) vyberte **Žádný,** protože aplikace nepoužívá databázi.

   1. V podokně **Funkce uživatelského rozhraní** zkontrolujte, zda je vybraná volba **Použít řádek nabídek a panel nástrojů.** Nechte všechny ostatní možnosti tak, jak jsou.

   1. V podokně **Upřesnit funkce** vyberte v části **Upřesnit funkce**pouze **ovládací prvky ActiveX** a **společný kontrolní manifest**. V části **Upřesnit podokna rámců**vyberte pouze možnost **Navigační podokno.** To způsobí, že průvodce vytvořit podokno nalevo `CMFCShellTreeCtrl` od okna s již vložené.

   1. V podokně **Generované třídy** neprovedeme žádné změny, takže kliknutím na **Dokončit** vytvořte nový projekt knihovny MFC.

::: moniker-end

Ověřte, zda byla aplikace úspěšně vytvořena sestavením a spuštěním. Chcete-li vytvořit aplikaci, v yberte v nabídce **Sestavení** **možnost Sestavit řešení**. Pokud se aplikace úspěšně vytvoří, spusťte aplikaci výběrem **možnosti Spustit ladění** z nabídky **Ladění.**

Průvodce automaticky vytvoří aplikaci, která má standardní řádek nabídek, standardní panel nástrojů, standardní stavový řádek a panel aplikace Outlook nalevo od okna se zobrazením **Složky** a **zobrazením kalendáře.**

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Přidání ovládacího prvku seznamu skořepin do zobrazení dokumentu

1. V této části přidáte instanci `CMFCShellListCtrl` do zobrazení, které průvodce vytvořil. Otevřete soubor záhlaví zobrazení poklepáním na **soubor MFCShellControlsView.h** v **Průzkumníku řešení**.

   Vyhledejte `#pragma once` direktivu v horní části souboru záhlaví. Okamžitě pod ním přidejte tento kód, aby zahrnoval a deiačník pro `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Nyní přidejte člennou `CMFCShellListCtrl`proměnnou typu . Nejprve vyhledejte v souboru záhlaví následující komentář:

   ```cpp
   // Generated message map functions
   ```

   Bezprostředně nad tento komentář, přidejte tento kód:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Průvodce aplikací knihovny MFC** již vytvořil `CMFCShellTreeCtrl` objekt ve `CMainFrame` třídě, ale je chráněným členem. K objektu se dostaneme později, takže pro něj vytvořte přistupující objekt. Otevřete soubor záhlaví MainFrm.h poklepáním v **Průzkumníku řešení**. Vyhledejte následující komentář:

   ```cpp
   // Attributes
   ```

   Okamžitě pod ním přidejte následující deklaraci metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Dále otevřete zdrojový soubor MainFrm.cpp poklepáním v **Průzkumníku řešení**. V dolní části tohoto souboru přidejte následující definici metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Nyní aktualizujeme `CMFCShellControlsView` třídu `WM_CREATE` pro zpracování zprávy systému Windows. Otevřete okno **Zobrazení třídy** a vyberte třídu. `CMFCShellControlsView` Klepněte pravým tlačítkem myši a vyberte **příkaz Vlastnosti**.

   Dále v [Průvodci třídami](reference/mfc-class-wizard.md)klikněte na kartu `WM_CREATE` **Zprávy.** V rozevíracím seznamu `WM_CREATE`vedle položky vyberte ** \<Přidat> OnCreate**. Příkaz pro nás vytvoří obslužnou rutinu zprávy a automaticky aktualizuje mapu zpráv knihovny MFC.

   V `OnCreate` metodě nyní vytvoříme `CMFCShellListCtrl` náš objekt. Najděte `OnCreate` definici metody ve zdrojovém souboru MFCShellControlsView.cpp a nahraďte její implementaci následujícím kódem:

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. Opakujte předchozí krok, `WM_SIZE` ale pro zprávu. To způsobí, že zobrazení aplikace překreslit vždy, když uživatel změní velikost okna aplikace. Nahraďte definici `OnSize` metody následujícím kódem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Posledním krokem je připojení `CMFCShellTreeCtrl` `CMFCShellListCtrl` objektů a pomocí metody [CMFCShellTreeCtrl::SetRelatedList.](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) Po volání `CMFCShellTreeCtrl::SetRelatedList`se `CMFCShellListCtrl` automaticky zobrazí obsah položky vybrané `CMFCShellTreeCtrl`v . Připojíme objekty `OnActivateView` v metodě, která je přepsána z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   V souboru hlavičky MFCShellControlsView.h přidejte do deklarace `CMFCShellControlsView` třídy následující deklaraci metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Dále přidejte definici metody do zdrojového souboru MFCShellControlsView.cpp:

    ```cpp
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

   Protože voláme metody z `CMainFrame` třídy, musíme přidat direktivu `#include` v horní části zdrojového souboru MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Ověřte, zda byla aplikace úspěšně vytvořena sestavením a spuštěním. Chcete-li vytvořit aplikaci, v yberte v nabídce **Sestavení** **možnost Sestavit řešení**. Pokud se aplikace úspěšně vytvoří, spusťte ji výběrem **možnosti Spustit ladění** z nabídky **Ladění.**

   Nyní byste měli vidět podrobnosti o `CMFCShellTreeCtrl` položce vybrané v podokně zobrazení. Po klepnutí na uzel `CMFCShellTreeCtrl`v `CMFCShellListCtrl` , bude automaticky aktualizován. Podobně pokud poklepete na složku `CMFCShellListCtrl`v `CMFCShellTreeCtrl` , měla by být automaticky aktualizována.

   Klepněte pravým tlačítkem myši na libovolnou položku v ovládacím prvku stromu nebo v ovládacím prvku seznamu. Získáte stejnou místní nabídku, jako byste používali skutečný **Průzkumník souborů**.

## <a name="next-steps"></a>Další kroky

- Průvodce vytvořil panel aplikace Outlook s podoknem **Složek** i podoknem **Kalendář.** Pravděpodobně nemá smysl mít **podokno Kalendáře** v okně **Průzkumníka,** proto toto podokno nyní odeberte.

- Podporuje `CMFCShellListCtrl` zobrazení souborů v různých režimech, jako jsou **velké ikony**, **malé ikony**, **seznam**a **podrobnosti**. Aktualizujte aplikaci a implementujte tuto funkci. Tip: viz [Visual C++ Samples](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[Postupy](../mfc/walkthroughs-mfc.md)
