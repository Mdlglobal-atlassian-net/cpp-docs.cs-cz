---
title: 'Návod: Použití nových ovládacích prvků prostředí MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: cf0a6bd230364b48c78c72b8e453e7e641fb2d0e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907411"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Návod: Použití nových ovládacích prvků prostředí MFC

V tomto návodu vytvoříte aplikaci, která bude vypadat jako Průzkumník souborů. Vytvoříte okno, které má dvě podokna. V levém podokně se zobrazí objekt [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) , který zobrazí vaši plochu v hierarchickém zobrazení. V pravém podokně se zobrazí [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) se soubory ve složce, která je vybrána v levém podokně.

## <a name="prerequisites"></a>Požadavky

- V aplikaci Visual Studio 2017 nebo novější je podpora MFC volitelnou součástí. Pokud ho chcete nainstalovat, otevřete Instalační program pro Visual Studio v nabídce Start systému Windows. Vyhledejte verzi sady Visual Studio, kterou používáte, a klikněte na tlačítko **Upravit** . Ujistěte se, že je zaškrtnutá možnost **vývoj desktopových aplikací pomocí C++**  dlaždice. V části **volitelné součásti**zaškrtněte tlačítko **Podpora MFC** .

- Tento návod předpokládá, že jste nastavili sadu Visual Studio tak, aby používala **Obecné vývojové nastavení**. Pokud používáte jiné vývojové nastavení, nemusí se ve výchozím nastavení zobrazovat některá okna sady Visual Studio, která v tomto návodu používáme.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Vytvoření nové aplikace MFC pomocí Průvodce aplikací knihovny MFC

Tyto kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že selektor verzí v levém horním rohu této stránky je nastaven správně.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Vytvoření projektu knihovny MFC v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. Do vyhledávacího pole v horní části zadejte **MFC** a pak zvolte **aplikace MFC** ze seznamu výsledků. 

1. Klikněte na **Další**. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

   Po zobrazení **Průvodce aplikací knihovny MFC** použijte následující možnosti:
 
   1. Na levé straně vyberte **Typ aplikace** . Pak vyberte možnost **jednotlivý dokument** a vyberte možnost **dokument/zobrazit podporu architektury**. V nabídce **styl projektu**vyberte možnost **Visual Studio**a v rozevíracím seznamu **vizuální styl a barvy** vyberte možnost **Office 2007 (modrý motiv)** .

   1. V podokně **Podpora složeného dokumentu** vyberte **None (žádné**).

   1. Neprovádějte žádné změny v podokně **vlastností šablony dokumentu** .

   1. V podokně **funkce uživatelského rozhraní** se ujistěte, že je vybraná možnost **použít řádek nabídek a panel nástrojů** . Všechny ostatní možnosti ponechte beze změny.

   1. V podokně **Pokročilé funkce** vyberte **ovládací prvky ActiveX**, **manifest obecného ovládacího prvku**a možnost **navigačního podokna** . Ponechte všechno ostatní, co je to. Možnost **navigační podokno** způsobí, že Průvodce vytvoří podokno vlevo od okna s již vloženým objektem `CMFCShellTreeCtrl` .

   1. Nebudeme dělat žádné změny v podokně **vygenerované třídy** , proto kliknutím na **Dokončit** vytvoříte nový projekt knihovny MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Vytvoření projektu knihovny MFC v aplikaci Visual Studio 2017 nebo starší

1. Použijte **Průvodce aplikací knihovny MFC** k vytvoření nové aplikace MFC. Chcete-li spustit průvodce, klikněte v nabídce **soubor** na příkaz **Nový**a vyberte možnost **projekt**. Zobrazí se dialogové okno **Nový projekt** .

1. V dialogovém okně **Nový projekt** rozbalte uzel **vizuál C++**  v podokně **typy projektů** a vyberte položku **MFC**. Poté v podokně **šablony** vyberte možnost **aplikace MFC**. Zadejte název projektu, například `MFCShellControls` a klikněte na tlačítko **OK**. 

   Po zobrazení **Průvodce aplikací knihovny MFC** použijte následující možnosti:

   1. V podokně **Typ aplikace** , v části **Typ aplikace**, zrušte zaškrtnutí možnosti **dokumenty s kartami** . Dále vyberte možnost **jeden dokument** a vyberte možnost **dokument/zobrazení Podpora architektury**. V nabídce **styl projektu**vyberte možnost **Visual Studio**a v rozevíracím seznamu **vizuální styl a barvy** vyberte možnost **Office 2007 (modrý motiv)** .

   1. V podokně **Podpora složeného dokumentu** vyberte **None (žádné**).

   1. V podokně **řetězce šablon dokumentů** neprovádějte žádné změny.

   1. V podokně **Podpora databáze** (Visual Studio 2015 a starší) vyberte možnost **žádné** , protože aplikace nepoužívá databázi.

   1. V podokně **funkce uživatelského rozhraní** se ujistěte, že je vybraná možnost **použít řádek nabídek a panel nástrojů** . Všechny ostatní možnosti ponechte beze změny.

   1. V podokně **Pokročilé funkce** vyberte v části **Rozšířené funkce**pouze **ovládací prvky ActiveX** a **obecný manifest ovládacího prvku**. V části **Pokročilá podokna snímků**vyberte pouze možnost **navigační podokno** . Způsobí to, že Průvodce vytvoří podokno vlevo od okna s již vloženým objektem `CMFCShellTreeCtrl` .

   1. Nebudeme dělat žádné změny v podokně **vygenerované třídy** , proto kliknutím na **Dokončit** vytvoříte nový projekt knihovny MFC.

::: moniker-end

