---
title: COleDataSource – – třída
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
ms.openlocfilehash: 5cd573590bc1adb303e0b4c5cd600b9fa6c685b2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855723"
---
# <a name="coledatasource-class"></a>COleDataSource – – třída

Slouží jako mezipaměť, do které aplikace umístí data, která budou nabídnuta během operací přenosu dat, jako je například schránka nebo operace přetažení.

## <a name="syntax"></a>Syntaxe

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDataSource –:: COleDataSource –](#coledatasource)|Vytvoří objekt `COleDataSource`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDataSource –:: CacheData](#cachedata)|Nabízí data v zadaném formátu pomocí `STGMEDIUM` struktury.|
|[COleDataSource –:: CacheGlobalData](#cacheglobaldata)|Nabízí data v zadaném formátu pomocí HGLOBAL.|
|[COleDataSource –::D elayRenderData](#delayrenderdata)|Nabízí data v zadaném formátu pomocí opožděného vykreslování.|
|[COleDataSource –::D elayRenderFileData](#delayrenderfiledata)|Nabízí v `CFile` ukazateli data v zadaném formátu.|
|[COleDataSource –::D elaySetData](#delaysetdata)|Volá se pro každý formát, který je podporovaný v `OnSetData`.|
|[COleDataSource –::D oDragDrop](#dodragdrop)|Provádí operace přetažení se zdrojem dat.|
|[COleDataSource –:: Empty](#empty)|Vyprázdní `COleDataSource` objekt dat.|
|[COleDataSource –:: FlushClipboard](#flushclipboard)|Vykreslí všechna data do schránky.|
|[COleDataSource –:: GetClipboardOwner](#getclipboardowner)|Ověřuje, zda jsou data umístěná ve schránce stále k dispozici.|
|[COleDataSource –:: OnRenderData](#onrenderdata)|Načte data jako součást zpožděného vykreslování.|
|[COleDataSource –:: OnRenderFileData](#onrenderfiledata)|Načte data do `CFile` jako součást zpožděného vykreslování.|
|[COleDataSource –:: OnRenderGlobalData](#onrenderglobaldata)|Načte data do HGLOBAL jako součást zpožděného vykreslování.|
|[COleDataSource –::-SetData](#onsetdata)|Volá se, aby se nahradila data v objektu `COleDataSource`.|
|[COleDataSource –:: SetClipboard](#setclipboard)|Umístí objekt `COleDataSource` do schránky.|

## <a name="remarks"></a>Poznámky

Můžete vytvořit zdroje dat OLE přímo. Případně třídy [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [odvozenou třídu COleServerItem](../../mfc/reference/coleserveritem-class.md) vytvářejí zdroje dat OLE v reakci na jejich `CopyToClipboard` a `DoDragDrop` členské funkce. Stručný popis najdete v tématu [odvozenou třídu COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) . Přepište členskou funkci `OnGetClipboardData` položky klienta nebo třídy položky serveru pro přidání dalších formátů schránky k datům ve zdroji dat OLE vytvořeném pro `CopyToClipboard` nebo `DoDragDrop` členské funkce.

Kdykoli budete chtít připravit data pro přenos, měli byste vytvořit objekt této třídy a vyplnit je daty pomocí nejvhodnější metody pro vaše data. Způsob, jakým je vložen do zdroje dat, je přímo ovlivněn tím, že data jsou zadána okamžitě (okamžité vykreslování) nebo na vyžádání (zpožděné vykreslování). Pro všechny formáty schránky, ve kterých poskytujete data předáním formátu schránky, který se má použít (a volitelné struktury [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) ), zavolejte [DelayRenderData](#delayrenderdata).

Další informace o zdrojích dat a přenosu dat najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Kromě toho [témata ve schránce](../../mfc/clipboard.md) v článcích popisují mechanismus schránky OLE.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="cachedata"></a>COleDataSource –:: CacheData

Voláním této funkce určíte formát, ve kterém jsou během operací přenosu dat nabídnuta data.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém mají být data nabídnuta. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpStgMedium*<br/>
Odkazuje na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) obsahující data v zadaném formátu.

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="remarks"></a>Poznámky

Je nutné dodat data, protože tato funkce poskytuje použití okamžitého vykreslování. Data se ukládají do mezipaměti, dokud ji nepotřebujete.

Poskytněte data pomocí struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) . Můžete také použít členskou funkci `CacheGlobalData`, pokud je množství dat, které zadáváte, dostatečně malé, aby bylo možné je převést efektivně pomocí HGLOBAL.

Po volání `CacheData` `ptd` členem `lpFormatEtc` a obsah *lpStgMedium* jsou vlastněn datovým objektem, nikoli volajícím.

Chcete-li použít zpožděné vykreslování, zavolejte členskou funkci [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) . Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v tématu struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="cacheglobaldata"></a>COleDataSource –:: CacheGlobalData

Voláním této funkce určíte formát, ve kterém jsou během operací přenosu dat nabídnuta data.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém mají být data nabídnuta. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*hGlobal*<br/>
Pořídí globální blok paměti obsahující data v zadaném formátu.

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí okamžitého vykreslování, takže při volání funkce je nutné dodat data. data se ukládají do mezipaměti, dokud ji nepotřebujete. Pokud zadáváte velké množství dat nebo pokud vyžadujete strukturované paměťové médium, použijte členskou funkci `CacheData`.

Chcete-li použít zpožděné vykreslování, zavolejte členskou funkci [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) . Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace najdete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="coledatasource"></a>COleDataSource –:: COleDataSource –

Vytvoří objekt `COleDataSource`.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>COleDataSource –::D elayRenderData

Voláním této funkce určíte formát, ve kterém jsou během operací přenosu dat nabídnuta data.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém mají být data nabídnuta. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí opožděného vykreslování, takže data nejsou dodána okamžitě. Je volána členská funkce [OnRenderData](#onrenderdata) nebo [OnRenderGlobalData](#onrenderglobaldata) , která požaduje data.

Tuto funkci použijte, pokud nebudete zadávat data prostřednictvím objektu `CFile`. Pokud budete zadávat data prostřednictvím objektu `CFile`, zavolejte členskou funkci [DelayRenderFileData](#delayrenderfiledata) . Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte členskou funkci [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) .

Další informace najdete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="delayrenderfiledata"></a>COleDataSource –::D elayRenderFileData

Voláním této funkce určíte formát, ve kterém jsou během operací přenosu dat nabídnuta data.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém mají být data nabídnuta. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají data nabízet. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="remarks"></a>Poznámky

Tato funkce poskytuje data pomocí opožděného vykreslování, takže data nejsou dodána okamžitě. Členská funkce [OnRenderFileData](#onrenderfiledata) je volána k vyžádání dat.

Tuto funkci použijte, pokud chcete k zadávání dat použít objekt `CFile`. Pokud nebudete používat objekt `CFile`, zavolejte členskou funkci [DelayRenderData](#delayrenderdata) . Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Chcete-li použít okamžité vykreslování, zavolejte členskou funkci [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) .

Další informace najdete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="delaysetdata"></a>COleDataSource –::D elaySetData

Voláním této funkce můžete podporovat změnu obsahu zdroje dat.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát schránky, ve kterém mají být data umístěna. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém mají být data nahrazena. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="remarks"></a>Poznámky

Pokud k tomu dojde, bude rozhraní volána rozhraním [SetData](#onsetdata) . Tato funkce se používá pouze v případě, že rozhraní vrátí zdroj dat z [odvozenou třídu COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Pokud není zavolána `DelaySetData`, vaše funkce `OnSetData` nebude nikdy volána. pro každou schránku nebo formát `FORMATETC`, které podporujete, by měla být volána `DelaySetData`.

Další informace najdete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="dodragdrop"></a>COleDataSource –::D oDragDrop

Voláním členské funkce `DoDragDrop` proveďte operaci přetažení pro tento zdroj dat, obvykle v obslužné rutině [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) .

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEffects*<br/>
Operace přetažení, které jsou povoleny v tomto zdroji dat. Může se jednat o jednu nebo více z následujících možností:

- DROPEFFECT_COPY může být provedena operace kopírování.

- DROPEFFECT_MOVE lze provést operaci přesunutí.

- Bylo by možné navázat DROPEFFECT_LINK odkaz z vynechaných dat na původní data.

- DROPEFFECT_SCROLL označuje, že by mohlo dojít k operaci přetažení.

*lpRectStartDrag*<br/>
Ukazatel na obdélník, který definuje, kde se má skutečně začít přetahování. Další informace naleznete v následující části poznámky.

*pDropSource*<br/>
Odkazuje na zdroj odkládacího umístění. Pokud je NULL, použije se výchozí implementace [COleDropSource](../../mfc/reference/coledropsource-class.md) .

### <a name="return-value"></a>Návratová hodnota

Odkládací efekt generovaný operací přetažení; jinak DROPEFFECT_NONE, pokud se operace nikdy nespustí, protože uživatel uvolnil tlačítko myši před tím, než opustí zadaný obdélník.

### <a name="remarks"></a>Poznámky

Operace přetažení se nespustí okamžitě. Počká, dokud ukazatel myši neopustí obdélník určený parametrem *lpRectStartDrag* , nebo dokud neuplyne zadaný počet milisekund. Pokud má *lpRectStartDrag* hodnotu null, je velikost obdélníku jeden pixel.

Doba zpoždění je určena nastavením klíče registru. Dobu zpoždění můžete změnit voláním [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte dobu zpoždění, použije se výchozí hodnota 200 milisekund. Čas zpoždění při přetahování je uložený takto:

- Čas zpoždění při přetahování Windows NT je uložený ve HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Čas zpoždění při přetahování Windows 3. x je uložený v souboru WIN. Soubor INI, v části [Windows}.

- Čas zpoždění při přetahování Windows 95/98 je uložený ve verzi WIN uložené v mezipaměti. Užívaný.

Další informace o tom, jak jsou informace o zpoždění při přetahování uloženy v registru nebo v. Soubor INI, viz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) v Windows SDK.

Další informace najdete v článku [přetažení OLE](../../mfc/drag-and-drop-ole.md).

##  <a name="empty"></a>COleDataSource –:: Empty

Voláním této funkce vyprázdněte objekt `COleDataSource` dat.

```
void Empty();
```

### <a name="remarks"></a>Poznámky

Formáty pro vykreslení v mezipaměti i zpožděné vykreslování se vyprázdní, takže se dají znovu použít.

Další informace najdete v tématu [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) v Windows SDK.

##  <a name="flushclipboard"></a>COleDataSource –:: FlushClipboard

Vykreslí data, která jsou ve schránce, a po ukončení aplikace umožňuje vložit data ze schránky.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Poznámky

Pomocí [SetClipboard](#setclipboard) umístěte data do schránky.

##  <a name="getclipboardowner"></a>COleDataSource –:: GetClipboardOwner

Určuje, zda se data ve schránce změnila od posledního volání [SetClipboard](#setclipboard) , a pokud ano, identifikuje aktuálního vlastníka.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Návratová hodnota

Zdroj dat, který je aktuálně ve schránce, nebo hodnotu NULL, pokud ve schránce není nic, nebo pokud schránku nevlastní volající aplikace.

##  <a name="onrenderdata"></a>COleDataSource –:: OnRenderData

Volá se rozhraním, aby se načetla data v zadaném formátu.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*lpStgMedium*<br/>
Odkazuje na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , ve které se mají vrátit data.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve umístěn do objektu `COleDataSource` pomocí členské funkce [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) pro zpožděné vykreslování. Výchozí implementace této funkce bude volat [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata) , pokud dodané paměťové médium je buď soubor, nebo paměť, v uvedeném pořadí. Pokud nejsou zadány žádné z těchto formátů, bude výchozí implementace vracet hodnotu 0 a neprovede žádnou akci. Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Pokud je TYMED_NULL *lpStgMedium*-> *TYMED* , `STGMEDIUM` by měl být přidělen a vyplněný, jak je uvedeno v *lpFormatEtc-> TYMED*. Pokud není TYMED_NULL, `STGMEDIUM` by se měla vyplnit daty.

Toto je pokročilá přepsatelné. Tuto funkci popište, pokud chcete data dodat v požadovaném formátu a středníku. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud jsou vaše data malá a pevná velikost, přepište `OnRenderGlobalData`. Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, popište `OnRenderFileData`.

Další informace naleznete v tématu struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , typ výčtu [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) a [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v Windows SDK.

##  <a name="onrenderfiledata"></a>COleDataSource –:: OnRenderFileData

Volá se rozhraním, aby se načetla data v zadaném formátu, když zadané paměťové médium je soubor.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*pFile*<br/>
Odkazuje na objekt [CFile –](../../mfc/reference/cfile-class.md) , ve kterém se mají data vykreslovat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve umístěn do objektu `COleDataSource` pomocí členské funkce [DelayRenderData](#delayrenderdata) pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu FALSE.

Toto je pokročilá přepsatelné. Tuto funkci popište, pokud chcete data dodat v požadovaném formátu a středníku. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více úložných médií, přepište [OnRenderData](#onrenderdata). Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, popište `OnRenderFileData`. Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v Windows SDK.

##  <a name="onrenderglobaldata"></a>COleDataSource –:: OnRenderGlobalData

Volá se rozhraním, aby se načetla data v zadaném formátu, pokud je zadané paměťové médium globální paměti.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém jsou požadovány informace.

*phGlobal*<br/>
Odkazuje na popisovač globální paměti, ve které mají být vrácena data. Pokud ještě není přidělený, tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadaný formát je dříve umístěn do objektu `COleDataSource` pomocí členské funkce [DelayRenderData](#delayrenderdata) pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrátí hodnotu FALSE.

Pokud má *phGlobal* hodnotu null, měl by se přidělit a vrátit nový HGLOBAL v *phGlobal*. V opačném případě by měl být HGLOBAL zadaný pomocí *phGlobal* vyplněn daty. Množství dat umístěných v HGLOBAL nesmí překročit aktuální velikost bloku paměti. Blok nelze také přidělit větší velikosti.

Toto je pokročilá přepsatelné. Tuto funkci popište, pokud chcete data dodat v požadovaném formátu a středníku. V závislosti na vašich datech možná budete chtít místo toho přepsat jednu z dalších verzí této funkce. Pokud chcete zpracovat více úložných médií, přepište [OnRenderData](#onrenderdata). Pokud jsou vaše data v souboru nebo mají proměnlivou velikost, přepište [OnRenderFileData](#onrenderfiledata). Další informace o zpožděném vykreslování, jak jsou zpracovávány knihovnou MFC, naleznete v článku [datové objekty a zdroje dat: manipulace](../../mfc/data-objects-and-data-sources-manipulation.md).

Další informace naleznete v tématu struktura [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v Windows SDK.

##  <a name="onsetdata"></a>COleDataSource –::-SetData

Volá se rozhraním, aby se nastavila nebo nahradila data v objektu `COleDataSource` v zadaném formátu.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) s určením formátu, ve kterém se data nahrazují.

*lpStgMedium*<br/>
Odkazuje na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) obsahující data, která nahradí aktuální obsah objektu `COleDataSource`.

*bRelease*<br/>
Označuje, kdo má po dokončení volání funkce vlastnictví úložného média. Volající určí, kdo zodpovídá za uvolnění prostředků přidělených za médium úložiště. Volající to provede nastavením *bRelease*. Pokud je *bRelease* nenulového, zdroj dat převezme vlastnictví a uvolní médium, až ho dokončí jeho používání. Pokud je *bRelease* 0, volající si zachová vlastnictví a zdroj dat může použít paměťové médium pouze po dobu trvání volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zdroj dat převezme vlastnictví dat, dokud je neúspěšně nezískal. To znamená, že nepřevezme vlastnictví, pokud `OnSetData` vrátí hodnotu 0. Pokud zdroj dat převezme vlastnictví, uvolní médium úložiště voláním funkce [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

Výchozí implementace neprovádí žádnou akci. Přepsáním této funkce nahradíte data v zadaném formátu. Toto je pokročilá přepsatelné.

Další informace naleznete v tématu struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) a funkce [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) a [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) v Windows SDK.

##  <a name="setclipboard"></a>COleDataSource –:: SetClipboard

Vloží data obsažená v objektu `COleDataSource` ve schránce po volání jedné z následujících funkcí: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)nebo [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Viz také

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject – třída](../../mfc/reference/coledataobject-class.md)
