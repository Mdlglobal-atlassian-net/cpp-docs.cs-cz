---
title: COleDataObject – třída
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: e706489a84ad564949e2c2d3d193173fc19b9828
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421154"
---
# <a name="coledataobject-class"></a>COleDataObject – třída

Používá se v přenosech dat pro načítání dat v různých formátech ze schránky, pomocí přetažení nebo z vložené položky OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDataObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Vytvoří objekt `COleDataObject`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDataObject:: Attach](#attach)|Připojí zadaný datový objekt OLE k `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Připojí datový objekt, který je ve schránce.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Připraví jednu nebo více dalších `GetNextFormat` volání.|
|[COleDataObject::D etach](#detach)|Odpojí přidružený objekt `IDataObject`.|
|[COleDataObject:: GetData](#getdata)|Zkopíruje data z připojeného datového objektu OLE v zadaném formátu.|
|[COleDataObject::GetFileData](#getfiledata)|Zkopíruje data z připojeného datového objektu OLE do ukazatele `CFile` v zadaném formátu.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Zkopíruje data z připojeného datového objektu OLE do `HGLOBAL` v zadaném formátu.|
|[COleDataObject::GetNextFormat](#getnextformat)|Vrátí následující datový formát, který je k dispozici.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Kontroluje, zda jsou data v zadaném formátu k dispozici.|
|[COleDataObject:: Release](#release)|Odpojí a uvolní přidružený objekt `IDataObject`.|

## <a name="remarks"></a>Poznámky

`COleDataObject` nemá základní třídu.

Mezi tyto typy přenosů dat patří zdroj a cíl. Zdroj dat je implementován jako objekt třídy [COleDataSource –](../../mfc/reference/coledatasource-class.md) . Pokaždé, když cílová aplikace obsahuje data, která jsou v něm Vyřazená, nebo se zobrazí výzva k provedení operace vložení ze schránky, musí se vytvořit objekt `COleDataObject` třídy.

Tato třída umožňuje určit, zda data existují v zadaném formátu. Můžete také vytvořit výčet dostupných formátů dat nebo ověřit, zda je daný formát k dispozici, a pak načíst data v upřednostňovaném formátu. Načítání objektů lze provést několika různými způsoby, včetně použití [CFile –](../../mfc/reference/cfile-class.md), HGLOBAL nebo struktury `STGMEDIUM`.

Další informace najdete v tématu struktura [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) v Windows SDK.

Další informace o použití datových objektů v aplikaci naleznete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleDataObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="attach"></a>COleDataObject:: Attach

Voláním této funkce přidružíte objekt `COleDataObject` k datovému objektu OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDataObject*<br/>
Odkazuje na datový objekt OLE.

*bAutoRelease*<br/>
TRUE, pokud by měl být datový objekt OLE uvolněn při zničení objektu `COleDataObject`; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) v Windows SDK.

##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard

Voláním této funkce připojíte datový objekt, který je aktuálně ve schránce, do objektu `COleDataObject`.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Voláním této funkce se schránka zamkne, dokud se tento datový objekt neuvolní. Datový objekt je uvolněn v destruktoru pro `COleDataObject`. Další informace najdete v tématu [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) a [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) v dokumentu Win32.

##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Voláním této funkce připravte na další volání `GetNextFormat` pro načtení seznamu formátů dat z položky.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Poznámky

Po volání `BeginEnumFormats`se uloží pozice prvního formátu podporovaného tímto datovým objektem. Po sobě jdoucí volání `GetNextFormat` vytvoří výčet seznamu dostupných formátů v datovém objektu.

K ověření dostupnosti dat v daném formátu použijte [COleDataObject:: IsDataAvailable](#isdataavailable).

Další informace naleznete v tématu [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) v Windows SDK.

##  <a name="coledataobject"></a>COleDataObject::COleDataObject

Vytvoří objekt `COleDataObject`.

```
COleDataObject();
```

### <a name="remarks"></a>Poznámky

Před voláním jiných funkcí `COleDataObject` musí být provedeno volání [COleDataObject:: Attach](#attach) nebo [COleDataObject:: AttachClipboard](#attachclipboard) .

> [!NOTE]
>  Vzhledem k tomu, že jeden z parametrů obslužných rutin přetažení je ukazatel na `COleDataObject`, není nutné volat tento konstruktor pro podporu přetahování myší.

##  <a name="detach"></a>COleDataObject::D etach

Voláním této funkce odpojíte objekt `COleDataObject` od přidruženého datového objektu OLE bez uvolnění datového objektu.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový objekt OLE, který byl odpojen.

### <a name="remarks"></a>Poznámky

##  <a name="getdata"></a>COleDataObject:: GetData

Voláním této funkce načtete data z položky v zadaném formátu.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát, ve kterém se mají vracet data Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpStgMedium*<br/>
Odkazuje na strukturu [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , která bude přijímat data.

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají vracet data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="getfiledata"></a>COleDataObject::GetFileData

Voláním této funkce vytvoříte objekt odvozený `CFile` nebo `CFile`a načtete data v zadaném formátu do ukazatele `CFile`.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát, ve kterém se mají vracet data Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají vracet data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový `CFile` nebo objekt odvozený `CFile`, který obsahuje data v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

V závislosti na médiu, ve kterém jsou data uložená, může být skutečný typ, na který odkazuje vrácená hodnota, `CFile`, `CSharedFile`nebo `COleStreamFile`.

> [!NOTE]
>  Objekt `CFile`, k němuž přistupovala vrácená hodnota této funkce, je vlastníkem volajícího. Je odpovědností volajícího **Odstranit** objekt `CFile`, takže soubor zavře.

Další informace najdete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData

Voláním této funkce přidělíte globální blok paměti a načtěte data v zadaném formátu do HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát, ve kterém se mají vracet data Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující formát, ve kterém se mají vracet data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="return-value"></a>Návratová hodnota

Popisovač globálního bloku paměti obsahující data v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

##  <a name="getnextformat"></a>COleDataObject::GetNextFormat

Voláním této funkce opakovaně získáte všechny formáty, které jsou k dispozici pro načtení dat z položky.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , která obdrží informace o formátu při návratu volání funkce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je k dispozici jiný formát; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Po volání metody [COleDataObject:: BeginEnumFormats](#beginenumformats)je uložena pozice prvního formátu podporovaného tímto datovým objektem. Po sobě jdoucí volání `GetNextFormat` vytvoří výčet seznamu dostupných formátů v datovém objektu. Pomocí těchto funkcí můžete zobrazit seznam dostupných formátů.

Chcete-li zjistit dostupnost daného formátu, zavolejte [COleDataObject:: IsDataAvailable](#isdataavailable).

Další informace naleznete v tématu [IEnumXXXX:: Next](/previous-versions//ms695273\(v=vs.85\)) v Windows SDK.

##  <a name="isdataavailable"></a>COleDataObject::IsDataAvailable

Voláním této funkce zjistíte, zda je k dispozici konkrétní formát pro načítání dat z položky OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formát dat ve schránce, který má být použit ve struktuře, na kterou odkazuje *lpFormatEtc*. Tento parametr může být jedním z předdefinovaných formátů schránky nebo hodnotou vrácenou nativní funkcí Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

*lpFormatEtc*<br/>
Odkazuje na strukturu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) popisující požadovaný formát. Zadejte hodnotu pro tento parametr pouze v případě, že chcete zadat další informace o formátu za formát schránky určený parametrem *cfFormat*. Pokud má hodnotu NULL, použijí se výchozí hodnoty pro ostatní pole ve struktuře `FORMATETC`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou data k dispozici v zadaném formátu; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná před voláním `GetData`, `GetFileData`nebo `GetGlobalData`.

Další informace naleznete v tématu [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v Windows SDK.

Další informace najdete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>COleDataObject:: Release

Voláním této funkce uvolníte vlastnictví objektu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) , který byl dříve přidružen k objektu `COleDataObject`.

```
void Release();
```

### <a name="remarks"></a>Poznámky

`IDataObject` byla k `COleDataObject` přidružena voláním `Attach` nebo `AttachClipboard` explicitně nebo rozhraním. Pokud je parametr *bAutoRelease* `Attach` false, nebude objekt `IDataObject` uvolněn. V tomto případě volající zodpovídá za uvolnění `IDataObject` voláním metody [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Viz také

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[OCLIENT Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource – třída](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
