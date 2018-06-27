---
title: 'TN041: Migrace z MFC OLE1 do MFC-2 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 486fd48a0d77c8c42a958dcb205854928fe00dc8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952447"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: Migrace z prostředí MFC/OLE1 do MFC/OLE2
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
## <a name="general-issues-relating-to-migration"></a>Obecné problémy týkající se migrace  
 Jedním z cílů návrhu pro třídy OLE 2 ve MFC 2.5 (a vyšší) se zachovat většinu stejnou architekturu zaveden MFC 2.0 pro podporu OLE 1.0. V důsledku toho řadu stejné třídy OLE ve MFC 2.0 stále existují v této verzi knihovny MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). Kromě toho řadu rozhraní API v tyto třídy jsou stejné. OLE 2 je však velmi výrazně liší od OLE 1.0, takže můžete očekávat, že některé podrobnosti změnit. Pokud jste obeznámeni s podporou OLE1 MFC 2.0, budete mít doma 2.0 Podpora MFC pro.  
  
 Pokud jsou trvá existující aplikaci MFC/OLE1 a přidání funkce OLE 2 k němu, měli byste si přečíst tato poznámka nejdřív. Tato poznámka popisuje některé běžné problémy, které můžete narazit při portování vaší funkce OLE1 do MFC/OLE 2 a pak popisuje problémů zjištěných při portování dvě aplikace, které jsou součástí MFC 2.0: ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md).  
  
## <a name="mfc-documentview-architecture-is-important"></a>Je důležité MFC Document/View – architektura  
 Pokud vaše aplikace nepoužívá MFC Document/View – architektura a chcete přidat do aplikace podporu OLE 2, nyní je čas na přechod na dokument/zobrazení. Řadu výhod na MFC – třídy OLE 2 realizovány pouze po vaše aplikace používá integrované architektura a komponenty MFC.  
  
 Implementace serveru nebo kontejneru bez použití architektury MFC je možné, ale nedoporučuje se.  
  
## <a name="use-mfc-implementation-instead-of-your-own"></a>Použít místo vlastní implementace MFC  
 Třídy MFC "konzervované implementace", jako `CToolBar`, `CStatusBar`, a `CScrollView` mají předdefinované speciální případu kód pro podporu OLE 2. Ano Pokud používáte tyto třídy ve vaší aplikaci budete mít výhodu úsilí umístí do nich tak, aby byly OLE vědět. Znovu je možné "vrácení vlastní" třídy sem pro tyto účely, ale není navrhované. Pokud potřebujete implementovat podobné funkce, MFC zdrojový kód je vynikající odkaz pro práci s některé z bodů jemnějšího OLE (zejména při rozhodování o aktivace na místě).  
  
## <a name="examine-the-mfc-sample-code"></a>Zkontrolujte ukázkového kódu knihovny MFC  
 Existuje několik MFC vzorků, které obsahují funkce OLE. Každá z těchto aplikací implementuje OLE z různých úhel:  
  
- [HIERSVR](../visual-cpp-samples.md) určené hlavně pro použití jako server aplikace. Je zahrnutý v MFC 2.0 jako aplikace MFC/OLE1 a bylo přesně do MFC/OLE 2 a pak se rozšíří tak, aby se implementuje mnoho funkcí dostupných ve OLE 2 OLE.  
  
- [OCLIENT](../visual-cpp-samples.md) Toto je aplikace s samostatné kontejneru určená k předvedení mnoho funkcí OLE z hlediska kontejneru. Ho byla příliš přenášet mezi MFC 2.0 a pak rozšířené k podpoře mnoho dalších pokročilých funkcí OLE, jako jsou formáty vlastní schránky a odkazy na vložené položky.  
  
- [DRAWCLI](../visual-cpp-samples.md) této aplikace implementuje podporu kontejneru OLE mnohem jako OCLIENT nemá, s tím rozdílem, že učiní tak v rámci existující objektově orientované kreslení programu. Ho ukazuje, jak implementovat podporu kontejneru OLE a jeho integraci do aplikace.  
  
- [SUPERPAD](../visual-cpp-samples.md) tuto aplikaci, jakož i se dobře samostatná aplikace, je také OLE server. Podpora serveru, které implementuje je minimalistické konce. Zajímají hlavně o je, jak používá služby schránky OLE zkopírovat data do schránky, ale používá funkce integrované do ovládacího prvku systému Windows "upravit" k implementaci funkci vložení schránky. Ukazuje to zajímavé směs tradiční využití rozhraní API systému Windows a také integraci s nových OLE rozhraní API.  
  
 Další informace o ukázkových aplikací najdete v části "MFC ukázka nápovědu k".  
  
## <a name="case-study-oclient-from-mfc-20"></a>Případová studie: OCLIENT z rozhraní MFC 2.0  
 Jak je popsáno výše, [OCLIENT](../visual-cpp-samples.md) je zahrnutý v MFC 2.0 a implementovat OLE s MFC/OLE1. Níže jsou popsané kroky, které tuto aplikaci byl původně převeden na použití tříd MFC/OLE 2. Celou řadu funkcí byly přidány po dokončení počáteční port abychom vám lépe předvedli třídy MFC/OLE. Tyto funkce nebudou uvedena zde; naleznete v ukázce sám sebe pro další informace o těchto pokročilých funkcí.  
  
