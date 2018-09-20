---
title: 'Návod: Použití nového prostředí MFC prostředí ovládací prvky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 81925cfa31c394a1b307a184388fb0d331d31fdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432487"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Návod: Použití nových ovládacích prvků prostředí MFC

V tomto návodu vytvoříte aplikaci, která se podobá Průzkumníku souborů. Vytvoří okno, které obsahuje dvě podokna. V levém podokně bude obsahovat [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) objekt, který se zobrazí v hierarchické zobrazení plochy. V pravém podokně bude obsahovat [CMFCShellListCtrl –](../mfc/reference/cmfcshelllistctrl-class.md) , která zobrazuje soubory ve složce, který je vybraný v levém podokně.

## <a name="prerequisites"></a>Požadavky

Tento názorný průvodce předpokládá, že jste nastavili sady Visual Studio, používat **obecným vývojovým nastavením**. Pokud používáte jiný vývojářský nastavení, některé okna sady Visual Studio, které používáme v tomto názorném postupu nemusí být zobrazeny ve výchozím nastavení.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Chcete-li vytvořit novou aplikaci knihovny MFC pomocí Průvodce aplikací MFC

1. Použití **Průvodce aplikací knihovny MFC** k vytvoření nové aplikace knihovny MFC. Chcete-li spustit průvodce, ze **souboru** nabídky vyberte možnost **nový**a pak vyberte **projektu**. **Nový projekt** se zobrazí dialogové okno.

2. V **nový projekt** dialogového okna rozbalte **Visual C++** uzlu v **typy projektů** podokně a vyberte **MFC**. Potom v **šablony** vyberte **aplikace knihovny MFC**. Zadejte název projektu, například `MFCShellControls` a klikněte na tlačítko **OK**. **Průvodce aplikací knihovny MFC** se zobrazí.

3. V **Průvodce aplikací knihovny MFC** dialogové okno, klikněte na tlačítko **Další**. **Typ aplikace** podokně se zobrazí.

4. Na **typ aplikace** podokně v části **typ aplikace**, zrušte zaškrtnutí políčka **dokumenty na kartách** možnost. V dalším kroku vyberte **jednotlivý dokument** a vyberte **podpora architektury Document/View**. V části **projektu styl**vyberte **sady Visual Studio**a od **vizuální styl a barvy** rozevíracím seznamu vyberte **Office 2007 (modrý motiv)**. Nechte ostatní možnosti, jak jsou. Klikněte na tlačítko **Další** zobrazíte **Podpora složených dokumentů** podokně.

5. Na **Podpora složených dokumentů** vyberte **žádný**. Klikněte na tlačítko **Další** zobrazíte **řetězce šablony dokumentu** podokně.

6. Neprovádějte žádné změny **řetězce šablony dokumentu** podokně. Klikněte na tlačítko **Další** zobrazíte **Podpora databáze** podokně.

7. Na **Podpora databáze** vyberte **žádný** vzhledem k tomu, že tuto aplikaci nebude používat databázi. Klikněte na tlačítko **Další** zobrazíte **funkce uživatelského rozhraní** podokně.

8. Na **funkce uživatelského rozhraní** podokno, ujistěte se, že **použít řádek nabídek a panelů nástrojů** je vybraná možnost. Nechte ostatní možnosti, jak jsou. Klikněte na tlačítko **Další** zobrazíte **rozšířené funkce** podokně.

9. Na **rozšířené funkce** podokně v části **pokročilé funkce**, vyberte pouze **ovládací prvky ActiveX** a **běžné Manifest ovládacího prvku**. V části **rozšířená podokna rámců**, vyberte pouze **navigačním podokně** možnost. To způsobí, že průvodce vytvoří v podokně nalevo od okna s `CMFCShellTreeCtrl` již vložen. Klikněte na tlačítko **Další** zobrazíte **třídy generované v** podokně.

10. Nebudeme žádné změny k **třídy generované v** podokně. Proto klikněte na tlačítko **Dokončit** k vytvoření nového projektu knihovny MFC.

11. Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, ze **sestavení** nabídky vyberte možnost **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte aplikaci tak, že vyberete **spustit ladění** z **ladění** nabídky.

   Průvodce automaticky vytvoří aplikaci, která má standardní nabídek, standardním panelu nástrojů, standardní stavového řádku a panel aplikace Outlook k levému okraji okna s **složky** zobrazení a **kalendáře** zobrazení .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Chcete-li přidat ovládací prvek seznamu prostředí na zobrazení dokumentu

