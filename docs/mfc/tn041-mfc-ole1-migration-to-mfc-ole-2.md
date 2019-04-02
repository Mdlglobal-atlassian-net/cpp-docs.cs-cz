---
title: 'TN041: Migrace MFC-OLE1 do MFC-OLE 2'
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767974"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: Migrace MFC/OLE1 do MFC/OLE2

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

## <a name="general-issues-relating-to-migration"></a>Obecné problémy týkající se migrace

Jedním z cílů návrhu pro třídy OLE 2 v MFC 2.5 (a vyšší) bylo zachovat velkou část stejnou architekturu zavedený ve verzi MFC 2.0 OLE 1.0 podporu. V důsledku toho řadu stejné třídy OLE v MFC 2.0 stále existují v této verzi knihovny MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). Kromě toho řadu rozhraní API v těchto tříd jsou stejné. OLE 2 je ale výrazně liší od OLE 1.0, takže můžete očekávat, že některé podrobnosti změnit. Pokud jste se seznámili s podporou OLE1 MFC 2.0, budete mít pocit, během chvilky se 2.0 podpory knihovny MFC.

Pokud trvá existující aplikaci MFC/OLE1 a přidání do funkce OLE 2, byste si měli přečíst tato poznámka nejprve. Tato poznámka popisuje některé obecné problémy mohou nastat při přenesení vaší funkce OLE1 do MFC/OLE 2 a pak tento článek popisuje problémů zjištěných při přenesení dvě aplikace, které jsou zahrnuté v MFC 2.0: ukázky MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>Je důležité architektury dokument/zobrazení MFC

Pokud vaše aplikace nepoužívá architektuře Document/View knihovny MFC a chcete přidat do svojí aplikace podporu OLE 2, nyní je čas na přechod na Document/View. Mnohé z výhod třídy MFC OLE 2 realizovány pouze po vaše aplikace používá integrované architektura a komponenty knihovny MFC.

Implementace serveru nebo kontejneru bez použití architektury MFC je možné, ale nedoporučuje se.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Použít místo vlastní implementace v prostředí MFC

Třídy MFC "konzervované implementace" jako `CToolBar`, `CStatusBar`, a `CScrollView` předdefinované speciální případu kód pro podporu OLE 2. Tak pokud používáte tyto třídy ve své aplikaci budete moct s výhodou úsilí do nich daly OLE vědět. Znovu je možné "vrácení vlastní" třídy zde pro tyto účely, ale není navržen. Pokud potřebujete implementovat podobné funkce, zdrojový kód knihovny MFC je vynikající referenční informace pro práci s některými zákoutí OLE (zejména pokud jde o aktivace na místě).

## <a name="examine-the-mfc-sample-code"></a>Projdete ukázkový kód knihovny MFC

Existuje mnoho z ukázek MFC, které zahrnují funkce OLE. Každá z těchto aplikací implementuje OLE z různých úhel:

- [HIERSVR](../overview/visual-cpp-samples.md) určena především pro použití jako server aplikace. Je zahrnutý v MFC 2.0 jako aplikace MFC/OLE1 a bylo přenést do MFC/OLE 2 a pak rozšířit tak, že implementuje mnoho funkcí dostupných ve OLE 2 OLE.

- [OCLIENT](../overview/visual-cpp-samples.md) Toto je samostatná aplikace typu kontejner pro, určená k předvedení řadu funkcí, OLE z hlediska kontejneru. To byla příliš přenést z knihovny MFC 2.0 a pak rozšířit pro zajištění podpory řadu pokročilejší funkce OLE, jako je například formáty vlastní schránky a odkazy na vložené položky.

- [DRAWCLI](../overview/visual-cpp-samples.md) tato aplikace implementuje podporu kontejneru OLE mnohem jako OCLIENT, s tím rozdílem, že provádí v rámci existující program výkresu objektově orientovaný. To se dozvíte, jak implementovat podporu kontejneru OLE a integrovat do své existující aplikace.

