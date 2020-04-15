---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 2)'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360231"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Návod: Aktualizace aplikace MFC Scribble (část 2)

[Část 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) tohoto návodu ukázala, jak přidat pás karet Aplikace Office Fluent do klasické aplikace Klikyháky. Tato část ukazuje, jak přidat panely pásu karet a ovládací prvky, které mohou uživatelé používat místo nabídek a příkazů.

## <a name="prerequisites"></a>Požadavky

[Visual C++ – ukázky](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>Oddíly

Tato část návodu má následující části:

- [Přidání nových panelů na pás karet](#addnewpanel)

- [Přidání panelu nápovědy na pás karet](#addhelppanel)

- [Přidání panelu pera na pás karet](#addpenpanel)

- [Přidání tlačítka Barva na pás karet](#addcolorbutton)

- [Přidání barevného člena do třídy dokumentu](#addcolormember)

- [Inicializace per a předvoleb ukládání](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>Přidání nových panelů na pás karet

Tyto kroky ukazují, jak přidat panel **zobrazení,** který obsahuje dvě zaškrtávací políčka, která řídí viditelnost panelu nástrojů a stavového řádku, a také panel **okna,** který obsahuje svisle orientované rozdělovací tlačítko, které řídí vytváření a uspořádání oken rozhraní mdi (multiple-document).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Přidání panelu Zobrazení a panelu Okno na panel pásu karet

1. Vytvořte panel `View`s názvem , který má dvě zaškrtávací políčka, která přepínají stavový řádek a panel nástrojů.

   1. Z **panelu nástrojů**přetáhněte **panel** do kategorie **Domů.** Pak přetáhněte dvě **zaškrtávací políčka** do panelu.

   1. Klepněte na panel a upravte jeho vlastnosti. Změnit **titulek** na `View`.

   1. Chcete-li upravit jeho vlastnosti, klepněte na první políčko. Změnit **ID** na `ID_VIEW_TOOLBAR` a **Titulek** na `Toolbar`.

   1. Chcete-li upravit jeho vlastnosti, klepněte na druhé políčko. Změnit **ID** na `ID_VIEW_STATUS_BAR` a **Titulek** na `Status Bar`.

1. Vytvořte panel `Window` s názvem s tlačítkem rozdělení. Když uživatel klepne na tlačítko rozdělení, v místní nabídce se zobrazí tři příkazy, které jsou již definovány v aplikaci Klikyháky.

   1. Z **panelu nástrojů**přetáhněte **panel** do kategorie **Domů.** Pak přetáhněte **tlačítko** na panel.

   1. Klepněte na panel a upravte jeho vlastnosti. Změnit **titulek** na `Window`.

   1. Klikněte na tlačítko. Změňte `Windows` **titulek** `w`na , **Klíče** na , `False`Index velkého **obrazu** na `1`a Režim **rozdělení** na . Kliknutím na tři tečky (**...**) vedle **položky nabídky** otevřete dialogové okno **Editor položek.**

   1. Kliknutím na **Přidat** třikrát přidáte tři tlačítka.

   1. Klepněte na první tlačítko a změňte `ID_WINDOW_NEW` **položku Titulek** na `New Window`položku a **ID** na .

   1. Klepněte na druhé tlačítko a změňte `ID_WINDOW_CASCADE` **položku Titulek** na `Cascade`položku a **ID** na .

   1. Klepněte na třetí tlačítko a změňte `ID_WINDOW_TILE_HORZ` **položku Titulek** na `Tile`položku a **ID** na .

1. Uložte změny a potom vytvořte a spusťte aplikaci. Měly by být zobrazeny panely **Zobrazení** a **Okna.** Kliknutím na tlačítka potvrďte, že fungují správně.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>Přidání panelu nápovědy na pás karet

Nyní můžete přiřadit dvě položky nabídky, které jsou definovány v aplikaci Klikyháky, tlačítkům pásu karet s názvem **Témata nápovědy** a **O klikyháky**. Tlačítka jsou přidána do nového panelu s názvem **Nápověda**.

### <a name="to-add-a-help-panel"></a>Přidání panelu Nápověda

1. Z **panelu nástrojů**přetáhněte **panel** do kategorie **Domů.** Pak přetáhněte dvě **tlačítka** na panel.

1. Klepněte na panel a upravte jeho vlastnosti. Změnit **titulek** na `Help`.

1. Klikněte na první tlačítko. Změňte `Help Topics` **titulek** na `ID_HELP_FINDER`a **ID** na .

1. Klikněte na druhé tlačítko. Změňte `About Scribble...` **titulek** na `ID_APP_ABOUT`a **ID** na .

1. Uložte změny a potom vytvořte a spusťte aplikaci. Měl by být zobrazen panel **nápovědy,** který obsahuje dvě tlačítka pásu karet.

   > [!IMPORTANT]
   > Po klepnutí na tlačítko **Témata nápovědy** otevře aplikace Klikyháky komprimovaný soubor nápovědy HTML (.chm) s názvem *your_project_name*chm. V důsledku toho pokud projekt není pojmenován klikyháky, je nutné přejmenovat soubor nápovědy na název projektu.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>Přidání panelu pera na pás karet

Nyní přidejte panel pro zobrazení tlačítek, která řídí tloušťku a barvu pera. Tento panel obsahuje zaškrtávací políčko, které přepíná mezi tlustými a tenkými pery. Jeho funkčnost se podobá položku nabídky **Tlustá čára** v aplikaci Klikyháky.

Původní aplikace Klikyháky umožňuje uživateli vybrat šířku pera z dialogového okna, které se zobrazí, když uživatel klepne na **šířku pera** v nabídce. Vzhledem k tomu, že panel pásu karet má dostatek místa pro nové ovládací prvky, můžete dialogové okno nahradit pomocí dvou polí se seznamem na pásu karet. Jedno pole se seznamem upravuje šířku tenkého pera a druhé pole se seznamem upravuje šířku tlustého pera.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Přidání panelu Pero a polí se seznamem na pás karet

1. Z **panelu nástrojů**přetáhněte **panel** do kategorie **Domů.** Pak přetáhněte **zaškrtávací políčko** a dvě **pole se seznamem** do panelu.

1. Klepněte na panel a upravte jeho vlastnosti. Změnit **titulek** na `Pen`.

1. Klikněte na zaškrtávací políčko. Změňte `Use Thick` **titulek** na `ID_PEN_THICK_OR_THIN`a **ID** na .

1. Klikněte na první pole se seznamem. Změňte `Thin Pen` **titulek** na `ID_PEN_THIN_WIDTH`, **ID** , **Zadejte** do `Drop List`, **Data** to `1;2;3;4;5;6;7;8;9;`a **Text** na `2`.

1. Klikněte na druhé pole se seznamem. Změňte `Thick Pen` **titulek** na `ID_PEN_THICK_WIDTH`, **ID** , **Zadejte** do `Drop List`, **Data** to `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`a **Text** na `5`.

1. Nová pole se seznamem neodpovídají žádné existující položky nabídky, takže je nutné vytvořit položku nabídky pro každou možnost pera.

   1. V okně **Zobrazení zdrojů** otevřete zdroj nabídky **IDR_SCRIBBTYPE.**

   1. Kliknutím na **Pero** otevřete nabídku pera. Potom klepněte na `Thi&n Pen`tlačítko **Zadejte sem** a zadejte .

   1. Kliknutím pravým tlačítkem myši na zadaný text otevřete okno **Vlastnosti** a změňte vlastnost ID na `ID_PEN_THIN_WIDTH`.

   1. Vytvořte obslužnou rutinu události pro každou položku nabídky pera. Klepněte pravým tlačítkem myši na položku nabídky **Thi&n Pen,** kterou jste vytvořili, a potom klepněte na příkaz **Přidat obslužnou rutinu události**. Zobrazí se **Průvodce obslužnou rutinou události.**

   1. V seznamu **Třída** v průvodci vyberte **CScribbleDoc** a pak klepněte na tlačítko **Přidat a upravit**. Příkaz vytvoří obslužnou rutinu události s názvem `CScribbleDoc::OnPenThinWidth`.

   1. Přidejte následující kód do `CScribbleDoc::OnPenThinWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Dále vytvořte položku nabídky a obslužné rutiny událostí pro tlusté pero.

   1. V okně **Zobrazení zdrojů** otevřete zdroj nabídky **IDR_SCRIBBTYPE.**

   1. Kliknutím na **Pero** otevřete nabídku pera. Potom klepněte na `Thic&k Pen`tlačítko **Zadejte sem** a zadejte .

   1. Kliknutím pravým tlačítkem myši na zadaný text zobrazíte okno **Vlastnosti.** Změňte vlastnost ID na `ID_PEN_THICK_WIDTH`.

   1. Klepněte pravým tlačítkem myši na položku nabídky **Silné pero,** kterou jste vytvořili, a potom klepněte na příkaz **Přidat obslužnou rutinu události**. Zobrazí se **Průvodce obslužnou rutinou události.**

   1. V **seznamu Třída** průvodce vyberte **CScribbleDoc** a klepněte na tlačítko **Přidat a upravit**. Příkaz vytvoří obslužnou rutinu události s názvem `CScribbleDoc::OnPenThickWidth`.

   1. Přidejte následující kód do `CScribbleDoc::OnPenThickWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Uložte změny a potom vytvořte a spusťte aplikaci. Měla by být zobrazena nová tlačítka a pole se seznamem. Zkuste pro klikyháky použít různé šířky pera.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>Přidání tlačítka Barvy do panelu Pero

Dále přidejte objekt [CMFCRibbonColorButton,](../mfc/reference/cmfcribboncolorbutton-class.md) který umožňuje uživateli čmárat barevně.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Přidání tlačítka barvy do panelu Pero

1. Před přidáním tlačítka barva pro něj vytvořte položku nabídky. V okně **Zobrazení zdrojů** otevřete zdroj nabídky **IDR_SCRIBBTYPE.** Klepnutím na položku nabídky **Pero** otevřete nabídku pera. Potom klepněte na `&Color`tlačítko **Zadejte sem** a zadejte . Kliknutím pravým tlačítkem myši na zadaný text zobrazíte okno **Vlastnosti.** Změňte ID `ID_PEN_COLOR`na .

1. Nyní přidejte tlačítko barvy. Z **panelu nástrojů**přetáhněte **tlačítko Barva** do panelu **Pero.**

1. Klikněte na tlačítko barva. Změňte `Color` **titulek** na `ID_PEN_COLOR`, **ID** na , `1` **Jednoduchý pohled** na `True`, **Index velkého obrazu** na a Režim **rozdělení** na `False`.

1. Uložte změny a potom vytvořte a spusťte aplikaci. Nové tlačítko barvy by se mělo zobrazit na panelu **Pero.** Nelze jej však použít, protože ještě nemá obslužnou rutinu události. Další kroky ukazují, jak přidat obslužnou rutinu události pro tlačítko barva.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>Přidání barevného člena do třídy dokumentu

Vzhledem k tomu, že původní aplikace Klikyháky nemá barevná pera, musíte pro ně napsat implementaci. Chcete-li uložit barvu pera dokumentu, přidejte do `CscribbleDoc`třídy dokumentu nový člen .

### <a name="to-add-a-color-member-to-the-document-class"></a>Přidání barevného člena do třídy dokumentu

1. V scribdoc.h, `CScribbleDoc` ve třídě, `// Attributes` najděte sekci. Za definici `m_nThickWidth` datového člena přidejte následující řádky kódu.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Každý dokument obsahuje seznam stokes, které uživatel již nakreslil. Každý tah je `CStroke` definován objektem. Třída `CStroke` neobsahuje informace o barvě pera, takže je nutné třídu upravit. V scribdoc.h, `CStroke` ve třídě, přidejte následující řádky kódu `m_nPenWidth` za definici datového člena.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. V souboru scribdoc.h `CStroke` přidejte nový konstruktor, jehož parametry určují šířku a barvu. Za `CStroke(UINT nPenWidth);` příkaz přidejte následující řádek kódu.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. V scribdoc.cpp přidejte implementaci `CStroke` nového konstruktoru. Přidejte následující kód po `CStroke::CStroke(UINT nPenWidth)` implementaci konstruktoru.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Změňte druhý řádek `CStroke::DrawStroke` metody následujícím způsobem.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Nastavte výchozí barvu pera pro třídu dokumentu. V souboru scribdoc.cpp přidejte `CScribbleDoc::InitDocument`za `m_nThickWidth = 5;` příkaz následující řádky .

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. V scribdoc.cpp změňte první `CScribbleDoc::NewStroke` řádek metody na následující.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Změňte poslední řádek `CScribbleDoc::ReplacePen` metody na následující.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Člen jste `m_penColor` přidali v předchozím kroku. Nyní vytvořte obslužnou rutinu události pro tlačítko barvy, které nastaví člen.

   1. V okně **Zobrazení zdrojů** otevřete zdroj nabídky IDR_SCRIBBTYPE.

   1. Klepněte pravým tlačítkem myši na položku nabídky **Barva** a klepněte na příkaz **Přidat obslužnou rutinu události**. Zobrazí se **Průvodce obslužnou rutinou události.**

   1. V **seznamu Třída** v průvodci vyberte **CScribbleDoc** a klikněte na tlačítko **Přidat a upravit.** Příkaz vytvoří `CScribbleDoc::OnPenColor` zástupný kód obslužné rutiny události.

1. Nahraďte zástupný `CScribbleDoc::OnPenColor` kód pro obslužnou rutinu události následujícím kódem.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. Uložte změny a potom vytvořte a spusťte aplikaci. Nyní můžete stisknout tlačítko barvy a změnit barvu pera.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>Inicializace per a předvoleb ukládání

Dále inicializujte barvu a šířku per. Nakonec uložte a načtěte barevný výkres ze souboru.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Inicializaci ovládacích prvků na panelu karet

1. Inicializovat pera na pruhu pásu karet.

   Přidejte následující kód do scribdoc.cpp, v metodě, `CScribbleDoc::InitDocument` za `m_sizeDoc = CSize(200,200)` příkaz.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. Uložte barevný výkres do souboru. Přidejte následující příkaz do scribdoc.cpp, v metodě, `CStroke::Serialize` za `ar << (WORD)m_nPenWidth;` příkaz.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Nakonec načtěte barevný výkres ze souboru. Přidejte následující řádek kódu `CStroke::Serialize` v metodě `m_nPenWidth = w;` za příkaz.

   ```cpp
   ar >> m_penColor;
   ```

1. Nyní klikyháky v barvě a uložit výkres do souboru.

## <a name="conclusion"></a>Závěr

Aktualizovali jste aplikaci MFC Scribble. Tento návod použijte jako vodítko při úpravách existujících aplikací.

## <a name="see-also"></a>Viz také

[Postupy](../mfc/walkthroughs-mfc.md)<br/>
[Návod: Aktualizace aplikace MFC Scribble (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
