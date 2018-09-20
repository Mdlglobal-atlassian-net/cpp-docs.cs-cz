---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 2) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 351aea09376d6cba7f091828225fd337fa3f68e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423154"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Návod: Aktualizace aplikace MFC Scribble (část 2)

[Část 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) tohoto návodu jsme si ukázali, jak přidat pásu karet Office Fluent classic Scribble aplikace. Tato část ukazuje, jak přidat panely pásu karet a ovládacích prvků, které uživatelé můžou používat místo nabídek a příkazů.

## <a name="prerequisites"></a>Požadavky

[Visual C++ – ukázky](../visual-cpp-samples.md)

##  <a name="top"></a> Oddíly

Tato část návodu obsahuje následující oddíly:

- [Přidávání nových panelů pásu karet](#addnewpanel)

- [Přidání Panel nápovědy na pás karet](#addhelppanel)

- [Přidání panelu Pero na pás karet](#addpenpanel)

- [Přidání barvy tlačítka na pás karet](#addcolorbutton)

- [Přidává se člen barvu pro třídy dokumentu](#addcolormember)

- [Inicializace pera a ukládání předvoleb](#initpensave)

##  <a name="addnewpanel"></a> Přidávání nových panelů pásu karet

Tyto kroky ukazují, jak přidat **zobrazení** panel, který obsahuje dvě zaškrtávací políčka, která řídí viditelnost panelu nástrojů a stavový řádek, a také **okno** panel, který obsahuje svisle orientovaný rozdělení tlačítko, které řídí vytváření a uspořádání oken rozhraní více dokumentů (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Chcete-li přidat panel zobrazení a panely okno na panel pásu karet

1. Vytvořit panel s názvem `View`, která má dvě zaškrtávací políčka, které přepnout stavový řádek a nástrojů.

   1. Z **nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Potom přetáhněte dva **zaškrtávací políčka** do panelu.

   2. Klikněte na panel k úpravě jeho vlastností. Změna **titulek** k `View`.

   3. Klikněte na první zaškrtávací políčko k úpravě jeho vlastností. Změna **ID** k `ID_VIEW_TOOLBAR` a **titulek** k `Toolbar`.

   4. Klikněte na druhý zaškrtávací políčko k úpravě jeho vlastností. Změna **ID** k `ID_VIEW_STATUS_BAR` a **titulek** k `Status Bar`.

2. Vytvořit panel s názvem `Window` , který má tlačítko rozdělení. Když uživatel klikne na tlačítko rozdělení, zobrazí místní nabídka tři příkazy, které jsou již definovány v aplikaci Scribble.

   1. Z **nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Potom přetáhněte **tlačítko** do panelu.

   2. Klikněte na panel k úpravě jeho vlastností. Změna **titulek** k `Window`.

   3. Klikněte na tlačítko. Změna **titulek** k `Windows`, **klíče** k `w`, **Index velkého obrázku** k `1`, a **rozdělený režim** k `False`. Pak klikněte na tlačítko se třemi tečkami (**...** ) vedle položky **položky nabídky** otevřít **Editor položek** dialogové okno.

   4. Klikněte na tlačítko **přidat** třikrát přidáte tři tlačítka.

   5. Klikněte na první tlačítko a pak změňte **titulek** k `New Window`, a **ID** k `ID_WINDOW_NEW`.

   6. Klikněte na druhé tlačítko a pak změňte **titulek** k `Cascade`, a **ID** k `ID_WINDOW_CASCADE`.

   7. Klikněte na třetí tlačítko a pak změňte **titulek** k `Tile`, a **ID** k `ID_WINDOW_TILE_HORZ`.

3. Uložte změny a potom sestavíte a spustíte aplikaci. **Zobrazení** a **okno** panelů by se mělo zobrazit. Klikněte na tlačítko potvrďte, že správně fungují.

[[Oddíly](#top)]

##  <a name="addhelppanel"></a> Přidání Panel nápovědy na pás karet

Teď můžete přiřadit dvě položky nabídky, které jsou definovány v aplikaci Scribble tlačítek na pásu karet, které jsou pojmenovány **témata nápovědy** a **o Scribble**. Tlačítka jsou přidány do nového panelu s názvem **pomáhají**.

### <a name="to-add-a-help-panel"></a>Chcete-li přidat panel nápovědy

1. Z **nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Potom přetáhněte dva **tlačítka** do panelu.

2. Klikněte na panel k úpravě jeho vlastností. Změna **titulek** k `Help`.

3. Klikněte na první tlačítko. Změna **titulek** k `Help Topics`, a **ID** k `ID_HELP_FINDER`.

4. Klikněte na druhé tlačítko. Změna **titulek** k `About Scribble...`, a **ID** k `ID_APP_ABOUT`.

5. Uložte změny a potom sestavíte a spustíte aplikaci. A **pomáhají** by se mělo zobrazit panel, který obsahuje dvě tlačítka pásu karet.

   > [!IMPORTANT]
   > Když kliknete **témata nápovědy** tlačítko, otevře se aplikace Scribble komprimovaný soubor nápovědy HTML (CHM) s názvem *your_project_name*. chm. V důsledku toho pokud váš projekt nejmenuje Scribble, třeba přejmenovat soubor nápovědy na název vašeho projektu.

[[Oddíly](#top)]

##  <a name="addpenpanel"></a> Přidání panelu Pero na pás karet

Teď přidejte panel pro zobrazení tlačítka, která řídí tloušťku a barvu pera. Tento panel obsahuje zaškrtávací políčko, přepne mezi silné a dynamicky pera. Funkčnost vypadá podobně jako u **tlustá čára** položky nabídky v aplikaci Scribble.

Původní aplikace Scribble umožní uživateli vybrat šířku pera z dialogového okna, která se zobrazí, když uživatel klikne **šířku pera** v nabídce. Vzhledem k tomu, že na pásu karet má dostatek místa pro nové ovládací prvky, můžete nahradit dialogových oken pomocí dvou polích se seznamem na pásu karet. Jedno pole se seznamem upraví šířku pera dynamického zajišťování a ostatní pole se seznamem upraví šířku tlustých pera.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Chcete-li přidat panel pera a pole se seznamem polí na pás karet

1. Z **nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Potom přetáhněte **zaškrtávací políčko** a dva **polích se seznamem** do panelu.

2. Klikněte na panel k úpravě jeho vlastností. Změna **titulek** k `Pen`.

3. Klikněte na zaškrtávací políčko. Změna **titulek** k `Use Thick`, a **ID** k `ID_PEN_THICK_OR_THIN`.

4. Klikněte na první pole se seznamem. Změna **titulek** k `Thin Pen`, **ID** k `ID_PEN_THIN_WIDTH`, **Text** k `2`, **typ** k `Drop List`, a **Data** k `1;2;3;4;5;6;7;8;9;`.

5. Klikněte na druhé pole se seznamem. Změna **titulek** k `Thick Pen`, **ID** k `ID_PEN_THICK_WIDTH`, **Text** k `5`, **typ** k `Drop List`, a **Data** k `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`.

6. Nová pole se seznamem nemusí odpovídat všechny stávající položky nabídky. Proto musíte vytvořit položku nabídky pro všechny dostupné možnosti pera.

   1. V **zobrazení prostředků** okně otevřete prostředek IDR_SCRIBBTYPE nabídky.

   2. Klikněte na tlačítko **pera** otevřít p**en** nabídky. Pak klikněte na tlačítko **typu tady** a typ `Thi&n Pen`.

   3. Klikněte pravým tlačítkem na text, který jste právě zadali, otevřete **vlastnosti** intervalu a poté změnit ID vlastnosti `ID_PEN_THIN_WIDTH`.

   4. Musíte také vytvořit obslužnou rutinu události pro každou položku nabídky pera. Klikněte pravým tlačítkem myši **tent & n pera** položku nabídky, který jste právě vytvořili a klikněte na **přidat obslužnou rutinu události**. **Průvodce obslužnou rutinou události** se zobrazí.

   5. V **seznamu tříd** pole v průvodci vyberte **CScribbleDoc** a potom klikněte na tlačítko **přidávat a upravovat**. Tím se vytvoří obslužnou rutinu události s názvem `CScribbleDoc::OnPenThinWidth`.

   6. Přidejte následující kód, který `CScribbleDoc::OnPenThinWidth`.

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
        m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));
    }

    // Create a new pen using the selected width
    ReplacePen();
    ```

7. Dále vytvořte nabídku položky a událost obslužné rutiny pro silné pera.

   1. V **zobrazení prostředků** okně otevřete prostředek IDR_SCRIBBTYPE nabídky.

   2. Klikněte na tlačítko **pera** otevřete nabídku pera. Pak klikněte na tlačítko **typu tady** a typ `Thic&k Pen`.

   3. Klikněte pravým tlačítkem na text, který jste právě zadali zobrazíte **vlastnosti** okna. Změnit vlastnosti ID na `ID_PEN_THICK_WIDTH`.

   4. Klikněte pravým tlačítkem na **silný pera** položku nabídky, který jste právě vytvořili a klikněte na **přidat obslužnou rutinu události**. **Průvodce obslužnou rutinou události** se zobrazí.

   5. V **seznamu tříd** pole v průvodci vyberte **CScribbleDoc** a potom klikněte na tlačítko **přidávat a upravovat**. Tím se vytvoří obslužnou rutinu události s názvem `CScribbleDoc::OnPenThickWidth`.

   6. Přidejte následující kód, který `CScribbleDoc::OnPenThickWidth`.

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
          m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));
      }

      // Create a new pen using the selected width
      ReplacePen();
      ```

8. Uložte změny a potom sestavíte a spustíte aplikaci. Nová tlačítka a pole se seznamem má být zobrazena. Zkuste použít jiné pero šířky zvyklí.

[[Oddíly](#top)]

##  <a name="addcolorbutton"></a> Přidání barevné tlačítko na panelu pera

V dalším kroku přidejte [cmfcribboncolorbutton –](../mfc/reference/cmfcribboncolorbutton-class.md) objekt, který umožňuje uživateli scribble barvou.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Chcete-li přidat barevné tlačítko panelu pera

1. Před přidáním bude tlačítko barev pro ni vytvořte položku nabídky. V **zobrazení prostředků** okně otevřete prostředek IDR_SCRIBBTYPE nabídky. Klikněte na tlačítko **pera** položky nabídky a otevřete nabídku pera. Pak klikněte na tlačítko **typu tady** a typ `&Color`. Klikněte pravým tlačítkem na text, který jste právě zadali zobrazíte **vlastnosti** okna. ID se má změnit `ID_PEN_COLOR`.

2. Nyní přidejte bude tlačítko barev. Z **nástrojů**, přetáhněte **barva – tlačítko** k **pera** panelu.

3. Klikněte na tlačítko barvy. Změna **titulek** k `Color`, **ID** k `ID_PEN_COLOR`, **SimpleLook** k `True`, **Index velkého obrázku** do `1`, a **rozdělený režim** k `False`.

4. Uložte změny a potom sestavíte a spustíte aplikaci. Tlačítko Barva má být zobrazena na **pera** panelu. Ale jej nelze použít, protože ještě nemá obslužné rutiny události. Následující kroky ukazují, jak přidat obslužnou rutinu události pro tlačítko barvy.

[[Oddíly](#top)]

##  <a name="addcolormember"></a> Přidává se člen barvu pro třídy dokumentu

Protože původní aplikace Scribble nemá Barva pera, musíte napsat implementaci pro ně. K ukládání Barva pera dokumentu, přidání nového člena do třídy dokumentu `CscribbleDoc.`

### <a name="to-add-a-color-member-to-the-document-class"></a>Přidat barvu člena třídy dokumentu

1. V scribdoc.h v `CScribbleDoc` třídy, vyhledejte `// Attributes` oddílu. Přidejte následující řádky kódu po definování `m_nThickWidth` datový člen.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

2. Každý dokument obsahuje seznam stokes, že má uživatel již vykreslen. Každý tah je definován `CStroke` objektu. `CStroke` Třída neobsahuje informace o barvu pera. Proto je třeba upravit třídu. V scribdoc.h v `CStroke` třídy, přidejte následující řádky kódu po definování `m_nPenWidth` datový člen.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

3. V scribdoc.h, přidejte novou `CStroke` konstruktor, jehož parametry zadejte šířku a barvu. Přidejte následující řádek kódu po `CStroke(UINT nPenWidth);` příkazu.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

4. V scribdoc.cpp, přidejte implementaci nového `CStroke` konstruktoru. Přidejte následující kód za implementaci `CStroke::CStroke(UINT nPenWidth)` konstruktoru.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

5. Změňte druhý řádek `CStroke::DrawStroke` metodu následujícím způsobem.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

6. Nastavte výchozí barva pera třídy dokumentu. V scribdoc.cpp, přidejte následující řádky do `CScribbleDoc::InitDocument`, poté, co `m_nThickWidth = 5;` příkazu.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

7. V scribdoc.cpp, změnit první řádek `CScribbleDoc::NewStroke` metoda pro následující.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

8. Změňte poslední řádek `CScribbleDoc::ReplacePen` metoda pro následující.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

9. Jste přidali `m_penColor` člena v předchozím kroku. Teď vytvořte obslužnou rutinu události pro tlačítko barvy, které nastaví člena.

   1. V **zobrazení prostředků** okně otevřete prostředek IDR_SCRIBBTYPE nabídky.

   2. Klikněte pravým tlačítkem **barva** položky nabídky a klikněte na tlačítko **přidat obslužnou rutinu události**. **Průvodce obslužnou rutinou události** se zobrazí.

   3. V **seznamu tříd** pole v průvodci vyberte **CScribbleDoc** a potom klikněte na tlačítko **přidávat a upravovat** tlačítko. Tím se vytvoří `CScribbleDoc::OnPenColor` zástupnou proceduru obslužné rutiny události.

10. Nahraďte zástupné procedury pro `CScribbleDoc::OnPenColor` obslužné rutiny události s následujícím kódem.

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

11. Uložte změny a potom sestavíte a spustíte aplikaci. Je třeba stiskněte tlačítko barvy a změnit barvu pera.

[[Oddíly](#top)]

##  <a name="initpensave"></a> Inicializace pera a ukládání předvoleb

V dalším kroku inicializujte barvu a šířku pera. A konečně uložit a načíst barvu ze souboru výkresu.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Chcete-li inicializovat ovládací prvky na panelu pásu karet

1. Inicializujte pera na panelu pásu karet.

   Přidejte následující kód k scribdoc.cpp, v `CScribbleDoc::InitDocument` metoda, poté, co `m_sizeDoc = CSize(200,200)` příkazu.

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

2. Uložte barvy vykreslování do souboru. Přidejte následující příkaz, kterým scribdoc.cpp, v `CStroke::Serialize` metoda, poté, co `ar << (WORD)m_nPenWidth;` příkazu.

   ```cpp
   ar << (COLORREF)m_penColor;
    ```

3. Nakonec načtěte barvu ze souboru výkresu. Přidejte následující řádek kódu, v `CStroke::Serialize` metoda, poté, co `m_nPenWidth = w;` příkazu.

   ```cpp
   ar >> m_penColor;
   ```

4. Nyní scribble barevně a uložit do souboru výkresu.

[[Oddíly](#top)]

## <a name="conclusion"></a>Závěr

Aplikace MFC Scribble aktualizována. Pomocí tohoto průvodce použijte jako vodítko při úpravě stávající aplikace.

## <a name="see-also"></a>Viz také

[Návody](../mfc/walkthroughs-mfc.md)<br/>
[Návod: Aktualizace aplikace MFC Scribble (část 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
