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
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371647"
---
# <a name="cstatic-class"></a>CStatic – třída

Poskytuje funkce statického ovládacího prvku systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Vytvoří `CStatic` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStatic::Vytvořit](#create)|Vytvoří statický ovládací prvek systému `CStatic` Windows a připojí jej k objektu.|
|[CStatic::DrawItem](#drawitem)|Přepsat nakreslit statický ovládací prvek nakreslený vlastníkem.|
|[CStatic::GetBitmap](#getbitmap)|Načte popisovač rastrového mapu dříve nastaveného pomocí [setBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Načte popisovač obrázku kurzoru dříve nastavené s [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Načte popisovač rozšířeného metasouboru, který byl dříve nastaven pomocí [souboru SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Načte popisovač ikony dříve nastavené pomocí [funkce SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Určuje bitmapu, která má být zobrazena ve statickém ovládacím prvku.|
|[CStatic::SetCursor](#setcursor)|Určuje obraz kurzoru, který se má zobrazit ve statickém ovládacím prvku.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Určuje rozšířený metasoubor, který se má zobrazit ve statickém ovládacím prvku.|
|[CStatic::SetIcon](#seticon)|Určuje ikonu, která má být zobrazena ve statickém ovládacím prvku.|

## <a name="remarks"></a>Poznámky

Statický ovládací prvek zobrazí textový řetězec, rámeček, obdélník, ikonu, kurzor, bitmapu nebo rozšířený metasoubor. Lze jej použít k označení, krabici nebo oddělení jiných ovládacích prvků. Statické řízení obvykle nepřijímá žádný vstup a neposkytuje žádný výstup; může však upozornit nadřazenou položku myši, pokud je vytvořena SS_NOTIFY stylu.

Vytvořte statický ovládací prvek ve dvou krocích. Nejprve zavolejte konstruktor `CStatic` u konstrukce objektu a pak volání [mařivé](#create) funkce Vytvořit člen vytvořte statický ovládací prvek a připojte jej k objektu. `CStatic`

Pokud vytvoříte `CStatic` objekt v dialogovém okně (prostřednictvím prostředku dialogového okna), `CStatic` objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vytvoříte `CStatic` objekt v okně, může být také nutné jej zničit. Objekt `CStatic` vytvořený v zásobníku v okně je automaticky zničen. Pokud vytvoříte `CStatic` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit, když jste hotovi s ním.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic::Vytvořit

Vytvoří statický ovládací prvek systému `CStatic` Windows a připojí jej k objektu.

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
Určuje text, který má být v ovládacím prvku umístit. Pokud null, žádný text bude viditelný.

*dwStyl*<br/>
Určuje styl okna statického ovládacího prvku. Aplikujte na ovládací prvek libovolnou kombinaci [stylů statického ovládacího](../../mfc/reference/styles-used-by-mfc.md#static-styles) prvku.

*Rect*<br/>
Určuje umístění a velikost statického ovládacího prvku. Může to být `RECT` buď `CRect` struktura nebo objekt.

*pParentWnd*<br/>
Určuje nadřazené `CStatic` `CDialog` okno, obvykle objekt. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku statického ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Vytvořte `CStatic` objekt ve dvou krocích. Nejprve zavolejte `CStatic`konstruktor a `Create`potom volání , který vytvoří statický `CStatic` ovládací prvek systému Windows a připojí jej k objektu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na statický ovládací prvek:

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

Pokud se chystáte zobrazit rastrový obrázek, kurzor, ikonu nebo metasoubor ve statickém ovládacím prvku, budete muset použít jeden z následujících [statických stylů](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP Tento styl použijte pro bitmapy.

- SS_ICON Tento styl použijte pro kurzory a ikony.

- SS_ENHMETAFILE Tento styl použijte pro rozšířené metasoubory.

Pro kurzory, rastrové obrázky nebo ikony můžete také použít následující styl:

- SS_CENTERIMAGE Slouží k vystředění obrazu ve statickém ovládacím prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic

Vytvoří `CStatic` objekt.

```
CStatic();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem

Volat rámci k nakreslení statického ovládacího prvku nakreslené vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) Struktura obsahuje informace o položce, která má být vykreslena, a o typu požadovaného výkresu.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci implementovat výkres pro `CStatic` objekt nakreslený vlastníkem (ovládací prvek má styl SS_OWNERDRAW).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

Získá popisovač bitmapy, dříve nastavené s [SetBitmap](#setbitmap), který je přidružen . `CStatic`

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač aktuální bitmapy nebo NULL, pokud nebyla nastavena žádná bitmapa.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

Získá popisovač kurzoru, dříve nastavena s `CStatic` [SetCursor](#setcursor), který je přidružen .

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač aktuální kurzor nebo NULL, pokud nebyl nastaven žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Získá popisovač rozšířené metasouboru, dříve nastavena s [SetEnhMetafile](#setenhmetafile), který je spojen s `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač aktuálního rozšířeného metasouboru nebo NULL, pokud nebyl nastaven žádný rozšířený metasoubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon

Získá popisovač ikony, dříve nastavena s [SetIcon](#seticon), který je přidružen . `CStatic`

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač aktuální ikony nebo NULL, pokud nebyla nastavena žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

Přidruží novou bitmapu ke statickému ovládacímu prvku.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrového souboru, který má být nakreslen ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového mapu, který byl dříve přidružen ke statickému ovládacímu prvku, nebo NULL, pokud nebyla ke statickému ovládacímu prvku přidružena žádná bitmapa.

### <a name="remarks"></a>Poznámky

Bitmapa bude automaticky nakreslena ve statickém ovládacím prvku. Ve výchozím nastavení bude vykreslen v levém horním rohu a statické ovládací prvek bude změnit velikost na velikost bitmapy.

Můžete použít různé styly oken a statických ovládacích prvků, včetně těchto:

- SS_BITMAP Tento styl používejte vždy pro bitmapy.

- SS_CENTERIMAGE Slouží k vystředění obrazu ve statickém ovládacím prvku. Pokud je obraz větší než statický ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, prázdné místo kolem obrazu bude vyplněno barvou obrazového bodu v levém horním rohu bitmapy.

- Knihovna MFC `CBitmap`poskytuje třídu , kterou můžete použít, když musíte udělat více s `LoadBitmap`bitmapovým obrazem než jen volat funkci Win32 . `CBitmap`, který obsahuje jeden druh objektu GDI, `CStatic`se často `CWnd` používá ve spolupráci s , což je třída, která se používá pro zobrazení grafického objektu jako statického ovládacího prvku.

`CImage`je třída KNIHOVNY ATL/MFC, která umožňuje snadněji pracovat s bitmapami nezávislými na zařízení (DIB). Další informace naleznete v tématu [CImage Class](../../atl-mfc-shared/reference/cimage-class.md).

- Typické použití je `CStatic::SetBitmap` poskytnout Objekt GDI, který je vrácen `CBitmap` operátorem HBITMAP nebo `CImage` objektu. Kód k tomu se podobá následující řádek.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

Následující příklad vytvoří `CStatic` dva objekty na haldě. To pak načte jeden s `CBitmap::LoadOEMBitmap` systémem bitmapy pomocí `CImage::Load`a druhý ze souboru pomocí .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

Přidruží nový obrázek kurzoru ke statickému ovládacímu prvku.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hKurzor*<br/>
Popisovač kurzoru, který má být nakreslen ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru dříve spojené se statickým ovládacím prvkem nebo NULL, pokud žádný kurzor byl přidružen ke statickému ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Kurzor bude automaticky nakreslen ve statickém ovládacím prvku. Ve výchozím nastavení bude nakreslena v levém horním rohu a statické ovládací prvek bude změnit velikost na velikost kurzoru.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ICON Tento styl používejte vždy pro kurzory a ikony.

- SS_CENTERIMAGE Slouží k vystředění statického ovládacího prvku. Pokud je obraz větší než statický ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Přidruží nový rozšířený obraz metasouboru ke statickému ovládacímu prvku.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parametry

*hMetaSoubor*<br/>
Popisovač rozšířenémetasouboru, které mají být vypracovány ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač rozšířenémetasouboru dříve spojené se statickým ovládacím prvkem nebo NULL, pokud žádný rozšířený metasoubor byl přidružen ke statickému ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Rozšířený metasoubor bude automaticky nakreslen ve statickém ovládacím prvku. Rozšířené metasoubor uvažuje tak, aby odpovídalvelikosti statického ovládacího prvku.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ENHMETAFILE Tento styl používejte vždy pro rozšířené metasoubory.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

Přidruží nový obrázek ikony ke statickému ovládacímu prvku.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIkona*<br/>
Popisovač ikony, která má být nakreslena ve statickém ovládacím prvku.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony dříve přidružené ke statickému ovládacímu prvku nebo NULL, pokud žádná ikona byla přidružena ke statickému ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Ikona bude automaticky nakreslena ve statickém ovládacím prvku. Ve výchozím nastavení bude vykreslen v levém horním rohu a statický ovládací prvek bude měnit velikost na velikost ikony.

Můžete použít různé styly oken a statických ovládacích prvků, včetně následujících:

- SS_ICON Tento styl používejte vždy pro kurzory a ikony.

- SS_CENTERIMAGE Slouží k vystředění statického ovládacího prvku. Pokud je obraz větší než statický ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, prázdné místo kolem obrázku bude vyplněno barvou pozadí statického ovládacího prvku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
