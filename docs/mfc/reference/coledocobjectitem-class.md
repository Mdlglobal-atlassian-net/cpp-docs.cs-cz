---
title: COleDocObjectItem Class
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: af6d866298309f5ddb8eb21a5caeb3d1526b166a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276283"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem Class

Implementuje Active document containment.

## <a name="syntax"></a>Syntaxe

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Vytvoří `COleDocObject` položky.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Vytiskne dokument aplikace typu kontejner pomocí výchozích nastavení tiskárny.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Provede příkaz specifikovaných uživatelem.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Načte zobrazení aktivního dokumentu.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Získá počet stránek v dokumentu aplikace typu kontejner.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Připraví dokumentu aplikace typu kontejner pro tisk.|
|[COleDocObjectItem::OnPrint](#onprint)|Vytiskne dokument aplikace typu kontejner.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Dotazy na stav jednoho nebo více příkazů vygenerované uživatelské rozhraní události.|
|[COleDocObjectItem::Release](#release)|Uvolní připojení k propojená položka OLE a zavře, pokud byla otevřena. Nezničí klientské položky.|

## <a name="remarks"></a>Poznámky

V knihovně MFC je aktivní dokument podobně zpracovat pravidelně, v místě upravovat vkládání, s těmito rozdíly:

- `COleDocument`-Odvozené třídy stále udržuje seznam aktuálně vložené položky; však mohou být tyto položky `COleDocObjectItem`-odvozené položky.

- Při aktivním aktivní dokument zabírá celé klientské oblasti zobrazení. když je aktivní místní.

- Kontejner pro aktivní dokument má plnou kontrolu nad **pomáhají** nabídky.

- **Pomáhají** nabídka obsahuje položky nabídky kontejner pro aktivní dokument i serveru.

Protože vlastní kontejner pro aktivní dokument **pomáhají** nabídce kontejneru je zodpovědný za předávání server **pomáhají** nabídky zprávy na server. Tato integrace se zpracovává souborem `COleDocObjectItem`.

Další informace o menu merging a aktivní dokument aktivace najdete v tématu Přehled [Active Document Containment](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem

Voláním této členské funkce inicializovat `COleDocObjectItem` objektu.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parametry

*pContainerDoc*<br/>
Ukazatel `COleDocument` objekt, který funguje jako kontejner pro aktivní dokument. Tento parametr musí mít hodnotu NULL, aby se povolilo IMPLEMENT_SERIALIZE. Položky OLE se obvykle vytvořen s ukazatelem dokumentu jinou hodnotu než NULL.

##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting

Volá se rozhraním, aby dokumentu s použitím výchozích nastavení.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel [CView](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz pro tisk.

*pInfo*<br/>
Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy, které se mají vytisknout.

##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand

Voláním této členské funkce k provedení příkazu specifikovaných uživatelem.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
Identifikátor příkazu ke spuštění. Musí být ve skupině identifikovaný *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Určuje možnosti provedení příkazu. Ve výchozím nastavení ke spuštění příkazu bez výzvy pro uživatele. Zobrazit [OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) seznam hodnot.

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů. Ve výchozím nastavení, NULL, který určuje skupiny standardní. Příkaz předaný *nCmdID* musí patřit do skupiny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK v případě úspěchu; v opačném případě vrátí jednu z následující kódy chyb.

|Hodnota|Popis|
|-----------|-----------------|
|E_UNEXPECTED, JE-|Došlo k neočekávané chybě.|
|E_FAIL|Došlo k chybě.|
|E_NOTIMPL|Označuje MFC sama má pokusit o přeložení a odeslání příkazu.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* je jiná než NULL, ale neurčuje skupinu rozpoznaný příkaz.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* nebyl rozpoznán jako platný příkaz v pGroup skupiny.|
|OLECMDERR_DISABLED|Příkaz určený *nCmdID* je zakázané a nejde provést.|
|OLECMDERR_NOHELP|Volající požádali o pomoc na příkaz určený *nCmdID* , ale není k dispozici žádná nápověda.|
|OLECMDERR_CANCELLED|Uživatel zrušil provádění.|

### <a name="remarks"></a>Poznámky

*PguidCmdGroup* a *nCmdID* parametry společně jednoznačné identifikaci příkazu, který má být vyvolán. *NCmdExecOpt* parametr určuje přesné akce má být provedena.

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

Voláním této členské funkce, chcete-li získat ukazatel `IOleDocumentView` rozhraní zobrazit aktuálně aktivní.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview) rozhraní zobrazit aktuálně aktivní. Pokud neexistuje žádné aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Počet odkazů na vrácený `IOleDocumentView` ukazatel není zvýší předtím, než je vrácená touto funkcí.

##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount

Voláním této členské funkce se načíst počet stránek v dokumentu.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parametry

*pnFirstPage*<br/>
Ukazatel na číslo první stránky dokumentu. Může mít hodnotu NULL, což znamená, že volající není nutné toto číslo.

*pcPages*<br/>
Ukazatel na celkový počet stránek v dokumentu. Může mít hodnotu NULL, což znamená, že volající není nutné toto číslo.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting

Tato členská funkce se volá se rozhraním Příprava dokument pro tisk.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel [CView](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz pro tisk.

*pInfo*<br/>
Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy, které se mají vytisknout.

*bPrintAll*<br/>
Určuje, zda celý dokument které se mají vytisknout.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="onprint"></a>  COleDocObjectItem::OnPrint

Tato členská funkce se volá se rozhraním pro tisk dokumentu.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel na objekt CView, který odesílá příkaz pro tisk.

*pInfo*<br/>
Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy, které se mají vytisknout.

*bPrintAll*<br/>
Určuje, zda celý dokument které se mají vytisknout.

##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand

Dotazy na stav jednoho nebo více příkazů vygenerované uživatelské rozhraní události.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
identifikátor příkazu, pro která je dotazována.

*pdwStatus*<br/>
Ukazatel na příznaky k navrácení výsledku dotazu. Seznam možných hodnot najdete v tématu [OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Ukazatel [OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-_tagolecmdtext) struktury, ve kterých se mají vracet informace o název a stav pro jeden příkaz. Může mít hodnotu NULL k označení, že volající není nutné tyto informace.

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů; může mít hodnotu NULL k určení standardní skupiny.

### <a name="return-value"></a>Návratová hodnota

Úplný seznam všech návratové hodnoty, najdete v části [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) způsob, jak je popsáno v sadě Windows SDK.

##  <a name="release"></a>  COleDocObjectItem::Release

Uvolní připojení k propojená položka OLE a zavře, pokud byla otevřena. Nezničí klientské položky.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Příznak určující, za jakých okolností je uložen položky OLE. až se obnoví načíst stav. Seznam možných hodnot najdete v tématu [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Poznámky

Nezničí klientské položky.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MFCBIND](../../visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem – třída](../../mfc/reference/cdocobjectserveritem-class.md)
