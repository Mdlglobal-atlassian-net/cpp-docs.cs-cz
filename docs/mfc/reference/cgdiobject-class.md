---
title: CGdiObject – třída
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373741"
---
# <a name="cgdiobject-class"></a>CGdiObject – třída

Poskytuje základní třídu pro různé druhy objektů rozhraní grafického zařízení systému Windows (GDI), jako jsou bitmapy, oblasti, stopy, pera, palety a písma.

## <a name="syntax"></a>Syntaxe

```
class CGdiObject : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|Vytvoří `CGdiObject` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CGdiObject::Připojit](#attach)|Připojí objekt GDI systému `CGdiObject` Windows k objektu.|
|[CGdiObject::CreateStockObject](#createstockobject)|Načte úchyt do jednoho z předdefinovaných zálohových per, stop nebo písem systému Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Odstraní objekt GDI systému Windows `CGdiObject` připojený k objektu z paměti uvolněním veškerého systémového úložiště přidruženého k objektu.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Odstraní všechny `CGdiObject` dočasné objekty vytvořené společností `FromHandle`.|
|[CGdiObject::Detach](#detach)|Odpojí objekt GDI systému `CGdiObject` Windows od objektu a vrátí popisovač objektu GDI systému Windows.|
|[CGdiObject::FromHandle](#fromhandle)|Vrátí ukazatel na `CGdiObject` objekt daný popisovač objektu GDI systému Windows.|
|[CGdiObject::GetObject](#getobject)|Vyplní vyrovnávací paměť daty, která popisují objekt GDI systému Windows připojený k objektu. `CGdiObject`|
|[CGdiObject::GetObjectType](#getobjecttype)|Načte typ objektu GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Vrátí, `m_hObject` pokud **toto** je NULL, v takovém případě null je vrácena.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Obnoví počátek stopy nebo obnoví logickou paletu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CGdiObject::operátor !=](#operator_neq)|Určuje, zda dva objekty GDI nejsou logicky stejné.|
|[CGdiObject::operátor ==](#operator_eq_eq)|Určuje, zda jsou dva objekty GDI logicky stejné.|
|[CGdiObject::operátor HGDIOBJ](#operator_hgdiobj)|Načte handle na připojený objekt GDI systému Windows.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|Popisovač obsahující HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN nebo HFONT připojené k tomuto objektu.|

## <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CGdiObject` přímo. Místo toho vytvoříte objekt z jedné z jeho `CPen` `CBrush`odvozených tříd, například nebo .