> [!NOTE]
>  Chyby kompilátoru a podrobný proces byl vytvořen s Visual C++ 2.0. Specifické chybové zprávy a umístění se mohl změnit s Visual C++ 4.0, ale zůstává v platnosti koncepční informace.  
  
## <a name="getting-it-up-and-running"></a>Jeho zprovoznění  
 Přístup k portu OCLIENT vzorku, který se MFC/OLE použitý je tak, že je sestavení a opravy chyb kompilátoru zřejmé, která způsobí. Pokud trvat ukázka OCLIENT MFC 2.0 a kompilaci v této verzi knihovny MFC, zjistíte, že nejsou k dispozici tolika chyby vyřešit. Dále jsou uvedená chyby v pořadí, ve kterém k nim došlo.  
  
## <a name="compile-and-fix-errors"></a>Kompilace a opravy chyb  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 První chyba se týká `COleClientItem::Draw`. V MFC/OLE1 trvalo víc parametrů, než provede verze knihovny MFC/OLE. Další parametry byly často není potřebné a obvykle hodnotu NULL (jako v následujícím příkladu). Tato verze knihovny MFC automaticky určit hodnoty lpWBounds, kdy CDC, který se přitahuje je metafile řadiče domény. Kromě toho parametr pFormatDC již není nutné vzhledem k tomu, že jednu z "atribut řadiče domény" předaná primární řadič domény bude vytvořit rozhraní. Chcete-li tento problém vyřešit, je jednoduše odebrat dva parametry pro volání kreslení velmi NULL.  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 Chyby výše výsledek ze skutečnosti, které všechny `COleClientItem::CreateXXXX` funkcí v MFC/OLE1 vyžaduje, aby jedinečný název předat představovat položku. To se požadavek základního OLE rozhraní API. To není nutné v MFC/OLE 2 vzhledem k tomu, že OLE 2 nepoužívá DDE jako základní mechanismus komunikace (název byl použit v konverzace DDE). Chcete-li tento problém vyřešit, můžete odstranit `CreateNewName` funkce a také všechny odkazy na ni. Je snadné a zjistěte, co jednotlivé funkce MFC/OLE očekává v této verzi jednoduše tak, že umístění kurzor na volání a stisknutím klávesy F1.  
  
 Další oblast, která se významně liší je zpracování schránky OLE 2. S OLE1 používá schránky systému Windows, které rozhraní API pro interakci s do schránky. S aktualizací 2 OLE to provádí pomocí jiný mechanismus. Rozhraní API MFC/OLE1 předpokládá, že byl schránky otevřete před kopírováním `COleClientItem` objektu do schránky. To už není nezbytné a způsobí, že všechny operace se schránkou MFC/OLE selhání. Když upravíte kód odebrání závislostí na `CreateNewName`, mělo odstranit také kód, který otevře a zavře schránky systému Windows.  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 Tyto chyby výsledkem `CMainView::OnInsertObject` obslužné rutiny. Zpracování příkazu "Vložit nový objekt" je další oblastí, kde věcí změnily odlišují. V takovém případě je nejjednodušší jednoduše sloučit původní implementace s poskytnutá objekty AppWizard pro novou aplikaci OLE kontejneru. Ve skutečnosti jde o techniku, který můžete použít pro přenos dalších aplikací. V MFC/OLE1, zobrazí dialogové okno "Objekt vložit" při volání `AfxOleInsertDialog` funkce. V této verzi můžete vytvořit `COleInsertObject` objektu dialogového okna a volání `DoModal`. Kromě toho jsou vytvořeny nové položky OLE s **CLSID** místo classname řetězec. Konečný výsledek by měl vypadat přibližně takto  
  
```  
COleInsertDialog dlg;  
if (dlg.DoModal() != IDOK)  
    return; 
 
BeginWaitCursor();

 
CRectItem* pItem = NULL;  
TRY  
{ *// First create the C++ object  
    pItem = GetDocument()->CreateItem();
ASSERT_VALID(pItem);

 *// Initialize the item from the dialog data.  
    if (!dlg.CreateItem(pItem))  
    AfxThrowMemoryException();
*// any exception will do  
    ASSERT_VALID(pItem);

 *// run the object if appropriate  
    if (dlg.GetSelectionType() == 
    COleInsertDialog::createNewItem) 
    pItem->DoVerb(OLEIVERB_SHOW,
    this);

 *// update right away  
    pItem->UpdateLink();
pItem->UpdateItemRectFromServer();

 *// set selection to newly inserted item  
    SetSelection(pItem);

 pItem->Invalidate();

}  
CATCH (CException,
    e)  
{ *// clean up item  
    if (pItem != NULL)  
    GetDocument()->DeleteItem(pItem);

 
    AfxMessageBox(IDP_FAILED_TO_CREATE);

} 
END_CATCH  
 
EndWaitCursor();
```  
  
