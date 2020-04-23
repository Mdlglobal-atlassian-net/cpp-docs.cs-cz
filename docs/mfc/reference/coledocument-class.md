---
title: Třída COleDocument
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
ms.openlocfilehash: 1500035cb8be3036678090918154829aace48d2f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753871"
---
# <a name="coledocument-class"></a>Třída COleDocument

Základní třída pro dokumenty OLE, které podporují vizuální úpravy.

## <a name="syntax"></a>Syntaxe

```
class COleDocument : public CDocument
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|Vytvoří `COleDocument` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDocument::Přidat položku](#additem)|Přidá položku do seznamu položek udržovaných dokumentem.|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|Nastaví zařízení pro cíl tisku pro všechny klientské položky v dokumentu.|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|Způsobí, že dokumenty budou uloženy ve formátu souboru strukturovaného úložiště OLE.|
|[COleDocument::GetInplaceActiveItem](#getinplaceactiveitem)|Vrátí položku OLE, která je aktuálně aktivní na místě.|
|[COleDocument::GetNextClientItem](#getnextclientitem)|Získá další položku klienta pro iterace.|
|[COleDocument::GetNextItem](#getnextitem)|Získá další položku dokumentu pro iterace.|
|[COleDocument::GetNextServerItem](#getnextserveritem)|Získá další položku serveru pro iterace.|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|Vrátí primární vybranou položku OLE v dokumentu.|
|[COleDocument::GetStartPosition](#getstartposition)|Získá počáteční pozici zahájit iteraci.|
|[COleDocument::hasBlankItems](#hasblankitems)|Zkontroluje prázdné položky v dokumentu.|
|[COleDocument::OnShowViews](#onshowviews)|Nazývá se, když se dokument stane viditelným nebo neviditelným.|
|[COleDocument::RemoveItem](#removeitem)|Odebere položku ze seznamu položek spravovaných dokumentem.|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|Označí dokument jako upravený, pokud byla změněna některá z obsažených položek OLE.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|Zpracovává události v příkazu Změnit ikonu.|
|[COleDocument::OnEditConvert](#oneditconvert)|Zpracovává převod vloženého nebo propojeného objektu z jednoho typu na jiný.|
|[COleDocument::OnEditLinks](#oneditlinks)|Zpracovává události v příkazu Odkazy v nabídce Úpravy.|
|[COleDocument::OnFileSendMail](#onfilesendmail)|Odešle e-mailovou zprávu s připojeným dokumentem.|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|Volat rámci aktualizovat příkaz uI pro možnost upravit nebo změnit ikonu nabídky.|
|[ColeDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|Volat rámci aktualizovat příkaz uI pro možnost nabídky Upravit/odkazy.|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|Nazývá rozhraní pro aktualizaci příkazu Uživatelské rozhraní pro možnost upravit / *ObjectName* a podnabídky Sloveso přístupné z Edit/ *ObjectName*.|
|[Coledocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|Volat rámci aktualizovat příkaz uI pro možnost vložit speciální menu.|
|[Coledocument::OnUpdatePasteMenu](#onupdatepastemenu)|Volat rámci aktualizovat příkaz uI pro možnost nabídky Vložit.|

## <a name="remarks"></a>Poznámky

`COleDocument`je odvozen `CDocument`z aplikace , která umožňuje aplikacím OLE používat architekturu dokumentu nebo zobrazení poskytovanou knihovnou tříd aplikace Microsoft Foundation.

`COleDocument`zpracovává dokument jako kolekci objektů [CDocItem](../../mfc/reference/cdocitem-class.md) pro zpracování položek OLE. Kontejnerové i serverové aplikace vyžadují takovou architekturu, protože jejich dokumenty musí obsahovat položky OLE. Třídy [COleServerItem](../../mfc/reference/coleserveritem-class.md) a [COleClientItem,](../../mfc/reference/coleclientitem-class.md) `CDocItem`odvozené z , spravují interakce mezi aplikacemi a položkami OLE.

Pokud píšete jednoduchou aplikaci kontejneru, `COleDocument`odvodit třídu dokumentu z . Pokud píšete kontejner aplikace, která podporuje propojení s vložené položky obsažené v jeho dokumenty, odvodit třídu dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md). Pokud píšete serverovou aplikaci nebo kombinovaný kontejner/server, odvoděte třídu dokumentu z [cOleServerDoc](../../mfc/reference/coleserverdoc-class.md). `COleLinkingDoc`a `COleServerDoc` jsou odvozeny z `COleDocument`, takže tyto `COleDocument` třídy dědí všechny služby dostupné v a `CDocument`.

Chcete-li použít `COleDocument`, odvodit třídu z něj a přidat funkce pro správu aplikace non-OLE data, stejně jako vložené nebo propojené položky. Pokud definujete `CDocItem`-derived třídy pro ukládání nativních dat aplikace, `COleDocument` můžete použít výchozí implementaci definovanou k uložení dat OLE i non-OLE. Můžete také navrhnout vlastní datové struktury pro ukládání dat mimo OLE odděleně od položek OLE. Další informace naleznete v článku [Kontejnery: Složené soubory](../../mfc/containers-compound-files.md)..

`CDocument`podporuje odesílání dokumentu poštou, pokud je k dispozici podpora pošty (MAPI). `COleDocument`Byl aktualizován [onFileSendMail](#onfilesendmail) správně zpracovávat složené dokumenty. Další informace naleznete v článcích [MAPI](../../mfc/mapi.md) a [podpora MAPI v knihovně MFC](../../mfc/mapi-support-in-mfc.md)..

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDokument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::Přidat položku

Volání této funkce pro přidání položky do dokumentu.

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na přidanou položku dokumentu.

### <a name="remarks"></a>Poznámky

Není nutné volat tuto funkci explicitně, pokud `COleClientItem` `COleServerItem` je volána nebo konstruktor, který přijímá ukazatel na dokument.

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice

Volání této funkce změnit zařízení cíl tisku pro všechny vložené [cOleClientItem](../../mfc/reference/coleclientitem-class.md) položky v dokumentu kontejneru aplikace.

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>Parametry

*Ptd*<br/>
Ukazatel na `DVTARGETDEVICE` datovou strukturu, která obsahuje informace o novém zařízení pro cíl tisku. Může být NULL.

*Ppd*<br/>
Ukazatel na `PRINTDLG` datovou strukturu, která obsahuje informace o novém zařízení pro cíl tisku. Může být NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce aktualizuje zařízení pro cíl tisku pro všechny položky, ale neaktualizuje mezipaměť prezentace pro tyto položky. Chcete-li aktualizovat mezipaměť prezentace pro položku, zavolejte [COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink).

Argumenty této funkce obsahují informace, které OLE používá k identifikaci cílového zařízení. Struktura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) obsahuje informace, které systém Windows používá k inicializaci společného tiskového dialogového okna. Poté, co uživatel zavře dialogové okno, vrátí systém Windows informace o výběru uživatele v této struktuře. Člen `m_pd` [cprintdialog](../../mfc/reference/cprintdialog-class.md) objektu `PRINTDLG` je struktura.

Další informace naleznete v tiskové [dllg](/windows/win32/api/commdlg/ns-commdlg-printdlga) struktury v sadě Windows SDK.

Další informace naleznete v [dvtargetdevice](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) struktury v sadě Windows SDK.

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument

Vytvoří `COleDocument` objekt.

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile

Tuto funkci zavolejte, pokud chcete dokument uložit ve formátu složeného souboru.

```cpp
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda je podpora složených souborů povolena nebo zakázána.

