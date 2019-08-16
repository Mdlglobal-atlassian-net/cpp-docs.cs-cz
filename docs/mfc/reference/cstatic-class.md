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
ms.openlocfilehash: fd7b6787b372e220a32770e19d54d149f5ba6934
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502418"
---
# <a name="cstatic-class"></a>CStatic – třída

Poskytuje funkce pro statický ovládací prvek systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|`CStatic` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CStatic:: Create](#create)|Vytvoří statický ovládací prvek Windows a připojí ho k `CStatic` objektu.|
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

Statický ovládací prvek zobrazuje textový řetězec, rámeček, rámeček, ikonu, kurzor, rastrový obrázek nebo rozšířený metasoubor. Dá se použít k označení, krabici nebo oddělení jiných ovládacích prvků. Statické řízení obvykle neprovádí žádné vstupy a neposkytuje žádný výstup. může však upozorňovat své nadřazené tlačítko myši, pokud je vytvořeno pomocí stylu SS_NOTIFY.

Vytvořte statický ovládací prvek ve dvou krocích. Nejdřív zavolejte konstruktor pro `CStatic` vytvoření objektu a potom zavolejte funkci [Create](#create) member a vytvořte statický ovládací prvek a `CStatic` připojte ho k objektu.

Pokud vytvoříte `CStatic` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna) `CStatic` , objekt je automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CStatic` objekt v rámci okna, může být také nutné jej zničit. `CStatic` Objekt vytvořený v zásobníku v rámci okna je automaticky zničen. Vytvoříte `CStatic` -li objekt na haldě pomocí **nové** funkce, je nutné volat metodu DELETE u objektu, aby jej bylo možné **Odstranit** , když s ním budete hotovi.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="create"></a>CStatic:: Create

Vytvoří statický ovládací prvek Windows a připojí ho k `CStatic` objektu.

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
Určuje umístění a velikost statického ovládacího prvku. Může se jednat o `RECT` strukturu `CRect` nebo objekt.

*pParentWnd*<br/>
Určuje nadřazené okno, `CDialog` obvykle objekt. `CStatic` Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku statického ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CStatic` Vytvořte objekt ve dvou krocích. Nejprve volejte konstruktor `CStatic`a potom zavolejte `Create`, čímž se vytvoří statický ovládací prvek Windows a `CStatic` připojí se k objektu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro statický ovládací prvek:

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED málokdy

Pokud se chystáte zobrazit rastrový obrázek, kurzor, ikonu nebo metasoubor ve statickém ovládacím prvku, je nutné použít jeden z následujících [statických stylů](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP tento styl použijte pro rastrové obrázky.

- SS_ICON tento styl slouží pro kurzory a ikony.

- SS_ENHMETAFILE tento styl použijte pro rozšířené metasoubory.

U kurzorů, rastrových obrázků nebo ikon můžete také použít následující styl:

- SS_CENTERIMAGE použijte k centrování obrázku ve statickém ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

`CStatic` Vytvoří objekt.

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

Přepište tuto funkci pro implementaci vykreslování pro objekt nakreslený `CStatic` vlastníkem (ovládací prvek má styl SS_OWNERDRAW).

##  <a name="getbitmap"></a>CStatic:: getbitmapa

Získá popisovač rastrového obrázku, který byl dříve nastaven pomocí [SetBitmap](#setbitmap), který je spojen `CStatic`s.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální rastrový obrázek nebo hodnotu NULL, pokud není nastaven rastrový obrázek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic:: GetCursor

Získá popisovač kurzoru, který byl dříve nastaven s [SetCursor](#setcursor), který je spojen s `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální kurzor nebo hodnotu NULL, pokud není nastaven žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Získá popisovač Enhanced Metafile, který byl dříve nastaven pomocí [SetEnhMetafile](#setenhmetafile), který je spojen s `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač k aktuálnímu rozšířenému metasouboru nebo hodnotu NULL, pokud není nastaven žádný rozšířený metasoubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic:: GetIcon

Získá popisovač ikony, která byla dříve nastavena pomocí [SetIcon](#seticon), která je přidružena `CStatic`k.

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

- SS_BITMAP tento styl používejte vždy pro rastrové obrázky.

- SS_CENTERIMAGE použijte k centrování obrázku ve statickém ovládacím prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pixelu v levém horním rohu rastrového obrázku.

- Knihovna MFC poskytuje třídu `CBitmap`, kterou lze použít v případě, že je nutné provést více s rastrovým obrázkem, než stačí volat `LoadBitmap`funkci Win32. `CBitmap`, který obsahuje jeden druh objektu GDI, se často používá ve spolupráci s `CStatic`, což `CWnd` je třída, která se používá pro zobrazení grafického objektu jako statického ovládacího prvku.

`CImage`je třída ATL/MFC, která umožňuje snadnější práci s rastrami nezávislými na zařízení (DIB). Další informace naleznete v tématu [Třída služby CImage ve](../../atl-mfc-shared/reference/cimage-class.md).

- Typickým použitím je poskytnout `CStatic::SetBitmap` objekt GDI, který je vrácen operátorem `CBitmap` HBITMAP objektu nebo `CImage` . Tento kód se bude podobat následujícímu řádku.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
Následující příklad vytvoří dva `CStatic` objekty v haldě. Pak ho načte pomocí systémového rastrového obrázku `CBitmap::LoadOEMBitmap` a druhý ze souboru pomocí. `CImage::Load`

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

- SS_ICON tento styl použijte vždycky pro kurzory a ikony.

- SS_CENTERIMAGE použijte k centrování statického ovládacího prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

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

- SS_ENHMETAFILE tento styl používejte vždy pro rozšířené metasoubory.

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

- SS_ICON tento styl použijte vždycky pro kurzory a ikony.

- SS_CENTERIMAGE použijte k centrování statického ovládacího prvku. Je-li obrázek větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