> [!NOTE]
>  Vložit nový objekt můžou být různé pro vaši aplikaci):  
  
 Je také nutné zahrnout \<afxodlgs.h >, která obsahuje deklaraci pro `COleInsertObject` třídy dialogového okna, jakož i jiné standardní dialogy poskytované MFC.  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 Tyto chyby jsou způsobeny skutečnost, že některé OLE1 konstanty změnily v OLE 2, i když koncept se shodují. V takovém případě `OLEVERB_PRIMARY` se změnila na `OLEIVERB_PRIMARY`. OLE1 i OLE 2 primární požadavek je obvykle spustit kontejner, když uživatel poklikáním na položku.  
  
 Kromě toho `DoVerb` nyní trvá speciálním parametrem – ukazatel na zobrazení (`CView`*). Tento parametr se používá pouze pro implementaci "Úpravy s náhledem" (nebo aktivace na místě). Teď nastavte tento parametr na hodnotu NULL, protože tato funkce nejsou implementace v tuto chvíli.  
  
 Abyste měli jistotu, že rozhraní nikdy pokusy o místní aktivovat, by měly přepsat `COleClientItem::CanActivate` následujícím způsobem:  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
 
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 V MFC/OLE1 `COleClientItem::GetBounds` a `SetBounds` měla použít pro dotazování a upravit rozsah položku ( **levém** a **horní** členů byly vždy nula). V MFC/OLE 2 to je více přímo nepodporuje `COleClientItem::GetExtent` a `SetExtent`, které pracují s **velikost** nebo `CSize` místo.  
  
 Kód pro vaše nové SetItemRectToServer a UpdateItemRectFromServer volání vypadat takto:  
  
```  
BOOL CRectItem::UpdateItemRectFromServer()  
{  
    ASSERT(m_bTrackServerSize);

 CSize size;  
    if (!GetExtent(&size))  
    return FALSE;    // blank  
 *// map from HIMETRIC to screen coordinates  
 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.LPtoDP(&size);

 } *// just set the item size  
    if (m_rect.Size() != size)  
 { *// invalidate the old size/position  
    Invalidate();
m_rect.right = m_rect.left + size.cx;  
    m_rect.bottom = m_rect.top + size.cy; *// as well as the new size/position  
    Invalidate();

 }  
    return TRUE;  
}  
 
BOOL CRectItem::SetItemRectToServer()  
{ *// set the official bounds for the embedded item  
    CSize size = m_rect.Size();

 {  
    CClientDC screenDC(NULL);

    screenDC.SetMapMode(MM_HIMETRIC);

 screenDC.DPtoLP(&size);

 }  
    TRY 
 {  
    SetExtent(size);
*// may do a wait  
 }  
    CATCH(CException, e)  
 {  
    return FALSE;  // links will not allow SetBounds  
 }  
    END_CATCH 
    return TRUE;  
}  
 
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 V MFC/OLE1 API synchronní volání z kontejneru na server byly *simulované*, protože byl ze své podstaty asynchronní v mnoha případech OLE1. Bylo potřeba zkontrolujte zbývající asynchronního volání probíhá před zpracováním příkazy od uživatele. Poskytuje MFC/OLE1 `COleClientItem::InWaitForRelease` funkce jak to udělat. V MFC/OLE 2 to není nutné, abyste je mohli odebrat přepsání OnCommand CMainFrame všechny společně.  
  
 V tomto okamžiku se OCLIENT zkompilování a odkaz.  
  
## <a name="other-necessary-changes"></a>Další potřebné změny  
 Existuje několik možností, které neprovádí které OCLIENT spuštění, ale. Je lepší teď místo později tyto problémy opravit.  
  
 Nejprve je nezbytné k chybě při inicializaci knihoven OLE. To se provádí volání `AfxOleInit` z `InitInstance`:  
  
```  
if (!AfxOleInit())  
{  
    AfxMessageBox("Failed to initialize OLE libraries");

    return FALSE;  
}  
```  
  
 Je také vhodné zkontrolovat virtuální funkce pro parametr zobrazit změny. Jeden takové funkce je `COleClientItem::OnChange`, přepsaného každou aplikaci MFC/OLE kontejneru. Prohlížením online nápovědy, uvidíte, že byl přidán navíc 'DWORD dwParam'. Nové CRectItem::OnChange vypadá takto:  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
    if (m_bTrackServerSize&& 
 !UpdateItemRectFromServer())  
 { *// Blank object  
    if (wNotification == OLE_CLOSED)  
 { *// no data received for the object - destroy it  
    ASSERT(!IsVisible());

 GetDocument()->DeleteItem(this);

    return; // no update (item is gone now)  
 }  
 }  
    if (wNotification != OLE_CLOSED)  
    Dirty();
Invalidate();
*// any change will cause a redraw  
}  
```  
  
 V MFC/OLE1 – aplikace typu kontejner odvozené třídy dokumentu z `COleClientDoc`. V MFC/OLE 2 bylo odstraněno této třídy a nahrazuje `COleDocument` (této nové organizace je snazší vytvářet aplikace typu server/kontejner). Je **#define** která se mapuje `COleClientDoc` k `COleDocument` zjednodušit portování aplikací MFC/OLE1 do MFC/OLE 2, jako je například OCLIENT. Jedna z funkcí není poskytl `COleDocument` který byl poskytnut `COleClientDoc` je zpráva standardních příkazů položek mapování. Děje se tak serverové aplikace, které také používají `COleDocument` (nepřímo), nemají s nimi nároky na tyto obslužné rutiny příkazů dokud je server/kontejner aplikace. Je třeba přidat do mapy zpráv CMainDoc následující položky:  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE,
    OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK,
    OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS,
    OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS,
    COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST,
    OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT,
    OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT,
    OnEditConvert)  
