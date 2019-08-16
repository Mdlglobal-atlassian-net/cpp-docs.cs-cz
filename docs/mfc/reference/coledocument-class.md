---
title: COleDocument – třída
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
ms.openlocfilehash: 666ca54f55c5bb0dd4070a4984500dc19dc9d372
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504041"
---
# <a name="coledocument-class"></a>COleDocument – třída

Základní třída pro dokumenty OLE, které podporují úpravy vizuálů.

## <a name="syntax"></a>Syntaxe

```
class COleDocument : public CDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|`COleDocument` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|Přidá položku do seznamu položek udržovaných dokumentem.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Nastaví zařízení cíle tisku pro všechny položky klienta v dokumentu.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Způsobí, že se dokumenty uloží pomocí formátu souboru strukturovaného úložiště OLE.|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|Vrátí položku OLE, která je aktuálně na místě aktivní.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Získá další položku klienta pro iteraci.|
|[COleDocument::GetNextItem](#getnextitem)|Získá další položku dokumentu pro iteraci.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Získá další položku serveru pro iteraci.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Vrátí primární vybranou položku OLE v dokumentu.|
|[COleDocument::GetStartPosition](#getstartposition)|Získá počáteční pozici pro začátek iterace.|
|[COleDocument::HasBlankItems](#hasblankitems)|Kontroluje prázdné položky v dokumentu.|
|[COleDocument::OnShowViews](#onshowviews)|Volá se, když se dokument zobrazí jako viditelný nebo neviditelný.|
|[COleDocument:: RemoveItem](#removeitem)|Odebere položku ze seznamu položek, které dokument uchovává.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Označí dokument jako změněný, pokud byla změněna kterákoli z obsažených položek OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Zpracovává události v příkazu nabídky ikony změny.|
|[COleDocument::OnEditConvert](#oneditconvert)|Zpracovává převod vloženého nebo propojeného objektu z jednoho typu na jiný.|
|[COleDocument::OnEditLinks](#oneditlinks)|Zpracovává události v příkazu odkazy v nabídce Upravit.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s připojeným dokumentem.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Volá se rozhraním, aby se aktualizovalo uživatelské rozhraní příkazu pro možnost nabídky upravit/změnit ikona.|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Volá se rozhraním, aby se aktualizovalo uživatelské rozhraní příkazu pro možnost nabídky upravit/odkazy.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Volá se rozhraním, aby se aktualizovalo uživatelské rozhraní příkazu pro možnost nabídky upravit/ *ObjectName* a podnabídka operace, která se přistupovala z Edit/ *ObjectName*.|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Volá se rozhraním, aby se aktualizovalo uživatelské rozhraní příkazu pro možnost vložení speciální nabídky.|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|Volá se rozhraním, aby se aktualizovalo uživatelské rozhraní příkazu pro možnost nabídky Vložit.|

## <a name="remarks"></a>Poznámky

`COleDocument`je odvozen z `CDocument`, což umožňuje vašim aplikacím OLE používat architekturu dokument/zobrazení poskytovanou knihovna Microsoft Foundation Class.

`COleDocument`zpracovává dokument jako kolekci objektů [CDocItem](../../mfc/reference/cdocitem-class.md) pro zpracování položek OLE. Aplikace typu kontejner a Server vyžadují takovou architekturu, protože jejich dokumenty musí být schopny obsahovat položky OLE. Třídy [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) a [COleClientItem](../../mfc/reference/coleclientitem-class.md) , jak jsou odvozeny `CDocItem`z, spravují interakce mezi aplikacemi a položkami OLE.

Pokud píšete jednoduchou aplikaci typu kontejner, odvodíte třídu dokumentu z `COleDocument`. Pokud píšete aplikaci typu kontejner, která podporuje propojení s vloženými položkami obsaženými v dokumentech, odvodíte třídu dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Při psaní serverové aplikace nebo kombinovaného kontejneru nebo serveru odvodíte třídu dokumentu z [COleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc`a `COleServerDoc` jsou odvozeny `COleDocument`z, takže tyto třídy dědí všechny služby, které `COleDocument` jsou `CDocument`k dispozici v a.