- [SUPERPAD](../overview/visual-cpp-samples.md) této aplikace, stejně jako se bez problémů samostatné aplikace, je také OLE server. Podpora serveru, který implementuje je minimalist ještě nejsme u konce. Zajímavé především je způsob používání mechanismu služeb OLE schránky pro kopírování dat do schránky, ale používá funkce, které jsou integrované do ovládacího prvku Windows "edit" k implementaci funkcionality schránky vložit. Ukazuje to zajímavé kombinaci tradiční použití rozhraní API Windows, stejně jako integraci s nových OLE rozhraní API.

Další informace o ukázkových aplikací najdete v článku "Knihovnu MFC ukázky Nápověda".

## <a name="case-study-oclient-from-mfc-20"></a>Případová studie: OCLIENT z knihovny MFC 2.0

Jak je popsáno výše, [OCLIENT](../overview/visual-cpp-samples.md) byl součástí knihovny MFC 2.0 a implementovaná pomocí knihovny MFC/OLE1 OLE. Kroky, podle kterých byl zpočátku převeden této aplikace použít třídy MFC/OLE 2 jsou popsané níže. Po dokončení počáteční port abychom vám lépe předvedli MFC/OLE – třídy byly přidány celou řadu funkcí. Tato funkce není součástí tohoto odkazovat na samotný vzorku pro další informace o těchto pokročilých funkcí.

> [!NOTE]
> Chyby kompilátoru a podrobný postup vytvoření s Visual C++ 2.0. Konkrétní chybové zprávy a umístění, může se změnila s Visual C++ 4.0, ale zůstává v platnosti koncepční informace.

## <a name="getting-it-up-and-running"></a>Jeho zprovoznění

Přístup na port OCLIENT vzorek MFC/OLE je začít tím, že jeho sestavení a opravy, které způsobí chyby kompilátoru zřejmé. Pokud trvat, než ukázku OCLIENT MFC 2.0 a jeho kompilace v této verzi knihovny MFC, zjistíte, že již nejsou tolik chyby vyřešit. Chyby v pořadí, ve kterém k nim došlo, jsou popsané níže.

## <a name="compile-and-fix-errors"></a>Kompilace a oprava chyb

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

První chyba se týká `COleClientItem::Draw`. V MFC/OLE1, jakou trvalo více parametrů, než má verzi knihovny MFC/OLE. Další parametry byly často není nezbytné a obvykle NULL (jako v následujícím příkladu). Této verze knihovny MFC můžete automaticky určit hodnoty lpWBounds po CDC nakreslený do metasouboru řadiče domény. Kromě toho parametr pFormatDC už nejsou potřebné od rozhraní bude sestavení z "atribut řadiče domény" předáno primární řadič domény. Proto pokud chcete vyřešit tento problém, jednoduše odebrat dvou dalších parametrů k volání Draw s hodnotou NULL.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Chyby nad výsledek ze skutečnosti, všechny `COleClientItem::CreateXXXX` funkce v MFC/OLE1 vyžaduje, aby jedinečný název předávat představující položku. To byl požadavek základního OLE rozhraní API. To není nutné v MFC/OLE 2 od OLE 2 nepoužívá DDE jako základní komunikační mechanismus (název se používá v konverzacích DDE). Chcete-li tento problém vyřešit, můžete odstranit `CreateNewName` fungovat stejně jako všechny odkazy na něj. Je snadné a zjistěte, co každá funkce MFC/OLE se očekává v této verzi jednoduše tak, že umístění kurzoru na volání a stisknutím klávesy F1.