```  
  
 Implementace všechny tyto příkazy se v `COleDocument`, což je základní třídu pro dokument.  
  
 V tomto okamžiku OCLIENT je funkční aplikaci kontejneru OLE. Je možné vložit položky jakéhokoli typu (OLE1 nebo OLE 2). Vzhledem k tomu, že není implementována nezbytného kódu povolit aktivace na místě, se v samostatném okně mnohem jako s OLE1 upravit položky. Další část popisuje potřebné změny, které povolit úpravy v místě (někdy nazývané "Úpravy s náhledem").  
  
## <a name="adding-visual-editing"></a>Přidání "Úpravy s náhledem"  
 Jedním z nejvíce zajímavé funkce OLE je aktivace na místě (nebo "Úpravy s náhledem"). Tato funkce umožňuje serverová aplikace převzít kontrolu nad části kontejneru uživatelské rozhraní, poskytuje pohodlnější způsob jednotného úpravy rozhraní pro uživatele. K implementaci aktivace na místě, abyste OCLIENT, některé speciální prostředky nutné přidat, a zároveň i některé další kód. Tyto prostředky a kód jsou obvykle poskytovány objekty AppWizard – ve skutečnosti většinu sem kód byla vždy pouze vypůjčí přímo z čerstvého objekty AppWizard aplikace s podporou "Kontejner".  
  
 Nejprve je potřeba přidat prostředek nabídky má být použit při určitá položka, která je aktivní na místě. Tento prostředek navíc nabídky můžete vytvořit v jazyce Visual C++ zkopírováním IDR_OCLITYPE prostředků a odebrat všechny uzly s výjimkou souborů a okna automaticky otevíraná okna. Mezi v souboru a okna automaticky otevíraná okna k označení oddělení skupiny jsou vloženy dva oddělovacích pruhů (by měl vypadat jako: soubor &#124; &#124; okno). Další informace o významu těchto oddělovačů a způsob sloučení nabídky serveru a kontejneru najdete v části "Nabídky a prostředky: slučování nabídek" v *OLE 2 třídy*.  
  
 Až budete mít tyto nabídky vytvořen, budete muset umožní framework vědět o nich. To se provádí volání `CDocTemplate::SetContainerInfo` šablony dokumentu předtím, než přidáte do seznamu šablony dokumentu ve vašem InitInstance. Nový kód k registraci šablona dokumentu vypadá takto:  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE, 
    RUNTIME_CLASS(CMainDoc), 
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame  
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```   
  
 Prostředek IDR_OLECLITYPE_INPLACE je speciální místního prostředku vytvořeného v jazyce Visual C++.  
  
 Pokud chcete povolit aktivace na místě, jsou některé věci, které je potřeba změnit v obou `CView` (CMainView) odvozené třídy a taky `COleClientItem` odvozené třídy (CRectItem). Všechna tato přepsání jsou poskytovány objekty AppWizard a většina implementace budou pocházet přímo z výchozí objekty AppWizard aplikaci.  
  
 V prvním kroku tohoto portu, byla zakázána aktivace na místě zcela přepsáním `COleClientItem::CanActivate`. Toto přepsání, měla by být odebrána pro povolení aktivace na místě. Kromě toho byl předán NULL všechna volání `DoVerb` (jsou uvedeny dvě z nich) kvůli poskytování zobrazení pouze nezbytné pro aktivace na místě. Chcete-li plně implementovat aktivace na místě, je nutné předat správné zobrazení v `DoVerb` volání. Je jedním z těchto v `CMainView::OnInsertObject`:  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);
```  
  
 Jiné je v `CMainView::OnLButtonDblClk`:  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```  
  
 Je nutné přepsat `COleClientItem::OnGetItemPosition`. Tato hodnota informuje server umístění její okno relativně ke kontejneru okno Položka po aktivaci. Pro OCLIENT jeho implementace je jednoduchá:  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 Většina serverů taky implementovat, co se nazývá "místní Změna velikosti." To umožňuje serveru okno na velikost a přesunout, když uživatel upravuje položky. Kontejner musí být součástí tuto akci, protože přesunutí nebo změnou velikosti okna obvykle ovlivňuje umístění a velikost v rámci samotného dokumentu kontejneru. Implementace pro OCLIENT synchronizuje interní rámeček udržované m_rect s nové umístění a velikost.  
  
