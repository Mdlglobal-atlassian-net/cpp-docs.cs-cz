---
title: COleDocObjectItem – třída
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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375042"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem – třída

Implementuje aktivní uzavření dokumentu.

## <a name="syntax"></a>Syntaxe

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Vytvoří položku. `COleDocObject`|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Vytiskne dokument aplikace kontejneru pomocí výchozího nastavení tiskárny.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Provede příkaz určený uživatelem.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Načte aktivní zobrazení dokumentu.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Načte počet stránek v dokumentu aplikace kontejneru.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Připraví dokument aplikace kontejneru pro tisk.|
|[COleDocObjectItem::OnPrint](#onprint)|Vytiskne dokument aplikace kontejneru.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Dotazy na stav jednoho nebo více příkazů generovaných událostmi uživatelského rozhraní.|
|[COleDocObjectItem::Vydání](#release)|Uvolní připojení k propojené položce OLE a zavře ji, pokud byla otevřena. Nezničí položku klienta.|

## <a name="remarks"></a>Poznámky

V knihovně MFC je aktivní dokument zpracován podobně jako běžné, na místě upravitelné vkládání, s následujícími rozdíly:

- -derived `COleDocument`třídy stále udržuje seznam aktuálně vložené položky; tyto položky však mohou být `COleDocObjectItem`odvozené položky.

- Pokud je aktivní dokument aktivní, zabírá celou klientskou oblast zobrazení, když je aktivní na místě.

- Kontejner aktivního dokumentu má plnou kontrolu nad nabídkou **Nápověda.**

- Nabídka **Nápověda** obsahuje položky nabídky pro kontejner aktivního dokumentu i server.

Vzhledem k tomu, že kontejner aktivního dokumentu vlastní nabídku **Nápověda,** je kontejner zodpovědný za předávání zpráv nabídky **nápovědy** serveru na server. Tato integrace je `COleDocObjectItem`zpracována .

Další informace o slučování nabídek a aktivaci aktivního dokumentu naleznete v tématu Přehled [aktivního zadržování dokumentů](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem

Volání této členské funkce k `COleDocObjectItem` inicializaci objektu.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parametry

*pContainerDoc*<br/>
Ukazatel na `COleDocument` objekt, který funguje jako aktivní kontejner dokumentu. Tento parametr musí být NULL povolit IMPLEMENT_SERIALIZE. Normálně ole položky jsou vytvořeny s non-NULL ukazatel dokumentu.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting

Volat rámci do dokumentu pomocí výchozí nastavení.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pVolající*<br/>
Ukazatel na [cview](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz print.

*pInformace*<br/>
Ukazatel na objekt [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) který popisuje úlohu, která má být vytištěna.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand

Volání této členské funkce k provedení příkazu určeného uživatelem.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
Identifikátor příkazu, který má být proveden. Musí být ve skupině označené *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Určuje možnosti spuštění příkazu. Ve výchozím nastavení nastavte spuštění příkazu bez zobrazení výzvy uživateli. Seznam hodnot najdete v tématu [OLECMDEXECOPT.](/windows/win32/api/docobj/ne-docobj-olecmdexecopt)

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů Ve výchozím nastavení null, který určuje standardní skupinu. Příkaz předaný v *nCmdID* musí patřit do skupiny.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK v případě úspěchu. v opačném případě vrátí jeden z následujících kódů chyb.

|Hodnota|Popis|
|-----------|-----------------|
|E_UNEXPECTED|Došlo k neočekávané chybě.|
|E_fail|Došlo k chybě.|
|E_NOTIMPL|Označuje, že mfc sám by se měl pokusit přeložit a odeslat příkaz.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* není null, ale neurčuje rozpoznanou skupinu příkazů.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* není rozpoznán jako platný příkaz ve skupině pGroup.|
|OLECMDERR_DISABLED|Příkaz identifikovaný *nCmdID* je zakázán a nelze jej provést.|
|OLECMDERR_NOHELP|Volající požádal o pomoc na příkaz identifikován *nCmdID,* ale žádná pomoc je k dispozici.|
|OLECMDERR_CANCELLED|Uživatel zrušil spuštění.|

### <a name="remarks"></a>Poznámky

*PguidCmdGroup* a *parametry nCmdID* společně jednoznačně identifikují příkaz, který chcete vyvolat. Parametr *nCmdExecOpt* určuje přesnou akci, která má být vykonat.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView

Volání této členské funkce získat `IOleDocumentView` ukazatel na rozhraní aktuálně aktivní zobrazení.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) aktuálně aktivního zobrazení. Pokud neexistuje žádné aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Počet odkazů na `IOleDocumentView` vrácený ukazatel není zvýšil před vrácení mne touto funkcí.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount

Volání této členské funkce načíst počet stránek v dokumentu.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parametry

*pnFirstPage*<br/>
Ukazatel na číslo první stránky dokumentu. Může být NULL, což znamená, že volající nepotřebuje toto číslo.

*pcStránky*<br/>
Ukazatel na celkový počet stránek v dokumentu. Může být NULL, což znamená, že volající nepotřebuje toto číslo.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting

Tato členská funkce je volána rámci připravit dokument pro tisk.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pVolající*<br/>
Ukazatel na [cview](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz print.

*pInformace*<br/>
Ukazatel na objekt [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) který popisuje úlohu, která má být vytištěna.

*bPrintAll*<br/>
Určuje, zda má být vytištěn celý dokument.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint

Tato členská funkce je volána rámci pro tisk dokumentu.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pVolající*<br/>
Ukazatel na cview objekt, který odesílá příkaz print.

*pInformace*<br/>
Ukazatel na objekt [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) který popisuje úlohu, která má být vytištěna.

*bPrintAll*<br/>
Určuje, zda má být vytištěn celý dokument.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand

Dotazy na stav jednoho nebo více příkazů generovaných událostmi uživatelského rozhraní.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
identifikátor dotazovaného příkazu.

*pdwStatus*<br/>
Ukazatel na příznaky vrácené v důsledku dotazu. Seznam možných hodnot naleznete v tématu [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Ukazatel na strukturu [OLECMDTEXT,](/windows/win32/api/docobj/ns-docobj-olecmdtext) ve které chcete vrátit informace o názvu a stavu pro jeden příkaz. Může být NULL označuje, že volající nepotřebuje tyto informace.

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů; může být NULL pro určení standardní skupiny.

### <a name="return-value"></a>Návratová hodnota

Úplný seznam vrácených hodnot naleznete v [tématu IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce metody [IOleCommandTarget::QueryStatus,](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) jak je popsáno v sadě Windows SDK.

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Vydání

Uvolní připojení k propojené položce OLE a zavře ji, pokud byla otevřena. Nezničí položku klienta.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Příznak určující, za jakých okolností je položka OLE uložena, když se vrátí do načteného stavu. Seznam možných hodnot naleznete v tématu [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Poznámky

Nezničí položku klienta.

## <a name="see-also"></a>Viz také

[Knihovna MFC Ukázka knihovny MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Třída CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