Další oblastí, které se výrazně liší je zpracování schránky OLE 2. Klauzuli WITH OLE1 použít schránky Windows, které rozhraní API pro interakci s do schránky. S OLE 2 je to s jiným způsobem. Rozhraní API knihovny MFC/OLE1 předpokládá, že schránky byla otevřena před kopírováním `COleClientItem` objektu do schránky. To již není nezbytné a způsobí, že všechny operace se schránkou MFC/OLE – selhání. Během úprav kódu a odebrání závislostí na `CreateNewName`, měli byste také odebrat kód, který se otevře a zavře schránky Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Výsledkem těchto chyb `CMainView::OnInsertObject` obslužné rutiny. Zpracování příkazu "Vložit nový objekt" je jiné oblasti, kde se věci změnily odlišují. V takovém případě je nejjednodušší jednoduše sloučit původní implementace pomocí AppWizard poskytuje nové aplikace kontejneru OLE. Ve skutečnosti jde o techniku, který můžete použít pro přenos dalších aplikací. V MFC/OLE1 zobrazí dialog "Vložit objekt" při volání `AfxOleInsertDialog` funkce. V této verzi můžete vytvořit `COleInsertObject` objektu dialogového okna a volání `DoModal`. Kromě toho budou vytvořeny nové položky OLE se **CLSID** namísto řetězce classname. Konečný výsledek by měl vypadat asi takhle nějak.

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> Vložit nový objekt může být odlišné pro vaši aplikaci):

Je také nutné zahrnout \<afxodlgs.h >, obsahující deklarace `COleInsertObject` třídy dialogového okna, stejně jako ostatní standardní dialogová okna poskytované knihovny MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Tyto chyby jsou způsobeny skutečnost, že některé konstanty OLE1 změnil OLE 2, i když je v principu se shodují. V tomto případě `OLEVERB_PRIMARY` se změnila na `OLEIVERB_PRIMARY`. OLE1 a OLE 2 primárního operaci obvykle provádí kontejnerem, když uživatel poklepe na položky.

Kromě toho `DoVerb` nyní přijímá další parametr – ukazatel na zobrazení (`CView`*). Tento parametr slouží pouze k implementaci "Úpravy s náhledem" (nebo aktivace na místě). Teď nastavte tento parametr na hodnotu NULL, protože v tuto chvíli nejsou implementaci této funkce.

Pokud chcete mít jistotu, že rozhraní nikdy pokusy o místní aktivace, by měly přepsat `COleClientItem::CanActivate` následujícím způsobem:

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

V MFC/OLE1 `COleClientItem::GetBounds` a `SetBounds` byly použity k dotazování a manipulaci s rozsah položky ( `left` a `top` členy byly vždy nula). V MFC/OLE 2 to více přímo podporuje `COleClientItem::GetExtent` a `SetExtent`, které řešení **velikost** nebo `CSize` místo.

Kód pro vaše nové SetItemRectToServer a volání UpdateItemRectFromServer vypadat nějak takto:

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

V synchronní API MFC/OLE1 volání z kontejneru serveru byly *simulované*, protože OLE1 byl v mnoha případech ze své podstaty asynchronní. Je nutné kontrolovat nevyřízené asynchronní volání probíhá před zpracováním příkazy od uživatele. K dispozici MFC/OLE1 `COleClientItem::InWaitForRelease` funkce to udělat. MFC/OLE 2 to není nutné, abyste je mohli odebrat přepsání OnCommand CMainFrame všechno dohromady.

V tomto okamžiku bude OCLIENT zkompilovat a propojit.

## <a name="other-necessary-changes"></a>Další potřebné změny

Existuje několik věcí, které se neprovádí, které budete mít OCLIENT spouštění, ale. Je lepší, chcete-li vyřešit tyto problémy teď místo později.

