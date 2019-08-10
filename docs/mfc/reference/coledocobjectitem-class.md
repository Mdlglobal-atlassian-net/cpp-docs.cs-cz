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
ms.openlocfilehash: 454be491fe5875b1b1ac9b2b85fdebe2f1663ebc
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916967"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem Class

Implementuje zahrnutí aktivního dokumentu.

## <a name="syntax"></a>Syntaxe

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|`COleDocObject` Vytvoří položku.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Vytiskne dokument aplikace kontejneru pomocí výchozího nastavení tiskárny.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Provede příkaz zadaný uživatelem.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Načte aktivní zobrazení dokumentu.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Načte počet stránek v dokumentu aplikace kontejneru.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Připraví dokument aplikace kontejneru pro tisk.|
|[COleDocObjectItem::OnPrint](#onprint)|Vytiskne dokument aplikace kontejneru.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Dotaz na stav jednoho nebo více příkazů generovaných událostmi uživatelského rozhraní.|
|[COleDocObjectItem:: Release](#release)|Uvolní připojení k propojené položce OLE a zavře je, pokud byla otevřená. Nezničí položku klienta.|

## <a name="remarks"></a>Poznámky

V knihovně MFC je aktivní dokument zpracováván podobně jako běžné a místní upravitelné vkládání s následujícími rozdíly:

- Třída-Derived stále udržuje seznam aktuálně vložených položek; tyto položky však mohou být `COleDocObjectItem`odvozeny položky. `COleDocument`

- Když je aktivní dokument aktivní, zabírá celou klientskou oblast zobrazení, když je aktivní na místě.

- Aktivní kontejner dokumentu má úplnou kontrolu nad nabídkou **help** .

- Nabídka **help** obsahuje položky nabídky pro kontejner aktivního dokumentu i server.

Vzhledem k tomu, že kontejner aktivního dokumentu je vlastníkem nabídky **help** , je kontejner zodpovědný za předávání zpráv nabídky serveru v **nápovědě** serveru. Tato integrace je zpracovávána `COleDocObjectItem`nástrojem.

Další informace o slučování nabídek a aktivaci aktivních dokumentů najdete v tématu Přehled [zahrnutí aktivního dokumentu](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem

Zavolejte tuto členskou funkci pro inicializaci `COleDocObjectItem` objektu.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parametry

*pContainerDoc*<br/>
Ukazatel na `COleDocument` objekt, který funguje jako kontejner aktivního dokumentu. Aby bylo možné povolit IMPLEMENT_SERIALIZE, musí mít tento parametr hodnotu NULL. Obvykle jsou položky OLE vytvořeny s ukazatelem dokumentu, který není NULL.

##  <a name="dodefaultprinting"></a>COleDocObjectItem::D oDefaultPrinting

Volá se rozhraním pro dokument s použitím výchozích nastavení.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel na objekt [CView](../../mfc/reference/cview-class.md) , který odesílá příkaz Print.

*pInfo*<br/>
Ukazatel na objekt [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , který popisuje úlohu, která má být vytištěna.

##  <a name="execcommand"></a>COleDocObjectItem:: ExecCommand

Zavolejte tuto členskou funkci pro provedení příkazu zadaného uživatelem.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
Identifikátor příkazu, který má být spuštěn. Musí být ve skupině určené pomocí *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Určuje možnosti spuštění příkazu. Ve výchozím nastavení se nastaví na spouštění příkazu bez zobrazení výzvy uživateli. Seznam hodnot naleznete v tématu [OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) .

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů Ve výchozím nastavení má hodnotu NULL, která určuje standardní skupinu. Příkaz předaný v *nCmdID* musí patřit do skupiny.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud bylo úspěšné. v opačném případě vrátí jeden z následujících kódů chyb.

|Value|Popis|
|-----------|-----------------|
|E_UNEXPECTED|Došlo k neočekávané chybě.|
|E_FAIL|Došlo k chybě.|
|E_NOTIMPL|Indikuje, že by se sama knihovna MFC měla pokusit přeložit a odeslat příkaz.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* je jiný než null, ale neurčuje rozpoznanou skupinu příkazů.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* není ve skupině pGroup rozpoznán jako platný příkaz.|
|OLECMDERR_DISABLED|Příkaz identifikovaný *nCmdID* je zakázaný a nedá se spustit.|
|OLECMDERR_NOHELP|Volající objekt požádal o nápovědu k příkazu identifikovanému funkcí *nCmdID* , ale není k dispozici žádná nápovědu.|
|OLECMDERR_CANCELLED|Uživatel zrušil provádění.|

### <a name="remarks"></a>Poznámky

Parametry *pguidCmdGroup* a *nCmdID* společně jednoznačně identifikují příkaz, který se má vyvolat. Parametr *nCmdExecOpt* určuje přesnou akci, která má být provedena.

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

Chcete-li získat ukazatel na `IOleDocumentView` rozhraní aktuálně aktivního zobrazení, zavolejte tuto členskou funkci.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní [IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview) aktuálně aktivního zobrazení. Pokud není k dispozici aktuální zobrazení, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Počet odkazů u vráceného `IOleDocumentView` ukazatele není zvýšen před jeho vrácením pomocí této funkce.

##  <a name="getpagecount"></a>COleDocObjectItem:: GetPageCount

Voláním této členské funkce načtete počet stránek v dokumentu.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parametry

*pnFirstPage*<br/>
Ukazatel na číslo první stránky dokumentu. Může mít hodnotu NULL, což znamená, že volající toto číslo nepotřebuje.

*pcPages*<br/>
Ukazatel na celkový počet stránek v dokumentu. Může mít hodnotu NULL, což znamená, že volající toto číslo nepotřebuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting

Tato členská funkce je volána rozhraním pro přípravu dokumentu pro tisk.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel na objekt [CView](../../mfc/reference/cview-class.md) , který odesílá příkaz Print.

*pInfo*<br/>
Ukazatel na objekt [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , který popisuje úlohu, která má být vytištěna.

*bPrintAll*<br/>
Určuje, zda bude vytištěn celý dokument.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="onprint"></a>  COleDocObjectItem::OnPrint

Tato členská funkce je volána rozhraním pro tisk dokumentu.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parametry

*pCaller*<br/>
Ukazatel na objekt CView, který odesílá příkaz Print.

*pInfo*<br/>
Ukazatel na objekt [CPrintInfo –](../../mfc/reference/cprintinfo-structure.md) , který popisuje úlohu, která má být vytištěna.

*bPrintAll*<br/>
Určuje, zda bude vytištěn celý dokument.

##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand

Dotaz na stav jednoho nebo více příkazů generovaných událostmi uživatelského rozhraní.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
identifikátor příkazu, pro který se má dotazovat

*pdwStatus*<br/>
Ukazatel na příznaky vracený jako výsledek dotazu. Seznam možných hodnot naleznete v tématu [OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Ukazatel na strukturu [OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-olecmdtext) , ve které se mají vrátit informace o názvu a stavu pro jeden příkaz. Může mít hodnotu NULL, která označuje, že volající nepotřebuje tyto informace.

*pguidCmdGroup*<br/>
Jedinečný identifikátor skupiny příkazů; může mít hodnotu NULL a zadat standardní skupinu.

### <a name="return-value"></a>Návratová hodnota

Úplný seznam vrácených hodnot naleznete v tématu [IOleCommandTarget –:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) v Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce metody [IOleCommandTarget –:: QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) , jak je popsáno v Windows SDK.

##  <a name="release"></a>COleDocObjectItem:: Release

Uvolní připojení k propojené položce OLE a zavře je, pokud byla otevřená. Nezničí položku klienta.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parametry

*dwCloseOption*<br/>
Příznak určující, za jakých okolností se položka OLE uloží při návratu do načteného stavu. Seznam možných hodnot naleznete v tématu [COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Poznámky

Nezničí položku klienta.

## <a name="see-also"></a>Viz také:

[MFCBIND Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem – třída](../../mfc/reference/cdocobjectserveritem-class.md)
