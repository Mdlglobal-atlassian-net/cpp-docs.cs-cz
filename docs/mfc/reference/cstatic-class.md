---
title: CStatic – třída
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: fc0164b2d0046ca2d36291696dd6137a9fcef069
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447427"
---
# <a name="cstatic-class"></a>CStatic – třída

Poskytuje funkce pro statický ovládací prvek systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Vytvoří objekt `CStatic`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStatic:: Create](#create)|Vytvoří statický ovládací prvek Windows a připojí ho k objektu `CStatic`.|
|[CStatic::D rawItem](#drawitem)|Přepište pro vykreslení statického ovládacího prvku vykresleného vlastníkem.|
|[CStatic:: getbitmapa](#getbitmap)|Načte popisovač rastrového obrázku dříve nastaveného pomocí [SetBitmap](#setbitmap).|
|[CStatic:: GetCursor](#getcursor)|Načte popisovač obrázku kurzoru, který jste dříve nastavili pomocí [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Načte popisovač Enhanced Metafile, který jste dříve nastavili pomocí [SetEnhMetaFile](#setenhmetafile).|
|[CStatic:: GetIcon](#geticon)|Načte popisovač ikony dříve nastaveného pomocí [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Určuje rastrový obrázek, který se má zobrazit ve statickém ovládacím prvku.|
|[CStatic::SetCursor](#setcursor)|Určuje obrázek kurzoru, který se má zobrazit ve statickém ovládacím prvku.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Určuje rozšířený metasoubor, který se má zobrazit ve statickém ovládacím prvku.|
|[CStatic::SetIcon](#seticon)|Určuje ikonu, která se má zobrazit ve statickém ovládacím prvku.|

## <a name="remarks"></a>Poznámky

Statický ovládací prvek zobrazuje textový řetězec, rámeček, rámeček, ikonu, kurzor, rastrový obrázek nebo rozšířený metasoubor. Dá se použít k označení, krabici nebo oddělení jiných ovládacích prvků. Statické řízení obvykle neprovádí žádné vstupy a neposkytuje žádný výstup. může však upozorňovat své nadřazené tlačítko myši, pokud je vytvořeno pomocí SS_NOTIFY stylu.

Vytvořte statický ovládací prvek ve dvou krocích. Nejdřív zavolejte konstruktor pro vytvoření objektu `CStatic` a potom zavolejte funkci [Create](#create) member a vytvořte statický ovládací prvek a připojte ho k objektu `CStatic`.

Vytvoříte-li objekt `CStatic` v dialogovém okně (prostřednictvím prostředku dialogového okna), je objekt `CStatic` automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte objekt `CStatic` v rámci okna, může být také nutné jej zničit. Objekt `CStatic` vytvořený v zásobníku v rámci okna je automaticky zničen. Vytvoříte-li objekt `CStatic` na haldě pomocí **nové** funkce, je nutné volat příkaz DELETE u objektu, aby jej bylo možné **Odstranit** , když s ním budete hotovi.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="create"></a>CStatic:: Create

Vytvoří statický ovládací prvek Windows a připojí ho k objektu `CStatic`.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Určuje text, který se má umístit do ovládacího prvku. Pokud má hodnotu NULL, žádný text nebude viditelný.

*dwStyle*<br/>
Určuje styl okna statického ovládacího prvku. Použití libovolné kombinace [stylů statického ovládacího prvku](../../mfc/reference/styles-used-by-mfc.md#static-styles) pro ovládací prvek.

*OBD*<br/>
Určuje umístění a velikost statického ovládacího prvku. Může to být buď struktura `RECT`, nebo objekt `CRect`.

*pParentWnd*<br/>
Určuje `CStatic` nadřazené okno, obvykle objekt `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku statického ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vytvořte objekt `CStatic` ve dvou krocích. Nejdřív zavolejte konstruktor `CStatic`a potom zavolejte `Create`, která vytvoří statický ovládací prvek Windows a připojí ho k objektu `CStatic`.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro statický ovládací prvek:

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED zřídka

Pokud se chystáte zobrazit rastrový obrázek, kurzor, ikonu nebo metasoubor ve statickém ovládacím prvku, je nutné použít jeden z následujících [statických stylů](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP použít tento styl pro rastrové obrázky.

- SS_ICON použít tento styl pro kurzory a ikony.

- SS_ENHMETAFILE tento styl použít pro rozšířené metasoubory.

U kurzorů, rastrových obrázků nebo ikon můžete také použít následující styl:

- SS_CENTERIMAGE použít k centrování obrázku ve statickém ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

Vytvoří objekt `CStatic`.

```
CStatic();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic::D rawItem

Volá se rozhraním, aby se nakreslil statický ovládací prvek vykreslený vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . Struktura obsahuje informace o položce, která se má vykreslit, a o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci pro implementaci vykreslování pro objekt `CStatic` nakreslený vlastníkem (ovládací prvek má SS_OWNERDRAW stylu).

##  <a name="getbitmap"></a>CStatic:: getbitmapa

Získá popisovač rastrového obrázku dříve nastaveného pomocí [SetBitmap](#setbitmap), který je spojen s `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální rastrový obrázek nebo hodnotu NULL, pokud není nastaven rastrový obrázek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic:: GetCursor

Získá popisovač kurzoru, který byl dříve nastaven pomocí [SetCursor](#setcursor), který je spojen s `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální kurzor nebo hodnotu NULL, pokud není nastaven žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Získá popisovač Enhanced Metafile, který se dřív nastavil pomocí [SetEnhMetafile](#setenhmetafile), který je spojený s `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač k aktuálnímu rozšířenému metasouboru nebo hodnotu NULL, pokud není nastaven žádný rozšířený metasoubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic:: GetIcon

Získá popisovač ikony, která byla dříve nastavena pomocí [SetIcon](#seticon), která je spojena s `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální ikonu nebo hodnotu NULL, pokud nebyla nastavena žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>CStatic::SetBitmap

Přidruží nový rastr k statickému ovládacímu prvku.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrového obrázku, který má být vykreslen ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového obrázku, který byl dříve přidružen ke statickému ovládacímu prvku, nebo hodnotu NULL, pokud nebyl k statickému ovládacímu prvku přidružen rastrový obrázek.

### <a name="remarks"></a>Poznámky

Bitmapa se automaticky vykreslí ve statickém ovládacím prvku. Ve výchozím nastavení se vykreslí v levém horním rohu a statický ovládací prvek se změní na velikost rastrového obrázku.

Můžete použít různé styly oken a statických ovládacích prvků, včetně těchto:

- SS_BITMAP tento styl použít vždy pro rastrové obrázky.

- SS_CENTERIMAGE použít k centrování obrázku ve statickém ovládacím prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pixelu v levém horním rohu rastrového obrázku.

- Knihovna MFC poskytuje třídu `CBitmap`, kterou můžete použít, pokud potřebujete více s rastrovým obrázkem, než stačí volat `LoadBitmap`funkce Win32. `CBitmap`, která obsahuje jeden druh objektu GDI, se často používá ve spolupráci s `CStatic`, což je třída `CWnd`, která se používá pro zobrazení grafického objektu jako statického ovládacího prvku.

`CImage` je třída ATL/MFC, která umožňuje snadnější práci s rastrami nezávislými na zařízení (DIB). Další informace naleznete v tématu [Třída služby CImage ve](../../atl-mfc-shared/reference/cimage-class.md).

- Typickým použitím je poskytnout `CStatic::SetBitmap` objekt GDI, který je vrácen operátorem HBITMAP objektu `CBitmap` nebo `CImage`. Tento kód se bude podobat následujícímu řádku.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

Následující příklad vytvoří dva objekty `CStatic` v haldě. Poté načte jednu se systémovou bitovou mapou pomocí `CBitmap::LoadOEMBitmap` a druhou ze souboru pomocí `CImage::Load`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>CStatic::SetCursor

Přidružuje nový obrázek kurzoru ke statickému ovládacímu prvku.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Popisovač kurzoru, který má být vykreslen ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru dříve přidružený ke statickému ovládacímu prvku nebo hodnotu NULL, pokud nebyl k statickému ovládacímu prvku přidružen žádný kurzor.

### <a name="remarks"></a>Poznámky

Kurzor se automaticky vykreslí ve statickém ovládacím prvku. Ve výchozím nastavení se vykreslí v levém horním rohu a statický ovládací prvek se změní na velikost kurzoru.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ICON tento styl použít vždycky pro kurzory a ikony.

- SS_CENTERIMAGE použít k centrování v rámci statického ovládacího prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Přidruží nové rozšířené obrázky metasouboru ke statickému ovládacímu prvku.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaFile*<br/>
Popisovač Enhanced Metafile, který se má vykreslit ve statickém ovládacím prvku

### <a name="return-value"></a>Návratová hodnota

Popisovač rozšířeného metasouboru dříve přidružený ke statickému ovládacímu prvku nebo hodnotu NULL, pokud nebyl k statickému ovládacímu prvku přidružen žádný rozšířený metasoubor.

### <a name="remarks"></a>Poznámky

Enhanced Metafile se automaticky vykreslí ve statickém ovládacím prvku. Velikost rozšířeného metasouboru se škáluje tak, aby odpovídala velikosti statického ovládacího prvku.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ENHMETAFILE tento styl použít vždy pro rozšířené metasoubory.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic::SetIcon

Přidruží nový obrázek ikony ke statickému ovládacímu prvku.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Popisovač ikony, která má být vykreslena ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Obslužná rutina ikony dříve přidružená ke statickému ovládacímu prvku nebo NULL, pokud k statickému ovládacímu prvku nebyla přidružena žádná ikona.

### <a name="remarks"></a>Poznámky

Ikona se automaticky vykreslí ve statickém ovládacím prvku. Ve výchozím nastavení se vykreslí v levém horním rohu a statický ovládací prvek se změní na velikost ikony.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ICON tento styl použít vždycky pro kurzory a ikony.

- SS_CENTERIMAGE použít k centrování v rámci statického ovládacího prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