Nejprve je potřeba inicializovat knihovny OLE. To se provádí voláním `AfxOleInit` z `InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Je také vhodné ke kontrole virtuálních funkcí pro změny seznamu parametrů. Jedna funkce je `COleClientItem::OnChange`, přepsané v každé aplikaci MFC/OLE – kontejner. Prohlédněte online nápovědy, uvidíte, že byl přidán další "typu DWORD dwParam". Nové CRectItem::OnChange by měl vypadat takto:

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

Aplikace typu kontejner v MFC/OLE1 odvozené dokumentové třídy z `COleClientDoc`. MFC/OLE 2 byl odebrán této třídy a nahrazuje `COleDocument` (této nové organizace je snazší vytvářet aplikace typu server/kontejner). Je **#define** , která se mapuje `COleClientDoc` k `COleDocument` ke zjednodušení přenesení aplikací MFC/OLE1 do MFC/OLE 2, jako je například OCLIENT. Jednou z funkcí není poskytnutých `COleDocument` , který byl poskytnut `COleClientDoc` je standardní příkaz zprávy položek mapování. Uděláte to tak serverové aplikace, které používají také `COleDocument` (nepřímo), nemají s nimi režijní náklady na tyto obslužné rutiny příkazů které nejsou typu server/kontejner aplikace. Je potřeba přidat následující položky do mapy zpráv CMainDoc:

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

Implementace všech těchto příkazů je v `COleDocument`, což je základní třída pro dokument.

V tomto okamžiku OCLIENT je funkční aplikace kontejneru OLE. Je možné vložit položky jakéhokoliv typu (OLE1 nebo OLE 2). Protože potřebný kód umožňující místní aktivace není implementována, jsou v samostatném okně velká, jako je s OLE1 upravovat položky. Další část popisuje potřebné změny, aby se povolily úpravy na místě (někdy nazývané "Vizuální úpravy").

## <a name="adding-visual-editing"></a>Přidání "Úpravy s náhledem"

Jedním z nejzajímavějších funkce OLE je aktivace na místě (nebo "Vizuální úpravy"). Tato funkce umožňuje se serverová aplikace mohla převzít kontrolu nad částí uživatelského rozhraní na kontejner, poskytuje pohodlnější editační rozhraní pro uživatele. K implementaci místní aktivaci za účelem OCLIENT, je potřeba přidat, a také další kód některé speciální prostředky. Tyto prostředky a kód se obvykle poskytované AppWizard – ve skutečnosti byla velkou část kódu tady si přímo z aplikace čerstvé AppWizard podpora "Kontejnerů".

Za prvé je potřeba přidat nabídce prostředků chcete použít, když je položka, která je na místě aktivní. Tento prostředek doplňující nabídky v jazyce Visual C++ můžete vytvořit zkopírováním IDR_OCLITYPE prostředků a odebírá všechny kromě souborů a okno automaticky otevíraná okna. Mezi souboru a okno automaticky otevíraná okna k označení oddělení skupiny jsou vloženy dvě oddělovacích pruhů (by měl vypadat: Soubor &#124; &#124; okno). Další informace o významu těchto oddělovače a jak slučování nabídek serveru a kontejneru najdete v části [nabídky a prostředky: Slučování nabídek](../mfc/menus-and-resources-menu-merging.md).

Jakmile máte těchto nabídek, které vytvořili, musíte nechat informovat o rámci. To se provádí voláním `CDocTemplate::SetContainerInfo` pro šablonu dokumentu, předtím, než přidáte na seznam šablon dokumentů do funkce InitInstance. vaše. Nový kód pro registraci šablonu dokumentu vypadá takto:

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

Prostředek IDR_OLECLITYPE_INPLACE je speciální místní prostředku vytvořeného v jazyce Visual C++.

Pokud chcete povolit aktivace na místě, se několik věcí, které je potřeba změnit v obou `CView` (CMainView) odvozené třídy i na `COleClientItem` odvozenou třídou (CRectItem). Všechna tato přepsání jsou k dispozici přes AppWizard a implementaci přijde přímo z aplikace AppWizard výchozí.

V prvním kroku tohoto portu, byla zakázána aktivace na místě zcela tak, že přepíšete `COleClientItem::CanActivate`. Povolit místní aktivace byste měli odebrat toto přepsání. Kromě toho byl předán všechna volání NULL `DoVerb` (existují dva z nich) vzhledem k tomu, že poskytnete zobrazení se pouze pro místní aktivace. K plné implementace aktivace na místě, je potřeba předat zobrazení správné `DoVerb` volání. Jedna z těchto volání `CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Další je v `CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Je nutné přepsat `COleClientItem::OnGetItemPosition`. Říká serveru, kam chcete vložit její okno vzhledem k oknu kontejneru, když je položka místní aktivaci. Pro OCLIENT je triviální implementace:

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

Většina serverů také implementovat, co se nazývá "místní změny velikosti." To umožňuje serveru okno velikosti a přesunutí, když uživatel upravuje položka. Kontejner musí být součástí této akce, protože přesunutí nebo změně velikosti okna obvykle ovlivní umístění a velikost v rámci samotného dokumentu kontejneru. Implementace OCLIENT synchronizuje interní obdélník udržuje m_rect s novou pozici a velikost.

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

V tomto okamžiku není dostatek kód umožňující položka aktivována na místě a změny velikosti a přesunutí položky, když je aktivní, ale žádný kód vám umožní uživateli ukončení relace úprav. I když některé servery se poskytují tuto funkci sami zpracováním klávesou ESC, doporučuje se, že kontejnery poskytují dva způsoby, jak deaktivovat položku: (1) kliknutím mimo položky a (2) stisknutím klávesy ESC.

Pro klávesu ESCAPE přidejte akcelerátor s jazykem Visual C++, který mapuje vk_escape – klíč k příkazu, ID_CANCEL_EDIT se přidá k prostředkům. Následující obslužná rutina tohoto příkazu:

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

Pro zpracování případu, ve kterém uživatel klikne mimo položky, přidejte následující kód do začátku `CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Pokud je položka místní aktivní, měl by mít fokus. Abyste měli jistotu, že tomu tak zpracovávat když se objekt tak, aby fokus je vždy převeden do aktivní položky při zobrazení bude vybrán:

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

