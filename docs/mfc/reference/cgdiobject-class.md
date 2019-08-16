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
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506259"
---
# <a name="cgdiobject-class"></a>CGdiObject – třída

Poskytuje základní třídu pro různé druhy objektů rozhraní Windows Graphics zařízení (GDI), jako jsou bitmapy, oblasti, štětce, pera, palety a písma.

## <a name="syntax"></a>Syntaxe

```
class CGdiObject : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|`CGdiObject` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGdiObject::Attach](#attach)|Připojí objekt GDI systému Windows k `CGdiObject` objektu.|
|[CGdiObject::CreateStockObject](#createstockobject)|Načte popisovač pro jednu z předdefinovaných uložených per, štětců nebo písem pro Windows.|
|[CGdiObject::DeleteObject](#deleteobject)|Odstraní objekt Windows GDI připojený k `CGdiObject` objektu z paměti uvolněním veškerého systémového úložiště přidruženého k objektu.|
|[CGdiObject::DeleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CGdiObject` objekty, které `FromHandle`vytvořil.|
|[CGdiObject::Detach](#detach)|Odpojí objekt Windows GDI od `CGdiObject` objektu a vrátí popisovač objektu Windows GDI.|
|[CGdiObject::FromHandle](#fromhandle)|Vrátí ukazatel na `CGdiObject` objekt s daným popisovačem na objekt GDI systému Windows.|
|[CGdiObject:: GetObject](#getobject)|Vyplní vyrovnávací paměť daty, která popisují objekt Windows GDI připojený k `CGdiObject` objektu.|
|[CGdiObject::GetObjectType](#getobjecttype)|Načte typ objektu GDI.|
|[CGdiObject::GetSafeHandle](#getsafehandle)|Vrátí `m_hObject` hodnotu, pokud **Tato** hodnota není null. v takovém případě je vrácena hodnota null.|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Obnoví počátek štětce nebo obnoví logickou paletu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CGdiObject:: operator! =](#operator_neq)|Určuje, zda jsou dva objekty GDI logicky nerovné.|
|[CGdiObject:: operator = = – operátor](#operator_eq_eq)|Určuje, zda jsou dva objekty GDI logicky stejné.|
|[CGdiObject:: operator HGDIOBJ](#operator_hgdiobj)|Načte popisovač k připojenému objektu Windows GDI.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|POPISOVAČ obsahující HBITMAP, HPALETTE, HRGN, HBRUSH, HPEN nebo HFONT připojený k tomuto objektu.|

## <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CGdiObject` přímo. Místo toho vytvoříte objekt z jedné z jeho odvozených tříd, například `CPen` nebo. `CBrush`

Další informace o `CGdiObject`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="attach"></a>CGdiObject:: Attach

Připojí objekt GDI systému Windows k `CGdiObject` objektu.

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
POPISOVAČ objektu GDI systému Windows (například HPEN nebo HBRUSH).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je příloha úspěšná; v opačném případě 0.

##  <a name="cgdiobject"></a>CGdiObject::CGdiObject

`CGdiObject` Vytvoří objekt.

```
CGdiObject();
```

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CGdiObject` přímo. Místo toho vytvoříte objekt z jedné z jeho odvozených tříd, například `CPen` nebo. `Cbrush`

##  <a name="createstockobject"></a>CGdiObject::CreateStockObject

Načte popisovač jednoho z předdefinovaných uložených per Windows GDI, štětců nebo písem a připojí objekt GDI k `CGdiObject` objektu.

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Konstanta určující typ požadovaného objektu zásob. Popis odpovídajících hodnot naleznete v parametru *fnObject* pro [GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce s jednou z odvozených tříd, které odpovídají typu objektu GDI systému Windows, například `CPen` pro burzovní pero.

##  <a name="deleteobject"></a>CGdiObject::D eleteObject

Odstraní připojený objekt Windows GDI z paměti uvolněním veškerého systémového úložiště přidruženého k objektu Windows GDI.

```
BOOL DeleteObject();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se objekt GDI úspěšně odstranil; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Úložiště přidružené `CGdiObject` k objektu není tímto voláním ovlivněno. Aplikace by neměla volat `DeleteObject` `CGdiObject` na objekt, který je aktuálně vybraný v kontextu zařízení.

Při odstranění štětce vzorku se neodstraní rastrový obrázek přidružený ke štětci. Rastrový obrázek musí být odstraněn nezávisle.

##  <a name="deletetempmap"></a>CGdiObject::D eleteTempMap

`CWinApp` Je volána automaticky obslužnou rutinou nečinného `DeleteTempMap` času a odstraní `CGdiObject` všechny dočasné objekty `FromHandle`vytvořené pomocí.

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Poznámky

`DeleteTempMap``CGdiObject` před`CGdiObject` odstraněním objektu odpojí objekt GDI systému Windows připojený k dočasnému objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>CGdiObject::D etach

Odpojí objekt Windows GDI od `CGdiObject` objektu a vrátí popisovač objektu Windows GDI.

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>Návratová hodnota

`HANDLE` Objekt rozhraní Windows GDI je odpojen. v opačném případě hodnota null, pokud není připojen žádný objekt GDI.

##  <a name="fromhandle"></a>CGdiObject::FromHandle

Vrátí ukazatel na `CGdiObject` objekt s daným popisovačem na objekt GDI systému Windows.

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>Parametry

*hObject*<br/>
POPISOVAČ objektu GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CGdiObject` , který může být dočasný nebo trvalý.

### <a name="remarks"></a>Poznámky

Pokud objekt již není připojen k objektu GDI systému Windows, je vytvořen a připojen `CGdiObject` dočasný objekt. `CGdiObject`

Tento dočasný `CGdiObject` objekt je platný pouze do příštího času, kdy aplikace nebude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to vyjádřit, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

##  <a name="getobject"></a>CGdiObject:: GetObject

Vyplní vyrovnávací paměť daty, která definují zadaný objekt.

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Určuje počet bajtů, které mají být zkopírovány do vyrovnávací paměti *lpObject* .

*lpObject*<br/>
Odkazuje na vyrovnávací paměť zadanou uživatelem, která má přijmout informace.

### <a name="return-value"></a>Návratová hodnota

Počet načtených bajtů; jinak 0, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Funkce načte datovou strukturu, jejíž typ závisí na typu grafického objektu, jak je znázorněno v následujícím seznamu:

|Objekt|Typ vyrovnávací paměti|
|------------|-----------------|
|`CPen`|[LOGPEN –](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|Není podporováno|

Pokud objekt je `CBitmap` objekt, `GetObject` vrátí pouze informace o šířce, výšce a formátu barvy rastrového obrázku. Skutečné bity lze načíst pomocí [CBitmap –:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).

Pokud objekt je `CPalette` objekt, `GetObject` načte slovo, které určuje počet položek v paletě. Funkce nenačte strukturu [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) , která definuje paletu. Aplikace může získat informace o položkách palet voláním [CPalette –:: GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).

##  <a name="getobjecttype"></a>CGdiObject:: GetObjectType

Načte typ objektu GDI.

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typ objektu, pokud je úspěšný; v opačném případě 0. Hodnota může být jedna z následujících:

- OBJ_BITMAP rastrový obrázek

- OBJ_BRUSH štětec

- Písmo OBJ_FONT

- OBJ_PAL paleta

- OBJ_PEN pero

- OBJ_EXTPEN rozšířené pero

- Oblast OBJ_REGION

- Kontext zařízení OBJ_DC

- OBJ_MEMDC paměti – kontext zařízení

- OBJ_METAFILE Metafile

- Kontext zařízení OBJ_METADC Metafile

- OBJ_ENHMETAFILE Enhanced Metafile

- OBJ_ENHMETADC – kontext zařízení s rozšířenými metasoubory

##  <a name="getsafehandle"></a>CGdiObject::GetSafeHandle

Vrátí `m_hObject` hodnotu, pokud **Tato** hodnota není null. v takovém případě je vrácena hodnota null.

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

POPISOVAČ připojeného objektu GDI systému Windows; jinak NULL, pokud není připojen žádný objekt.

### <a name="remarks"></a>Poznámky

Toto je součást obecného rozhraní s popisovačem, která je užitečná, pokud je hodnota NULL platnou nebo speciální hodnotou pro popisovač.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

POPISOVAČ obsahující HBITMAP, HRGN, HBRUSH, HPEN, HPALETTE nebo HFONT připojený k tomuto objektu.

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: operator! =

Určuje, zda jsou dva objekty GDI logicky nerovné.

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Ukazatel na existující `CGdiObject`.

### <a name="remarks"></a>Poznámky

Určuje, zda se objekt GDI na levé straně nerovná objektu GDI na pravé straně.

##  <a name="operator_eq_eq"></a>CGdiObject:: operator = = – operátor

Určuje, zda jsou dva objekty GDI logicky stejné.

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Odkaz na existující `CGdiObject`.

### <a name="remarks"></a>Poznámky

Určuje, zda je objekt GDI na levé straně roven objektu GDI na pravé straně.

##  <a name="operator_hgdiobj"></a>CGdiObject:: operator HGDIOBJ

Načte popisovač k připojenému objektu Windows GDI; jinak NULL, pokud není připojen žádný objekt.

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

Obnoví počátek štětce nebo obnoví logickou paletu.

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zatímco `UnrealizeObject` je členskou funkcí `CGdiObject` třídy, měla by být vyvolána pouze pro `CBrush` objekty nebo `CPalette` .

U `CBrush` objektů přesměruje systém, `UnrealizeObject` aby obnovil počátek daného štětce při příštím výběru do kontextu zařízení. Pokud objekt je `CPalette` objekt, přesměruje systém, `UnrealizeObject` aby provedl tuto paletu, protože předtím nebyla dříve realizována. Až aplikace příště zavolá funkci [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) pro zadanou paletu, systém kompletně změní mapování logické palety na paletu systému.

`UnrealizeObject` Funkce by neměla být použita s skladovými objekty. Funkce musí být volána vždy, když je nastaven nový počátek štětce (pomocí funkce [CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) ). `UnrealizeObject` `UnrealizeObject` Funkce nesmí být volána pro aktuálně vybranou štětce nebo aktuálně vybranou paletu libovolného kontextu zobrazení.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBitmap – třída](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush – třída](../../mfc/reference/cbrush-class.md)<br/>
[CFont – třída](../../mfc/reference/cfont-class.md)<br/>
[CPalette – třída](../../mfc/reference/cpalette-class.md)<br/>
[CPen – třída](../../mfc/reference/cpen-class.md)<br/>
[CRgn – třída](../../mfc/reference/crgn-class.md)