Chcete- `COleDocument`li použít, odvodit z něj třídu a přidat funkce pro správu dat nevyužívajících OLE aplikace a také vložené nebo propojené položky. Pokud definujete `CDocItem`odvozené třídy pro ukládání nativních dat aplikace, můžete použít výchozí implementaci definovanou nástrojem `COleDocument` k uložení dat OLE a non OLE. Můžete také navrhnout vlastní datové struktury pro ukládání dat, která nepoužívají technologii OLE, odděleně od položek OLE. Další informace najdete v kontejnerech článků [: Složené soubory](../../mfc/containers-compound-files.md)...

`CDocument`podporuje odesílání dokumentů prostřednictvím pošty, pokud je k dispozici podpora pošty (MAPI). `COleDocument`má aktualizovaný [OnFileSendMail](#onfilesendmail) pro správné zpracování složených dokumentů. Další informace najdete v článcích podpora [rozhraní MAPI](../../mfc/mapi.md) a [MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[Objektu CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="additem"></a>COleDocument:: AddItem

Voláním této funkce přidáte položku do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, která se má přidat

### <a name="remarks"></a>Poznámky

Tuto funkci není nutné volat explicitně, je-li volána `COleClientItem` konstruktorem nebo `COleServerItem` , který přijímá ukazatel na dokument.

##  <a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Voláním této funkce změníte zařízení cílení na tisk pro všechny vložené [COleClientItem](../../mfc/reference/coleclientitem-class.md) položky v dokumentu kontejneru aplikace.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*ptd*<br/>
Ukazatel na `DVTARGETDEVICE` strukturu dat, která obsahuje informace o novém zařízení cílového tisku. Může mít hodnotu NULL.

*ppd*<br/>
Ukazatel na `PRINTDLG` strukturu dat, která obsahuje informace o novém zařízení cílového tisku. Může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce aktualizuje zařízení cíle tisku pro všechny položky, ale neaktualizuje mezipaměť prezentace pro tyto položky. Chcete-li aktualizovat mezipaměť prezentace pro položku, zavolejte [COleClientItem:: UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty této funkce obsahují informace, které technologie OLE používá k identifikaci cílového zařízení. Struktura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw) obsahuje informace, které systém Windows používá k inicializaci běžného tiskového dialogového okna. Po zavření uživatele v dialogovém okně vrátí systém Windows informace o výběru uživatele v této struktuře. Člen objektu `PRINTDLG` CPrintDialog je struktura. [](../../mfc/reference/cprintdialog-class.md) `m_pd`

Další informace najdete v tématu struktura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw) v Windows SDK.

Další informace najdete v tématu struktura [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) v Windows SDK.

##  <a name="coledocument"></a>COleDocument::COleDocument

`COleDocument` Vytvoří objekt.

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Tuto funkci zavolejte, pokud chcete dokument uložit ve formátu složeného souboru.

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, jestli je povolená nebo zakázaná Podpora složených souborů.

### <a name="remarks"></a>Poznámky

Označuje se taky jako strukturované úložiště. Tuto funkci obvykle vyvoláte z konstruktoru vaší `COleDocument`odvozené třídy. Další informace o složených dokumentech najdete v kontejnerech článků [: Složené soubory](../../mfc/containers-compound-files.md)...

Pokud tuto členskou funkci nebudete volat, dokumenty budou uloženy ve formátu nestrukturovaného ("plochého") souboru.

Po povolení nebo zakázání podpory složených souborů v dokumentu by toto nastavení nemělo být změněno během doby platnosti dokumentu.

##  <a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem

Voláním této funkce získáte položku OLE, která je aktuálně aktivována na místě v okně rámce, které obsahuje zobrazení identifikované *pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které zobrazí dokument kontejneru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jednu místně aktivní položku OLE; Hodnota NULL, pokud není aktuálně k dispozici žádná položka OLE ve stavu "místní aktivní".