Při změně velikosti zobrazení, je potřeba upozornit aktivní položky, které se změnily obdélník oříznutí. K tomu zadejte obslužnou rutinu pro `OnSize`:

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>Případová studie: HIERSVR z knihovny MFC 2.0

[HIERSVR](../overview/visual-cpp-samples.md) byl také součástí knihovny MFC 2.0 a implementovaná pomocí knihovny MFC/OLE1 OLE. Tato poznámka stručně popisuje kroky, podle kterých byl zpočátku převeden této aplikace použít třídy MFC/OLE 2. Po dokončení počáteční port abychom vám lépe předvedli třídy MFC/OLE 2 byly přidány celou řadu funkcí. Tato funkce není součástí tohoto odkazovat na samotný vzorku pro další informace o těchto pokročilých funkcí.

> [!NOTE]
> Chyby kompilátoru a podrobný postup vytvoření s Visual C++ 2.0. Konkrétní chybové zprávy a umístění, může se změnila s Visual C++ 4.0, ale zůstává v platnosti koncepční informace.

## <a name="getting-it-up-and-running"></a>Jeho zprovoznění

Přístup na port HIERSVR vzorek MFC/OLE je začít tím, že jeho sestavení a opravy, které způsobí chyby kompilátoru zřejmé. Pokud trvat, než ukázku HIERSVR MFC 2.0 a jeho kompilace v této verzi knihovny MFC, zjistíte, že již nejsou mnoho chyb, chcete-li vyřešit (i když jsou více než s ukázkou OCLIENT). Chyby v pořadí, ve kterém k nim obvykle dojde, jsou popsané níže.

## <a name="compile-and-fix-errors"></a>Kompilace a oprava chyb

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Tato první chyba poukazuje na mnohem větší potíže s `InitInstance` funkce pro servery. Inicializace požadována pro OLE server je pravděpodobně jednou z největších změn, které budete muset provést aplikace MFC/OLE1 její spuštění. Je nejlepší krokem je podívat se na AppWizard nevytvoří pro OLE server a upravte kód podle potřeby. Tady jsou některé body, které mějte na paměti:

Je nutné inicializovat knihovny OLE voláním `AfxOleInit`

Volat SetServerInfo pro objekt šablony dokumentu popisovače prostředku serveru a informace o modulu runtime třídy, které nelze nastavit pomocí nastavení `CDocTemplate` konstruktoru.

Nezobrazovat hlavní okno aplikace, pokud je k dispozici v příkazovém řádku/Embedding.