```  
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
  
 V tomto okamžiku není dostatek kód umožňující položku být aktivována na místě a jak nakládat s Změna velikosti a přesunutí položce, když je aktivní, ale žádný kód vám umožní uživatelům ukončit relaci úprav. I když některé servery budou tuto funkčnost zajistit sami pomocí klávesy ESC zpracování, je doporučeno, že kontejnery poskytovat dva způsoby, jak deaktivovat položku: (1) kliknutím na mimo položky a (2) po stisknutí klávesy řídicí.  
  
 Pro klíč řídicí přidání akcelerátoru s Visual C++, která se mapuje na příkaz vk_escape – klíč, přidá se k prostředkům ID_CANCEL_EDIT. Následuje obslužná rutina pro tento příkaz:  
  
```  
// The following command handler provides the standard  
// keyboard user interface to cancel an in-place  
// editing session.void CMainView::OnCancelEdit()  
{ *// Close any in-place active item on this view.  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->Close();
ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);

}  
```  
  
 Pro zpracování případu, kdy uživatel klikne na mimo položky, přidejte následující kód do začátku `CMainView::SetSelection`:  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& pActiveItem != pNewSel)  
    pActiveItem->Close();

} 
 
```  
  
 Pokud je položka místní aktivní, měl by mít fokus. Abyste měli jistotu, že je tomu zpracování OnSetFocus tak, aby fokus se vždy přenese na aktivní položku při zobrazení bude vybrán:  
  
```  
// Special handling of OnSetFocus and OnSize are required   
// when an object is being edited in-place.  
void CMainView::OnSetFocus(CWnd* pOldWnd)  
{  
    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL&& 
    pActiveItem->GetItemState() == COleClientItem::activeUIState)  
 { *// need to set focus to this item if it is same view  
    CWnd* pWnd = pActiveItem->GetInPlaceWindow();
if (pWnd != NULL)  
 {  
    pWnd->SetFocus();
*// don't call the base class  
    return; 
 }  
 }  
 
    CView::OnSetFocus(pOldWnd);

} 
```  
  
 Při změně velikosti zobrazení, je třeba upozornit active položku rámeček výstřižek došlo ke změně. K tomu je zadat obslužnou rutinu pro `OnSize`:  
  
```  
void CMainView::OnSize(UINT nType,
    int cx,
    int cy)  
{  
    CView::OnSize(nType,
    cx,
    cy);

    COleClientItem* pActiveItem = 
    GetDocument()->GetInPlaceActiveItem(this);

 if (pActiveItem != NULL)  
    pActiveItem->SetItemRects();

} 
```  
  
## <a name="case-study-hiersvr-from-mfc-20"></a>Případová studie: HIERSVR z rozhraní MFC 2.0  
 [HIERSVR](../visual-cpp-samples.md) byla také součástí MFC 2.0 a implementovat OLE s MFC/OLE1. Tato poznámka stručně popisuje kroky, které tuto aplikaci byl původně převeden na použití tříd MFC/OLE 2. Po dokončení počáteční port abychom vám lépe předvedli třídy MFC/OLE 2, byly přidány celou řadu funkcí. Tyto funkce nebudou uvedena zde; naleznete v ukázce sám sebe pro další informace o těchto pokročilých funkcí.  
  
> [!NOTE]
>  Chyby kompilátoru a podrobný proces byl vytvořen s Visual C++ 2.0. Specifické chybové zprávy a umístění se mohl změnit s Visual C++ 4.0, ale zůstává v platnosti koncepční informace.  
  
## <a name="getting-it-up-and-running"></a>Jeho zprovoznění  
 Přístup k portu HIERSVR vzorku, který se MFC/OLE použitý je tak, že je sestavení a opravy chyb kompilátoru zřejmé, která způsobí. Pokud trvat ukázka HIERSVR MFC 2.0 a kompilaci v této verzi knihovny MFC, zjistíte, že nejsou k dispozici mnoho chyb řešení (i když jsou více než s ukázkou OCLIENT). Chyby v pořadí, ve kterém se obvykle objevují jsou popsané níže.  
  
## <a name="compile-and-fix-errors"></a>Kompilace a opravy chyb  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 Tato první chyba poukazuje na mnohem větší problém s `InitInstance` funkce pro servery. Inicializace požadována pro OLE server je pravděpodobně jednou z největších změn, které budete muset udělat aplikace MFC/OLE1 ho systémem. Nejlepším krokem je podívejte se na objekty AppWizard vytvoří pro OLE server a upravit kód podle potřeby. Zde jsou některé body třeba vzít v úvahu:  
  
 Je potřeba při volání inicializace knihovny OLE `AfxOleInit`  
  
 V objektu šablony dokumentu nastavit popisovače prostředku serveru a informace o třídě runtime, který nejde nastavit s volat SetServerInfo `CDocTemplate` konstruktor.  
  
 Nezobrazovat v hlavním okně aplikace, pokud je k dispozici na příkazovém řádku /Embedding.  
  
 Budete potřebovat **GUID** pro dokument. Toto je jedinečný identifikátor pro typ vašeho dokumentu (128 bitů). Objekty AppWizard vytvoří za vás, takže pokud se zde můžete použít techniky popsané kopírování nový kód z nové objekty AppWizard generované serverové aplikace, můžete jednoduše "kradou" identifikátor GUID z této aplikace. Pokud ne, můžete použít Guidgen –. EXE nástroje v adresáři BIN.  
  
 Je nutné "připojit" vaší `COleTemplateServer` objekt, který má šablona dokumentu voláním `COleTemplateServer::ConnectTemplate`.  
  
 Aktualizace registru systém při spuštění samostatné aplikace. Tímto způsobem, pokud se uživatel přesune. EXE pro vaši aplikaci, spuštění z jeho novém umístění zaktualizuje databázi registrace systému Windows tak, aby odkazoval na nové umístění.  
  
 Po použití všechny tyto změny podle objekty AppWizard vytvoří pro `InitInstance`, `InitInstance` (a související identifikátor GUID) pro HIERSVR vypadat takto:  
  