Vytvořením a spuštěním aplikace ověřte, zda byla aplikace vytvořena úspěšně. Chcete-li sestavit aplikaci, v nabídce **sestavení** vyberte **sestavení řešení**. Pokud se aplikace úspěšně sestaví, spusťte aplikaci výběrem možnosti **Spustit ladění** v nabídce **ladění** .

Průvodce automaticky vytvoří aplikaci, která má standardní panel nabídek, standardní panel nástrojů, standardní stavový řádek a panel aplikace Outlook nalevo od okna se zobrazením **složek** a zobrazením **kalendáře** .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Přidání ovládacího prvku seznam prostředí do zobrazení dokumentu

1. V této části přidáte instanci `CMFCShellListCtrl` do zobrazení, které vytvořil průvodce. Otevřete hlavičkový soubor kliknutím dvakrát na **MFCShellControlsView. h** v **Průzkumník řešení**.

   `#pragma once` Vyhledejte direktivu v horní části hlavičkového souboru. Hned pod ním přidejte tento kód, aby zahrnoval hlavičkový soubor `CMFCShellListCtrl`pro:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Nyní přidejte členskou proměnnou typu `CMFCShellListCtrl`. Nejdřív vyhledejte v hlavičkovém souboru následující komentář:

   ```cpp
   // Generated message map functions
   ```

   Hned nad tento komentář přidejte tento kód:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Průvodce aplikací knihovny MFC** již vytvořil `CMFCShellTreeCtrl` objekt ve `CMainFrame` třídě, ale je to chráněný člen. Později se k objektu pokusíme vytvořit přistupující objekt. Otevřete hlavičkový soubor MainFrm. h dvojitým kliknutím na něj na **Průzkumník řešení**. Vyhledejte následující komentář:

   ```cpp
   // Attributes
   ```

   Hned pod ním přidejte následující deklaraci metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Pak otevřete zdrojový soubor MainFrm. cpp dvojitým kliknutím na něj v **Průzkumník řešení**. V dolní části tohoto souboru přidejte následující definici metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Nyní aktualizujeme `CMFCShellControlsView` třídu pro `WM_CREATE` zpracování zprávy systému Windows. Otevřete okno **zobrazení tříd** a vyberte `CMFCShellControlsView` třídu. Klikněte pravým tlačítkem a vyberte **vlastnosti**.

   Potom v [Průvodci třídou](reference/mfc-class-wizard.md)klikněte na kartu **zprávy** . Posuňte se `WM_CREATE` dolů, dokud nenajdete zprávu. V rozevíracím seznamu vedle `WM_CREATE`vyberte  **\<přidat > vytvořit**. Příkaz vytvoří obslužnou rutinu zprávy pro nás a automaticky aktualizuje mapu zpráv knihovny MFC.

   V metodě teď vytvoříme náš `CMFCShellListCtrl` objekt. `OnCreate` Vyhledejte definici `OnCreate` metody ve zdrojovém souboru MFCShellControlsView. cpp a nahraďte její implementaci následujícím kódem:

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

1. Opakujte předchozí krok, ale pro `WM_SIZE` zprávu. Způsobí to, že se vaše aplikace překreslí, kdykoli uživatel změní velikost okna aplikace. Nahraďte definici pro `OnSize` metodu následujícím kódem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Posledním krokem je připojení `CMFCShellTreeCtrl` objektů a `CMFCShellListCtrl` pomocí metody [CMFCShellTreeCtrl:: SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) . Po volání `CMFCShellTreeCtrl::SetRelatedList` `CMFCShellListCtrl` se automaticky zobrazí obsah položky vybrané v `CMFCShellTreeCtrl`. Propojíme objekty v `OnActivateView` metodě, která je přepsána z [CView:: OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   V hlavičkovém souboru MFCShellControlsView. h uvnitř `CMFCShellControlsView` deklarace třídy přidejte následující deklaraci metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Dále přidejte definici pro metodu do zdrojového souboru MFCShellControlsView. cpp:

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

   Vzhledem k tomu, že voláte metody `CMainFrame` ze třídy, je nutné `#include` přidat direktivu v horní části zdrojového souboru MFCShellControlsView. cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Vytvořením a spuštěním aplikace ověřte, zda byla aplikace vytvořena úspěšně. Chcete-li sestavit aplikaci, v nabídce **sestavení** vyberte **sestavení řešení**. Pokud se aplikace úspěšně sestaví, spusťte ji výběrem možnosti **Spustit ladění** v nabídce **ladění** .

   Nyní byste měli vidět podrobnosti o položce vybrané v `CMFCShellTreeCtrl` podokně zobrazení. Když kliknete na uzel v `CMFCShellTreeCtrl` `CMFCShellListCtrl` , bude automaticky aktualizován. Podobně pokud dvakrát kliknete na složku v `CMFCShellListCtrl` `CMFCShellTreeCtrl` , měla by se automaticky aktualizovat.

   Pravým tlačítkem myši klikněte na libovolnou položku v ovládacím prvku stromu nebo v ovládacím prvku seznam. Dostanete stejnou kontextovou nabídku jako v případě, že jste používali skutečný **Průzkumník souborů**.

## <a name="next-steps"></a>Další kroky

- Průvodce vytvořil panel Outlooku v podokně **složky** i v podokně **kalendáře** . Pravděpodobně nemá smysl mít podokno **kalendáře** v okně **Průzkumníka** , proto toto podokno teď odeberte.

- Podporuje zobrazování souborů v různých režimech, jako jsou například velké ikony, malé ikony, seznam a podrobnosti. `CMFCShellListCtrl` Aktualizujte svou aplikaci pro implementaci této funkce. Nápověda: Podívejte se na [ukázky vizuálů C++ ](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
