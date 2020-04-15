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
ms.openlocfilehash: 5e1545a033ab482e838fbc944b0ca9b3e543d651
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366135"
---
# <a name="coledataobject-class"></a>COleDataObject – třída

Používá se při přenosu dat pro načítání dat v různých formátech ze schránky, přetažení nebo z vložené položky OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDataObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Vytvoří `COleDataObject` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDataObject::Připojit](#attach)|Připojí zadaný datový objekt `COleDataObject`OLE k souboru .|
|[COleDataObject::AttachClipboard](#attachclipboard)|Připojí datový objekt, který je ve schránce.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Připravuje se na jedno `GetNextFormat` nebo více následných hovorů.|
|[COleDataObject::Detach](#detach)|Odpojí přidružený `IDataObject` objekt.|
|[COleDataObject::GetData](#getdata)|Zkopíruje data z připojeného datového objektu OLE v určeném formátu.|
|[COleDataObject::GetFileData](#getfiledata)|Zkopíruje data z připojeného datového objektu `CFile` OLE do ukazatele v určeném formátu.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Zkopíruje data z připojeného datového objektu OLE do zadaného `HGLOBAL` formátu.|
|[COleDataObject::GetNextFormat](#getnextformat)|Vrátí další dostupný formát dat.|
|[COleDataObject::isDataAvailable](#isdataavailable)|Zkontroluje, zda jsou data k dispozici v určeném formátu.|
|[COleDataObject::Vydání](#release)|Odpojí a uvolní přidružený `IDataObject` objekt.|

## <a name="remarks"></a>Poznámky

`COleDataObject`nemá základní třídu.

Tyto druhy přenosů dat zahrnují zdroj a cíl. Zdroj dat je implementován jako objekt třídy [COleDataSource.](../../mfc/reference/coledatasource-class.md) Vždy, když cílová aplikace má data klesla v něm nebo je požádán `COleDataObject` o provedení operace vložení ze schránky, musí být vytvořen objekt třídy.

Tato třída umožňuje určit, zda data existuje v zadaném formátu. Můžete také vytvořit výčet dostupných formátů dat nebo zkontrolovat, zda je daný formát k dispozici, a potom je načíst v upřednostňovaném formátu. Načítání objektů lze provést několika různými způsoby, včetně použití [CFile](../../mfc/reference/cfile-class.md), HGLOBAL nebo `STGMEDIUM` struktury.

Další informace naleznete v [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) struktury v sadě Windows SDK.

Další informace o použití datových objektů v aplikaci naleznete v článku [Datové objekty a zdroje dat (OLE).](../../mfc/data-objects-and-data-sources-ole.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`COleDataObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject::Připojit

Volání této funkce `COleDataObject` přidružit objekt s datovým objektem OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDataObject*<br/>
Odkazuje na datový objekt OLE.

*bAutoRelease*<br/>
PRAVDA, pokud by měl být `COleDataObject` datový objekt OLE uvolněn při zničení objektu. jinak FALSE.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) v sadě Windows SDK.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard

Volání této funkce připojit datový objekt, který je aktuálně `COleDataObject` ve schránce k objektu.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Volání této funkce zamkne schránku, dokud nebude tento datový objekt uvolněn. Datový objekt je uvolněn v destruktoru pro `COleDataObject`. Další informace viz [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) a [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) v dokumentu Win32.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Volání této funkce připravit pro `GetNextFormat` následné volání pro načtení seznamu formátů dat z položky.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Poznámky

Po volání `BeginEnumFormats`je uložena pozice prvního formátu podporovaného tímto datovým objektem. Následná `GetNextFormat` volání budou výčet seznamu dostupných formátů v datovém objektu.

Chcete-li zkontrolovat dostupnost dat v daném formátu, použijte [cOleDataObject::IsDataAvailable](#isdataavailable).

Další informace naleznete v tématu [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) v sadě Windows SDK.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject

Vytvoří `COleDataObject` objekt.

```
COleDataObject();
```

### <a name="remarks"></a>Poznámky

Před voláním jiných `COleDataObject` funkcí musí být provedeno volání [COleDataObject::Attach](#attach) nebo [COleDataObject::AttachClipboard.](#attachclipboard)

> [!NOTE]
> Vzhledem k tomu, že jeden z parametrů obslužné rutiny přetažení je ukazatel na `COleDataObject`, není nutné volat tento konstruktor pro podporu přetažení.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach

Volání této funkce odpojit `COleDataObject` objekt od jeho přidružené ole datový objekt bez uvolnění datového objektu.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový objekt OLE, který byl odpojen.

### <a name="remarks"></a>Poznámky

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData

Volání této funkce pro načtení dat z položky v zadaném formátu.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát, ve kterém mají být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgStřední*<br/>
Odkazuje na [stgmedium](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) strukturu, která bude přijímat data.

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu popisující formát, ve kterém mají být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají pro `FORMATETC` ostatní pole ve struktuře.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématech IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData

Volání této funkce `CFile` k `CFile`vytvoření nebo odvozeného objektu a k `CFile` načtení dat v zadaném formátu do ukazatele.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát, ve kterém mají být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu popisující formát, ve kterém mají být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají pro `FORMATETC` ostatní pole ve struktuře.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CFile` nový `CFile`nebo odvozený objekt obsahující data v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

V závislosti na médiu, ve které jsou data uložena, `CFile`může `CSharedFile`být `COleStreamFile`skutečný typ, na který se vrací, , nebo .

> [!NOTE]
> Objekt, `CFile` ke kterého má přístup vrácená hodnota této funkce, je vlastněn volajícím. Je odpovědností volajícího **odstranit** `CFile` objekt, a tím zavřete soubor.

Další informace naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData

Volání této funkce přidělit globální blok paměti a načíst data v zadaném formátu do HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát, ve kterém mají být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu popisující formát, ve kterém mají být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají pro `FORMATETC` ostatní pole ve struktuře.

### <a name="return-value"></a>Návratová hodnota

Popisovač bloku globální paměti obsahující data v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat

Volání této funkce opakovaně získat všechny formáty, které jsou k dispozici pro načítání dat z položky.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu, která přijímá informace o formátu při volání funkce vrátí.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je k dispozici jiný formát; jinak 0.

### <a name="remarks"></a>Poznámky

Po volání [COleDataObject::BeginEnumFormats](#beginenumformats)je uložena pozice prvního formátu podporovaného tímto datovým objektem. Následná `GetNextFormat` volání budou výčet seznamu dostupných formátů v datovém objektu. Pomocí těchto funkcí můžete uvést dostupné formáty.

Chcete-li zkontrolovat dostupnost daného formátu, zavolejte [COleDataObject::IsDataAvailable](#isdataavailable).

Další informace naleznete v [tématu IEnumXXXX::Next](/previous-versions//ms695273\(v=vs.85\)) v sadě Windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::isDataAvailable

Volání této funkce k určení, pokud je k dispozici určitý formát pro načítání dat z položky OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormát*<br/>
Formát dat schránky, který má být použit ve struktuře ukázal *lpFormatEtc*. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnota vrácená nativní funkcí Windows [RegisterClipBoardFormat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Odkazuje na [formatetc](/windows/win32/api/objidl/ns-objidl-formatetc) strukturu popisující požadovaný formát. Zadejte hodnotu pro tento parametr pouze v případě, že chcete zadat další informace o formátu nad rámec formátu schránky určeného *formátem cfFormat*. Pokud je null, výchozí hodnoty se používají pro `FORMATETC` ostatní pole ve struktuře.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou data k dispozici v určeném formátu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je `GetData`užitečná před voláním , `GetFileData`, nebo `GetGlobalData`.

Další informace naleznete v tématu [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) a [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) v sadě Windows SDK.

Další informace naleznete v tématu [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject::Vydání

Volání této funkce uvolnit vlastnictví [objektu IDataObject,](/windows/win32/api/objidl/nn-objidl-idataobject) `COleDataObject` který byl dříve přidružen k objektu.

```
void Release();
```

### <a name="remarks"></a>Poznámky

Byl `IDataObject` spojen s `COleDataObject` `Attach` voláním `AttachClipboard` nebo explicitně nebo rámci. Pokud `Attach` je parametr *bAutoRelease* nepravda, `IDataObject` objekt nebude uvolněn. V tomto případě volající je zodpovědný `IDataObject` za uvolnění voláním [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[OKLIENT ukázkový příklad knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída COleDataSource](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