##  <a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Voláním této funkce opakovaně získáte přístup ke všem položkám klienta v dokumentu.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Odkaz na hodnotu pozice nastavenou předchozím voláním metody `GetNextClientItem`; počáteční hodnota je vrácena `GetStartPosition` členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku klienta v dokumentu nebo hodnotu NULL, pokud nejsou k dispozici žádné další položky klienta.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota vlastnosti *POS* nastavena pro další položku v dokumentu, která může nebo nemusí být položkou klienta.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument::GetNextItem

Voláním této funkce opakovaně získáte přístup ke všem položkám v dokumentu.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Odkaz na hodnotu pozice nastavenou předchozím voláním metody `GetNextItem`; počáteční hodnota je vrácena `GetStartPosition` členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku dokumentu na zadané pozici.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota *POS* nastavena na hodnotu pozice další položky v dokumentu. Pokud je načtený prvek posledním prvkem v dokumentu, nová hodnota *POS* je null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Voláním této funkce opakovaně získáte přístup ke všem položkám serveru v dokumentu.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*POS*<br/>
Odkaz na hodnotu pozice nastavenou předchozím voláním metody `GetNextServerItem`; počáteční hodnota je vrácena `GetStartPosition` členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku serveru v dokumentu nebo hodnotu NULL, pokud nejsou k dispozici žádné další položky serveru.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota vlastnosti *POS* nastavena pro další položku v dokumentu, která může nebo nemusí být položkou serveru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Volá se rozhraním, aby se načetla aktuálně vybraná položka OLE v zadaném zobrazení.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Ukazatel na objekt aktivního zobrazení, který zobrazuje dokument.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jednu vybranou položku OLE; NULL, pokud nejsou vybrány žádné položky OLE nebo pokud je vybráno více než jedna položka.

### <a name="remarks"></a>Poznámky

Výchozí implementace prohledá seznam obsažených položek OLE pro jednu vybranou položku a vrátí na ni ukazatel. Pokud není vybrána žádná položka, nebo pokud je vybrána více než jedna položka, vrátí funkce hodnotu NULL. Aby tato funkce fungovala, je nutné přepsat `CView::IsSelected` členskou funkci ve třídě zobrazení. Tuto funkci můžete přepsat, pokud máte vlastní metodu ukládání obsažených položek OLE.

##  <a name="getstartposition"></a>COleDocument::GetStartPosition

Voláním této funkce získáte pozici první položky v dokumentu.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota pozice, kterou lze použít k zahájení iterace v rámci položek dokumentu; Hodnota NULL, pokud dokument neobsahuje žádné položky.

### <a name="remarks"></a>Poznámky

Předejte hodnotu vrácenou `GetNextItem`do `GetNextClientItem`, nebo `GetNextServerItem`.

##  <a name="hasblankitems"></a>COleDocument::HasBlankItems

Voláním této funkce určíte, zda dokument obsahuje prázdné položky.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dokument obsahuje prázdné položky; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Prázdná položka je taková, jejíž obdélník je prázdný.

##  <a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Zobrazí dialogové okno ikona změny OLE a změní ikonu reprezentující aktuálně vybranou položku OLE na ikonu, kterou uživatel vybere v dialogovém okně.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Poznámky

`OnEditChangeIcon`Vytvoří a spustí `COleChangeIconDialog` dialogové okno Změnit ikonu.

##  <a name="oneditconvert"></a>COleDocument::OnEditConvert

Zobrazí dialogové okno převést OLE a převede nebo aktivuje aktuálně vybranou položku OLE podle výběrů uživatele v dialogovém okně.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Poznámky

`OnEditConvert`Vytvoří a spustí `COleConvertDialog` dialogové okno převést.

Příkladem převodu je převod dokumentu aplikace Microsoft Word na dokument WordPad.

##  <a name="oneditlinks"></a>COleDocument::OnEditLinks

Zobrazí dialogové okno Upravit/odkazy OLE.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Poznámky

`OnEditLinks`Vytvoří a spustí `COleLinksDialog` dialogové okno odkazy, které umožňuje uživateli změnit propojené objekty.