```  
// this is the GUID for HIERSVR documents  
static const GUID BASED_CODE clsid = 
 { 0xA0A16360L,
    0xC19B,
    0x101A, { 0x8C,
    0xE5,
    0x00,
    0xDD,
    0x01,
    0x11,
    0x3F,
    0x12 } };  
 
/////////////////////////////////////////////////////////////////////////////  
// COLEServerApp initialization  
 
BOOL COLEServerApp::InitInstance()  
{ *// OLE 2 initialization  
    if (!AfxOleInit())  
 {  
    AfxMessageBox("Initialization of the OLE failed!");

    return FALSE;  
 }  
 *// Standard initialization  
    LoadStdProfileSettings();

// Load standard INI file options   
 *// Register document templates  
    CDocTemplate* pDocTemplate;  
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,  
    RUNTIME_CLASS(CServerDoc), 
    RUNTIME_CLASS(CMDIChildWnd), 
    RUNTIME_CLASS(CServerView));

 pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);

    AddDocTemplate(pDocTemplate);

 *// create main MDI Frame window  
    CMainFrame* pMainFrame = new CMainFrame;  
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))  
    return FALSE;  
    m_pMainWnd = pMainFrame;  
 
    SetDialogBkColor();
*// gray look  
 *// enable file manager drag/drop and DDE Execute open  
    m_pMainWnd->DragAcceptFiles();
EnableShellOpen();

 
    m_server.ConnectTemplate(clsid,
    pDocTemplate,
    FALSE);

    COleTemplateServer::RegisterAll();

 *// try to launch as an OLE server  
    if (RunEmbedded())  
 { *// "short-circuit" initialization -- run as server!  
    return TRUE;  
 }  
    m_server.UpdateRegistry();
RegisterShellFileTypes();

 *// not run as OLE server,
    so show the main window  
    if (m_lpCmdLine[0] == '\0')  
 { *// create a new (empty) document  
    OnFileNew();

 }  
    else 
 { *// open an existing document  
    OpenDocumentFile(m_lpCmdLine);

 }  
 
    pMainFrame->ShowWindow(m_nCmdShow);

 pMainFrame->UpdateWindow();

 
    return TRUE;  
}  
```  
  
 Si všimnete, že výše uvedený kód odkazuje nové ID prostředku IDR_HIERSVRTYPE_SRVR_EMB. Toto je nabídky prostředek má být použit při dokument, který se vloží v jiném kontejneru je upravit. V MFC/OLE1 pozměněna specifické pro úpravy vložené položky nabídky položky za chodu. Pomocí strukturu úplně jinou nabídky při úpravě položku vložená místo úpravy dokumentu na základě souborů je mnohem jednodušší zadejte jiné uživatelské rozhraní pro tyto dva samostatné režimy. Jak uvidíte později, používá se při úpravě vložený objekt místní prostředek zcela samostatné nabídky.  
  
 Pokud chcete vytvořit tento prostředek, načtení skriptu prostředků do Visual C++ a zkopírujte existující prostředek IDR_HIERSVRTYPE nabídky. Přejmenujte nový prostředek IDR_HIERSVRTYPE_SRVR_EMB (je to stejné zásady vytváření názvů, který používá objekty AppWizard). Dále změňte "Uložit soubor" na "Soubor Update"; Poskytněte příkaz id_file_update – ID. Také změníte "Soubor uložit jako" na "Soubor uložit kopii jako"; Poskytněte příkaz id_file_save_copy_as – ID. Rozhraní framework poskytuje implementaci i z těchto příkazů.  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 Existuje několik chyb způsobených přepis metody `OnSetData`, protože odkazuje na **OLESTATUS** typu. **OLESTATUS** způsob OLE1 vrátila chyby. To se změnila na **HRESULT** ve OLE 2, i když MFC obvykle převádí **HRESULT** do `COleException` obsahující chyby. V tomto konkrétním případě přepis metody `OnSetData` již potřeby proto nejjednodušší cesta je jeho odebrání.  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 `COleServerItem` Konstruktor přebírá další parametr 'BOOL'. Tento příznak určuje, jak se provádí správa paměti na `COleServerItem` objekty. Nastavit na hodnotu TRUE, zpracovává rozhraní správy paměti tyto objekty – jejich odstranění, když již nejsou potřebné. Používá HIERSVR `CServerItem` (odvozený z `COleServerItem`) objektů v rámci nativní dat, takže budete tento příznak nastavit na hodnotu FALSE. Díky tomu HIERSVR určit, když je odstraněn každou položku serveru.  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 Jak tyto chyby implikují, jsou některé 'čistý virtuální, funkce, které nebyly přepsány v CServerItem. Nejpravděpodobnější příčinou je fakt, že se změnil na OnDraw – seznam parametrů. Chcete-li tuto chybu opravit, změňte `CServerItem::OnDraw` takto (i deklarace v svritem.h):  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC,
    CSize& rSize)  
{ *// request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT);

// always in pixels  
    return DoDraw(pDC,
    CPoint(0,
    0),
    FALSE);

}  
```  
  
 Nový parametr je 'parametru rSize'. To umožňuje vyplnit velikost kreslení, pokud je to vhodné. Tato velikost musí být v **HIMETRIC**. V takovém případě není vhodné k vyplnění tuto hodnotu v, takže volá framework `OnGetExtent` načíst v rozsahu. Pro tento postup, budete mít k implementaci `OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect,
    CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
    return COleServerItem::OnGetExtent(dwDrawAspect,
    rSize);

 
    rSize = CalcNodeSize();