Další informace `CGdiObject`naleznete v tématu [Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::Připojit

Připojí objekt GDI systému `CGdiObject` Windows k objektu.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Handle na objekt GDI systému Windows (například HPEN nebo HBRUSH).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je příloha úspěšná; jinak 0.

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject::CGdiObject

Vytvoří `CGdiObject` objekt.

```
CGdiObject();
```

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CGdiObject` přímo. Místo toho vytvoříte objekt z jedné z jeho `CPen` `Cbrush`odvozených tříd, například nebo .

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::CreateStockObject

Načte úchyt k jednomu z předdefinovaných skladových per, stop, stop nebo písem Windows `CGdiObject` GDI a připojí k objektu objektu GDI.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Konstanta určující požadovaný typ objektu zásob. Popis příslušných hodnot naleznete v parametru *fnObject* pro [getstockobject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce s jednou z odvozených tříd, která odpovídá typu `CPen` objektu Windows GDI, například pro základní pero.

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

Odstraní připojený objekt GDI systému Windows z paměti uvolněním veškerého systémového úložiště přidruženého k objektu GDI systému Windows.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl objekt GDI úspěšně odstraněn; jinak 0.

### <a name="remarks"></a>Poznámky

Úložiště přidružené k `CGdiObject` objektu není ovlivněna toto volání. Aplikace by neměla `DeleteObject` `CGdiObject` volat objekt, který je aktuálně vybrán do kontextu zařízení.

Při odstranění stopy se vzorkem se bitmapa přidružená ke stopě neodstraní. Bitmapa musí být odstraněna nezávisle.

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

Automaticky volaná obslužnou `CWinApp` rutinou doby nečinnosti odstraní `DeleteTempMap` všechny dočasné `CGdiObject` objekty vytvořené . `FromHandle`

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Poznámky

`DeleteTempMap`Před odstraněním objektu odpojí objekt GDI systému Windows připojený k dočasnému `CGdiObject` objektu. `CGdiObject`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::Detach

Odpojí objekt GDI systému `CGdiObject` Windows od objektu a vrátí popisovač objektu GDI systému Windows.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Návratová hodnota

A `HANDLE` k objektu GDI systému Windows odpojen; jinak NULL, pokud není připojen žádný objekt GDI.

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::FromHandle

Vrátí ukazatel na `CGdiObject` objekt daný popisovač objektu GDI systému Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObjekt*<br/>
Handle na objekt GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CGdiObject` a, který může být dočasný nebo trvalý.

### <a name="remarks"></a>Poznámky

Pokud `CGdiObject` objekt ještě není připojen k objektu GDI `CGdiObject` systému Windows, je vytvořen a připojen dočasný objekt.

Tento `CGdiObject` dočasný objekt je platný pouze do dalšího okamžiku, kdy aplikace má dobu nečinnosti ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to říct, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject::GetObject

Vyplní vyrovnávací paměť daty, která definují zadaný objekt.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Určuje počet bajtů, které mají být zkopírovány do vyrovnávací paměti *lpObject.*

*lpObject*<br/>
Odkazuje na uživatelem zadanou vyrovnávací paměť, která má přijímat informace.

### <a name="return-value"></a>Návratová hodnota

Počet načtených bajtů; jinak 0, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Funkce načte datovou strukturu, jejíž typ závisí na typu grafického objektu, jak ukazuje následující seznam:

|Objekt|Typ vyrovnávací paměti|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[PROTOKOLOVÝ KARTÁČEK](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[Logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[Bitmapové](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Nepodporuje se|

Pokud je objektem `CBitmap` `GetObject` objekt, vrátí pouze informace o šířce, výšce a barevném formátu bitmapy. Skutečné bity lze načíst pomocí [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Pokud je `CPalette` objektem, `GetObject` načte word, který určuje počet položek v paletě. Funkce nenačte strukturu [LOGPALETTE,](/windows/win32/api/wingdi/ns-wingdi-logpalette) která definuje paletu. Aplikace může získat informace o položkách palety voláním [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject::GetObjectType

Načte typ objektu GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ objektu, pokud je úspěšný; jinak 0. Může jít o následující hodnoty:

- OBJ_BITMAP bitmapu

- OBJ_BRUSH štětec

- písmo OBJ_FONT

- OBJ_PAL paleta

- Pero OBJ_PEN

- OBJ_EXTPEN Rozšířené pero

- OBJ_REGION Region

- kontext OBJ_DC zařízení

- kontext OBJ_MEMDC paměťového zařízení

- OBJ_METAFILE metasoubor

- OBJ_METADC kontext zařízení Metafile

- OBJ_ENHMETAFILE rozšířený metasoubor

- OBJ_ENHMETADC kontext zařízení s rozšířenými metasoubory

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Vrátí, `m_hObject` pokud **toto** je NULL, v takovém případě null je vrácena.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Handle připojené ho objektu GDI systému Windows; jinak NULL, pokud není připojen žádný objekt.

### <a name="remarks"></a>Poznámky

Toto je součástí paradigmatu rozhraní obecné zpracování a je užitečné, když NULL je platná nebo zvláštní hodnota pro popisovač.

### <a name="example"></a>Příklad

  Viz příklad pro [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject::m_hObject

Popisovač obsahující HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE nebo HFONT připojené k tomuto objektu.

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::operátor !=

Určuje, zda dva objekty GDI nejsou logicky stejné.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Ukazatel na existující `CGdiObject`.

### <a name="remarks"></a>Poznámky

Určuje, zda se objekt GDI na levé straně nerovná objektu GDI na pravé straně.

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::operátor ==

Určuje, zda jsou dva objekty GDI logicky stejné.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Odkaz na existující `CGdiObject`.

### <a name="remarks"></a>Poznámky

Určuje, zda je objekt GDI na levé straně roven objektu GDI na pravé straně.

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::operátor HGDIOBJ

Načte handle na připojený objekt GDI systému Windows; jinak NULL, pokud není připojen žádný objekt.

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

Obnoví počátek stopy nebo obnoví logickou paletu.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Zatímco `UnrealizeObject` je členská `CGdiObject` funkce třídy, by měla `CBrush` `CPalette` být vyvolána pouze na nebo objekty.

U `CBrush` objektů `UnrealizeObject` nasměruje systém k obnovení počátku dané stopy při příštím výběru do kontextu zařízení. Pokud je objekt `CPalette` objekt, `UnrealizeObject` nasměruje systém k realizaci palety, jako by nebyla dříve realizována. Při příštím volání aplikace [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkce pro zadanou paletu, systém zcela přemapuje logickou paletu na paletu systému.

Funkce `UnrealizeObject` by neměla být použita s skladovými objekty. Funkce `UnrealizeObject` musí být volána vždy, když je nastaven nový počátek stopy (pomocí funkce [CDC::SetBrushOrg).](../../mfc/reference/cdc-class.md#setbrushorg) Funkce `UnrealizeObject` nesmí být volána pro aktuálně vybranou stopu nebo aktuálně vybranou paletu libovolného kontextu zobrazení.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBitmap – třída](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush – třída](../../mfc/reference/cbrush-class.md)<br/>
[CFont – třída](../../mfc/reference/cfont-class.md)<br/>
[CPalette – třída](../../mfc/reference/cpalette-class.md)<br/>
[CPen – třída](../../mfc/reference/cpen-class.md)<br/>
[Třída CRgn](../../mfc/reference/crgn-class.md)
