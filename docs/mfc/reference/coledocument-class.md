---
title: Coledocument – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 7f36557a4a993e8abd3004dc59372cc5a089e044
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259747"
---
# <a name="coledocument-class"></a>Coledocument – třída

Základní třída pro dokumenty OLE, které podporují vizuální úpravy.

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
|[COleDocument::AddItem](#additem)|Přidá položku do seznamu položek udržuje dokumentu.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Nastaví tiskové cílovému zařízení pro všechny klientské položky v dokumentu.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Způsobí, že dokumenty mají být uloženy ve formátu souboru strukturovaného úložiště OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Vrátí hodnotu, která je aktuálně místní aktivní položky OLE.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Získá další položku klienta pro iterace.|
|[COleDocument::GetNextItem](#getnextitem)|Získá další položka dokumentu pro iterace.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Získá další položku server pro iterace.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Vrátí primární vybraná položka OLE v dokumentu.|
|[COleDocument::GetStartPosition](#getstartposition)|Získá počáteční pozici zahájíte iterace.|
|[COleDocument::HasBlankItems](#hasblankitems)|Kontroluje prázdné položky v dokumentu.|
|[COleDocument::OnShowViews](#onshowviews)|Volá se, když dokument se stane viditelné nebo neviditelné.|
|[COleDocument::RemoveItem](#removeitem)|Odebere položku ze seznamu položek udržuje dokumentu.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Označí dokumentu jako upravovat žádnou z obsažených položek OLE byl změněn.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Zpracovává události v příkazu nabídky Změnit ikonu.|
|[COleDocument::OnEditConvert](#oneditconvert)|Zpracovává server převod vložený nebo připojený objekt z jednoho typu na jiný.|
|[COleDocument::OnEditLinks](#oneditlinks)|Zpracovává události v příkazu odkazy v nabídce Úpravy.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu se na dokument připojený.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Volá se rozhraním aktualizovat příkaz uživatelského rozhraní pro položku nabídky, upravit nebo změnit ikonu.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Volá se rozhraním aktualizovat příkaz uživatelského rozhraní pro položku nabídky Upravit/odkazy.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Volá se rozhraním, aby aktualizace příkaz uživatelského rozhraní pro úpravy / *ObjectName* nabídky a podnabídky příkaz k němu přistupovat z úpravy / *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Volá se rozhraním aktualizovat příkaz uživatelského rozhraní pro položku nabídky, Vložit jinak.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Volá se rozhraním příkaz uživatelského rozhraní pro položku nabídky Vložit, aktualizovat.|

## <a name="remarks"></a>Poznámky

`COleDocument` je odvozen z `CDocument`, který umožňuje vašim aplikacím OLE, chcete-li využívají architekturu document/view – poskytuje knihovnu Microsoft Foundation Class.

`COleDocument` dokumentu považuje za kolekce [cdocitem –](../../mfc/reference/cdocitem-class.md) objekty zpracování položek OLE. Kontejner a serverové aplikace vyžadují takové architektury, protože jejich dokumenty musí být schopen obsahovat položky OLE. [Odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) a [COleClientItem](../../mfc/reference/coleclientitem-class.md) třídy, obě odvozeny z `CDocItem`, Správa interakcí mezi aplikacemi a položky OLE.

Pokud píšete kontejneru na jednoduchou aplikaci, jsou odvozeny vaše dokumentové třídy z `COleDocument`. Při psaní aplikace typu kontejner, který podporuje propojování vložené položky obsažené v jeho dokumenty, odvodit vaše dokumentové třídy z [colelinkingdoc –](../../mfc/reference/colelinkingdoc-class.md). Pokud vytváříte server aplikace nebo kombinaci typu server/kontejner odvodit vaše dokumentové třídy z [coleserverdoc –](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc` a `COleServerDoc` jsou odvozeny z `COleDocument`, takže tyto třídy dědí všechny služby, které jsou k dispozici v `COleDocument` a `CDocument`.

Chcete-li použít `COleDocument`, odvodit třídu z něj a přidávat funkce pro správu aplikace jiných než OLE a také vložené nebo propojené položky. Pokud definujete `CDocItem`-odvozené třídy pro uložení data nativní aplikace, můžete použít výchozí implementace určené `COleDocument` k uložení OLE a data jiných než OLE. Také si můžete navrhovat vlastní datové struktury pro ukládání dat jiných než OLE odděleně od položky OLE. Další informace najdete v článku [kontejnerů: Složené soubory](../../mfc/containers-compound-files.md)...

`CDocument` zajišťuje podporu pro odesílání dokumentu e-mailem. Pokud je k dispozici podpora e-mailu (MAPI). `COleDocument` byl aktualizován [onfilesendmail –](#onfilesendmail) zpracování složených dokumentů správně. Další informace najdete v článcích [MAPI](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md)...

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="additem"></a>  COleDocument::AddItem

Voláním této funkce přidání položky do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na přidávaná položka dokumentu.

### <a name="remarks"></a>Poznámky

Není potřeba explicitně volat tuto funkci je volán `COleClientItem` nebo `COleServerItem` konstruktor, který přijímá ukazatel na dokument.

##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice

Voláním této funkce, chcete-li změnit tisk cílové zařízení pro všechny vložené [COleClientItem](../../mfc/reference/coleclientitem-class.md) položky v dokumentu kontejneru vaší aplikace.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*ptd*<br/>
Ukazatel `DVTARGETDEVICE` datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může mít hodnotu NULL.

*ppd*<br/>
Ukazatel `PRINTDLG` datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce aktualizuje tisk cílovému zařízení pro všechny položky, ale ne k aktualizaci mezipaměti prezentaci pro tyto položky. Chcete-li aktualizovat mezipaměť prezentaci pro některou položku, zavolejte [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty pro tuto funkci obsahují informace, které OLE se používá k identifikaci cílové zařízení. [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktura obsahuje informace, které Windows používá k inicializaci dialogového okna běžné tisk. Poté, co uživatel zavře dialogové okno, Windows vrátí informace o výběru uživatele v této struktuře. `m_pd` Členem [cprintdialog –](../../mfc/reference/cprintdialog-class.md) je objekt `PRINTDLG` struktury.

Další informace najdete v tématu [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktura v sadě Windows SDK.

Další informace najdete v tématu [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) struktura v sadě Windows SDK.

##  <a name="coledocument"></a>  COleDocument::COleDocument

Vytvoří `COleDocument` objektu.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile

Voláním této funkce, pokud chcete uložit ve formátu souboru složeného dokumentu.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda je povolena podpora složených souborů.

### <a name="remarks"></a>Poznámky

To se také nazývá strukturované úložiště. Obvykle voláním této funkce z konstruktoru vaše `COleDocument`-odvozené třídy. Další informace o složených dokumentů, najdete v článku [kontejnerů: Složené soubory](../../mfc/containers-compound-files.md)...

Pokud není tato členská funkce volána, dokumenty se uloží v nestrukturovaném ("ploché") formátu.

Po Podpora složených souborů povolený nebo zakázaný pro dokument, nastavení by neměla změnit během životnosti dokumentu.

##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem

Volání této funkce získáte OLE položku, která je aktuálně aktivovaná na místě v okně rámce obsahující zobrazení identifikovaný *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno zobrazující dokumentu kontejneru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden, místní aktivní položky OLE.; Hodnota NULL, pokud neexistuje žádná položka OLE aktuálně ve stavu "místní aktivní".

##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem

Voláním této funkce opakovaně přístup ke všem klientské položky v dokumentu.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Odkaz na POZICI hodnota sady předchozí volání `GetNextClientItem`; počáteční hodnota je vrácený `GetStartPosition` členskou funkci.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další klientské položky v dokumentu, nebo hodnota NULL, pokud neexistují žádné další položky klienta.

### <a name="remarks"></a>Poznámky

Po každé volání hodnotu *pos* nastavený pro další položky v dokumentu, který může nebo nemusí být klientské položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>  COleDocument::GetNextItem

Voláním této funkce opakovaně přístup ke každé položky v dokumentu.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Odkaz na POZICI hodnota sady předchozí volání `GetNextItem`; počáteční hodnota je vrácený `GetStartPosition` členskou funkci.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na dokument položky na zadané pozici.

### <a name="remarks"></a>Poznámky

Po každé volání hodnotu *pos* je nastavena na hodnotu pozice na další položku v dokumentu. Pokud po posledním prvku v dokumentu, nová hodnota je načtený element *pos* má hodnotu NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem

Voláním této funkce opakovaně přístup ke každé z položek serveru v dokumentu.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*pos*<br/>
Odkaz na POZICI hodnota sady předchozí volání `GetNextServerItem`; počáteční hodnota je vrácený `GetStartPosition` členskou funkci.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další server položky v dokumentu, nebo hodnota NULL, pokud neexistují žádné další položky serveru.

### <a name="remarks"></a>Poznámky

Po každé volání hodnotu *pos* nastavený pro další položky v dokumentu, který může nebo nemusí být položka serveru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem

Volá se rozhraním pro načtení aktuálně vybraná položka OLE v zadaném náhledu.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Ukazatel na objekt zobrazení aktivního zobrazení dokumentu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden, vybrané položky OLE.; Hodnota NULL, pokud nejsou vybrány žádné položky OLE nebo pokud více než jedna je vybrána.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyhledá seznam omezením OLE pro jednu položku vybrané položky a vrátí ukazatel na něj. Pokud není vybrané žádné položky, nebo pokud existuje více než jedna položka vybrána, funkce vrátí hodnotu NULL. Je nutné přepsat `CView::IsSelected` členské funkce ve třídě zobrazení této funkce pro práci. Tato funkce přepište, pokud máte vlastní způsob ukládání obsažené položky OLE.

##  <a name="getstartposition"></a>  COleDocument::GetStartPosition

Voláním této funkce získá pozici první položky v dokumentu.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

POZICE hodnotu, která slouží k zahájení iterace v rámci dokumentu položek; Hodnota NULL, pokud dokument neobsahuje žádné položky.

### <a name="remarks"></a>Poznámky

Předejte hodnotu vrátí `GetNextItem`, `GetNextClientItem`, nebo `GetNextServerItem`.

##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems

Voláním této funkce určete, jestli dokument obsahuje všechny prázdné položky.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument obsahuje všechny prázdné položky; jinak 0.

### <a name="remarks"></a>Poznámky

Prázdná položka je jednou z jehož obdélníku je prázdný.

##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon

Zobrazí dialogové okno změny ikony OLE a změní ikona představující aktuálně vybraná položka OLE na ikonu, kterou uživatel vybere v dialogovém okně.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Poznámky

`OnEditChangeIcon` umožňuje vytvářet a spouštět `COleChangeIconDialog` dialogové okno změny ikony.

##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert

Zobrazí dialogové okno Převést OLE a aktivuje nebo převede aktuálně vybrané položky OLE podle volby uživatele v dialogovém okně.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Poznámky

`OnEditConvert` umožňuje vytvářet a spouštět `COleConvertDialog` dialogové okno Převést.

Příklad převodu je převod dokumentu Microsoft Wordu do dokumentu WordPad.

##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks

Zobrazí dialogové okno Upravit/odkazů OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Poznámky

`OnEditLinks` umožňuje vytvářet a spouštět `COleLinksDialog` odkazy dialogové okno, které umožňuje uživateli změnit propojené objekty.

##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail

Odešle zprávu přes hostitele rezidenční e-mailu (pokud existuje) s dokumentem jako přílohu.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail` volání `OnSaveDocument` k serializaci (bez názvu a upravené dokumenty do dočasného souboru, kterou pak odesílají prostřednictvím elektronické pošty Uložit). Pokud dokument nebyl změněn, není potřeba dočasný soubor; Původní se odesílají. `OnFileSendMail` načte MAPI32. Knihovny DLL, pokud ho ještě nenačetl.

Na rozdíl od implementace `OnFileSendMail` pro `CDocument`, tato funkce zpracovává složené soubory správně.

Další informace najdete v tématu [MAPI témata](../../mfc/mapi.md) a [Podpora MAPI v MFC](../../mfc/mapi-support-in-mfc.md) články...

##  <a name="onshowviews"></a>  COleDocument::OnShowViews

Rozhraní volá tuto funkci po dokumentu viditelnost změny stavu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*bVisible*<br/>
Určuje, zda dokumentu stal viditelné nebo neviditelné.

### <a name="remarks"></a>Poznámky

Výchozí verze této funkce nemá žádný účinek. Přepište ji, pokud vaše aplikace musí provádět žádné zvláštní zpracování, když se změní viditelnost dokumentu.

##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon

Volá se rozhraním aktualizace změnit ikonu příkaz v nabídce Úpravy.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel `CCmdUI` struktura, která představuje nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateEditChangeIcon` aktualizace uživatelského rozhraní příkaz v závislosti na tom, jestli existuje platná ikona v dokumentu. Tato funkce umožňuje měnit chování přepište.

##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu

Volá se rozhraním aktualizovat odkazy příkaz v nabídce Úpravy.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel `CCmdUI` struktura, která představuje nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Počínaje první položka OLE v dokumentu, `OnUpdateEditLinksMenu` přistupuje ke každé položky, testuje, jestli položka odkaz a pokud je to odkaz povolit příkaz odkazy. Tato funkce umožňuje měnit chování přepište.

##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu

Volá se rozhraním, aby aktualizace *ObjectName* příkaz v nabídce Upravit a k němu přistupovat z podnabídky příkaz *ObjectName* příkaz, kde *ObjectName* je název Objekt OLE vloží do dokumentu.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel `CCmdUI` struktura, která představuje nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateObjectVerbMenu` aktualizace *ObjectName* příkazu uživatelské rozhraní v závislosti na tom, zda je či není platný objekt existuje v dokumentu. Pokud objekt existuje, *ObjectName* povolen příkaz v nabídce Úpravy. Při výběru tohoto příkazu nabídky se zobrazí v podnabídce příkaz. Příkaz podnabídka obsahuje všechny příkazy příkaz k dispozici pro objekt, jako jsou úpravy, vlastnosti a tak dále. Tato funkce umožňuje měnit chování přepište.

##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu

Volá se rozhraním, chcete-li zjistit, zda propojená položka OLE můžete vkládaná ze schránky.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel `CCmdUI` struktura, která představuje nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz nabídky Vložit jinak povolit nebo zakázat v závislosti na tom, zda položka lze vložit do dokumentu nebo ne.

##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu

Volá se rozhraním, chcete-li zjistit, zda lze ze schránky vložit vložené položky OLE.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel `CCmdUI` struktura, která představuje nabídky, která vygeneruje příkazu update. Volání obslužné rutiny aktualizace `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz nabídky Vložit a tlačítko povolených a zakázaných v závislosti na tom, zda položka lze vložit do dokumentu nebo ne.

##  <a name="removeitem"></a>  COleDocument::RemoveItem

Voláním této funkce odeberte položku z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na dokument položky k odebrání.

### <a name="remarks"></a>Poznámky

Obvykle není potřeba explicitně; voláním této funkce je volána metodou destruktory `COleClientItem` a `COleServerItem`.

##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag

Voláním této funkce označíte dokument jako upravovat žádnou z obsažených položek OLE byl změněn.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Poznámky

To umožňuje rozhraní pro výzvu uživateli uložit dokument před jeho zavřením, i v případě, že byl změněn nativní data v dokumentu.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC KONTEJNERU](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC MFCBIND](../../visual-cpp-samples.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