return TRUE;  
}  
 
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 Ve funkci CServerItem::CalcNodeSize velikost položky jsou převedeny na **HIMETRIC** a uložené v *m_rectBounds*. Nedokumentovanými '*m_rectBounds*' členem `COleServerItem` neexistuje (jeho částečně nahradila *m_sizeExtent*, ale v OLE 2 Tento člen má mírně odlišné použití než *m_rectBounds* nebyla v OLE1). Místo nastavení **HIMETRIC** velikost do této členské proměnné, budete ho vrátit. Tato návratová hodnota se používá v `OnGetExtent`, dřív implementovaná.  
  
```  
CSize CServerItem::CalcNodeSize()  
{  
    CClientDC dcScreen(NULL);

 
    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,  
    m_strDescription.GetLength());

 m_sizeNode += CSize(CX_INSET* 2,
    CY_INSET* 2);

 *// set suggested HIMETRIC size  
    CSize size(m_sizeNode.cx,
    m_sizeNode.cy);

    dcScreen.SetMapMode(MM_HIMETRIC);

 dcScreen.DPtoLP(&size);

    return size;  
}  
```  
  
 CServerItem také přepsání `COleServerItem::OnGetTextData`. Tato funkce je zastaralé v prostředí MFC/OLE a je nahrazena jiný mechanismus. Verze MFC 3.0 vzorku MFC OLE [HIERSVR](../visual-cpp-samples.md) implementuje tuto funkci přepsáním `COleServerItem::OnRenderFileData`. Tato funkce není důležité pro tento základní port, proto můžete odebrat OnGetTextData přepsání.  
  
 Existuje mnoho další chyby v svritem.cpp, které nebyly vyřeší. Nejsou "Skutečná" chyby – jenom chyby způsobené předchozí chyby.  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard` již nepodporuje příznak 'bIncludeNative'. Nativní data (data naprogramovaný funkce serializace položku serveru) je vždy kopírovat, takže odeberete první parametr. Kromě toho `CopyToClipboard` vyvolá výjimku při chybě místo vrací hodnotu FALSE. Změňte kód pro CServerView::OnEditCopy takto:  
  
```  
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
  
 I když vyplývající z kompilace na verzi MFC 2.0 HIERSVR, než bylo pro stejnou verzi nástroje OCLIENT více chybám, byly ve skutečnosti méně změn.  
  
 V tomto okamžiku HIERSVR bude zkompilování a propojit a fungovat jako OLE server, ale bez úpravy funkce na místě, které budou vedle implementované.  
  
## <a name="adding-visual-editing"></a>Přidání "Úpravy s náhledem"  
 Pokud chcete přidat do této aplikace na serveru "Úpravy s náhledem" (nebo aktivace na místě), jsou pouze několik věcí, které musí postará o:  
  
-   Budete potřebovat speciální nabídky prostředek má být použit při položka je na místě aktivní.  
  
-   Tato aplikace má panel nástrojů, takže musíte panel nástrojů s jenom podmnožinu normální nástrojů tak, aby odpovídala na serveru k dispozici příkazů nabídky (odpovídá prostředků nabídek uvedených výše).  
  
-   Budete potřebovat nové třídy odvozené od `COleIPFrameWnd` , který poskytuje místní uživatelské rozhraní (podobně jako CMainFrame, odvozené od `CMDIFrameWnd`, poskytuje uživatelské rozhraní MDI).  
  
