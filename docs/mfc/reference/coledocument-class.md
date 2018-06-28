---
title: Třída COleDocument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f492e7fc3e29c74caba7303179b72c5dacad72e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040685"
---
# <a name="coledocument-class"></a>COleDocument – třída
Základní třída pro OLE dokumenty, které podporují úpravy s náhledem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|Vytvoří `COleDocument` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|Přidá položku do seznamu položek udržované dokumentu.|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Nastaví tiskových cílové zařízení pro všechny klientské položky v dokumentu.|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Způsobí, že dokumenty k uložení souboru formátu OLE strukturovaných úložiště.|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Vrátí položku OLE, který je aktuálně místní aktivní.|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|Získá další položka klienta pro iterace.|  
|[COleDocument::GetNextItem](#getnextitem)|Získá další položka dokumentu pro iterace.|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|Získá položku Další server pro iterace.|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Vrátí primární vybrané položky OLE v dokumentu.|  
|[COleDocument::GetStartPosition](#getstartposition)|Získá počáteční pozice zahájíte iterací.|  
|[COleDocument::HasBlankItems](#hasblankitems)|Kontroluje prázdné položky v dokumentu.|  
|[COleDocument::OnShowViews](#onshowviews)|Voláno, pokud se změní na dokument viditelný nebo neviditelná.|  
|[COleDocument::RemoveItem](#removeitem)|Odebere položku ze seznamu položek udržované dokumentu.|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Označí dokumentu jako v případě, že některé z obsažených položek OLE změnili upravit.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Zpracovává události v příkazu nabídky Změnit ikonu.|  
|[COleDocument::OnEditConvert](#oneditconvert)|Zpracovává server převod vložené nebo propojené objekt z jednoho typu do jiného.|  
|[COleDocument::OnEditLinks](#oneditlinks)|Zpracovává události v na odkazy v nabídce Upravit.|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s dokumentem připojen.|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Voláno rámcem aktualizovat příkaz uživatelského rozhraní pro položku nabídky ikonu upravit nebo změnit.|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Voláno rámcem aktualizovat příkaz uživatelského rozhraní pro položku nabídky odkazů pro úpravy.|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Voláno rámcem aktualizace příkaz uživatelského rozhraní pro úpravy / *ObjectName* nabídky a k němu přistupovat z upravit příkaz podnabídky / *ObjectName*.|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Voláno rámcem aktualizovat příkaz uživatelského rozhraní pro položku nabídky Vložit jinak.|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Voláno rámcem aktualizovat příkaz uživatelského rozhraní pro položku nabídky vložení.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDocument` je odvozený od `CDocument`, což umožňuje vaší aplikace rozhraní OLE používat architektuře dokument/zobrazení poskytované knihovny Microsoft Foundation Class.  
  
 `COleDocument` zpracovává dokumentu jako kolekce [CDocItem](../../mfc/reference/cdocitem-class.md) objekty zpracování položek OLE. Kontejner a serverové aplikace vyžadují takové architekturu, protože své dokumenty musí být schopen obsahovat OLE – položky. [COleServerItem](../../mfc/reference/coleserveritem-class.md) a [COleClientItem](../../mfc/reference/coleclientitem-class.md) třídy, i odvozený od `CDocItem`, Správa interakcí mezi aplikacemi a OLE – položky.  
  
 Pokud píšete aplikace jednoduché kontejneru, odvozena třídě dokumentu z `COleDocument`. Pokud píšete kontejneru aplikace, která podporuje propojování vložené položky obsažený v jeho dokumenty, odvozena třídě dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Pokud píšete serveru aplikace nebo kombinaci typu server/kontejner odvozena třídě dokumentu z [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` a `COleServerDoc` jsou odvozeny od `COleDocument`, takže tyto třídy dědí všechny služby k dispozici v `COleDocument` a `CDocument`.  
  
 Chcete-li použít `COleDocument`, odvození třídy z něj a přidá funkce pro správu aplikace jiných než OLE data a také vložené nebo propojené položky. Pokud definujete `CDocItem`-odvozených třídách k uložení dat nativní aplikace, můžete použít výchozí implementace definované `COleDocument` k uložení OLE a jiných než OLE data. Můžete taky navrhnout vlastní datové struktury pro ukládání dat jiných než OLE odděleně od položky OLE. Další informace najdete v článku [kontejnery: složené soubory](../../mfc/containers-compound-files.md)...  
  
 `CDocument` podporuje odesílání vašeho dokumentu prostřednictvím e-mailu, pokud je k dispozici podporu pošty (MAPI). `COleDocument` byl aktualizován [onfilesendmail –](#onfilesendmail) správně zpracovat složené dokumenty. Další informace najdete v článcích [MAPI](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 Volání této funkce k přidání položky do dokumentu.  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Ukazatel na dokument položku přidávanou.  
  
### <a name="remarks"></a>Poznámky  
 Není potřeba explicitně volání této funkce, když je volána metodou `COleClientItem` nebo `COleServerItem` konstruktor, který přijímá ukazatel na dokument.  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 Volání této funkce, chcete-li změnit tiskových cílové zařízení pro všechny vložených [COleClientItem](../../mfc/reference/coleclientitem-class.md) položky v dokumentu kontejneru vaší aplikace.  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Parametry  
 *ptd*  
 Ukazatel na **DVTARGETDEVICE** datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může být **NULL**.  
  
 *PPD*  
 Ukazatel na **PRINTDLG** datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce aktualizací tiskových cílové zařízení pro všechny položky, ale neaktualizuje mezipaměť prezentace pro tyto položky. Chcete-li aktualizovat mezipaměť prezentace pro položku, volejte [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).  
  
 Argumenty, které se tato funkce obsahují informace, které OLE používá k identifikaci cílové zařízení. [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktura obsahuje informace, které používá systém Windows k chybě při inicializaci běžné dialogové okno tisku. Jakmile uživatel zavře dialogové okno, Windows vrací informace o výběr uživatele v této struktuře. `m_pd` Členem [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objekt **PRINTDLG** struktury.  
  
 Další informace najdete v tématu [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) struktura ve Windows SDK.  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 Vytvoří `COleDocument` objektu.  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 Pokud chcete uložit dokument pomocí složené formát volání této funkce.  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnable*  
 Určuje, zda je povoleno podpora složené souborů.  
  
### <a name="remarks"></a>Poznámky  
 To je také označován strukturovaných úložiště. Obvykle volání této funkce z konstruktoru vaší `COleDocument`-odvozené třídy. Další informace o složených dokumentů, najdete v článku [kontejnery: složené soubory](../../mfc/containers-compound-files.md)...  
  
 Pokud tuto funkci člen Nevolejte, dokumenty budou uloženy ve formátu souboru nestrukturovaném ("ploché").  
  
 Po podpora složené souborů je povoleno nebo zakázáno pro dokument, neměli byste ji měnit nastavení během doby platnosti dokumentu.  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 Volání této funkce můžete získat OLE položku, která je aktuálně aktivovat zavedené v rámci okna obsahující zobrazení identifikovaný *pWnd*.  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na okno, které zobrazí dokument kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na jednom, místní aktivní OLE položku; **NULL** Pokud neexistuje žádná položka OLE aktuálně ve stavu "místní aktivní".  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 Volání této funkce opakovaně pro všechny klientské položky v dokumentu přístup.  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Odkaz na **pozice** hodnotu sadu voláním předchozí `GetNextClientItem`; počáteční hodnota je vrácený `GetStartPosition` – členská funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku klienta v dokumentu, nebo **NULL** Pokud neexistují žádné další položky klienta.  
  
### <a name="remarks"></a>Poznámky  
 Po každé volání hodnotu *pos* je nastaven pro další položky v dokumentu, který může nebo nemusí být položku klienta.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 Volání této funkce opakovaně pro každou položku v dokumentu přístup.  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Odkaz na **pozice** hodnotu sadu voláním předchozí `GetNextItem`; počáteční hodnota je vrácený `GetStartPosition` – členská funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument položky na zadané pozici.  
  
### <a name="remarks"></a>Poznámky  
 Po každé volání hodnotu *pos* je nastaven na **pozice** hodnota další položky v dokumentu. Pokud je načtený element posledním prvkem v dokumentu, nová hodnota *pos* je **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 Volání této funkce opakovaně pro každý server položky v dokumentu přístup.  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Odkaz na **pozice** hodnotu sadu voláním předchozí `GetNextServerItem`; počáteční hodnota je vrácený `GetStartPosition` – členská funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku serveru v dokumentu, nebo **NULL** Pokud neexistují žádné další položky serveru.  
  
### <a name="remarks"></a>Poznámky  
 Po každé volání hodnotu *pos* je nastaven pro další položky v dokumentu, který může nebo nemusí být položku serveru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 Voláno rámcem načíst aktuálně vybrané položky OLE v zadané zobrazení.  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 *pView*  
 Ukazatel na objekt active zobrazení zobrazení dokumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na hodnotu single vybranou položku OLE; **NULL** Pokud nejsou vybrány žádné položky OLE nebo pokud se více než jedna je vybrána.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vyhledá seznam obsažené OLE položek pro jednu vybranou položku a vrátí ukazatel na ni. Pokud není vybrané žádné položky, nebo pokud je vybrána více než jednu položku, funkce vrátí hodnotu **NULL**. Je nutné přepsat `CView::IsSelected` členské funkce ve třídě zobrazení pro tuto funkci pro práci. Tato funkce přepsání, pokud máte vlastní metodu ukládání obsažených položek OLE.  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 Volání této funkce se získá pozice první položky v dokumentu.  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která slouží k zahájení iterace v rámci položky dokumentu; **NULL** jestli má dokument žádné položky.  
  
### <a name="remarks"></a>Poznámky  
 Předejte hodnotu vrátí `GetNextItem`, `GetNextClientItem`, nebo `GetNextServerItem`.  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 Volání této funkce lze zjistit, zda dokument obsahuje všechny prázdné položky.  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dokument obsahuje všechny prázdné položky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Prázdná položka je jedním jejichž obdélníku je prázdný.  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 Zobrazí dialogové okno OLE změnit ikonu a změní na ikonu představující aktuálně vybrané položky OLE na ikonu, které uživatel vybere v dialogovém okně.  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>Poznámky  
 `OnEditChangeIcon` vytvoří a spustí `COleChangeIconDialog` dialogové okno Změnit ikonu.  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 Zobrazí dialogové okno Převést OLE a aktivuje nebo převede aktuálně vybrané položky OLE podle volby uživatele v dialogovém okně.  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>Poznámky  
 `OnEditConvert` vytvoří a spustí `COleConvertDialog` dialogové okno Převést.  
  
 Příklad převodu převádí do dokumentu WordPad dokumentu Microsoft Wordu.  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 Zobrazí dialogové okno OLE/odkazů pro úpravy.  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>Poznámky  
 `OnEditLinks` vytvoří a spustí `COleLinksDialog` odkazy dialogu, který umožňuje uživatelům změnit propojené objekty.  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 Odešle zprávu přes hostitele trvalé e-mailu (pokud existuje) s dokumentem jako přílohu.  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>Poznámky  
 `OnFileSendMail` volání `OnSaveDocument` k serializaci (bez názvu a upravené dokumenty do dočasného souboru, která se pak posílají pomocí e-mailové Uložit). Pokud dokument byl změněn, není potřeba dočasný soubor; Původní se odesílají. `OnFileSendMail` načte MAPI32. Knihovny DLL, pokud již nebyla načtena.  
  
 Na rozdíl od implementace `OnFileSendMail` pro `CDocument`, tato funkce zpracovává složené soubory správně.  
  
 Další informace najdete v tématu [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md) články...  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 Rozhraní framework volá tuto funkci po dokumentu viditelnost změny stavu.  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>Parametry  
 *bVisible*  
 Určuje, zda dokument má stát viditelný nebo neviditelná.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí verze této funkce neprovede žádnou akci. Přepište Pokud vaše aplikace musí provádět žádné zvláštní zpracování, když se změní viditelnost dokumentu.  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 Voláno rámcem aktualizovat na ikonu změnit v nabídce Upravit.  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Ukazatel na `CCmdUI` struktura, která představuje v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace `Enable` členské funkce `CCmdUI` struktury prostřednictvím *pCmdUI* aktualizace uživatelského rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 `OnUpdateEditChangeIcon` aktualizuje uživatelské rozhraní příkazu v závislosti na tom, zda existuje platné ikona v dokumentu. Potlačí tuto funkci můžete změnit chování.  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 Voláno rámcem aktualizovat na odkazy v nabídce Upravit.  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Ukazatel na `CCmdUI` struktura, která představuje v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace `Enable` členské funkce `CCmdUI` struktury prostřednictvím *pCmdUI* aktualizace uživatelského rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Počínaje první OLE položky v dokumentu, `OnUpdateEditLinksMenu` přistupuje k jednotlivých položek, testuje, zda položka je odkaz a pokud je odkaz, umožňuje příkaz propojení. Potlačí tuto funkci můžete změnit chování.  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 Voláno rámcem aktualizovat *ObjectName* příkazu v nabídce Upravit a dílčí příkaz k němu přistupovat z *ObjectName* příkaz, kde *ObjectName* je název Objekt OLE vložených v dokumentu.  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Ukazatel na `CCmdUI` struktura, která představuje v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace `Enable` členské funkce `CCmdUI` struktury prostřednictvím *pCmdUI* aktualizace uživatelského rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 `OnUpdateObjectVerbMenu` aktualizace *ObjectName* příkazu uživatelské rozhraní v závislosti na tom, zda existuje platný objekt v dokumentu. Pokud objekt existuje, *ObjectName* příkaz v nabídce Upravit je povolen. Pokud je vybraný tento příkaz nabídky, zobrazí se příkaz podnabídky. Příkaz podnabídky obsahuje všechny příkazy příkaz k dispozici pro objekt, jako jsou úpravy, vlastnosti a tak dále. Potlačí tuto funkci můžete změnit chování.  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 Voláno rámcem k určení, zda lze vložit propojené položky OLE ze schránky.  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Ukazatel na `CCmdUI` struktura, která představuje v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace `Enable` členské funkce `CCmdUI` struktury prostřednictvím *pCmdUI* aktualizace uživatelského rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Příkaz nabídky Vložit jinak povolená nebo zakázaná v závislosti na tom, zda položka lze vložit do dokumentu nebo ne.  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 Voláno rámcem k určení, zda lze vložit vložené položky OLE ze schránky.  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 *pCmdUI*  
 Ukazatel na `CCmdUI` struktura, která představuje v nabídce, která vygenerovala příkaz update. Volání obslužné rutiny aktualizace `Enable` členské funkce `CCmdUI` struktury prostřednictvím *pCmdUI* aktualizace uživatelského rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Příkaz nabídky Paste a tlačítko povolených a zakázaných v závislosti na tom, zda položka lze vložit do dokumentu nebo ne.  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 Volání této funkce pro odebrání položky z dokumentu.  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Ukazatel na položku dokumentu odeberou.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle není potřeba explicitně; volání této funkce je volána metodou destruktory pro `COleClientItem` a `COleServerItem`.  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 Volání této funkce označit dokumentu jako v případě, že některé z obsažených položek OLE změnili upravit.  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje rozhraní pro vyzvání uživatele k uložení dokumentu před jeho zavřením, i v případě, že se nezměnil nativní data v dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC KONTEJNERU](../../visual-cpp-samples.md)   
 [Ukázka MFC MFCBIND](../../visual-cpp-samples.md)   
 [CDocument – třída](../../mfc/reference/cdocument-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