### <a name="remarks"></a>Poznámky

To se také nazývá strukturované úložiště. Obvykle voláte tuto funkci z konstruktoru vaší `COleDocument`odvozené třídy. Další informace o složených dokumentech naleznete v článku [Kontejnery: Složené soubory](../../mfc/containers-compound-files.md)..

Pokud tuto členní funkci nezavoláte, dokumenty budou uloženy v nestrukturovaném ("plochém") formátu souboru.

Po povolení nebo zakázání podpory složených souborů pro dokument by se nastavení nemělo během doby trvání dokumentu měnit.

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInplaceActiveItem

Volání této funkce získat položku OLE, která je aktuálně aktivována v okně rámce obsahující pohled označený *pomocí pWnd*.

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na okno, které zobrazuje dokument kontejneru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jednu aktivní položku OLE na místě; Null, pokud není žádná položka OLE aktuálně ve stavu "na místě aktivní".

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem

Volání této funkce opakovaně pro přístup ke každé položky klienta v dokumentu.

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Odkaz na hodnotu POSITION nastavenou `GetNextClientItem`předchozím voláním ; počáteční hodnota je vrácena členovou `GetStartPosition` funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku klienta v dokumentu nebo NULL, pokud neexistují žádné další položky klienta.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota *pos* nastavena pro další položku v dokumentu, která může nebo nemusí být klientskou položkou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem

Volání této funkce opakovaně pro přístup ke každé z položek v dokumentu.

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Odkaz na hodnotu POSITION nastavenou `GetNextItem`předchozím voláním ; počáteční hodnota je vrácena členovou `GetStartPosition` funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na položku dokumentu v zadané poloze.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota *pos* nastavena na hodnotu POSITION další položky v dokumentu. Pokud načtený prvek je poslední prvek v dokumentu, nová hodnota *pos* je NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem

Volání této funkce opakovaně pro přístup ke každé položky serveru v dokumentu.

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>Parametry

*Pos*<br/>
Odkaz na hodnotu POSITION nastavenou `GetNextServerItem`předchozím voláním ; počáteční hodnota je vrácena členovou `GetStartPosition` funkcí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku serveru v dokumentu nebo NULL, pokud neexistují žádné další položky serveru.

### <a name="remarks"></a>Poznámky

Po každém volání je hodnota *pos* nastavena pro další položku v dokumentu, která může nebo nemusí být položkou serveru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem

Volat rámci načíst aktuálně vybrané položky OLE v zadaném zobrazení.

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>Parametry

*pZobrazit*<br/>
Ukazatel na aktivní objekt zobrazení zobrazující dokument.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jednu vybranou položku OLE; Null, pokud nejsou vybrány žádné položky OLE nebo pokud je vybráno více než jedno.

### <a name="remarks"></a>Poznámky

Výchozí implementace prohledá seznam obsažených položek OLE pro jednu vybranou položku a vrátí na ni ukazatel. Pokud není vybrána žádná položka nebo je vybrána více než jedna položka, vrátí funkce hodnotu NULL. Aby tato funkce `CView::IsSelected` fungovala, musíte přepsat členská funkci ve třídě zobrazení. Přepsat tuto funkci, pokud máte vlastní metodu ukládání obsažené položky OLE.

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition

Volání této funkce získat pozici první položky v dokumentu.

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota POSITION, kterou lze použít k zahájení iterace prostřednictvím položek dokumentu; Null, pokud dokument nemá žádné položky.

### <a name="remarks"></a>Poznámky

Předajte `GetNextItem`vrácenou hodnotu do , `GetNextClientItem`, nebo `GetNextServerItem`.

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::hasBlankItems

Volání této funkce k určení, zda dokument obsahuje nějaké prázdné položky.

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud dokument obsahuje prázdné položky; jinak 0.

### <a name="remarks"></a>Poznámky

Prázdná položka je položka, jejíž obdélník je prázdný.

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon

Zobrazí dialogové okno Ikona změny OLE a změní ikonu představující aktuálně vybranou položku OLE na ikonu, kterou uživatel vybere v dialogovém okně.

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>Poznámky

`OnEditChangeIcon`vytvoří a spustí `COleChangeIconDialog` dialogové okno Změnit ikonu.

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert

Zobrazí dialogové okno Převést OLE a převede nebo aktivuje aktuálně vybranou položku OLE podle výběru uživatele v dialogovém okně.

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>Poznámky

`OnEditConvert`vytvoří a spustí `COleConvertDialog` dialogové okno Převést.

Příkladem převodu je převod dokumentu aplikace Microsoft Word na dokument aplikace Word.

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks

Zobrazí dialogové okno Ole Edit/Links.

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>Poznámky

`OnEditLinks`vytvoří a spustí `COleLinksDialog` dialogové okno Odkazy, které uživateli umožní změnit propojené objekty.

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail

Odešle zprávu prostřednictvím rezidentního poštovního hostitele (pokud existuje) s dokumentem jako přílohou.

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>Poznámky

`OnFileSendMail`volá `OnSaveDocument` serializovat (uložit) dokumenty bez názvu a upravené do dočasného souboru, který je pak odeslán prostřednictvím elektronické pošty. Pokud dokument nebyl změněn, dočasný soubor není potřeba. originál odeslán. `OnFileSendMail`načte MAPI32. DLL, pokud ještě nebyla načtena.

