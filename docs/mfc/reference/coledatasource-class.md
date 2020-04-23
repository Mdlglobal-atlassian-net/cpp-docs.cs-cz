---
title: Třída COleDataSource
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
ms.openlocfilehash: 8746be43e3f2a31558904323392983b183d4f198
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753894"
---
# <a name="coledatasource-class"></a>Třída COleDataSource

Funguje jako mezipaměť, do které aplikace umístí data, která nabídne během operací přenosu dat, jako je například schránka nebo operace přetažení.

## <a name="syntax"></a>Syntaxe

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|Vytvoří `COleDataSource` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Nabízí data v určeném `STGMEDIUM` formátu pomocí struktury.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Nabízí data v určeném formátu pomocí HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Nabízí data v určeném formátu pomocí zpožděného vykreslování.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Nabízí data v určeném `CFile` formátu v ukazateli.|
|[COleDataSource::DelaySetData](#delaysetdata)|Volána pro každý formát, který je podporován v `OnSetData`.|
|[COleDataSource::DoDragDrop](#dodragdrop)|Provádí operace přetažení s datovým zdrojem.|
|[COleDataSource::Prázdný](#empty)|Vyprázdní `COleDataSource` objekt dat.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Vykreslí všechna data do schránky.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Ověří, zda data umístěná ve schránce stále existují.|
|[COleDataSource::OnRenderData](#onrenderdata)|Načte data jako součást zpožděného vykreslování.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Načte data `CFile` do jako součást zpožděného vykreslování.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděného vykreslování.|
|[COleDataSource::OnSetData](#onsetdata)|Nazývá se nahrazení dat `COleDataSource` v objektu.|
|[COleDataSource::SetClipboard](#setclipboard)|Umístí `COleDataSource` objekt do schránky.|

## <a name="remarks"></a>Poznámky

Zdroje dat OLE můžete vytvořit přímo. Alternativně [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [COleServerItem](../../mfc/reference/coleserveritem-class.md) třídy vytvořit zdroje `CopyToClipboard` dat `DoDragDrop` OLE v reakci na jejich a členské funkce. Stručný popis naleznete v [tématu COleServerItem::CopyToClipboard.](../../mfc/reference/coleserveritem-class.md#copytoclipboard) Přepište `OnGetClipboardData` členskou funkci klientské položky nebo třídy položky serveru a přidejte další `CopyToClipboard` formáty schránky do dat ve zdroji dat OLE vytvořeném pro členskou funkci nebo. `DoDragDrop`

Kdykoli chcete připravit data pro přenos, měli byste vytvořit objekt této třídy a vyplnit je daty pomocí nejvhodnější metody pro vaše data. Způsob, jakým je vložen do zdroje dat je přímo ovlivněna, zda jsou data poskytnuta okamžitě (okamžité vykreslování) nebo na vyžádání (zpožděné vykreslování). Pro každý formát schránky, ve kterém poskytujete data předáním formátu schránky, který má být použit (a volitelnou strukturu [FORMATETC),](/windows/win32/api/objidl/ns-objidl-formatetc) volejte [DelayRenderData](#delayrenderdata).

Další informace o zdrojích dat a přenosu dat naleznete v článku [Datové objekty a zdroje dat (OLE).](../../mfc/data-objects-and-data-sources-ole.md) Kromě toho článek [Témata schránky](../../mfc/clipboard.md) popisuje mechanismus schránky OLE.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleDataSource::CacheData

Volání této funkce k určení formátu, ve kterém jsou data nabízena během operací přenosu dat.

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát schránky, ve kterém mají být nabízena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgStřední*<br/>
Odkazuje na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu obsahující data v zadaném formátu.

*lpFormatEtc*<br/>
Poukazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být údaje nabízeny. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají `FORMATETC` pro ostatní pole ve struktuře.

### <a name="remarks"></a>Poznámky

Je nutné zadat data, protože tato funkce poskytuje pomocí okamžité vykreslování. Data jsou ukládána do mezipaměti, dokud není potřeba.

Zadávat data pomocí [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) struktury. Členní `CacheGlobalData` funkci můžete také použít, pokud je množství dat, které dodáváte, dostatečně malé, aby bylo možné je efektivně přenášet pomocí HGLOBAL.

Po `CacheData` volání `ptd` člena `lpFormatEtc` a obsah *lpStgMedium* jsou vlastněny datový objekt, nikoli volajícím.

Chcete-li použít zpožděné vykreslování, zavolejte člennou funkci [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData.](#delayrenderfiledata) Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete [v stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData

Volání této funkce k určení formátu, ve kterém jsou data nabízena během operací přenosu dat.

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát schránky, ve kterém mají být nabízena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*hGlobální*<br/>
Zpracovat globální blok paměti obsahující data v zadaném formátu.

*lpFormatEtc*<br/>
Poukazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být údaje nabízeny. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají `FORMATETC` pro ostatní pole ve struktuře.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí okamžitévykresit, takže je nutné zadat data při volání funkce; data jsou ukládána do mezipaměti, dokud není potřeba. `CacheData` Členské funkce použijte, pokud dodáváte velké množství dat nebo pokud požadujete strukturované paměťové médium.

Chcete-li použít zpožděné vykreslování, zavolejte člennou funkci [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData.](#delayrenderfiledata) Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>COleDataSource::COleDataSource

Vytvoří `COleDataSource` objekt.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleDataSource::DelayRenderData

Volání této funkce k určení formátu, ve kterém jsou data nabízena během operací přenosu dat.

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát schránky, ve kterém mají být nabízena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Poukazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být údaje nabízeny. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají `FORMATETC` pro ostatní pole ve struktuře.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí zpožděné vykreslování, takže data nejsou zadána okamžitě. Členská funkce [OnRenderData](#onrenderdata) nebo [OnRenderGlobalData](#onrenderglobaldata) je volána pro vyžádání dat.

Tuto funkci použijte, pokud nebudete zadávat `CFile` data prostřednictvím objektu. Pokud se chystáte zadat data `CFile` prostřednictvím objektu, volejte [DelayRenderFileData](#delayrenderfiledata) členská funkce. Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte člennou funkci [CacheData](#cachedata) nebo [CacheGlobalData.](#cacheglobaldata)

Další informace naleznete [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData

Volání této funkce k určení formátu, ve kterém jsou data nabízena během operací přenosu dat.

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát schránky, ve kterém mají být nabízena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Poukazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být údaje nabízeny. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají `FORMATETC` pro ostatní pole ve struktuře.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí zpožděné vykreslování, takže data nejsou zadána okamžitě. Členská funkce [OnRenderFileData](#onrenderfiledata) je volána pro vyžádání dat.

Tuto funkci použijte, pokud chcete `CFile` k dodání dat použít objekt. Pokud nebudete používat `CFile` objekt, zavolejte člennou funkci [DelayRenderData.](#delayrenderdata) Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte člennou funkci [CacheData](#cachedata) nebo [CacheGlobalData.](#cacheglobaldata)

Další informace naleznete [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleDataSource::DelaySetData

Volání této funkce pro podporu změny obsahu zdroje dat.

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát schránky, ve kterém mají být data umístěna. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Poukazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být data nahrazena. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají `FORMATETC` pro ostatní pole ve struktuře.

### <a name="remarks"></a>Poznámky

[OnSetData](#onsetdata) bude volána rámci, když k tomu dojde. Používá se pouze v případě, že rozhraní framework vrátí zdroj dat z [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Pokud `DelaySetData` není volána, vaše `OnSetData` funkce nikdy nebude volána. `DelaySetData`by měla být volána `FORMATETC` pro každou schránku nebo formát, který podporujete.

Další informace naleznete [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleDataSource::DoDragDrop

Volání `DoDragDrop` členské funkce k provedení operace přetažení pro tento zdroj dat, obvykle v [cWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) obslužné rutiny.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEfekty*<br/>
Operace přetažení, které jsou povoleny v tomto zdroji dat. Může být jeden nebo více z následujících:

- DROPEFFECT_COPY Mohla by být provedena operace kopírování.

- DROPEFFECT_MOVE Může být provedena operace přesunutí.

- DROPEFFECT_LINK Bylo možné navázat spojení z vynechaná data s původními daty.

- DROPEFFECT_SCROLL Označuje, že může dojít k operaci přetahování.

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, kde přetažení skutečně začíná. Další informace naleznete v následující části poznámky.

*pDropSource*<br/>
Odkazuje na zdroj přetažení. Pokud null pak bude použita výchozí implementace [COleDropSource.](../../mfc/reference/coledropsource-class.md)

### <a name="return-value"></a>Návratová hodnota

Efekt přetažení generovaný operací přetažení; jinak DROPEFFECT_NONE pokud operace nikdy nezačne, protože uživatel uvolnil tlačítko myši před opuštěním dodaného obdélníku.

### <a name="remarks"></a>Poznámky

Operace přetažení se nespustí okamžitě. Čeká, dokud kurzor myši opustí obdélník určený *lpRectStartDrag* nebo dokud neuplyne zadaný počet milisekund. Pokud *lpRectStartDrag* je NULL, velikost obdélníku je jeden pixel.

Doba zpoždění je určena nastavením klíče registru. Čas zpoždění můžete změnit voláním [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, použije se výchozí hodnota 200 milisekund. Doba zpoždění přetažení je uložena následujícím způsobem:

- Doba zpoždění přetažení systému Windows NT je uložena v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Windows 3.x Drag delay time je uložen v WIN. ini, v části [Windows}.

- Windows 95/98 Doba zpoždění přetažení je uložena ve verzi win uložené v mezipaměti. Ini.

Další informace o tom, jak jsou informace o zpoždění přetažení uloženy v registru nebo v . INI, viz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) v sadě Windows SDK.

Další informace naleznete v článku [OLE přetažení .](../../mfc/drag-and-drop-ole.md)

## <a name="coledatasourceempty"></a><a name="empty"></a>COleDataSource::Prázdný

Volání této funkce `COleDataSource` vyprázdnit objekt dat.

```cpp
void Empty();
```

### <a name="remarks"></a>Poznámky

Formáty vykreslení uložené v mezipaměti i zpoždění jsou vyprázdněny, takže je lze znovu použít.

Další informace naleznete v tématu [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) v sadě Windows SDK.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleDataSource::FlushClipboard

Vykreslí data, která je ve schránce, a potom umožňuje vložit data ze schránky po ukončení aplikace.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Poznámky

Pomocí [funkce SetClipboard](#setclipboard) můžete data umístit do schránky.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner

Určuje, zda se data ve schránce od posledního volání [setclipboardu](#setclipboard) změnila, a pokud ano, identifikuje aktuálního vlastníka.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Návratová hodnota

Zdroj dat aktuálně ve schránce nebo NULL, pokud není nic ve schránce nebo pokud schránka není vlastněna volající aplikací.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleDataSource::OnRenderData

Volat rámci načíst data v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*lpStgStřední*<br/>
Odkazuje na [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, ve kterém mají být vrácena data.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) členfunkce pro zpožděné vykreslování. Výchozí implementace této funkce bude volat [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData,](#onrenderglobaldata) pokud je dodané paměťové médium soubor emituje nebo paměť. Pokud nejsou zadány žádné z těchto formátů, pak výchozí implementace vrátí 0 a neprovede nic. Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Pokud *lpStgMedium*-> *tymed* je `STGMEDIUM` TYMED_NULL, by měly být přiděleny a vyplněny podle *lpFormatEtc->tymed*. Pokud není TYMED_NULL, `STGMEDIUM` měla by být vyplněna na místě s údaji.

Tohle je pokročilé překažné. Přepsat tuto funkci a zadat data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud jsou data malá a pevná, přepište . `OnRenderGlobalData` Pokud jsou data v souboru nebo mají proměnnou velikost, přepište to `OnRenderFileData`.

Další informace naleznete [v stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) struktury, typ výčtu [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) a [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData

Volat rámci načíst data v zadaném formátu, pokud je zadané paměťové médium soubor.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*pSoubor*<br/>
Odkazuje na [cfile](../../mfc/reference/cfile-class.md) objekt, ve kterém mají být vykresleny data.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](#delayrenderdata) členské funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu NEPRAVDA.

Tohle je pokročilé překažné. Přepsat tuto funkci a zadat data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více paměťových médií, přepište [OnRenderData](#onrenderdata). Pokud jsou data v souboru nebo mají proměnnou velikost, přepište to `OnRenderFileData`. Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) struktura a [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData

Volat rámci načíst data v zadaném formátu, pokud zadané paměťové médium je globální paměti.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou požadovány informace.

*phGlobální*<br/>
Odkazuje na popisovač globální paměti, ve kterém mají být vrácena data. Pokud jeden ještě nebylpřidělen, tento parametr může být NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve `COleDataSource` umístěn v objektu pomocí [delayrenderdata](#delayrenderdata) členské funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu NEPRAVDA.

Pokud *phGlobal* je NULL, pak nový HGLOBAL by měly být přiděleny a vráceny v *phGlobal*. V opačném případě hglobal určené *phGlobal* by měla být vyplněna data. Množství dat umístěných v HGLOBAL nesmí překročit aktuální velikost bloku paměti. Také blok nelze přerozděleny na větší velikost.

Tohle je pokročilé překažné. Přepsat tuto funkci a zadat data v požadovaném formátu a médiu. V závislosti na datech můžete místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více paměťových médií, přepište [OnRenderData](#onrenderdata). Pokud jsou data v souboru nebo má proměnnou velikost, přepište [onRenderFileData](#onrenderfiledata). Další informace o zpožděném vykreslování, jak je zpracovává knihovna MFC, naleznete v článku [Datové objekty a zdroje dat: Manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) struktura a [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleDataSource::OnSetData

Volat rámci nastavit nebo nahradit data `COleDataSource` v objektu v zadaném formátu.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu určující formát, ve kterém jsou data nahrazována.

*lpStgStřední*<br/>
Odkazuje na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu obsahující data, která nahradí `COleDataSource` aktuální obsah objektu.

*bUvolnění*<br/>
Označuje, kdo má vlastnictví paměťového média po dokončení volání funkce. Volající rozhodne, kdo je zodpovědný za uvolnění prostředků přidělených jménem paměťového média. Volající to provádí nastavením *bRelease*. Pokud *bRelease* je nenulová, zdroj dat přebírá vlastnictví, uvolnění média po dokončení jeho použití. Když *bRelease* je 0, volající si zachová vlastnictví a zdroj dat můžete použít paměťové médium pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zdroj dat nepřevezme vlastnictví dat, dokud je úspěšně nezíská. To znamená, že nepřevezme `OnSetData` vlastnictví, pokud vrátí 0. Pokud zdroj dat převezme vlastnictví, uvolní paměťové médium voláním [releasestgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) funkce.

Výchozí implementace neprovede žádné provádění. Přepište tuto funkci a nahraďte data v určeném formátu. Tohle je pokročilé překažné.

Další informace naleznete v strukturách [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a ve funkcích [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) a [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v sadě Windows SDK.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleDataSource::SetClipboard

Umístí data obsažená `COleDataSource` v objektu do schránky po volání jedné z následujících funkcí: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)nebo [DelayRenderFileData](#delayrenderfiledata).

```cpp
void SetClipboard();
```

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject – třída](../../mfc/reference/coledataobject-class.md)
