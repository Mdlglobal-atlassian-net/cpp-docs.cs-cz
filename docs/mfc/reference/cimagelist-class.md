---
title: CImageList – třída
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 17cd2a94cb397e59e4622aea8ed7bb6fbe1eee43
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752695"
---
# <a name="cimagelist-class"></a>CImageList – třída

Poskytuje funkce ovládacího prvku seznamu společných bitových obrázků systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CImageList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Vytvoří `CImageList` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CImageList::Přidat](#add)|Přidá obrázek nebo obrázky do seznamu obrázků.|
|[CImageList::Připojit](#attach)|Připojí k objektu `CImageList` seznam obrázků.|
|[CImageList::BeginDrag](#begindrag)|Začne přetahovat obraz.|
|[CImageList::Kopírovat](#copy)|Zkopíruje obraz `CImageList` uvnitř objektu.|
|[CImageList::Vytvořit](#create)|Inicializuje seznam obrázků a připojí `CImageList` jej k objektu.|
|[CImageList::DeleteImageList](#deleteimagelist)|Odstraní seznam obrázků.|
|[CImageList::DeleteTempMap](#deletetempmap)|Volána [cwinapp](../../mfc/reference/cwinapp-class.md) nečinnosti rutiny odstranit `CImageList` všechny `FromHandle`dočasné objekt vytvořený .|
|[CImageList::Detach](#detach)|Odpojí objekt seznamu obrázků `CImageList` od objektu a vrátí úchyt do seznamu obrázků.|
|[CImageList::DragEnter](#dragenter)|Zamkne aktualizace během operace přetažení a zobrazí obraz přetažení v zadané poloze.|
|[CImageList::DragLeave](#dragleave)|Odemkne okno a skryje přetahování obrazu, aby bylo možné okno aktualizovat.|
|[CImageList::DragMove](#dragmove)|Přesune obraz, který je přetahován během operace přetažení myší.|
|[CImageList::DragShowNolock](#dragshownolock)|Zobrazí nebo skryje přetahovací obraz během operace přetažení bez uzamčení okna.|
|[CImageList::Draw](#draw)|Nakreslí obraz, který je přetahován během operace přetažení myší.|
|[CImageList::DrawEx](#drawex)|Nakreslí položku seznamu obrázků v zadaném kontextu zařízení. Funkce používá zadaný styl kreslení a prolne obraz se zadanou barvou.|
|[CImageList::DrawIndirect](#drawindirect)|Nakreslí obrázek ze seznamu obrázků.|
|[CImageList::EndDrag](#enddrag)|Ukončí operaci přetažení.|
|[CImageList::ExtractIcon](#extracticon)|Vytvoří ikonu založenou na obrázku a masce v seznamu obrázků.|
|[CImageList::FromHandle](#fromhandle)|Vrátí ukazatel na `CImageList` objekt, když je k seznamu obrázků přidělen popisovač. Pokud `CImageList` objekt není připojen k popisovač, `CImageList` dočasný objekt je vytvořen a připojen.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Vrátí ukazatel na `CImageList` objekt, když je k seznamu obrázků přidělen popisovač. Pokud `CImageList` objekt není připojen k popisovač, null je vrácena.|
|[CImageList::GetBkColor](#getbkcolor)|Načte aktuální barvu pozadí pro seznam obrázků.|
|[CImageList::GetDragImage](#getdragimage)|Získá dočasný seznam obrázků, který se používá pro přetažení.|
|[CImageList::GetImageCount](#getimagecount)|Načte počet obrázků v seznamu obrázků.|
|[CImageList::GetImageInfo](#getimageinfo)|Načte informace o obrázku.|
|[CImageList::GetSafeHandle](#getsafehandle)|Načte `m_hImageList`.|
|[CImageList::Číst](#read)|Přečte seznam obrázků z archivu.|
|[CImageList::Odebrat](#remove)|Odebere obrázek ze seznamu obrázků.|
|[CImageList::Nahradit](#replace)|Nahradí obrázek v seznamu obrázků novým obrázkem.|
|[CImageList::SetBkColor](#setbkcolor)|Nastaví barvu pozadí pro seznam obrázků.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Vytvoří nový obraz přetažení.|
|[CImageList::SetImageCount](#setimagecount)|Obnoví počet obrázků v seznamu obrázků.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Přidá index obrazu založený na nule do seznamu obrazů, které mají být použity jako masky překrytí.|
|[CImageList::Zápis](#write)|Zapíše seznam obrázků do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CImageList::operátor HIMAGELIST](#operator_himagelist)|Vrátí hodnotu FUNKCE HIMAGELIST připojené k souboru `CImageList`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Úchyt obsahující seznam obrázků připojený k tomuto objektu.|

## <a name="remarks"></a>Poznámky

"Seznam obrázků" je kolekce obrázků stejné velikosti, z nichž každý může být odkazován jeho nula-založené indexu. Seznamy obrázků se používají k efektivní správě velkých sad ikon nebo bitmap. Všechny obrazy v seznamu obrazů jsou obsaženy v jedné široké bitmapě ve formátu obrazovky zařízení. Seznam obrázků může také obsahovat monochromatický rastr, který obsahuje masky používané k průhlednému kreslení obrázků (styl ikony). Microsoft Win32 aplikační programovací rozhraní (API) poskytuje funkce seznamu obrázků, které vám umožní kreslit obrázky, vytvářet a ničit seznamy obrázků, přidávat a odebírat obrázky, nahrazovat obrázky, slučovat obrázky a přetahovat obrázky.

Tento ovládací prvek `CImageList` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Další informace o `CImageList`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList::Přidat

Voláním této funkce přidáte jeden nebo více obrázků nebo ikonu do seznamu obrázků.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*pbmImage*<br/>
Ukazatel na bitmapu obsahující obraz nebo obrazy. Počet obrazů je odvozen z šířky bitmapy.

*pbmMask*<br/>
Ukazatel na bitmapu obsahující masku. Pokud se v seznamu obrázků nepoužívá žádná maska, bude tento parametr ignorován.

*crMask*<br/>
Barva použitá ke generování masky. Každý obrazový bod této barvy v dané bitmapě se změní na černý a odpovídající bit v masce je nastaven na jeden.

*hIkona*<br/>
Úchyt ikony, která obsahuje bitmapu a masku pro nový obraz.

### <a name="return-value"></a>Návratová hodnota

Nulový index prvního nového obrázku, pokud je úspěšný; jinak - 1.

### <a name="remarks"></a>Poznámky

Jste zodpovědní za uvolnění popisovače ikony, když jste hotovi s ním.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList::Připojit

Voláním této funkce připojte k `CImageList` objektu seznam obrázků.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hSeznam obrázků*<br/>
Úchyt k objektu seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla příloha úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag

Voláním této funkce začněte přetahovat obraz.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrazu, který chcete přetáhnout.

*ptHotSpot*<br/>
Souřadnice výchozí polohy přetahování (obvykle pozice kurzoru). Souřadnice jsou relativní vzhledem k levému hornímu rohu obrazu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří dočasný seznam obrázků, který se používá pro přetažení. Obraz kombinuje zadaný obraz a jeho masku s aktuálním kurzorem. V reakci na následné WM_MOUSEMOVE zprávy můžete přesunout `DragMove` přetahovací obraz pomocí členské funkce. Chcete-li ukončit operaci přetažení, můžete použít členovou `EndDrag` funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList

Vytvoří `CImageList` objekt.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList::Kopírovat

Tato členská funkce implementuje chování funkce Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), jak je popsáno v sadě Windows SDK.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>Parametry

*iDst*<br/>
Index obrázku založený na nule, který má být použit jako cíl operace kopírování.

*iSrc*<br/>
Index na základě nuly obrázku, který má být použit jako zdroj operace kopírování.

*uPříznaky*<br/>
Hodnota příznaku bitu, která určuje typ operace kopírování, která má být provedena. Tento parametr může být jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILCF_MOVE|Zdrojový obraz se zkopíruje do indexu cílového obrázku. Výsledkem této operace je více instancí daného obrázku. ILCF_MOVE je výchozí.|
|ILCF_SWAP|Zdrojové a cílové obrázky si vyměňují pozice v seznamu obrázků.|

*pSrc*<br/>
Ukazatel na `CImageList` objekt, který je cílem operace kopírování.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList::Vytvořit

Inicializuje seznam obrázků a připojí jej k objektu [CImageList.](../../mfc/reference/cimagelist-class.md)

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Rozměry každého obrazu v obrazových bodech.

*Cy*<br/>
Rozměry každého obrazu v obrazových bodech.

*nPříznaky*<br/>
Určuje typ seznamu obrázků, který chcete vytvořit. Tento parametr může být kombinací následujících hodnot, ale může `ILC_COLOR` obsahovat pouze jednu z hodnot.

|Hodnota|Význam|
|-----------|-------------|
|ILC_COLOR|Výchozí chování použijte, pokud není zadán žádný z ostatních příznaků ILC_COLOR*. Výchozí hodnota je obvykle ILC_COLOR4; ale u starších ovladačů zobrazení je výchozí nastavení ILC_COLORDDB.|
|ILC_COLOR4|Jako bitmapu pro seznam obrazů použijte čtyřbitový (16barevný) bitmapový oddíl (DIB) nezávislý na zařízení.|
|ILC_COLOR8|Použijte 8bitový oddíl DIB. Barvy použité pro tabulku barev mají stejné barvy jako paleta polotónů.|
|ILC_COLOR16|Použijte 16bitový (32/64k barevný) oddíl DIB.|
|ILC_COLOR24|Použijte 24bitový oddíl DIB.|
|ILC_COLOR32|Použijte 32bitový oddíl DIB.|
|ILC_COLORDDB|Použijte bitmapu závislou na zařízení.|
|ILC_MASK|Používá masku. Seznam obrazů obsahuje dvě rastrové obrázky, z nichž jeden je monochromatický rastrový obrázek používaný jako maska. Pokud tato hodnota není zahrnuta, seznam obrázků obsahuje pouze jednu bitmapu. Další informace o maskovaných obrázcích najdete v [tématu Kreslení obrázků ze seznamu obrázků.](../../mfc/drawing-images-from-an-image-list.md)|

*nPočáteční*<br/>
Počet obrázků, které seznam obrázků zpočátku obsahuje.

*nRůst*<br/>
Počet obrázků, o které může seznam obrázků růst, když systém potřebuje změnit velikost seznamu, aby se uvolnilo místo pro nové obrázky. Tento parametr představuje počet nových obrázků, které může seznam obrázků se velikosti obsahovat.

*nBitmapID*<br/>
ID prostředků bitmapy, která mají být přidružena k seznamu obrázků.

*crMask*<br/>
Barva použitá ke generování masky. Každý obrazový bod této barvy v zadané bitmapě se změní na černý a odpovídající bit v masce je nastaven na jeden.

*lpszBitmapID*<br/>
Řetězec obsahující ID prostředků bitových kopií.

*seznam obrázků1*<br/>
Odkaz na `CImageList` objekt.

*nObrázek1*<br/>
Index první existující bitové kopie.

*seznam obrázků2*<br/>
Odkaz na `CImageList` objekt.

*nObrázek2*<br/>
Index druhého existujícího obrázku.

*Dx*<br/>
Posun osy x druhého obrazu ve vztahu k prvnímu obrazu v obrazových bodech.

*dy*<br/>
Posun osy y druhého obrazu ve vztahu k prvnímu obrazu v obrazových bodech.

*seznam obrázků pImage*<br/>
Ukazatel na `CImageList` objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CImageList` ve dvou krocích. Nejprve zavolejte konstruktora `Create`a potom volání , který vytvoří `CImageList` seznam obrázků a připojí jej k objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

Voláním této funkce odstraníte seznam obrázků.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

Volána automaticky `CWinApp` obslužnou `DeleteTempMap` rutinou `CImageList` nečinnosti, odstraní všechny dočasné objekty `hImageList`vytvořené [FromHandle](#fromhandle), ale nezničí žádné popisovače ( ) dočasně přidružené k objektům. `ImageList`

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::Detach

Voláním této funkce odpojte objekt seznamu `CImageList` obrázků od objektu.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k objektu seznamu obrázků.

### <a name="remarks"></a>Poznámky

Tato funkce vrátí popisovač objektu seznamu obrázků.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter

Během operace přetažení uzamkne aktualizace okna určeného *společností pWndLock* a zobrazí obraz přetažení na pozici určené *bodem*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno, které vlastní přetahovací obraz.

*Bod*<br/>
Pozice, na které chcete zobrazit přetahovací obraz. Souřadnice jsou relativní vzhledem k levému hornímu rohu okna (nikoli k oblasti klienta).

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Souřadnice jsou relativní vzhledem k levému hornímu rohu okna, takže při zadávání souřadnic je nutné kompenzovat šířky prvků okna, jako je ohraničení, záhlaví a řádek nabídek.

Pokud *pWndLock* je NULL, tato funkce nakreslí obraz v kontextu zobrazení spojené s oknem plochy a souřadnice jsou relativní vzhledem k levému hornímu rohu obrazovky.

Tato funkce uzamkne všechny ostatní aktualizace daného okna během operace přetažení. Pokud potřebujete provést jakýkoli výkres během operace přetažení, jako je například zvýraznění cíle operace přetažení, můžete dočasně skrýt přetažený obraz pomocí funkce [CImageList::DragLeave.](#dragleave)

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave

Odemkne okno určené *pWndLock* a skryje obrázek přetažení, což umožňuje okno aktualizovat.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno, které vlastní přetahovací obraz.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::EndDrag](#enddrag).

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove

Volánítéto funkce přesunout obraz, který je přetahován během operace přetažení.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Nová pozice přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána v reakci na WM_MOUSEMOVE zprávu. Chcete-li zahájit operaci `BeginDrag` přetažení, použijte členovou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock

Zobrazí nebo skryje přetahovací obraz během operace přetažení bez uzamčení okna.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bZobrazit*<br/>
Určuje, zda má být přetahován obraz.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Funkce [CImageList::DragEnter](#dragenter) uzamkne všechny aktualizace okna během operace přetažení. Tato funkce však nezamkne okno.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::Draw

Volání této funkce k nakreslení obrazu, který je přetahován během operace přetažení myší.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext cílového zařízení.

*nObrázek*<br/>
Nulový index obrázku k nakreslení.

*Pt*<br/>
Umístění, ve kterém chcete kreslit v rámci zadaného kontextu zařízení.

*nStyl*<br/>
Příznak určující styl výkresu. Může to být jedna nebo více z těchto hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Nakreslí obraz a prolne 25 procent s barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masku.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Nakreslí obraz a prolne 50 procent s barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masku.|
|ILD_MASK|Nakreslí masku.|
|ILD_NORMAL|Nakreslí obraz pomocí barvy pozadí pro seznam obrázků. Pokud je barva pozadí CLR_NONE hodnotou, obraz se nakreslí transparentně pomocí masky.|
|ILD_TRANSPARENT|Nakreslí obraz transparentně pomocí masky, bez ohledu na barvu pozadí.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx

Nakreslí položku seznamu obrázků v zadaném kontextu zařízení.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext cílového zařízení.

*nObrázek*<br/>
Nulový index obrázku k nakreslení.

*Pt*<br/>
Umístění, ve kterém chcete kreslit v rámci zadaného kontextu zařízení.

*Sz*<br/>
Velikost části obrazu, která má být nakresleta vzhledem k levému hornímu rohu obrazu. Viz *dx* a *dy* v [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*clrBk*<br/>
Barva pozadí obrázku. Viz *rgbBk* v [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*clrFg*<br/>
Barva popředí obrazu. Viz *rgbFg* v [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*nStyl*<br/>
Příznak určující styl výkresu. Viz *fStyle* v [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Funkce používá zadaný styl kreslení a prolne obraz se zadanou barvou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect

Volání této členské funkce k nakreslení obrázku ze seznamu obrázků.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>Parametry

*pimldp*<br/>
Ukazatel na strukturu [IMAGELISTDRAWPARAMS,](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) která obsahuje informace o operaci kreslení.

*Pdc*<br/>
Ukazatel na kontext cílového zařízení. Po dokončení práce je nutné odstranit tento objekt [CDC.](../../mfc/reference/cdc-class.md)

*nObrázek*<br/>
Nulový index obrázku, který má být vykreslen.

*Pt*<br/>
A [POINT](/windows/win32/api/windef/ns-windef-point) struktura obsahující souřadnice x a y, kde bude obraz nakreslena.

*Sz*<br/>
Struktura [SIZE](/windows/win32/api/windef/ns-windef-size) označující velikost obrázku, který má být nakreslen.

*ptOrigin*<br/>
A [POINT](/windows/win32/api/windef/ns-windef-point) struktura obsahující souřadnice x a y určující levý horní roh operace kreslení vzhledem k samotnému obrazu. Obrazové body obrazu, které jsou vlevo od souřadnice x a nad souřadnicí y, nejsou vykresleny.

*fStyl*<br/>
Příznak určující styl kreslení a volitelně překryvné zobrazení. Informace o překryvném obrázku najdete v části Poznámky. Výchozí implementace knihovny MFC, ILD_NORMAL, nakreslí obrázek pomocí barvy pozadí pro seznam obrázků. Pokud je barva pozadí CLR_NONE hodnotou, obraz se nakreslí transparentně pomocí masky.

Další možné styly jsou popsány pod členem *fStyle* struktury [IMAGELISTDRAWPARAMS.](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)

*dwRop*<br/>
Hodnota určující kód rastrové operace. Tyto kódy definují, jak budou barevná data pro zdrojový obdélník kombinována s barevnými daty pro cílový obdélník, aby bylo dosaženo konečné barvy. Výchozí implementace knihovny MFC, SRCCOPY, zkopíruje zdrojový obdélník přímo do cílového obdélníku. Tento parametr je ignorován, pokud parametr *fStyle* neobsahuje příznak ILD_ROP.

Další možné hodnoty jsou popsány pod členem *dwRop* struktury [IMAGELISTDRAWPARAMS.](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)

*rgbZpět*<br/>
Barva pozadí obrázku ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaná aplikací nebo jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva pozadí. Obrázek je nakreslen pomocí barvy pozadí seznamu obrázků.|
|CLR_NONE|Žádná barva pozadí. Obrázek je nakreslena transparentně.|

*rgbFore*<br/>
Barva popředí obrazu ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaná aplikací nebo jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva popředí. Obraz je nakreslen pomocí barvy zvýraznění systému jako barvy popředí.|
|CLR_NONE|Žádná míchaná barva. Obraz se prolne s barvou kontextu cílového zařízení.|

Tento parametr se používá pouze v *případě, že fStyle* obsahuje příznak ILD_BLEND25 nebo ILD_BLEND50.

*fStát*<br/>
Příznak určující stav výkresu. Tento člen může obsahovat jeden nebo více příznaků stavu seznamu obrázků.

*Rámec*<br/>
Ovlivňuje chování účinků na nasycení a alfa prolnutí.

Při použití s ILS_SATURATE tento člen obsahuje hodnotu, která je přidána do každé barevné součásti Trojčata RGB pro každý obrazový bod v ikoně.

Při použití s ILS_APLHA tento člen obsahuje hodnotu alfa kanálu. Tato hodnota může být od 0 do 255, přičemž 0 je zcela průhledné a 255 je zcela neprůhledné.

*crEffect*<br/>
Hodnota [COLORREF](/windows/win32/gdi/colorref) použitá pro efekty záře a stínu.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je obrázek úspěšně nakreslen; jinak FALSE.

### <a name="remarks"></a>Poznámky

Použijte první verzi, pokud chcete vyplnit Win32 strukturu sami. Druhou verzi použijte, pokud chcete využít jeden nebo více výchozích argumentů knihovny MFC nebo se vyhnout správě struktury.

Překryvný obraz je obraz, který je nakreslen ý nad primárním obrazem, určený v této členské funkci parametrem *nImage.* Nakreslete masku překrytí pomocí členské funkce [Draw](#draw) s indexem jednoho objektu masky překrytí určeným pomocí makra [INDEXTOOVERLAYMASK.](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag

Volání této funkce ukončit operaci přetažení.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Poznámky

Chcete-li zahájit operaci `BeginDrag` přetažení, použijte členovou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon

Voláním této funkce vytvořte ikonu založenou na obrázku a jeho související masce v seznamu obrázků.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrázku.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda závisí na chování [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) makro k vytvoření ikony. Další informace o vytváření a čištění ikon naleznete v [makru ImageList_ExtractIcon.](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::FromHandle

Vrátí ukazatel na `CImageList` objekt, když je k seznamu obrázků přidělen popisovač.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hSeznam obrázků*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CImageList` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CImageList` a není již připojen k popisovač, dočasný `CImageList` objekt je vytvořen a připojen. Tento `CImageList` dočasný objekt je platný pouze do příště aplikace má dobu nečinnosti ve smyčce událostí, kdy jsou odstraněny všechny dočasné objekty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent

Vrátí ukazatel na `CImageList` objekt, když je k seznamu obrázků přidělen popisovač.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hSeznam obrázků*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CImageList` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CImageList` objekt není připojen k popisovač, null je vrácena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor

Voláním této funkce načtěte aktuální barvu pozadí pro seznam obrázků.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB `CImageList` barvy pozadí objektu.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList::GetDragImage

Získá dočasný seznam obrázků, který se používá pro přetažení.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lpPoint*<br/>
Adresa [point](/windows/win32/api/windef/ns-windef-point) struktury, která přijímá aktuální pozici přetažení.

*lpPointHotSpot*<br/>
Adresa `POINT` struktury, která přijímá odsazení obrazu přetažení vzhledem k poloze přetažení.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na dočasný seznam obrázků, který se používá pro přetažení; jinak NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList::GetImageCount

Voláním této funkce načtete počet obrázků v seznamu obrázků.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet obrázků.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList::GetImageInfo

Volání této funkce k načtení informací o obrázku.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrázku.

*pImageInfo*<br/>
Ukazatel na strukturu [IMAGEINFO,](/windows/win32/api/commctrl/ns-commctrl-imageinfo) která přijímá informace o obrázku. Informace v této struktuře lze použít k přímé manipulaci s bitmapami obrazu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Struktura `IMAGEINFO` obsahuje informace o obrázku v seznamu obrázků.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle

Volání této funkce `m_hImageList` k načtení datového člena.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k připojenému seznamu obrázků; jinak NULL, pokud není připojen žádný objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList

Úchyt seznamu obrázků připojený k tomuto objektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Poznámky

Datový `m_hImageList` člen je veřejná proměnná typu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::operátor HIMAGELIST

Pomocí tohoto operátoru získáte připojené `CImageList` úchyt objektu.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač seznamu `CImageList` obrázků reprezentované objektem; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor odlitků, který podporuje přímé použití objektu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList::Číst

Voláním této funkce si můžete přečíst seznam obrázků z archivu.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchiv*<br/>
Ukazatel na `CArchive` objekt, ze kterého má být přečten seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList::Odebrat

Voláním této funkce odeberete obraz z objektu seznamu obrázků.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrázku, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Všechny položky následující *po nImage* nyní přesunout dolů o jednu pozici. Pokud například seznam obrázků obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nImage*=0 pro položku v první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList::Nahradit

Voláním této funkce nahradíte obrázek v seznamu obrázků novým obrázkem.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrázku, který chcete nahradit.

*pbmImage*<br/>
Ukazatel na bitmapu obsahující obraz.

*pbmMask*<br/>
Ukazatel na bitmapu obsahující masku. Pokud se v seznamu obrázků nepoužívá žádná maska, bude tento parametr ignorován.

*hIkona*<br/>
Úchyt k ikoně, která obsahuje bitmapu a masku pro nový obraz.

### <a name="return-value"></a>Návratová hodnota

Verze vracející BOOL vrátí nenulovou, pokud je úspěšná; jinak 0.

Verze vracející **int** vrátí index image na základě nuly, pokud je úspěšná; jinak - 1.

### <a name="remarks"></a>Poznámky

Volání této členské funkce po volání [SetImageCount](#setimagecount) přiřadit nové, platné obrázky zástupný obrázek čísla indexu.

### <a name="example"></a>Příklad

  Viz příklad pro [CImageList::SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor

Voláním této funkce nastavte barvu pozadí pro seznam obrázků.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*Čr*<br/>
Barva pozadí nastavena. Dá se to CLR_NONE. V takovém případě jsou obrázky nakresleny transparentně pomocí masky.

### <a name="return-value"></a>Návratová hodnota

Předchozí barva pozadí v případě úspěchu; jinak CLR_NONE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage

Vytvoří nový přetahovací obraz kombinací daného obrazu (obvykle obrázku kurzoru myši) s aktuálním přetažením obrazu.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nPřetáhnout*<br/>
Index nového obrázku, který má být kombinován s přetahovaný obraz.

*ptHotSpot*<br/>
Umístění aktivního bodu v novém obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že funkce přetahování používají nový obrázek během operace přetažení, `CImageList::SetDragCursorImage`měli byste použít funkci Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) ke skrytí skutečného kurzoru myši po volání . V opačném případě systém může zdát, že dva kurzory myši po dobu trvání operace přetažení.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount

Volání této členské funkce obnovit počet `CImageList` obrázků v objektu.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount*<br/>
Hodnota určující nový celkový počet obrázků v seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud zavoláte tuto členovou funkci pro zvýšení počtu obrázků v seznamu obrázků, pak volání [Nahradit](#replace) pro každý další obrázek přiřadit nové indexy platné obrázky. Pokud se vám nepodaří přiřadit indexy platné obrázky, nakreslit operace, které vytvářejí nové obrázky bude nepředvídatelné.

Pokud pomocí této funkce zmenšíte velikost seznamu obrázků, zkrácené obrazy se uvolní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::SetOverlayImage

Voláním této funkce přidáte index obrazu na základě nuly do seznamu obrazů, které mají být použity jako masky překrytí.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrazu, který se má použít jako maska překrytí.

*nOverlay*<br/>
Jednozaložený index masky překrytí.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Do seznamu lze přidat až čtyři indexy.

Maska překrytí je obraz nakreslený transparentně nad jiným obrazem. Nakreslete přes obraz masku překrytí pomocí členské funkce [CImageList::Draw](#draw) s jednozaloženým indexem masky překrytí určeným pomocí makra INDEXTOOVERLAYMASK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList::Zápis

Volánítéto funkce k zápisu objektu seznamu obrázků do archivu.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchiv*<br/>
Ukazatel na `CArchive` objekt, ve kterém má být uložen seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[Třída CTabCtrl](../../mfc/reference/ctabctrl-class.md)