Na rozdíl `OnFileSendMail` od `CDocument`implementace for , tato funkce zpracovává složené soubory správně.

Další informace naleznete v [tématech Témata rozhraní MAPI](../../mfc/mapi.md) a podpora rozhraní MAPI v článcích [knihovny MFC.](../../mfc/mapi-support-in-mfc.md)

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews

Rámec volá tuto funkci po změně stavu viditelnosti dokumentu.

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>Parametry

*b*<br/>
Označuje, zda se dokument stal viditelným nebo neviditelným.

### <a name="remarks"></a>Poznámky

Výchozí verze této funkce neprovede žádné funkce. Přepište ji, pokud vaše aplikace musí provést jakékoli zvláštní zpracování při změně viditelnosti dokumentu.

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon

Volat rámci aktualizovat změnit ikonu příkaz u nabídky Upravit.

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která generovala příkaz aktualizace. Obslužná `Enable` rutina `CCmdUI` aktualizace volá členská funkce struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateEditChangeIcon`aktualizuje uživatelské rozhraní příkazu v závislosti na tom, zda v dokumentu existuje platná ikona. Přepsáním této funkce změňte chování.

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>ColeDocument::OnUpdateEditLinksMenu

Volat rámci aktualizovat odkazy příkaz v nabídce Upravit.

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která generovala příkaz aktualizace. Obslužná `Enable` rutina `CCmdUI` aktualizace volá členská funkce struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Počínaje první položkou OLE v `OnUpdateEditLinksMenu` dokumentu přistupuje ke každé položce, testuje, zda je položka odkaz, a pokud se jedná o propojení, povolí příkaz Odkazy. Přepsáním této funkce změňte chování.

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu

Nazývá rozhraní pro aktualizaci *příkazu ObjectName* v nabídce Edit a podnabídky Sloveso, ke které přistupuje příkaz *Vlastnost objektu,* kde *Název objektu ObjectName* je název objektu OLE vloženého do dokumentu.

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která generovala příkaz aktualizace. Obslužná `Enable` rutina `CCmdUI` aktualizace volá členská funkce struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

`OnUpdateObjectVerbMenu`Aktualizuje uživatelské rozhraní příkazu *ObjectName* v závislosti na tom, zda v dokumentu existuje platný objekt. Pokud objekt existuje, je povolen příkaz *Objekt v* nabídce Úpravy. Když je vybrán tento příkaz nabídky, zobrazí se podnabídka Sloveso. Podnabídka Sloveso obsahuje všechny příkazy sloves, které jsou k dispozici pro objekt, například Upravit, Vlastnosti a tak dále. Přepsáním této funkce změňte chování.

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>Coledocument::OnUpdatePasteLinkMenu

Volat rámci k určení, zda propojené položky OLE lze vložit ze schránky.

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která generovala příkaz aktualizace. Obslužná `Enable` rutina `CCmdUI` aktualizace volá členská funkce struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz Vložit jinak je povolen nebo zakázán v závislosti na tom, zda lze položku vložit do dokumentu či nikoli.

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>Coledocument::OnUpdatePasteMenu

Volat rámci k určení, zda vložené položky OLE lze vložit ze schránky.

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na `CCmdUI` strukturu, která představuje nabídku, která generovala příkaz aktualizace. Obslužná `Enable` rutina `CCmdUI` aktualizace volá členská funkce struktury prostřednictvím *pCmdUI* k aktualizaci uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Příkaz a tlačítko Vložit nabídku jsou povoleny nebo zakázány v závislosti na tom, zda lze položku vložit do dokumentu nebo ne.

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::RemoveItem

Voláním této funkce odeberte položku z dokumentu.

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na položku dokumentu, která má být odebrána.

### <a name="remarks"></a>Poznámky

Obvykle není nutné volat tuto funkci explicitně; je volána destruktory pro `COleClientItem` `COleServerItem`a .

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag

Volání této funkce označí dokument jako upravený, pokud byly změněny některé z obsažených položek OLE.

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>Poznámky

To umožňuje rozhraní vyzvat uživatele k uložení dokumentu před zavřením, i v případě, že nativní data v dokumentu nebyla změněna.

## <a name="see-also"></a>Viz také

[KONTEJNER Se vzorkem knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Knihovna MFC Ukázka knihovny MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument – třída](../../mfc/reference/cdocument-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
