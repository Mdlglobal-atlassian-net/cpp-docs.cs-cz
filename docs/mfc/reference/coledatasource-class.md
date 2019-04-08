---
title: COleDataSource Class
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 37de6fd74f1e9210dcd9b9a356719436814c0c7f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776827"
---
# <a name="coledatasource-class"></a>COleDataSource Class

Slouží jako mezipaměť, do které aplikace umístí data, která bude nabízet během data transfer operace, jako je například schránky nebo operace přetažení myší.

## <a name="syntax"></a>Syntaxe

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|Vytvoří `COleDataSource` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Nabízí data v zadaném formátu pomocí `STGMEDIUM` struktury.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Nabízí data v zadaném formátu pomocí HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Nabízí data v zadaném formátu pomocí zpožděného vykreslování.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Nabízí data ve formátu určeného v `CFile` ukazatele.|
|[COleDataSource::DelaySetData](#delaysetdata)|Volá se pro každý formátu, který je podporovaný v `OnSetData`.|
|[COleDataSource::DoDragDrop](#dodragdrop)|Provádí operace přetažení myší se zdrojem dat.|
|[COleDataSource::Empty](#empty)|Vyprázdní `COleDataSource` objektu data.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Vykreslí všechna data do schránky.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Ověří, zda data umístěná ve schránce je stále existuje.|
|[COleDataSource::OnRenderData](#onrenderdata)|Načte data jako součást zpožděné vykreslování.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Načte data do `CFile` jako součást zpožděné vykreslování.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděné vykreslování.|
|[COleDataSource::OnSetData](#onsetdata)|Volá se, aby se nahradit data v `COleDataSource` objektu.|
|[COleDataSource::SetClipboard](#setclipboard)|Místa `COleDataSource` objektu do schránky.|

## <a name="remarks"></a>Poznámky

Zdroje dat OLE můžete vytvořit přímo. Alternativně [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) třídy vytvořit zdroje dat OLE v reakci na jejich `CopyToClipboard` a `DoDragDrop` členské funkce. Zobrazit [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) stručný popis. Přepsat `OnGetClipboardData` členské funkce třídy vašeho klienta položky nebo server položky pro přidání dalších formátů schránky do dat ve zdroji dat OLE vytvořené pro `CopyToClipboard` nebo `DoDragDrop` členskou funkci.

Pokaždé, když chcete připravit data pro přenos, by měl vytvořit objekt této třídy a naplňte ji s daty pomocí metody nejvhodnější pro vaše data. Způsob, jakým je vložen do zdroje dat je přímo ovlivňován řadou okamžitě zadaná data (okamžité vykreslování) nebo na vyžádání (odložené vykreslování). Pro každou formát schránky, ve kterém jsou poskytování dat tím, že předáte formát schránky, který se má použít (a případně [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury), volání [DelayRenderData](#delayrenderdata).

Další informace o zdrojích dat a přenos dat, najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Kromě toho článku [schránky témata](../../mfc/clipboard.md) popisuje mechanismu schránky OLE.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="cachedata"></a>  COleDataSource::CacheData

Voláním této funkce můžete určit formát, ve kterém dat se nabízelo pro data operace přenosu.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.

*lpStgMedium*<br/>
Odkazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura obsahující data ve formátu určeném.

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.

### <a name="remarks"></a>Poznámky

Je nutné zadat data, protože tato funkce poskytuje okamžitou vykreslování pomocí. Data se do mezipaměti, dokud není potřeba.

Zadat data s využitím [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury. Můžete také použít `CacheGlobalData` členskou funkci, pokud dodání množství dat je dostatečně malá, aby přenést efektivně pomocí HGLOBAL.

Po volání `CacheData` `ptd` členem `lpFormatEtc` a obsah *lpStgMedium* jsou vlastněny datový objekt volajícím.

Použití zpožděného vykreslování, zavolejte [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) členskou funkci. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury v sadě Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.

##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData

Voláním této funkce můžete určit formát, ve kterém dat se nabízelo pro data operace přenosu.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.

*hGlobal*<br/>
Zpracování bloku globální paměti obsahující data ve formátu určeném.

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data s využitím okamžité vykreslování, takže při volání funkce; je nutné zadat data data se do mezipaměti, dokud není potřeba. Použití `CacheData` členskou funkci, pokud zadáváte velká množství dat nebo pokud požadujete střední strukturované úložiště.

Použití zpožděného vykreslování, zavolejte [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) členskou funkci. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.

##  <a name="coledatasource"></a>  COleDataSource::COleDataSource

Vytvoří `COleDataSource` objektu.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData

Voláním této funkce můžete určit formát, ve kterém dat se nabízelo pro data operace přenosu.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí zpožděného vykreslování, takže data není zadáno okamžitě. [OnRenderData](#onrenderdata) nebo [OnRenderGlobalData](#onrenderglobaldata) členská funkce je volána k požadavku data.

Tuto funkci použít, pokud se chystáte zadat data prostřednictvím `CFile` objektu. Pokud se chystáte zadat data prostřednictvím `CFile` objektů, zavolejte [DelayRenderFileData](#delayrenderfiledata) členskou funkci. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) členskou funkci.

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.

##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData

Voláním této funkce můžete určit formát, ve kterém dat se nabízelo pro data operace přenosu.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí zpožděného vykreslování, takže data není zadáno okamžitě. [OnRenderFileData](#onrenderfiledata) členská funkce je volána k požadavku data.

Tuto funkci použít, pokud se chystáte použít `CFile` objekt slouží k poskytování data. Pokud se chystáte použít `CFile` objektů, zavolejte [DelayRenderData](#delayrenderdata) členskou funkci. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) členskou funkci.

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.

##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData

Voláním této funkce pro podporu změnit obsah datového zdroje.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém se data budou umístěny. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém se nahradit data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.

### <a name="remarks"></a>Poznámky

[OnSetData](#onsetdata) se volá se rozhraním, když k tomu dojde. Používá se jenom návratu zdroj dat v rámci [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Pokud `DelaySetData` není volána, vaše `OnSetData` funkce nebude nikdy volána. `DelaySetData` by měla být volána pro každý schránky nebo `FORMATETC` formátu, které podporujete.

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura v sadě Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.

##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop

Volání `DoDragDrop` členská funkce k provedení operace přetažení myší pro tento zdroj dat, obvykle v [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) obslužné rutiny.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEffects*<br/>
Přetáhněte myší operace, které jsou povolené v tomto zdroji dat. Může být jeden nebo více z následujících akcí:

- DROPEFFECT_COPY, které nejde provést operaci kopírování.

- Operace přesunu A DROPEFFECT_MOVE může provést.

- Nedá se navázat odkaz A DROPEFFECT_LINK z vyřazené dat na původní data.

- DROPEFFECT_SCROLL znamená, že může dojít k posouvání operace přetažení.

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, ve kterém ve skutečnosti spustí přetahování. Další informace naleznete v následující části poznámky.

*pDropSource*<br/>
Body do zdroje přemístění. Pokud se hodnota NULL, pak výchozí implementaci třídy [coledropsource –](../../mfc/reference/coledropsource-class.md) se použije.

### <a name="return-value"></a>Návratová hodnota

Přetáhněte efekt generovaných operace přetažení myší; jinak DROPEFFECT_NONE Pokud nikdy zahájení operace vzhledem k tomu, že uživatel vydané před opuštěním zadaný obdélník tlačítko myši.

### <a name="remarks"></a>Poznámky

Operace přetažení myší nespustí ihned. To počká, dokud kurzor myši opustí obdélník určené *lpRectStartDrag* nebo dokud se zadaný počet milisekund prošly. Pokud *lpRectStartDrag* má hodnotu NULL, je velikost pravoúhelníku jeden pixel.

Doba zpoždění je určené nastavení klíče registru. Doba zpoždění lze změnit pomocí volání [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, je použita výchozí hodnota 200 MS. Přetáhněte zpoždění je uložen následujícím způsobem:

- Doba zpoždění přetáhněte Windows NT se ukládají do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Doba zpoždění přetáhněte 3.x Windows se ukládají do VÍTĚZSTVÍ. Soubor INI [Windows} oddílu.

- Přetáhněte Windows 95/98 zpoždění je uložen v mezipaměti verzi Windows. INI.

Pro další informace o tom, přetáhněte zpoždění informace jsou uloženy v registru buď nebo. Soubor INI, naleznete v tématu [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) v sadě Windows SDK.

Další informace najdete v článku [přetažení: Implementace zdroje přemístění](../../mfc/drag-and-drop-implementing-a-drop-source.md).

##  <a name="empty"></a>  COleDataSource::Empty

Voláním této funkce prázdný `COleDataSource` objektu data.

```
void Empty();
```

### <a name="remarks"></a>Poznámky

Obě do mezipaměti a formáty vykreslení zpoždění jsou vyprázdněny, takže se můžete znovu použít.

Další informace najdete v tématu [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) v sadě Windows SDK.

##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard

Vykreslí data, která je do schránky a pak umožňuje vložení dat ze schránky po ukončení vaší aplikace.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Poznámky

Použití [Modul SetClipboard](#setclipboard) dávat data do schránky.

##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner

Určuje, jestli se data do schránky změnila od [Modul SetClipboard](#setclipboard) poslední se volá a pokud ano, identifikuje aktuální vlastník.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Návratová hodnota

Data source aktuálně do schránky nebo hodnota NULL, pokud není nic do schránky nebo jestliže schránky není vlastněn volající aplikace.

##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData

Volá se rozhraním, k načtení dat v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*lpStgMedium*<br/>
Odkazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, ve kterém má být vrácena data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce bude volat [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata) Pokud je zadaný paměťovému médiu souboru nebo paměti, v uvedeném pořadí. Pokud ani jedno z těchto formátů údaje nezadáte, bude výchozí implementace vrátí 0 a Neprovádět žádnou akci. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Pokud *lpStgMedium*-> *objekt tymed* je TYMED_NULL, `STGMEDIUM` by měl být přiděleno a vyplní podle specifikace *lpFormatEtc -> objekt tymed*. Pokud není TYMED_NULL, `STGMEDIUM` by mělo být vyplněno místo s daty.

To je moderní overridable. Tato funkce slouží k poskytování dat v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud vaše data je malý a pevnou velikost, má přednost před `OnRenderGlobalData`. Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před `OnRenderFileData`.

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury, [objekt TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) typ výčtu a [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) ve Windows SDK.

##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData

Volá se rozhraním, k načtení dat v zadaném formátu souboru po zadanou paměťovému médiu.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*pFile*<br/>
Odkazuje [cfile –](../../mfc/reference/cfile-class.md) objektu, ve kterém se data mají být vykresleny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací hodnotu FALSE.

To je moderní overridable. Tato funkce slouží k poskytování dat v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud chcete zpracovávat více úložná média, má přednost před [OnRenderData](#onrenderdata). Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před `OnRenderFileData`. Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) strukturu a [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData

Volá se rozhraním, k načtení dat v zadaném formátu po globální paměti zadaná paměťovému médiu.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve které je požadované informace.

*phGlobal*<br/>
Odkazuje na popisovač do globální paměti, ve kterém má být vrácena data. Pokud nebyla ještě jeden byly přiděleny, tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je jedna dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) členskou funkci pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací hodnotu FALSE.

Pokud *phGlobal* má hodnotu NULL, pak nové HGLOBAL by měl být přiděleno a vrácené v *phGlobal*. V opačném případě HGLOBAL určené *phGlobal* by měl být vyplněny data. Množství dat, které jsou umístěny v HGLOBAL nesmí být delší než aktuální velikost bloku paměti. Navíc bloku nejde znovu přidělit, větší velikosti.

To je moderní overridable. Tato funkce slouží k poskytování dat v požadovaný formát a střední přepište. V závislosti na vašich dat můžete chtít přepsat místo toho některou z dalších verzí této funkce. Pokud chcete zpracovávat více úložná média, má přednost před [OnRenderData](#onrenderdata). Pokud vaše data se v souboru nebo se s proměnnou velikostí, má přednost před [OnRenderFileData](#onrenderfiledata). Další informace o vykreslování zpožděné jako zpracované knihovnou MFC naleznete v článku [datové objekty a zdroje dat: Manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) strukturu a [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

##  <a name="onsetdata"></a>  COleDataSource::OnSetData

Volá se rozhraním, aby nastavila nebo nahradila data v `COleDataSource` objektu v zadaném formátu.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura určující formát, ve kterém se nahrazuje data.

*lpStgMedium*<br/>
Odkazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury obsahující data, která nahradí aktuální obsah `COleDataSource` objektu.

*bRelease*<br/>
Označuje, kdo je vlastníkem úložiště média po dokončení volání funkce. Volající rozhodne, kdo je zodpovědná za uvolnění prostředků přidělených jménem paměťovému médiu. Volající toho dosahuje tím, že nastavíte *bRelease*. Pokud *bRelease* je nenulová, zdroj dat převezme vlastnictví, uvolnění médium po dokončení jeho použití. Když *bRelease* je 0, že volajícímu zůstane vlastnictví a zdroj dat můžete využít paměťovému médiu pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Zdroj dat není převzít vlastnictví dat, dokud ji má byly úspěšně načteny. To znamená, nebere v vlastnictví Pokud `OnSetData` vrátí hodnotu 0. Pokud zdroj dat trvá vlastnictví, takže paměťovému médiu voláním [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) funkce.

Výchozí implementace nemá žádný účinek. Přepsání této funkce můžete nahradit data v zadaném formátu. To je moderní overridable.

Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury a [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) a [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) funkce v sadě Windows SDK.

##  <a name="setclipboard"></a>  COleDataSource::SetClipboard

Vloží data obsažená v `COleDataSource` objektu do schránky po volání jedné z následujících funkcí: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), or [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Coledataobject – třída](../../mfc/reference/coledataobject-class.md)