Budete potřebovat **GUID** dokumentu. Toto je jedinečný identifikátor pro typ dokumentu (128 bitů). AppWizard ho vytvoří za vás – Pokud používáte popsaného zde kopírování z a new server application AppWizard vygeneruje nový kód, je můžete jednoduše "ukrást" identifikátoru GUID z této aplikace. Pokud ne, můžete použít Guidgen –. Nástroj EXE v adresáři BIN.

Je potřeba "připojení" vaší `COleTemplateServer` objektu do šablony dokumentu voláním `COleTemplateServer::ConnectTemplate`.

Aktualizujte registr systému při spuštění samostatné aplikace. Tímto způsobem, pokud se uživatel přesune. EXE pro vaši aplikaci, spouštění ze své nové pozice aktualizujeme, registrační databáze systému Windows tak, aby odkazoval na nové umístění.

Po použití všech těchto změn podle AppWizard nevytvoří pro `InitInstance`, `InitInstance` (a související s identifikátorem GUID) pro HIERSVR vypadat takto:

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

Můžete si všimnout, že výše uvedený kód odkazuje nové ID prostředku, IDR_HIERSVRTYPE_SRVR_EMB. Toto je nabídka prostředek má být použit při úpravě dokumentu, který je vložený v jiném kontejneru. V MFC/OLE1 specifické pro úpravu položky vložené položky nabídky byly změněny v reálném čase. Pomocí struktury úplně jiné nabídky při úpravách vložená položka. místo pro úpravy dokument založený na souboru, je mnohem jednodušší předat různých uživatelských rozhraní pro tyto dvě samostatné režimy. Jak uvidíte později, prostředek zcela samostatné nabídky se používá při úpravách vložený objekt místní.

Chcete-li vytvořit tento prostředek, načtení skriptu prostředku do jazyka Visual C++ a zkopírovat existující prostředek IDR_HIERSVRTYPE nabídky. Přejmenujte nový prostředek na IDR_HIERSVRTYPE_SRVR_EMB (je to stejné zásady vytváření názvů, který používá AppWizard). Dále změňte "Uložit soubor" na "File Update"; Zadejte příkaz id_file_update – ID. Také změňte "Uložit jako" na "Soubor uložit kopii jako"; Zadejte příkaz id_file_save_copy_as – ID. Rozhraní poskytuje provádění oba tyto příkazy.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Existuje několik chyb vyplývající z přepsané `OnSetData`, protože odkazuje na **OLESTATUS** typu. **OLESTATUS** se způsob, jakým OLE1 vrácené chyby. To se změnila na **HRESULT** v OLE 2, i když obvykle převede knihovny MFC **HRESULT** do `COleException` obsahující chybu. V tomto konkrétním případě přepsané `OnSetData` již není nezbytné, proto je nejjednodušší krokem jeho odstranění.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem` Konstruktoru přijímá další parametr 'BOOL'. Tento příznak určuje, jak se provádí správa paměti na `COleServerItem` objekty. Rozhraní tak, že ji nastavíte na hodnotu TRUE, postará o správu paměti tyto objekty, jejich odstranění, když už nejsou potřebné. Používá HIERSVR `CServerItem` (odvozený od `COleServerItem`) objektů v rámci jeho nativní data, takže tento příznak bude nastavena na hodnotu FALSE. Díky tomu HIERSVR určit, kdy se odstraní položka každý server.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Jak tyto chyby znamenají, existují některé 'čistě virtuální' funkce, které nebyly přepsány v CServerItem. Nejspíš to je způsobeno skutečnost, že došlo ke změně OnDraw v seznamu parametrů. Chcete-li tuto chybu vyřešit, změňte `CServerItem::OnDraw` následujícím způsobem (stejně jako deklaraci v svritem.h):

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Nový parametr je 'parametru ' rSize. To umožňuje vyplňte velikost kreslení, pokud je to vhodné. Tato velikost musí být v **HIMETRIC**. V tomto případě není vhodné k vyplnění tuto hodnotu, takže volá framework `OnGetExtent` načíst v rozsahu. Pro tento postup, budete muset implementovat `OnGetExtent`:

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

Ve funkci CServerItem::CalcNodeSize velikost položky je převedena na **HIMETRIC** a uložené v *m_rectBounds*. Nedokumentované "*m_rectBounds*" členem `COleServerItem` neexistuje (jeho částečně nahradila ji *m_sizeExtent*, ale v OLE 2 Tento člen má mírně odlišné použití než *m_rectBounds* to udělali v OLE1). Místo nastavení **HIMETRIC** velikost do této členské proměnné, budete ji vrátit. Tato návratová hodnota se používá v `OnGetExtent`, dřív implementovaná.

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

Také přepisuje CServerItem `COleServerItem::OnGetTextData`. Tato funkce je zastaralá v prostředí MFC/OLE a je nahrazen jiným způsobem. Verze MFC 3.0 ukázky MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) implementuje tuto funkci tak, že přepíšete `COleServerItem::OnRenderFileData`. Tato funkce není důležité pro tento základní port, abyste mohli odstranit OnGetTextData přepsání.

Existuje mnoho další chyby v svritem.cpp, které dosud nebylo řešeno. Nejsou "real" chyby – pouze chyby způsobené předchozí chyby.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` už nepodporuje `bIncludeNative` příznak. Nativní dat (dat zapsaných funkci Serialize položka serveru) je vždy zkopírovány, proto odebrat první parametr. Kromě toho `CopyToClipboard` vyvolá výjimku, pokud dojde k chybě místo vrácení hodnoty FALSE. Změňte kód pro CServerView::OnEditCopy následujícím způsobem:

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