##  <a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Pošle zprávu prostřednictvím hostitele rezidentního e-mailu (pokud existuje) s dokumentem jako přílohou.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail`volá `OnSaveDocument` k serializaci (uložení) bez názvu a změněných dokumentů do dočasného souboru, který se pak pošle prostřednictvím elektronické pošty. Pokud dokument nebyl upraven, dočasný soubor není potřeba. původní odeslání. `OnFileSendMail`Načte MAPI32. DLL, pokud ještě nebyla načtena.

Na rozdíl od implementace `OnFileSendMail` pro `CDocument`, tato funkce zpracovává složené soubory správně.

Další informace najdete v [tématech rozhraní MAPI](../../mfc/mapi.md) a [Podpora rozhraní MAPI v článcích knihovny MFC](../../mfc/mapi-support-in-mfc.md) ..

##  <a name="onshowviews"></a>COleDocument::OnShowViews

Rozhraní volá tuto funkci po změně stavu viditelnosti dokumentu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*bVisible*<br/>
Označuje, zda se dokument zobrazuje jako viditelný nebo neviditelný.

### <a name="remarks"></a>Poznámky

Výchozí verze této funkce neprovádí žádnou akci. Přepsat, pokud vaše aplikace musí provádět zvláštní zpracování, když se změní viditelnost dokumentu.

##  <a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Volá se rozhraním, aby se aktualizoval příkaz ikony změny v nabídce Upravit.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateEditChangeIcon`aktualizuje uživatelské rozhraní příkazu v závislosti na tom, zda v dokumentu existuje platná ikona. Chcete-li změnit chování, přepište tuto funkci.

##  <a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu

Volá se rozhraním, aby se aktualizoval příkaz odkazy v nabídce Upravit.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Počínaje první položkou OLE v dokumentu `OnUpdateEditLinksMenu` přistupuje k jednotlivým položkám, otestuje, jestli je položka odkaz, a pokud se jedná o odkaz, povolí příkaz odkazy. Chcete-li změnit chování, přepište tuto funkci.

##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu

Volá se rozhraním, aby se aktualizoval příkaz *ObjectName* v nabídce Úpravy a podnabídce příkazu, která se přistupovala z příkazu *ObjectName* , kde *ObjectName* je název objektu OLE, který je vložený v dokumentu.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateObjectVerbMenu`aktualizuje uživatelské rozhraní příkazu *ObjectName* v závislosti na tom, zda v dokumentu existuje platný objekt. Pokud objekt existuje, je povolen příkaz *ObjectName* v nabídce Upravit. Při výběru tohoto příkazu nabídky se zobrazí podnabídka operace. Podnabídka operace obsahuje všechny příkazy příkazu, které jsou k dispozici pro objekt, jako je například upravit, vlastnosti a tak dále. Chcete-li změnit chování, přepište tuto funkci.

##  <a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu

Volá se rozhraním, aby se určilo, jestli se odkazovaná položka OLE dá vložit ze schránky.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz pro vložení speciální nabídky je povolen nebo zakázán v závislosti na tom, zda lze položku vložit do dokumentu nebo ne.

##  <a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu

Volá se rozhraním, aby se určilo, jestli se vložená položka OLE dá vložit ze schránky.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která vygenerovala příkaz Update. Obslužná rutina aktualizace volá `Enable` členskou funkci `CCmdUI` struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz a tlačítko nabídky Vložit jsou povoleny nebo zakázány v závislosti na tom, zda lze položku vložit do dokumentu nebo ne.

##  <a name="removeitem"></a>COleDocument:: RemoveItem

Voláním této funkce odeberete položku z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku dokumentu, která se má odebrat

### <a name="remarks"></a>Poznámky

Tuto funkci obvykle nemusíte volat explicitně; je volána destruktory pro `COleClientItem` a. `COleServerItem`

##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag

Voláním této funkce označíte dokument jako upravený, pokud byla změněna kterákoli z obsažených položek OLE.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Poznámky

To umožňuje rozhraní vyzvat uživatele k uložení dokumentu před jeho zavřením, a to i v případě, že se nativní data v dokumentu nezměnila.

## <a name="see-also"></a>Viz také:

[KONTEJNER ukázek MFC](../../overview/visual-cpp-samples.md)<br/>
[MFCBIND Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
