---
title: 'Návod: Použití nových ovládacích prvků prostředí MFC'
ms.date: 09/20/2018
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: ef0e4856a844503f8d13b7b6ed37318b76b6af69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358174"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Návod: Použití nových ovládacích prvků prostředí MFC

V tomto návodu vytvoříte aplikaci, která se podobá Průzkumníku souborů. Vytvoříte okno, které obsahuje dvě podokna. V levém podokně se uloží [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objekt, který se zobrazí v hierarchické zobrazení plochy. V pravém podokně se uloží [CMFCShellListCtrl –](../mfc/reference/cmfcshelllistctrl-class.md) , která zobrazuje soubory ve složce, který je vybraný v levém podokně.

## <a name="prerequisites"></a>Požadavky

Tento názorný průvodce předpokládá, že jste nastavili sady Visual Studio, používat **obecným vývojovým nastavením**. Pokud používáte jiný vývojářský nastavení, některé okna sady Visual Studio, které používáme v tomto názorném postupu nemusí být zobrazeny ve výchozím nastavení.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Chcete-li vytvořit novou aplikaci knihovny MFC pomocí Průvodce aplikací MFC

1. Použití **Průvodce aplikací knihovny MFC** k vytvoření nové aplikace knihovny MFC. Chcete-li spustit průvodce, ze **souboru** nabídky vyberte možnost **nový**a pak vyberte **projektu**. **Nový projekt** se zobrazí dialogové okno.

1. V **nový projekt** dialogového okna rozbalte **Visual C++** uzlu v **typy projektů** podokně a vyberte **MFC**. Potom v **šablony** vyberte **aplikace knihovny MFC**. Zadejte název projektu, například `MFCShellControls` a klikněte na tlačítko **OK**. Po **Průvodce aplikací knihovny MFC** zobrazí, pomocí následujících možností:

    1. Na **typ aplikace** podokně v části **typ aplikace**, zrušte zaškrtnutí políčka **dokumenty na kartách** možnost. V dalším kroku vyberte **jednotlivý dokument** a vyberte **podpora architektury Document/View**. V části **projektu styl**vyberte **sady Visual Studio**a od **vizuální styl a barvy** rozevíracím seznamu vyberte **Office 2007 (modrý motiv)**.

    1. Na **Podpora složených dokumentů** vyberte **žádný**.

    1. Neprovádějte žádné změny k **řetězce šablony dokumentu** podokně.

    1. Na **Podpora databáze** podokně (Visual Studio 2015 a starší), vyberte **žádný** vzhledem k tomu, že aplikace nepoužívá databázi.

    1. Na **funkce uživatelského rozhraní** podokno, ujistěte se, že **použít řádek nabídek a panelů nástrojů** je vybraná možnost. Nechte ostatní možnosti, jak jsou.

    1. Na **rozšířené funkce** podokně v části **pokročilé funkce**, vyberte pouze **ovládací prvky ActiveX** a **běžné Manifest ovládacího prvku**. V části **rozšířená podokna rámců**, vyberte pouze **navigačním podokně** možnost. To způsobí, že průvodce vytvoří v podokně nalevo od okna s `CMFCShellTreeCtrl` již vložen.

    1. Nebudeme žádné změny k **třídy generované v** podokně, klikněte na tlačítko Ano **Dokončit** k vytvoření nového projektu knihovny MFC.

1. Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, ze **sestavení** nabídky vyberte možnost **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte aplikaci tak, že vyberete **spustit ladění** z **ladění** nabídky.

   Průvodce automaticky vytvoří aplikaci, která má standardní nabídek, standardním panelu nástrojů, standardní stavového řádku a panel aplikace Outlook k levému okraji okna s **složky** zobrazení a **kalendáře** zobrazení .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Chcete-li přidat ovládací prvek seznamu prostředí na zobrazení dokumentu

1. V této části přidáte instanci `CMFCShellListCtrl` do zobrazení, který průvodce vytvořil. Dvojitým kliknutím otevřete soubor záhlaví zobrazení **MFCShellControlsView.h** v **Průzkumníka řešení**.

   Vyhledejte `#pragma once` direktiv v horní části souboru hlaviček. Bezprostředně pod ní přidejte tento kód přikazující zahrnutí souboru hlaviček pro `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Nyní přidat členskou proměnnou typu `CMFCShellListCtrl`. Nejprve v hlavičkovém souboru vyhledejte následující komentář:

   ```cpp
   // Generated message map functions
   ```

   Bezprostředně nad tento komentář, přidejte tento kód:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Průvodce aplikací knihovny MFC** už vytvořili `CMFCShellTreeCtrl` objekt `CMainFrame` třídy, ale je chráněný člen. Jsme budete později přístup k objektu, takže teď vytvořte přístupový objekt pro něj. Otevřete soubor hlaviček MainFrm.h poklepáním v **Průzkumníka řešení**. Vyhledejte následující komentář:

   ```cpp
   // Attributes
   ```

   Bezprostředně pod ním, přidejte následující deklarace metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Dále otevřete zdrojový soubor MainFrm.cpp poklepáním v **Průzkumníka řešení**. V dolní části tohoto souboru přidejte následující definici metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Nyní aktualizujeme `CMFCShellControlsView` třídy pro zpracování `WM_CREATE` zpráv systému windows. Otevřít **zobrazení tříd** okna a vyberte `CMFCShellControlsView` třídy. Klikněte pravým tlačítkem a vyberte **vlastnosti**.

    Vedle **vlastnosti** okna, klikněte na tlačítko **zprávy** ikonu. Posuňte se dolů, dokud nenajdete `WM_CREATE` zprávy. Z rozevíracího seznamu vedle položky `WM_CREATE`vyberte  **\<Přidat > OnCreate**. Příkaz vytvoří obslužné rutiny zpráv pro nás a automaticky aktualizuje mapování zpráv knihovny MFC.

   V `OnCreate` metoda, vytvoříme teď naše `CMFCShellListCtrl` objektu. Najít `OnCreate` definici metody v MFCShellControlsView.cpp zdrojového souboru a jeho implementace nahraďte následujícím kódem:

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

1. Opakujte předchozí krok, ale pro `WM_SIZE` zprávy. To způsobí, že zobrazení aplikací, aby vyžadovaly překreslení pokaždé, když uživatel změní velikost okna aplikace. Nahraďte definici `OnSize` metodu s následujícím kódem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Posledním krokem je připojení `CMFCShellTreeCtrl` a `CMFCShellListCtrl` objektů pomocí [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po zavolání `CMFCShellTreeCtrl::SetRelatedList`, `CMFCShellListCtrl` se automaticky zobrazí obsah položky vybrané v `CMFCShellTreeCtrl`. Objekty v se nám připojit `OnActivateView` metodu, která je přepsána z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   V souboru hlaviček MFCShellControlsView.h uvnitř `CMFCShellControlsView` deklarace třídy, přidejte následující deklarace metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   V dalším kroku přidejte definici pro metodu do zdrojového souboru MFCShellControlsView.cpp:

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

   Protože voláme metody ze `CMainFrame` třídy, musí přidáme `#include` direktiv v horní části souboru se zdrojovým MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, ze **sestavení** nabídky vyberte možnost **sestavit řešení**. Je-li aplikace sestavena úspěšně, spustit tak, že **spustit ladění** z **ladění** nabídky.

   Teď byste měli vidět podrobnosti o položce vybrané `CMFCShellTreeCtrl` v podokně zobrazení. Po kliknutí na uzel v `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se automaticky aktualizují. Podobně pokud dvakrát kliknete na složku, do `CMFCShellListCtrl`, `CMFCShellTreeCtrl` mají být automaticky aktualizováni.

   Klikněte pravým tlačítkem na libovolnou položku v ovládacím prvku stromu nebo v ovládacím prvku seznamu. Získáte stejné místní nabídce, jako kdyby jste používali skutečné **Průzkumníka souborů**.

## <a name="next-steps"></a>Další kroky

- Průvodce vytvoří panel aplikace Outlook s oběma **složky** podokně a **kalendáře** podokně. Pravděpodobně nemá smysl mít **kalendáře** v podokně **Explorer** okno, proto teď odebrat toto podokno.

- `CMFCShellListCtrl` Podporuje zobrazení souborů v různých režimech, jako například **velké ikony**, **malé ikony**, **seznamu**, a **podrobnosti**. Aktualizace aplikace pro implementaci této funkce. Tip: viz [Visual C++ – ukázky](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
