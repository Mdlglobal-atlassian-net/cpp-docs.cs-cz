---
title: Cstatic – třída
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
ms.openlocfilehash: 02e2f20cc568e8846923f7189da3ea45478fc289
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284434"
---
# <a name="cstatic-class"></a>Cstatic – třída

Poskytuje funkce pro statický ovládací prvek Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Vytvoří `CStatic` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStatic::Create](#create)|Statický ovládací prvek Windows vytvoří a připojí ho k `CStatic` objektu.|
|[CStatic::DrawItem](#drawitem)|Přepsání nastavení za účelem vykreslení statický ovládací prvek vykreslovaných vlastníkem.|
|[CStatic::GetBitmap](#getbitmap)|Načte popisovač rastrového obrázku dříve nastaven s [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Načte popisovač obrázek kurzoru dříve nastaven s [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Načte popisovač EMF dříve nastaven s [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Načte popisovač ikony dříve nastaven s [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Určuje rastrového obrázku zobrazeného v statický ovládací prvek.|
|[CStatic::SetCursor](#setcursor)|Určuje obrázek kurzoru zobrazeného v statický ovládací prvek.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Určuje rozšířený metasoubor zobrazeného v statický ovládací prvek.|
|[CStatic::SetIcon](#seticon)|Určuje ikonu, který se má zobrazit v ovládacím prvku statické.|

## <a name="remarks"></a>Poznámky

Statický ovládací prvek zobrazí textový řetězec, pole, obdélník, ikony, kurzor, rastrový obrázek nebo rozšířený metasoubor. Slouží k popisku, pole nebo oddělení další ovládací prvky. Statický ovládací prvek obvykle nemá žádný vstup a poskytuje žádný výstup; Pokud je vytvořen s SS_NOTIFY styl, je však oznámení svému nadřazenému objektu kliknutí myší.

Vytvořte statický ovládací prvek ve dvou krocích. Nejprve volat konstruktor k vytvoření `CStatic` objekt a potom voláním [vytvořit](#create) členská funkce, které chcete vytvořit statický ovládací prvek a připojit ho k `CStatic` objektu.

Pokud vytvoříte `CStatic` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CStatic` objekt je zničen automaticky, když uživatel zavře dialogové okno.

Pokud jste vytvořili `CStatic` objektů v okně a také je nutné ji odstranit. A `CStatic` objekt vytvořený v zásobníku v rámci časového období se automaticky odstraní. Pokud jste vytvořili `CStatic` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete zničit ho, až budete hotovi s ním.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="create"></a>  CStatic::Create

Statický ovládací prvek Windows vytvoří a připojí ho k `CStatic` objektu.

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
Určuje text, který umístěte do ovládacího prvku. Pokud má hodnotu NULL, se nebude zobrazovat žádný text.

*dwStyle*<br/>
Určuje styl okna statický ovládací prvek. Použít libovolnou kombinaci [statický ovládací prvek styly](../../mfc/reference/styles-used-by-mfc.md#static-styles) do ovládacího prvku.

*Rect*<br/>
Určuje umístění a velikost statickému ovládacímu prvku. Může se jednat buď `RECT` struktury nebo `CRect` objektu.

*pParentWnd*<br/>
Určuje, `CStatic` nadřazené okno, obvykle `CDialog` objektu. Nesmí být NULL.

*nID*<br/>
Určuje ID statický ovládací prvek ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Vytvoření `CStatic` objektu ve dvou krocích. Nejprve volat konstruktor `CStatic`a pak vyvolejte `Create`, vytvoří statický ovládací prvek Windows a připojí ho k `CStatic` objektu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na statický ovládací prvek:

- WS_CHILD vždy

- WS_VISIBLE obvykle

- WS_DISABLED jen zřídka

Pokud se chystáte zobrazí rastrový obrázek, kurzor, ikona nebo metasoubor v statický ovládací prvek, musíte použít jednu z následujících [statické styly](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP použít tento styl pro rastrových obrázků.

- SS_ICON použít tento styl pro ikony a kurzory.

- SS_ENHMETAFILE použít tento styl pro EMF.

Pro ukazatele, rastrové obrázky a ikony může být také vhodné použít následující styl:

- SS_CENTERIMAGE použití na střed bitové kopie v statický ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>  CStatic::CStatic

Vytvoří `CStatic` objektu.

```
CStatic();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>  CStatic::DrawItem

Volá se rozhraním, chcete-li nakreslit statický ovládací prvek vykreslovaných vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) struktury. Struktura obsahuje informace o položka, která má být vykreslena a typ kresby vyžaduje.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, která implementuje výkresu vykreslovaných vlastníkem `CStatic` objektu (ovládací prvek má styl SS_OWNERDRAW).

##  <a name="getbitmap"></a>  CStatic::GetBitmap

Získá popisovač rastrový obrázek, dříve nastaven s [SetBitmap](#setbitmap), který je přidružený k `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální rastrový obrázek nebo hodnota NULL, pokud byla nastavena žádná rastrového obrázku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

Získá popisovač kurzor dříve nastaven s [SetCursor](#setcursor), který je přidružený k `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální kurzor, nebo hodnota NULL, pokud byl nastaven žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

Získá popisovač EMF dříve nastaven s [SetEnhMetafile](#setenhmetafile), který je přidružený k `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální EMF nebo hodnota NULL, pokud byla nastavena žádná EMF.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

Získá popisovač ikony dříve nastaven s [SetIcon](#seticon), který je přidružený k `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro aktuální ikony nebo hodnota NULL, pokud byla nastavena žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

Přidruží nový rastrový obrázek statický ovládací prvek.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrový obrázek pro vykreslen na statický ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Obslužná rutina, která byla dříve přidružená statický ovládací prvek, nebo hodnota NULL, pokud žádné rastrového obrázku byl přidružen statický ovládací prvek rastrového obrázku.

### <a name="remarks"></a>Poznámky

Rastrový obrázek bude automaticky vykreslen na statický ovládací prvek. Ve výchozím nastavení bude nutné vykreslit v levém horním rohu a statickému ovládacímu prvku se změněnou velikostí velikost rastrového obrázku.

Můžete použít různé okna a styly statický ovládací prvek, včetně těchto:

- Tento styl SS_BITMAP vždy použít pro rastrových obrázků.

- SS_CENTERIMAGE použití na střed bitové kopie v statický ovládací prvek. Na obrázku je větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku sestavil barva pixel v levém horním rohu rastrového obrázku.

- Knihovna MFC poskytuje třídu `CBitmap`, který můžete použít v případě, že máte více s rastrový obrázek než stačí zavolat rozhraní Win32 funkce `LoadBitmap`. `CBitmap`, která obsahuje jednoho druhu objektu GDI se často používá ve spolupráci s `CStatic`, což je `CWnd` třídu, která slouží k zobrazení grafického objektu jako statický ovládací prvek.

`CImage` je třída ATL/MFC, která umožňuje jednoduchá práci s bitmap nezávislých zařízení (DIB). Další informace najdete v tématu [cimage – třída](../../atl-mfc-shared/reference/cimage-class.md).

- Typické použití je umožnit `CStatic::SetBitmap` GDI objektu, který je vrácen provozovatelem HBITMAP `CBitmap` nebo `CImage` objektu. Kód k tomu se podobá následující řádek.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
Následující příklad vytvoří dva `CStatic` objektů na haldě. Potom načte jeden pomocí bitmapu systém `CBitmap::LoadOEMBitmap` a další ze souboru pomocí `CImage::Load`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

Přidruží nový obrázek kurzoru statický ovládací prvek.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Popisovač kurzoru vykreslen na statický ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzor bylo dřív přidružené statický ovládací prvek nebo hodnota NULL, pokud byl statický ovládací prvek přidružen žádný kurzor.

### <a name="remarks"></a>Poznámky

Kurzor se automaticky vykreslen na statický ovládací prvek. Ve výchozím nastavení bude nutné vykreslit v levém horním rohu a statický ovládací prvek bude změněna na velikost kurzoru.

Můžete použít různé okna a styly statický ovládací prvek, včetně následujících:

- Tento styl SS_ICON vždy použít pro ikony a kurzory.

- SS_CENTERIMAGE použití na střed v statický ovládací prvek. Na obrázku je větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statickému ovládacímu prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

Přiřadí novou bitovou kopii EMF statický ovládací prvek.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaFile*<br/>
Popisovač rozšířený metasoubor pro vykreslen na statický ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Popisovač EMF bylo dřív přidružené statický ovládací prvek nebo hodnota NULL, pokud žádné EMF byl přidružen statický ovládací prvek.

### <a name="remarks"></a>Poznámky

Rozšířený metasoubor bude automaticky vykreslen na statický ovládací prvek. Rozšířený metasoubor je škálovat pro přizpůsobení statickému ovládacímu prvku.

Můžete použít různé okna a styly statický ovládací prvek, včetně následujících:

- SS_ENHMETAFILE používat tento styl vždy pro rozšířené metasoubory.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

Přidruží nový obrázek ikony statický ovládací prvek.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Popisovač ikony vykreslen na statický ovládací prvek.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony dříve přidružené statický ovládací prvek nebo hodnota NULL, pokud žádná ikona byl přidružen statický ovládací prvek.

### <a name="remarks"></a>Poznámky

Ikona bude automaticky vykreslen na statický ovládací prvek. Ve výchozím nastavení bude nutné vykreslit v levém horním rohu a statický ovládací prvek bude změněna na velikost ikony.

Můžete použít různé okna a styly statický ovládací prvek, včetně následujících:

- Tento styl SS_ICON vždy použít pro ikony a kurzory.

- SS_CENTERIMAGE použití na střed v statický ovládací prvek. Na obrázku je větší než statický ovládací prvek, bude oříznut. Pokud je menší než statický ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statickému ovládacímu prvku.

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