-   Je potřeba říct o tyto speciální prostředky a třídy rozhraní.  
  
 Prostředek nabídky je snadné vytvořit. Spusťte Visual C++, kopírování prostředků nabídky IDR_HIERSVRTYPE do nabídky prostředek s názvem IDR_HIERSVRTYPE_SRVR_IP. V nabídce upravte tak, aby jsou ponechána pouze vyskakovací nabídky Upravit a nápovědy. Přidejte dva oddělovače do nabídky mezi nabídky Upravit a nápovědy (by měl vypadat jako: Upravit &#124; &#124; Nápověda). Další informace o významu těchto oddělovačů a způsob sloučení nabídky serveru a kontejneru, najdete v části "Nabídky a prostředky: slučování nabídek" v *OLE 2 třídy*.  
  
 Rastrový obrázek pro panel nástrojů podmnožina lze snadno vytvořit tak, že zkopírujete z čerstvého objekty AppWizard generované aplikací s možností "Server" zaškrtnutí. Tento rastrový obrázek lze importovat do Visual C++. Nezapomeňte poskytnout ID IDR_HIERSVRTYPE_SRVR_IP bitové mapy.  
  
 Třídy odvozené od `COleIPFrameWnd` lze kopírovat z aplikace objekty AppWizard generované s také podpora serveru. Zkopírujte oba soubory, IPFRAME. CPP a IPFRAME. H a přidat je do projektu. Ujistěte se, že `LoadBitmap` volání odkazuje na IDR_HIERSVRTYPE_SRVR_IP rastrový obrázek vytvořili v předchozím kroku.  
  
 Teď, když jsou vytvořeny nové prostředky a třídy, přidání nezbytného kódu tak, aby rozhraní ví o tyto (a ví, že tuto aplikaci nyní podporuje úpravy na místě). K tomu je potřeba některé další parametry pro přidání `SetServerInfo` volání v `InitInstance` funkce:  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```  
  
 Je nyní připraven ke spuštění na místě v kontejneru, který taky podporuje aktivace na místě. Je ale, jeden menších chyb stále skrývá se v kódu. HIERSVR podporuje z kontextové nabídky, zobrazí, když uživatel stiskne pravým tlačítkem myši. Tato nabídka funguje, když je zcela otevřený HIERSVR, ale nefunguje při úpravě vnoření místní. Z důvodu můžete připnuté na tento jediný řádek kódu v CServerView::OnRButtonDown:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```  
  
 Všimněte si, odkaz na *`AfxGetApp()->m_pMainWnd*`. Server je aktivován na místě, má hlavní okno a m_pMainWnd nastavená, ale je obvykle neviditelná. Kromě toho toto okno odkazuje *hlavní* okno aplikace rámec okna MDI, který se zobrazí, když server je plně otevření nebo spuštění samostatné. Neodkazuje na aktivní rámec okna – když místní aktivovat tedy rámeček okno odvozené z `COleIPFrameWnd`. Chcete-li získat správné aktivní okno i v případě, že místní úpravy, tato verze knihovny MFC přidá novou funkci, `AfxGetMainWnd`. Obecně platí, měli byste použít tuto funkci místo *`AfxGetApp()->m_pMainWnd*`. Tento kód je potřeba změnit takto:  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x,
    point.y,
    AfxGetMainWnd());
```  
  
 Nyní máte server OLE minimálně povoleno funkčnosti aktivace na místě. Ale ještě nejsou k dispozici s MFC/OLE 2, které nebyly k dispozici v MFC/OLE1 řadu funkcí. Naleznete v ukázce HIERSVR pro další návrhy na funkce, které chcete implementovat. Níže jsou uvedeny některé funkce, které implementuje HIERSVR:  
  
-   Přibližování true chování WYSISYG s ohledem na kontejneru.  
  
-   Přetáhněte či přetažení a formát vlastní schránky.  
  
-   Posouvání okna kontejneru jako výběr se změní.  
  
 Ukázka HIERSVR v MFC 3.0 také používá mírně odlišný návrhu pro položky na serveru. To pomáhá šetřit paměť a zajišťuje flexibilnější vaše odkazy. 2.0 verzi HIERSVR každý uzel ve stromové struktuře *je a* `COleServerItem`. `COleServerItem` představuje trochu další režii než je nezbytně nutné pro každý z těchto uzlů, ale `COleServerItem` je vyžadována pro každé aktivní připojení. Je ale ve většině případů jen několik aktivních odkazů v daném okamžiku. Chcete-li to efektivnější, HIERSVR v této verzi knihovny MFC odděluje uzlu ze `COleServerItem`. Má oba CServerNode a `CServerItem` třídy. `CServerItem` (Odvozený z `COleServerItem`) je vytvořen pouze podle potřeby. Jakmile kontejneru (nebo kontejnery) přestat používat tuto konkrétní odkaz na příslušném uzlu, je odstraněn objekt CServerItem, přidružené CServerNode. Tento návrh je efektivnější a flexibilnější. Je flexibilní se dodává při plánování práce s více odkazy pro výběr. Ani jeden z těchto dvou verzích HIERSVR podporovat více výběrů, ale je mnohem snazší, chcete-li přidat (a podporu odkazů na tyto možnosti) s verzí MFC 3.0 HIERSVR, protože `COleServerItem` je oddělená od nativní data.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