Přestože výsledkem kompilace verze MFC 2.0 HIERSVR než bylo pro stejnou verzi OCLIENT více chybám, byly ve skutečnosti méně změn.

V tomto okamžiku HIERSVR se zkompilovat a propojit a fungovat jako OLE server, ale bez funkce úprav na místě, které budou implementovány dále.

## <a name="adding-visual-editing"></a>Přidání "Úpravy s náhledem"

Přidat do této aplikace serveru "Úpravy s náhledem" (nebo aktivace na místě), jsou jenom pár věcí, které musí postará o:

- Budete potřebovat speciální nabídce prostředku se použije, když je položka místní aktivní.

- Tato aplikace má panel nástrojů, takže je třeba panel nástrojů s jenom určité podmnožiny běžných nástrojů tak, aby odpovídaly na serveru k dispozici příkazy nabídky (odpovídá prostředků nabídek uvedených výše).

- Budete potřebovat nové třídy odvozené od `COleIPFrameWnd` , který poskytuje místní uživatelské rozhraní (podobně jako CMainFrame odvozený od `CMDIFrameWnd`, poskytuje uživatelské rozhraní MDI).

- Budete muset o tyto speciální prostředky a třídy informování rozhraní framework.

Nabídce prostředků je snadné vytvořit. Spusťte Visual C++, kopírování prostředků nabídky IDR_HIERSVRTYPE do nabídky prostředek s názvem IDR_HIERSVRTYPE_SRVR_IP. V nabídce upravte tak, aby zůstaly jenom upravit a nápovědu nabídky automaticky otevíraná okna. Přidejte dva oddělovače do nabídky mezi nabídky Úpravy a nápovědy (by měl vypadat: Upravit &#124; &#124; Nápověda). Další informace o významu těchto oddělovače a jak slučování nabídek serveru a kontejneru najdete v tématu [nabídky a prostředky: Slučování nabídek](../mfc/menus-and-resources-menu-merging.md).

Rastrový obrázek pro panel nástrojů dílčí můžete snadno vytvořit zkopírováním z čerstvého AppWizard vygeneruje aplikace s možností "Server" zaškrtnuté. Tento rastrový obrázek jde pak importovat do Visual C++. Je potřeba poskytnout ID IDR_HIERSVRTYPE_SRVR_IP rastrového obrázku.

Třída odvozena z `COleIPFrameWnd` lze kopírovat z aplikace vygenerované průvodcem AppWizard se také podpora serveru. Zkopírujte oba soubory IPFRAME. CPP a IPFRAME. H a přidat je do projektu. Ujistěte se, že `LoadBitmap` volání odkazuje na IDR_HIERSVRTYPE_SRVR_IP rastrový obrázek vytvořili v předchozím kroku.

Teď, když se vytvoří nové prostředky a třídy, přidání nezbytného kódu tak, aby rozhraní ví o těchto (a ví, že tuto aplikaci teď podporuje úpravy na místě). To se provádí tak, že přidáte nějaké další parametry pro `SetServerInfo` volání `InitInstance` funkce:

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Nyní je připraven ke spuštění na místě v kontejneru, který podporuje také místní aktivace. Ale je stále skrývá v kódu jednu menších chyb. HIERSVR podporuje místní nabídce zobrazí, když uživatel stiskne pravé tlačítko myši. Tato nabídka funguje v případě HIERSVR je zcela otevřená, ale nefunguje při úpravě vložení v místě. Důvodem je možné připnout na tento jediný řádek kódu v CServerView::OnRButtonDown:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Všimněte si, že odkaz na `AfxGetApp()->m_pMainWnd`. Server je aktivovat v místě, má hlavní okno a nastavení m_pMainWnd., ale je obvykle neviditelné. Kromě toho toto okno odkazuje *hlavní* okna aplikace okno rámce MDI, která se zobrazí, když je server plně otevřít nebo spustí samostatně. Neodkazuje na aktivní rámec okna – což při místní aktivaci je rámec okna odvozený od `COleIPFrameWnd`. Chcete-li získat správný aktivního okna i v případě, že místní úpravy této verze knihovny MFC přidá novou funkci, `AfxGetMainWnd`. Obecně platí, používejte tuto funkci místo `AfxGetApp()->m_pMainWnd`. Tento kód je potřeba změnit následujícím způsobem:

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Teď máte minimálně povolit pro funkční místní aktivace server OLE. Ale ještě nejsou k dispozici s MFC/OLE 2, které nebyly k dispozici v MFC/OLE1 mnoho funkcí. Najdete v ukázce HIERSVR Další nápady na funkce, které chcete implementovat. Některé funkce, které implementuje HIERSVR jsou uvedeny níže:

- Změna měřítka zobrazení, true WYSIWYG chování s ohledem na kontejneru.

- Přetažení a formát vlastní schránky.

- Okno kontejner jako výběr posouvání se změní.

Ukázka HIERSVR 3.0 MFC také používá mírně odlišné návrhu pro položky na serveru. To pomáhá šetřit paměť a umožňuje flexibilnější propojení. S verzí 2.0 HIERSVR každý uzel ve stromu *je a* `COleServerItem`. `COleServerItem` představuje trochu více režie, než je nezbytně nutné pro každý z těchto uzlů, ale `COleServerItem` se vyžaduje pro každé aktivní propojení. Ale ve většině případů je velmi málo aktivních odkazů v daném okamžiku. Chcete-li to efektivnější, HIERSVR v této verzi knihovny MFC odděluje uzlu z `COleServerItem`. Obsahuje oba CServerNode a `CServerItem` třídy. `CServerItem` (Odvozený od `COleServerItem`) se vytvoří pouze v případě potřeby. Jakmile kontejneru (nebo kontejnery) přestat používat tuto konkrétní odkaz na tuto konkrétní uzel, CServerItem objekt přidružený k CServerNode je odstraněna. Tento návrh je efektivnější a flexibilnější. Při práci s více propojeními výběr, je dostupná v jeho flexibilitu. Ani jeden z těchto dvou verzí HIERSVR podporovat více výběrů, ale bylo by mnohem jednodušší, chcete-li přidat (a pro podporu odkazů na tyto výběry) verze MFC 3.0 HIERSVR, protože `COleServerItem` je oddělená od nativních datových.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