1. V této části přidáte instanci `CMFCShellListCtrl` do zobrazení, který průvodce vytvořil. Otevřete soubor záhlaví zobrazení dvojitým kliknutím MFCShellControlsView.h v **Průzkumníka řešení**.

   Vyhledejte `#pragma once` direktiv v horní části souboru hlaviček. Bezprostředně pod ní přidejte tento kód přikazující zahrnutí souboru hlaviček pro `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Nyní přidat členskou proměnnou typu `CMFCShellListCtrl`. Nejprve v hlavičkovém souboru vyhledejte následující komentář:

   ```cpp
   // Generated message map functions
   ```

   Bezprostředně nad tento komentář přidejte tento kód:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

2. **Průvodce aplikací knihovny MFC** už vytvořili `CMFCShellTreeCtrl` objekt `CMainFrame` třídy, ale je chráněný člen. Tento objekt jsme se později přístup. Proto teď vytvořte přístupový objekt pro něj. Otevřete soubor hlaviček MainFrm.h poklepáním v **Průzkumníka řešení**. Vyhledejte následující komentář:

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

3. Nyní aktualizujeme `CMFCShellControlsView` třídy pro zpracování **WM_CREATE** zpráv systému windows. Otevřete soubor hlaviček MFCShellControlsView.h a klikněte na tento řádek kódu:

    ```cpp
    class CMFCShellControlsView : public CView
    ```

   Vedle **vlastnosti** okna, klikněte na tlačítko **zprávy** ikonu. Posuňte se dolů, dokud nenajdete **WM_CREATE** zprávy. Z rozevíracího seznamu vedle **WM_CREATE**vyberte  **\<Přidat > OnCreate**. Tím se vytvoří obslužné rutiny zpráv pro nás a automaticky aktualizuje mapování zpráv knihovny MFC.

   V `OnCreate` metoda teď vytvoříme naši `CMFCShellListCtrl` objektu. Najít `OnCreate` definici metody v MFCShellControlsView.cpp zdrojového souboru a jeho implementace nahraďte následujícím kódem:

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

4. Opakujte předchozí krok, ale pro **WM_SIZE** zprávy. To způsobí, že zobrazení aplikací, aby vyžadovaly překreslení pokaždé, když uživatel změní velikost okna aplikace. Nahraďte definici `OnSize` metodu s následujícím kódem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

5. Posledním krokem je připojení `CMFCShellTreeCtrl` a `CMFCShellListCtrl` objektů pomocí [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po volání této metody `CMFCShellListCtrl` se automaticky zobrazí obsah položky vybrané v `CMFCShellTreeCtrl`. Uděláme to `OnActivateView` metodu, která je přepsána z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   V souboru hlaviček MFCShellControlsView.h uvnitř `CMFCShellControlsView` deklarace třídy, přidejte následující deklarace metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   V dalším kroku přidejte definici pro tuto metodu do zdrojového souboru MFCShellControlsView.cpp:

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

   Protože jsme se volání metod z `CMainFrame` třídy, musí přidáme `#include` direktiv v horní části souboru se zdrojovým MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

6. Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, ze **sestavení** nabídky vyberte možnost **sestavit řešení**. Je-li aplikace sestavena úspěšně, spustit tak, že **spustit ladění** z **ladění** nabídky.

   Teď byste měli vidět podrobnosti o položce vybrané `CMFCShellTreeCtrl` v podokně zobrazení. Po kliknutí na uzel v `CMFCShellTreeCtrl`, `CMFCShellListCtrl` se automaticky aktualizují. Podobně pokud dvakrát kliknete na složku, do `CMFCShellListCtrl`, `CMFCShellTreeCtrl` mají být automaticky aktualizováni.

   Klikněte pravým tlačítkem myši klikněte na libovolnou položku v ovládacím prvku stromu nebo v ovládacím prvku seznamu. Všimněte si, že dostanete stejné místní nabídce, jako kdyby jste používali skutečné Průzkumníka souborů.

## <a name="next-steps"></a>Další kroky

- Průvodce vytvoří panel aplikace Outlook s oběma **složky** podokně a **kalendáře** podokně. To pravděpodobně nemá smysl mít **kalendáře** podokno v okně Průzkumníka. Proto teď odeberte toto podokno.

- `CMFCShellListCtrl` Podporuje zobrazení souborů v různých režimech, jako například **velké ikony**, **malé ikony**, **seznamu**, a **podrobnosti**. Aktualizace aplikace pro implementaci této funkce. Tip: viz [Visual C++ – ukázky](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)
