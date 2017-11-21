---
title: "Návod: Aktualizace aplikace MFC Scribble (část 2) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4213bcc0321749ddda1ee0b85f577b01044bfc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Návod: Aktualizace aplikace MFC Scribble (část 2)
[Část 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) Tento průvodce vám ukázal, jak přidat Office Fluent Ribbon do classic Klikyháky aplikace. Tato část popisuje postup pro přidání panelů pásu karet a ovládacích prvků, které uživatelé můžou použít místo nabídek a příkazů.  
  
## <a name="prerequisites"></a>Požadavky  
 [Visual C++ – ukázky](../visual-cpp-samples.md)  
  
##  <a name="top"></a>Oddíly  
 Tato část průvodce obsahuje následující části:  
  
- [Přidávání nových panelů na pásu karet](#addnewpanel)  
  
- [Přidávání panelů nápovědy na pásu karet](#addhelppanel)  
  
- [Přidávání panelů pera na pásu karet](#addpenpanel)  
  
- [Přidání tlačítka Barva na pásu karet](#addcolorbutton)  
  
- [Přidání člena barvu k třídě dokumentů](#addcolormember)  
  
- [Inicializace pera a ukládání předvoleb](#initpensave)  
  
##  <a name="addnewpanel"></a>Přidávání nových panelů na pásu karet  
 Tyto kroky ukazují, jak přidat **zobrazení** panel, který obsahuje dvě zaškrtávací políčka, která řídí viditelnost panelu nástrojů a na stavovém řádku, a také **okno** panel, který obsahuje svisle orientované rozdělení tlačítko, které řídí vytváření a uspořádání systému windows, rozhraní více dokumentů (MDI).  
  
#### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>K přidání panelů zobrazení a oken panelech na panelu pásu karet  
  
1.  Vytvořit panel s názvem `View`, která má dva políček, která přepnutí stavového řádku a panelu nástrojů.  
  
    1.  Z **sada nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Přetáhněte dvě **zaškrtávací políčka** do panelu.  
  
    2.  Klikněte na panel, který chcete upravit její vlastnosti. Změna **popisek** k `View`.  
  
    3.  Klikněte na první zaškrtávací políčko, chcete-li upravit jeho vlastnosti. Změna **ID** k `ID_VIEW_TOOLBAR` a **popisek** k `Toolbar`.  
  
    4.  Klikněte na tlačítko Upravit její vlastnosti, druhý zaškrtnutím políčka. Změna **ID** k `ID_VIEW_STATUS_BAR` a **popisek** k `Status Bar`.  
  
2.  Vytvořit panel s názvem `Window` s tlačítko rozdělení. Když uživatel klikne na tlačítko rozdělení, zobrazí místní nabídka tři příkazy, které jsou již definováni v aplikaci Scribble.  
  
    1.  Z **sada nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Přetáhněte **tlačítko** do panelu.  
  
    2.  Klikněte na panel, který chcete upravit její vlastnosti. Změna **popisek** k `Window`.  
  
    3.  Klikněte na tlačítko. Změna **popisek** k `Windows`, **klíče** k `w`, **velký obrázek indexu** k `1`, a **rozdělení režimu** k `False`. Pak klikněte na tlačítko se třemi tečkami (**...** ) vedle **položky nabídky** otevřete **položky Editor** dialogové okno.  
  
    4.  Klikněte na tlačítko **přidat** třikrát přidat tři tlačítka.  
  
    5.  Klikněte na první tlačítko a poté změňte **popisek** k `New Window`, a **ID** k `ID_WINDOW_NEW`.  
  
    6.  Klikněte na tlačítko druhý a poté změňte **popisek** k `Cascade`, a **ID** k `ID_WINDOW_CASCADE`.  
  
    7.  Klikněte na tlačítko třetí a poté změňte **popisek** k `Tile`, a **ID** k `ID_WINDOW_TILE_HORZ`.  
  
3.  Uložte změny a sestavte a spusťte aplikaci. **Zobrazení** a **okno** panelů má být zobrazen. Pomocí tlačítek potvrďte, že fungují správně.  
  
 [[Části](#top)]  
  
##  <a name="addhelppanel"></a>Přidávání panelů nápovědy na pásu karet  
 Nyní můžete přiřadit dvě položky nabídky, které jsou definovány v aplikaci Scribble tlačítka pásu karet, které jsou s názvem **témata nápovědy** a **o Klikyháky**. Tlačítka se přidají do nových panelů s názvem **pomoci**.  
  
#### <a name="to-add-a-help-panel"></a>K přidání panelu nápovědy  
  
1.  Z **sada nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Přetáhněte dvě **tlačítka** do panelu.  
  
2.  Klikněte na panel, který chcete upravit její vlastnosti. Změna **popisek** k `Help`.  
  
3.  Klikněte na první tlačítko. Změna **popisek** k `Help Topics`, a **ID** k `ID_HELP_FINDER`.  
  
4.  Klikněte na tlačítko druhý. Změna **popisek** k `About Scribble...`, a **ID** k `ID_APP_ABOUT`.  
  
5.  Uložte změny a sestavte a spusťte aplikaci. A **pomoci** má být zobrazen panel, který obsahuje dvě tlačítka pásu karet.  
  
    > [!IMPORTANT]
    >  Když kliknete **témata nápovědy** tlačítko aplikace Scribble otevře komprimovaný soubor nápovědy HTML (CHM.) s názvem *your_project_name*. chm. V důsledku toho pokud váš projekt nejmenuje Scribble, je třeba přejmenovat soubor nápovědy na název projektu.  
  
 [[Části](#top)]  
  
##  <a name="addpenpanel"></a>Přidávání panelů pera na pásu karet  
 Nyní přidejte panel pro zobrazení tlačítka, která řídí tloušťka a barvy pera. Tento panel obsahuje zaškrtávací políčko, které přepíná mezi pera silné a dynamické. Jeho funkce podobá se **konvenčním řádku** položky nabídky v aplikaci Scribble.  
  
 Původní Scribble aplikace umožňuje uživateli vybrat pera šířek z dialogu, který se zobrazí, když uživatel klikne na **pera šířek** v nabídce. Protože panelu pásu karet má dostatečným místo pro nové ovládací prvky, můžete nahradit dialogové okno s použitím dvě pole se seznamem na pásu karet. Jednoho pole se seznamem upraví šířku dynamické pera a další pole se seznamem upraví šířku silných pera.  
  
#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Chcete-li přidat pera panely a pole se seznamem polí na pásu karet  
  
1.  Z **sada nástrojů**, přetáhněte **Panel** k **Domů** kategorie. Přetáhněte **políčko** a dvě **pole se seznamem** do panelu.  
  
2.  Klikněte na panel, který chcete upravit její vlastnosti. Změna **popisek** k `Pen`.  
  
3.  Klikněte na zaškrtávací políčko. Změna **popisek** k `Use Thick`, a **ID** k `ID_PEN_THICK_OR_THIN`.  
  
4.  Klikněte na první pole se seznamem. Změna **popisek** k `Thin Pen`, **ID** k `ID_PEN_THIN_WIDTH`, **Text** k `2`, **typ** k `Drop List`, a **Data** k `1;2;3;4;5;6;7;8;9;`.  
  
5.  Klikněte na tlačítko druhé pole se seznamem. Změna **popisek** k `Thick Pen`, **ID** k `ID_PEN_THICK_WIDTH`, **Text** k `5`, **typ** k `Drop List`, a **Data** k `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`.  
  
6.  Nové pole se seznamem nemusí odpovídat všechny existující položky nabídky. Proto je nutné vytvořit položku nabídky pro všechny dostupné možnosti pera.  
  
    1.  V **zobrazení prostředků** okně Otevřít prostředek IDR_SCRIBBTYPE nabídky.  
  
    2.  Klikněte na tlačítko **pera** otevřete p**en** nabídky. Pak klikněte na tlačítko **zde typ** a typ `Thi&n Pen`.  
  
    3.  Klikněte pravým tlačítkem na text, který jste právě zadali, otevřete **vlastnosti** okna a potom změnu ID vlastnosti `ID_PEN_THIN_WIDTH`.  
  
    4.  Musíte taky vytvořit obslužnou rutinu události pro každou položku nabídky pera. Klikněte pravým tlačítkem myši **Thi & n pera** položky nabídky, který jste právě vytvořili a potom klikněte na **přidejte obslužné rutiny události**. **Průvodce obslužnou rutinou události** se zobrazí.  
  
    5.  V **seznam tříd** pole v průvodci vyberte **CScribbleDoc** a pak klikněte na **přidávat a upravovat**. Tím se vytvoří obslužnou rutinu události s názvem `CScribbleDoc::OnPenThinWidth`.  
  
    6.  Přidejte následující kód, který `CScribbleDoc::OnPenThinWidth`.  
  
 ``` *Získání ukazatele na pásu karet panel CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar(); ASSERT_VALID(pRibbon); */ / Získání ukazatele na pole se seznamem dynamické šířka CMFCRibbonComboBox* pThinComboBox = dynamic_downcast – (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THIN_WIDTH)); * //Get vybrané hodnoty  
    int nCurSel = pThinComboBox -> GetCurSel(); Pokud (nCurSel > = 0)  
{  
m_nThinWidth = atoi – (pThinComboBox -> GetItem(nCurSel));

 } * / / Vytvoření pera nové pomocí vybrané šířka  
    ReplacePen();

 ```  
  
7.  Next, create a menu item and event handlers for the thick pen.  
  
    1.  In the **Resource View** window, open the IDR_SCRIBBTYPE menu resource.  
  
    2.  Click **Pen** to open the pen menu. Then click **Type Here** and type `Thic&k Pen`.  
  
    3.  Right-click the text that you just typed to display the **Properties** window. Change the ID property to `ID_PEN_THICK_WIDTH`.  
  
    4.  Right-click the **Thick Pen** menu item that you just created and then click **Add Event Handler**. The **Event Handler Wizard** is displayed.  
  
    5.  In the **Class list** box of the wizard, select **CScribbleDoc** and then click **Add and Edit**. This creates an event handler named `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Add the following code to `CScribbleDoc::OnPenThickWidth`.  
  
 ``` *// Get a pointer to the ribbon bar  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
*// Get the selected value  
    int nCurSel = pThickComboBox->GetCurSel();
if (nCurSel>= 0)  
 {  
    m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));

 } *// Create a new pen using the selected width  
    ReplacePen();

 ```  
  
8.  Uložte změny a sestavte a spusťte aplikaci. Nová tlačítka a pole se seznamem má být zobrazena. Zkuste použít jiné pero šířek zvyklí.  
  
 [[Části](#top)]  
  
##  <a name="addcolorbutton"></a>Přidání tlačítka barvy pera panely  
 Dál přidejte [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objekt, který umožňuje uživatelům scribble barvou.  
  
#### <a name="to-add-a-color-button-to-the-pen-panel"></a>Přidání tlačítka barvy pera panely  
  
1.  Než přidáte tlačítko barvy, vytvořte pro tuto položku nabídky. V **zobrazení prostředků** okně Otevřít prostředek IDR_SCRIBBTYPE nabídky. Klikněte **pera** položku otevřete nabídku pera. Pak klikněte na tlačítko **zde typ** a typ `&Color`. Klikněte pravým tlačítkem na text, který jste právě zadali zobrazíte **vlastnosti** okno. Změnit ID na `ID_PEN_COLOR`.  
  
2.  Nyní přidejte tlačítko barvy. Z **sada nástrojů**, přetáhněte **barva tlačítko** k **pera** panelu.  
  
3.  Klikněte na tlačítko barvy. Změna **popisek** k `Color`, **ID** k `ID_PEN_COLOR`, **SimpleLook** k `True`, **velký obrázek indexu** na `1`, a **rozdělení režimu** k `False`.  
  
4.  Uložte změny a sestavte a spusťte aplikaci. Tlačítko nové barva se má zobrazit na **pera** panelu. Ale jej nelze použít, protože ještě nemá obslužné rutiny události. Další kroky ukazují, jak přidat obslužné rutiny události pro tlačítko barvy.  
  
 [[Části](#top)]  
  
##  <a name="addcolormember"></a>Přidání člena barvu k třídě dokumentů  
 Vzhledem k tomu, že původní Scribble aplikace nemá barvy pera, musí zapsat implementace pro ně. K uložení barvy pera dokumentu, přidejte nový člen k třídě dokumentů`CscribbleDoc.`  
  
#### <a name="to-add-a-color-member-to-the-document-class"></a>Barva člena přidat do třídy dokumentů  
  
1.  V scribdoc.h v `CScribbleDoc` třídy, vyhledejte `// Attributes` části. Přidejte následující řádky kódu po definování `m_nThickWidth` – datový člen.  
  
 "' * / / Aktuální pera barev  
    COLORREF m_penColor;  
 ```  
  
2.  Every document contains a list of stokes that the user has already drawn. Every stroke is defined by a `CStroke` object. The `CStroke` class does not include information about pen color. Therefore, you must modify the class. In scribdoc.h, in the `CStroke` class, add the following lines of code after the definition of the `m_nPenWidth` data member.  
  
 ``` *// Pen color for the stroke  
    COLORREF m_penColor;  
 ```  
  
3.  V scribdoc.h, přidejte nový `CStroke` konstruktor, jejíž parametry zadejte šířky a barvy. Přidejte následující řádek kódu po `CStroke(UINT nPenWidth);` příkaz.  
  
 ```  
    CStroke(UINT nPenWidth, COLORREF penColor);

 ```  
  
4.  V scribdoc.cpp, přidat nové implementace `CStroke` konstruktor. Přidejte následující kód po implementaci `CStroke::CStroke(UINT nPenWidth)` konstruktor.  
  
 "' * / / Konstruktor, který používá dokumentu je aktuální šířky a barvy  
    CStroke::CStroke (Celé_číslo nPenWidth, COLORREF pera)  
 {  
    m_nPenWidth = nPenWidth;  
    m_penColor = pera;  
    m_rectBounding.SetRectEmpty();

 }  
 ```  
  
5.  Change the second line of the `CStroke::DrawStroke` method as follows.  
  
 ```  
    Pokud (! penStroke.CreatePen (PS_SOLID, m_nPenWidth, m_penColor))  
 ```  
  
6.  Set the default pen color for the document class. In scribdoc.cpp, add the following lines to `CScribbleDoc::InitDocument`, after the `m_nThickWidth = 5;` statement.  
  
 ``` *// default pen color is black  
    m_penColor = RGB(0,
    0,
    0);

 ```  
  
7.  Scribdoc.cpp, změňte první řádek `CScribbleDoc::NewStroke` metoda pro následující.  
  
 ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);

 ```  
  
8.  Změnit poslední řádek `CScribbleDoc::ReplacePen` metoda pro následující.  
  
 ```  
    m_penCur.CreatePen(PS_SOLID,
    m_nPenWidth,
    m_penColor);

 ```  
  
9. Jste přidali `m_penColor` člen v předchozím kroku. Teď vytvořte obslužnou rutinu události pro tlačítko barvu, která nastaví člena.  
  
    1.  V **zobrazení prostředků** okně Otevřít prostředek IDR_SCRIBBTYPE nabídky.  
  
    2.  Klikněte pravým tlačítkem myši **barva** položky nabídky a klikněte na tlačítko **přidejte obslužné rutiny události**. **Průvodce obslužnou rutinou události** se zobrazí.  
  
    3.  V **seznam tříd** pole v průvodci vyberte možnost **CScribbleDoc** a klikněte **přidávat a upravovat** tlačítko. Tím se vytvoří `CScribbleDoc::OnPenColor` se zakázaným inzerováním obslužná rutina události.  
  
10. Nahraďte se zakázaným inzerováním pro `CScribbleDoc::OnPenColor` obslužné rutiny události s následujícím kódem.  
  
 ```  
    void CScribbleDoc::OnPenColor()  
 { *// Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
    CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

    m_penColor = pColorBtn->GetColor();
*// Create new pen using the selected color  
    ReplacePen();

 }  
 ```  
  
11. Uložte změny a sestavte a spusťte aplikaci. Nyní byste měli mít klikněte na tlačítko barvy a změnit barva.  
  
 [[Části](#top)]  
  
##  <a name="initpensave"></a>Inicializace pera a ukládání předvoleb  
 V dalším kroku inicializujte barva a šířka per. Nakonec uložit a načíst barvy kreslení ze souboru.  
  
#### <a name="to-initialize-controls-on-the-ribbon-bar"></a>K chybě při inicializaci ovládacích prvků na panelu pásu karet  
  
1.  Inicializujte pera na panelu pásu karet.  
  
     Přidejte následující kód do scribdoc.cpp, v `CScribbleDoc::InitDocument` metoda, po `m_sizeDoc = CSize(200,200)` příkaz.  
  
 ```*/ / Reset uživatelské rozhraní pásu karet na jeho počáteční hodnoty CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar(); ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton * pColorBtn = dynamic_downcast – (CMFCRibbonColorButton, pRibbon -> FindByID(ID_PEN_COLOR)); * / / Set ColorButton do černé  
    pColorBtn -> setcolor – (RGB (0, 0, 0));

 CMFCRibbonComboBox * pThinComboBox = dynamic_downcast – (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THIN_WIDTH)); * / / Set dynamické pera combobox 2  
    pThinComboBox -> SelectItem(1);

 CMFCRibbonComboBox * pThickComboBox = dynamic_downcast – (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THICK_WIDTH)); * / / Set silných pera combobox 5  
    pThickComboBox -> SelectItem(0);

 ```  
  
2.  Save a color drawing to a file. Add the following statement to scribdoc.cpp, in the `CStroke::Serialize` method, after the `ar << (WORD)m_nPenWidth;` statement.  
  
 ```  
    ar << m_penColor (COLORREF);  
 ```  
  
3.  Finally, load a color drawing from a file. Add the following line of code, in the `CStroke::Serialize` method, after the `m_nPenWidth = w;` statement.  
  
 ```  
    ar >> m_penColor;  
 ```  
  
4.  Now scribble in color and save your drawing to a file.  
  
 [[Sections](#top)]  
  
## Conclusion  
 You have updated the MFC Scribble application. Use this walkthrough as a guide when you modify your existing applications.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

