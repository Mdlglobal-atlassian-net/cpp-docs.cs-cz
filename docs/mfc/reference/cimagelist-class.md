---
title: Atributu CImageList – třída
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
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890704"
---
# <a name="cimagelist-class"></a>Atributu CImageList – třída

Poskytuje funkce pro běžný ovládací prvek seznamu obrázků systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CImageList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Atributu CImageList:: atributu CImageList](#cimagelist)|Vytvoří objekt `CImageList`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Atributu CImageList:: Add](#add)|Přidá obrázek nebo obrázky do seznamu obrázků.|
|[Atributu CImageList:: Attach](#attach)|Připojí seznam obrázků k objektu `CImageList`.|
|[Atributu CImageList:: přetahovacích funkcí](#begindrag)|Začne přetahovat obrázek.|
|[Atributu CImageList:: Copy](#copy)|Kopíruje obrázek v rámci objektu `CImageList`.|
|[Atributu CImageList:: Create](#create)|Inicializuje seznam obrázků a připojí ho k objektu `CImageList`.|
|[Atributu CImageList::D eleteImageList](#deleteimagelist)|Odstraní seznam obrázků.|
|[Atributu CImageList::D eleteTempMap](#deletetempmap)|Volána obslužnou rutinou pro nečinnost v [CWinApp](../../mfc/reference/cwinapp-class.md) k odstranění dočasného objektu `CImageList` vytvořeného pomocí `FromHandle`.|
|[Atributu CImageList::D etach](#detach)|Odpojí objekt seznamu obrázků od objektu `CImageList` a vrátí popisovač do seznamu obrázků.|
|[Atributu CImageList::D ragEnter](#dragenter)|Zamkne aktualizace během operace přetažení a zobrazí obrázek přetáhnutí na zadané pozici.|
|[Atributu CImageList::D ragLeave](#dragleave)|Odemkne okno a skryje obrázek přetažení, aby bylo možné aktualizovat okno.|
|[Atributu CImageList::D ragMove](#dragmove)|Přesune obrázek, který se přetahuje během operace přetažení.|
|[Atributu CImageList::D ragShowNolock](#dragshownolock)|Zobrazí nebo skryje obrázek přetažení během operace přetažení bez uzamknutí okna.|
|[Atributu CImageList: nezpracované:D](#draw)|Nakreslí obrázek, který se přetahuje během operace přetažení.|
|[Atributu CImageList::D rawEx](#drawex)|Nakreslí položku seznamu obrázků v zadaném kontextu zařízení. Funkce používá zadaný styl vykreslování a smíchá obrázek se zadanou barvou.|
|[Atributu CImageList::D rawIndirect](#drawindirect)|Nakreslí obrázek ze seznamu obrázků.|
|[Atributu CImageList:: EndDrag](#enddrag)|Ukončí operaci přetažení.|
|[Atributu CImageList:: ExtractIcon](#extracticon)|Vytvoří ikonu založenou na obrázku a masce v seznamu obrázků.|
|[Atributu CImageList:: FromHandle](#fromhandle)|Vrátí ukazatel na objekt `CImageList`, pokud je předána obslužná rutina seznamu obrázků. Pokud objekt `CImageList` není připojen k popisovači, je vytvořen a připojen dočasný objekt `CImageList`.|
|[Atributu CImageList:: FromHandlePermanent](#fromhandlepermanent)|Vrátí ukazatel na objekt `CImageList`, pokud je předána obslužná rutina seznamu obrázků. Pokud objekt `CImageList` není připojen k popisovači, je vrácena hodnota NULL.|
|[Atributu CImageList:: GetBkColor](#getbkcolor)|Načte aktuální barvu pozadí seznamu obrázků.|
|[Atributu CImageList:: GetDragImage](#getdragimage)|Načte dočasný seznam obrázků, který se používá k přetahování.|
|[Atributu CImageList:: GetImageCount](#getimagecount)|Načte počet obrázků v seznamu obrázků.|
|[Atributu CImageList:: GetImageInfo](#getimageinfo)|Načte informace o obrázku.|
|[Atributu CImageList:: GetSafeHandle](#getsafehandle)|Načte objekt `m_hImageList`.|
|[Atributu CImageList:: Read](#read)|Přečte seznam obrázků z archivu.|
|[Atributu CImageList:: Remove](#remove)|Odebere obrázek ze seznamu obrázků.|
|[Atributu CImageList:: Replace](#replace)|Nahradí obrázek v seznamu obrázků novým obrázkem.|
|[Atributu CImageList:: SetBkColor](#setbkcolor)|Nastaví barvu pozadí seznamu obrázků.|
|[Atributu CImageList:: SetDragCursorImage](#setdragcursorimage)|Vytvoří nový obrázek přetažení.|
|[Atributu CImageList:: SetImageCount](#setimagecount)|Obnoví počet obrázků v seznamu obrázků.|
|[Atributu CImageList:: SetOverlayImage](#setoverlayimage)|Přidá index obrázku založený na nule do seznamu obrázků, které mají být použity jako překryté masky.|
|[Atributu CImageList:: Write](#write)|Zapíše seznam obrázků do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Atributu CImageList:: operator HIMAGELIST](#operator_himagelist)|Vrátí HIMAGELIST připojenou k `CImageList`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Atributu CImageList:: m_hImageList](#m_himagelist)|Popisovač obsahující seznam obrázků připojený k tomuto objektu.|

## <a name="remarks"></a>Poznámky

"Seznam obrázků" je kolekce obrázků stejné velikosti, z nichž každá může být odkazována jeho indexem založeným na nule. Seznamy obrázků slouží k efektivní správě velkých sad ikon nebo rastrových obrázků. Všechny obrázky v seznamu obrázků jsou obsaženy ve formátu obrazovky s jedním, velkým rastrovým obrázkem. Seznam obrázků může obsahovat také monochromatický rastrový obrázek, který obsahuje masky používané pro transparentní vykreslování obrázků (styl ikony). Rozhraní API (Application Programming Interface) pro Microsoft Win32 nabízí funkce seznamu obrázků, které umožňují kreslit obrázky, vytvářet a zničit seznamy obrázků, přidávat a odebírat obrázky, nahrazovat obrázky, slučovat obrázky a přetahovat obrázky.

Tento ovládací prvek (a proto třída `CImageList`) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Další informace o použití `CImageList`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="add"></a>Atributu CImageList:: Add

Voláním této funkce přidáte jednu nebo více obrázků nebo ikonu do seznamu obrázků.

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
Ukazatel na rastrový obrázek obsahující obrázek nebo obrázky. Počet obrázků je odvozený od šířky rastrového obrázku.

*pbmMask*<br/>
Ukazatel na rastrový obrázek obsahující masku. Pokud se v seznamu obrázků nepoužívá žádná maska, tento parametr se ignoruje.

*crMask*<br/>
Barva použitá k vygenerování masky Každý pixel této barvy v dané bitmapě je změněn na černou a odpovídající bit v masce je nastaven na hodnotu One.

*hIcon*<br/>
Popisovač ikony, která obsahuje rastrový obrázek a masku pro nový obrázek.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule prvního nového obrázku, pokud je úspěšný; v opačném případě-1.

### <a name="remarks"></a>Poznámky

Zodpovídáte za uvolnění popisovače ikony, když s ním budete hotovi.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>Atributu CImageList:: Attach

Voláním této funkce připojíte seznam obrázků k objektu `CImageList`.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Popisovač objektu seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla příloha úspěšná; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>Atributu CImageList:: přetahovacích funkcí

Voláním této funkce zahájíte přetahování obrázku.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index založený na nule obrázku, který chcete přetáhnout

*ptHotSpot*<br/>
Souřadnice počáteční pozice pro přetažení (obvykle pozice kurzoru) Souřadnice jsou relativní vzhledem k levému hornímu rohu obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří dočasný seznam obrázků, který se používá k přetahování. Obrázek kombinuje zadaný obrázek a jeho masku s aktuálním kurzorem. V reakci na následné zprávy WM_MOUSEMOVE můžete přesunout obrázek přetažením pomocí členské funkce `DragMove`. Chcete-li ukončit operaci přetažení, můžete použít členskou funkci `EndDrag`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>Atributu CImageList:: atributu CImageList

Vytvoří objekt `CImageList`.

```
CImageList();
```

##  <a name="copy"></a>Atributu CImageList:: Copy

Tato členská funkce implementuje chování funkce Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), jak je popsáno v Windows SDK.

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
Index založený na nule obrázku, který má být použit jako cíl operace kopírování.

*iSrc*<br/>
Index založený na nule obrázku, který má být použit jako zdroj operace kopírování.

*uFlags*<br/>
Hodnota bitového příznaku, která určuje typ operace kopírování, která má být provedena. Tento parametr může být jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILCF_MOVE|Zdrojový obrázek se zkopíruje do indexu cílové image. Výsledkem této operace je více instancí daného obrázku. Výchozím nastavením je ILCF_MOVE.|
|ILCF_SWAP|Pozice pro výměnu zdrojových a cílových imagí v rámci seznamu obrázků.|

*pSrc*<br/>
Ukazatel na objekt `CImageList`, který je cílem operace kopírování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>Atributu CImageList:: Create

Inicializuje seznam obrázků a připojí ho k objektu [atributu CImageList](../../mfc/reference/cimagelist-class.md) .

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

*CX*<br/>
Rozměry každého obrázku (v pixelech)

*kr*<br/>
Rozměry každého obrázku (v pixelech)

*nFlags*<br/>
Určuje typ seznamu obrázků, který se má vytvořit. Tento parametr může být kombinací následujících hodnot, ale může obsahovat pouze jednu z `ILC_COLOR` hodnot.

|Hodnota|Význam|
|-----------|-------------|
|ILC_COLOR|Pokud není zadán žádný z dalších příznaků ILC_COLOR *, použijte výchozí chování. Výchozí hodnota je obvykle ILC_COLOR4; u starších ovladačů displeje se ale výchozí hodnota ILC_COLORDDB.|
|ILC_COLOR4|Jako rastrový obrázek pro seznam obrázků použijte 8bitové oddíly (16 barev) DIB (16 barev).|
|ILC_COLOR8|Použijte 8bitový oddíl se znaménkem DIB. Barvy použité pro tabulku barev jsou stejné barvy jako paleta polotónů.|
|ILC_COLOR16|Použijte 16bitový oddíl DIB (32/64 KB barev).|
|ILC_COLOR24|Použijte 24bitového oddílu DIB.|
|ILC_COLOR32|Použijte 32 oddíl DIB.|
|ILC_COLORDDB|Použijte rastrový obrázek závislý na zařízení.|
|ILC_MASK|Používá masku. Seznam obrázků obsahuje dvě bitmapy, jedna z nich je monochromatický rastr použitý jako maska. Pokud tato hodnota není zahrnutá, zobrazí se v seznamu obrázků jenom jedna bitmapa. Další informace o maskovaných obrázcích najdete v tématu [vykreslování obrázků ze seznamu obrázků](../../mfc/drawing-images-from-an-image-list.md) .|

*nInitial*<br/>
Počet obrázků, které obsahuje původně seznam obrázků.

*nGrow*<br/>
Počet imagí, podle kterých se může seznam obrázků zvětšit, když systém potřebuje změnit velikost seznamu, aby uvolnil místo pro nové image. Tento parametr představuje počet nových obrázků, které může seznam obrázků se změněnou velikostí obsahovat.

*nBitmapID*<br/>
ID prostředků rastrového obrázku, který má být přidružen k seznamu obrázků.

*crMask*<br/>
Barva použitá k vygenerování masky Každý pixel této barvy v zadané bitmapě je změněn na černou a odpovídající bit v masce je nastaven na hodnotu One.

*lpszBitmapID*<br/>
Řetězec obsahující ID prostředků imagí.

*imagelist1*<br/>
Odkaz na objekt `CImageList`.

*nImage1*<br/>
Index první existující image

*imagelist2*<br/>
Odkaz na objekt `CImageList`.

*nImage2*<br/>
Index druhého existujícího obrázku

*DX*<br/>
Posun druhého obrázku ve vztahu k prvnímu obrázku (v pixelech) na ose x

*dy*<br/>
Posun druhého obrázku ve vztahu k prvnímu obrázku (v pixelech) na ose y

*pImageList*<br/>
Ukazatel na objekt `CImageList`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Sestavíte `CImageList` ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, který vytvoří seznam obrázků a připojí ho k objektu `CImageList`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>Atributu CImageList::D eleteImageList

Voláním této funkce odstraníte seznam obrázků.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>Atributu CImageList::D eleteTempMap

Volána automaticky `CWinApp` obslužným rutinou nečinných časů `DeleteTempMap` odstraní všechny dočasné `CImageList` objekty vytvořené pomocí [FromHandle](#fromhandle), ale nezničí žádné popisovače (`hImageList`) dočasně asociované s `ImageList` objekty.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>Atributu CImageList::D etach

Voláním této funkce odpojíte objekt seznamu obrázků od objektu `CImageList`.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu seznamu obrázků.

### <a name="remarks"></a>Poznámky

Tato funkce vrací popisovač do objektu seznamu obrázků.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: Attach](#attach).

##  <a name="dragenter"></a>Atributu CImageList::D ragEnter

Během operace přetažení zamkne aplikace aktualizace okna zadaného parametrem *pWndLock* a zobrazí obrázek přetáhnutí na pozici určené *bodem*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno, které vlastní obrázek přetažení.

*Vyberte*<br/>
Pozice, na které se má zobrazit obrázek přetažení Souřadnice jsou relativní vzhledem k levému hornímu rohu okna (nikoli klientské oblasti).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Souřadnice jsou relativní vzhledem k levému hornímu rohu okna, takže při zadávání souřadnic musíte kompenzovat šířku prvků oken, jako je například ohraničení, záhlaví a řádek nabídek.

Pokud má *pWndLock* hodnotu null, tato funkce nakreslí obrázek v kontextu zobrazení přidruženého k oknu plocha a souřadnice jsou relativní vzhledem k levému hornímu rohu obrazovky.

Tato funkce zamkne všechny ostatní aktualizace daného okna během operace přetažení. Pokud během operace přetažení potřebujete udělat všechny kresby, jako je například zvýraznění cíle operace přetažení, můžete přetažený obrázek dočasně skrýt pomocí funkce [atributu CImageList::D ragleave](#dragleave) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: přetahovacích funkcí](#begindrag).

##  <a name="dragleave"></a>Atributu CImageList::D ragLeave

Odemkne okno určené *pWndLock* a skryje obrázek přetažení, což umožňuje aktualizovat okno.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno, které vlastní obrázek přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: EndDrag](#enddrag).

##  <a name="dragmove"></a>Atributu CImageList::D ragMove

Voláním této funkce přesunete obrázek, který je přetažen během operace přetažení.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
Nová pozice pro přetažení

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle volá v reakci na zprávu WM_MOUSEMOVE. Chcete-li zahájit operaci přetažení, použijte členskou funkci `BeginDrag`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>Atributu CImageList::D ragShowNolock

Zobrazí nebo skryje obrázek přetažení během operace přetažení bez uzamknutí okna.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda má být zobrazen obrázek přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce [atributu CImageList::D ragenter](#dragenter) zamkne všechny aktualizace okna během operace přetažení. Tato funkce však okno nezamkne.

##  <a name="draw"></a>Atributu CImageList: nezpracované:D

Voláním této funkce nakreslíte obrázek, který se přetahuje během operace přetažení.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Ukazatel na cílový kontext zařízení.

*nImage*<br/>
Index vykreslování obrázku založený na nule

*bodů*<br/>
Umístění, ve kterém se má nakreslit v rámci určeného kontextu zařízení.

*nStyle*<br/>
Příznak určující styl vykreslování Může to být jedna nebo víc z těchto hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILD_BLEND25 ILD_FOCUS|Nakreslí obrázek, promícháním 25 procent pomocí barvy zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masku.|
|ILD_BLEND50, ILD_SELECTED ILD_BLEND|Nakreslí obrázek, míchání 50 procent s barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masku.|
|ILD_MASK|Nakreslí masku.|
|ILD_NORMAL|Nakreslí obrázek pomocí barvy pozadí seznamu obrázků. Pokud je barva pozadí CLR_NONE hodnotou, obrázek je vykreslen transparentně pomocí masky.|
|ILD_TRANSPARENT|Nakreslí obraz transparentně pomocí masky bez ohledu na barvu pozadí.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>Atributu CImageList::D rawEx

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

*Emulátor*<br/>
Ukazatel na cílový kontext zařízení.

*nImage*<br/>
Index vykreslování obrázku založený na nule

*bodů*<br/>
Umístění, ve kterém se má nakreslit v rámci určeného kontextu zařízení.

*'s*<br/>
Velikost části obrázku, která se má vykreslit vzhledem k levému hornímu rohu obrázku Viz *DX* a *dy* v [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK.

*clrBk*<br/>
Barva pozadí obrázku Přečtěte si téma *rgbBk* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v Windows SDK.

*clrFg*<br/>
Barva popředí obrázku Přečtěte si téma *rgbFg* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v Windows SDK.

*nStyle*<br/>
Příznak určující styl vykreslování Přečtěte si téma *fStyle* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Funkce používá zadaný styl vykreslování a smíchá obrázek se zadanou barvou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>Atributu CImageList::D rawIndirect

Voláním této členské funkce vykreslíte obrázek ze seznamu obrázků.

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
Ukazatel na strukturu [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) , která obsahuje informace o operaci Draw.

*Emulátor*<br/>
Ukazatel na kontext cílového zařízení. Pokud s tím budete hotovi, musíte tento objekt [CDC](../../mfc/reference/cdc-class.md) odstranit.

*nImage*<br/>
Index založený na nule obrázku, který má být vykreslen.

*bodů*<br/>
Struktura [bodu](/previous-versions/dd162805\(v=vs.85\)) obsahující souřadnice x a y, kde se obrázek vykreslí.

*'s*<br/>
Struktura [velikosti](/windows/win32/api/windef/ns-windef-size) označující velikost obrázku, který se má vykreslit.

*ptOrigin*<br/>
Struktura [bodu](/previous-versions/dd162805\(v=vs.85\)) obsahující souřadnice x a y, které určují levý horní roh operace kreslení vzhledem k samotné imagi. Obrazové body obrázku vlevo od souřadnice x a nad souřadnicí y nejsou vykresleny.

*fStyle*<br/>
Příznak určující styl vykreslování a volitelně překryvný obrázek. Informace o překryté imagi najdete v části s poznámkami. Výchozí implementace knihovny MFC, ILD_NORMAL, nakreslí obrázek pomocí barvy pozadí seznamu obrázků. Pokud je barva pozadí CLR_NONE hodnotou, obrázek je vykreslen transparentně pomocí masky.

Další možné styly jsou popsány v rámci *fStyle* člena struktury [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*dwRop*<br/>
Hodnota, která určuje kód pro rastrovou operaci. Tyto kódy definují, jak budou barevná data pro zdrojový obdélník kombinována s barevnými daty pro cílový obdélník, aby se dosáhlo konečné barvy. Výchozí implementace knihovny MFC, SRCCOPY, kopíruje zdrojový obdélník přímo do cílového obdélníku. Tento parametr se ignoruje v případě, že parametr *fStyle* neobsahuje příznak ILD_ROP.

Další možné hodnoty jsou popsány v rámci *dwRop* člena struktury [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*rgbBack*<br/>
Barva pozadí obrázku ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaná aplikací nebo jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva pozadí Obrázek se vykreslí pomocí barvy pozadí v seznamu obrázků.|
|CLR_NONE|Barva pozadí není k dispozici. Obrázek je vykreslen transparentně.|

*rgbFore*<br/>
Barva popředí obrázku ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaná aplikací nebo jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva popředí Obrázek je vykreslen pomocí barvy zvýraznění systému jako barva popředí.|
|CLR_NONE|Žádná barva Blendu. Obrázek je Blend s barvou cílového zařízení v kontextu.|

Tento parametr se používá pouze v případě, že *fStyle* obsahuje příznak ILD_BLEND25 nebo ILD_BLEND50.

*fState*<br/>
Příznak určující stav kreslení Tento člen může obsahovat jeden nebo více příznaků stavu seznamu obrázků.

*Rámec*<br/>
Ovlivňuje chování sytosti a alfa efektů prolnutí.

Při použití s ILS_SATURATE obsahuje tento člen hodnotu, která je přidána do každé složky barev s trojicí RGB pro každý pixel v ikoně.

Při použití s ILS_APLHA obsahuje tento člen hodnotu pro alfa kanál. Tato hodnota může být od 0 do 255, s 0 je zcela transparentní a 255 je zcela neprůhledné.

*crEffect*<br/>
Hodnota [COLORREF](/windows/win32/gdi/colorref) , která se používá pro efekt záře a stín.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se obrázek úspěšně vykreslil; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

První verzi použijte v případě, že chcete strukturu Win32 vyplnit sami. Druhou verzi použijte v případě, že chcete využít výhod jednoho nebo více výchozích argumentů knihovny MFC nebo se vyhnout správě struktury.

Překryvný obrázek je obrázek vykreslený na primárním obrázku, který je zadaný v této členské funkci pomocí parametru *nImage* . Nakreslete překrytí masky pomocí funkce [Draw](#draw) member, která je založená na jednom indexu překryté masky určené pomocí makra [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>Atributu CImageList:: EndDrag

Voláním této funkce ukončíte operaci přetažení.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Poznámky

Chcete-li zahájit operaci přetažení, použijte členskou funkci `BeginDrag`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>Atributu CImageList:: ExtractIcon

Voláním této funkce vytvoříte ikonu založenou na obrázku a jeho související masce v seznamu obrázků.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index obrázku založený na nule.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda spoléhá na chování [ImageList_ExtractIconho](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) makra k vytvoření ikony. Další informace o vytváření a čištění ikon naleznete v makru [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>Atributu CImageList:: FromHandle

Vrátí ukazatel na objekt `CImageList`, pokud je předána obslužná rutina seznamu obrázků.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CImageList` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud k popisovači již není připojen `CImageList`, je vytvořen a připojen dočasný objekt `CImageList`. Tento dočasný `CImageList` objekt je platný pouze do okamžiku, kdy aplikace bude mít čas nečinnosti ve smyčce události, kdy se všechny dočasné objekty odstraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>Atributu CImageList:: FromHandlePermanent

Vrátí ukazatel na objekt `CImageList`, pokud je předána obslužná rutina seznamu obrázků.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CImageList` v případě úspěchu; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt `CImageList` není připojen k popisovači, je vrácena hodnota NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>Atributu CImageList:: GetBkColor

Voláním této funkce načtete aktuální barvu pozadí seznamu obrázků.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB barvy pozadí objektu `CImageList`

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>Atributu CImageList:: GetDragImage

Načte dočasný seznam obrázků, který se používá k přetahování.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lpPoint*<br/>
Adresa struktury [bodu](/previous-versions/dd162805\(v=vs.85\)) , která přijímá aktuální polohu při přetahování.

*lpPointHotSpot*<br/>
Adresa `POINT` struktury, která přijímá posunutí obrázku přetažením vzhledem k poloze pro přetažení.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na seznam dočasných obrázků, který se používá pro přetahování; v opačném případě hodnota NULL.

##  <a name="getimagecount"></a>Atributu CImageList:: GetImageCount

Voláním této funkce načtete počet obrázků v seznamu obrázků.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet imagí.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>Atributu CImageList:: GetImageInfo

Voláním této funkce načtete informace o obrázku.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index obrázku založený na nule.

*pImageInfo*<br/>
Ukazatel na strukturu [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) , která přijímá informace o imagi. Informace v této struktuře lze použít k přímé manipulaci s bitmapami pro obrázek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Struktura `IMAGEINFO` obsahuje informace o obrázku v seznamu obrázků.

##  <a name="getsafehandle"></a>Atributu CImageList:: GetSafeHandle

Voláním této funkce načtete datový člen `m_hImageList`.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač seznamu připojených obrázků; jinak NULL, pokud není připojen žádný objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>Atributu CImageList:: m_hImageList

Popisovač seznamu obrázků připojeného k tomuto objektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Poznámky

Datový člen `m_hImageList` je veřejná proměnná typu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>Atributu CImageList:: operator HIMAGELIST

Tento operátor použijte k získání připojeného popisovače objektu `CImageList`.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač seznamu obrázků reprezentovaného objektem `CImageList`; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>Atributu CImageList:: Read

Voláním této funkce načtete seznam obrázků z archivu.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Ukazatel na objekt `CArchive`, ze kterého má být načten seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>Atributu CImageList:: Remove

Voláním této funkce odeberete obrázek z objektu seznamu obrázků.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index s nulovým základem obrázku, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Všechny položky, které následují *nImage* , se teď přesunou o jednu pozici dolů. Například pokud seznam obrázků obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nImage*= 0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>Atributu CImageList:: Replace

Voláním této funkce můžete nahradit obrázek v seznamu obrázků novým obrázkem.

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

*nImage*<br/>
Index založený na nule obrázku, který má být nahrazen.

*pbmImage*<br/>
Ukazatel na rastrový obrázek, který obsahuje obrázek.

*pbmMask*<br/>
Ukazatel na rastrový obrázek obsahující masku. Pokud se v seznamu obrázků nepoužívá žádná maska, tento parametr se ignoruje.

*hIcon*<br/>
Popisovač ikony, která obsahuje rastrový obrázek a masku pro nový obrázek.

### <a name="return-value"></a>Návratová hodnota

Verze vracející BOOL vrátí nenulovou hodnotu, pokud je úspěšná; v opačném případě 0.

Verze **vracející** celočíselný vrátí index založený na nule, pokud je to úspěšné; v opačném případě-1.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci volejte po volání [SetImageCount](#setimagecount) a přiřaďte nové platné image k číslům indexů zástupných obrázků.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [atributu CImageList:: SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>Atributu CImageList:: SetBkColor

Voláním této funkce nastavíte barvu pozadí seznamu obrázků.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*znaky*<br/>
Barva pozadí, která se má nastavit Může být CLR_NONE. V takovém případě jsou obrázky transparentně vykreslovány pomocí masky.

### <a name="return-value"></a>Návratová hodnota

Předchozí barva pozadí v případě úspěchu; jinak CLR_NONE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>Atributu CImageList:: SetDragCursorImage

Vytvoří nový obrázek přetáhnutím kombinováním daného obrázku (obvykle obrázku ukazatele myši) s aktuálním obrázkem přetažení.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nDrag*<br/>
Index nového obrázku, který se má zkombinovat s obrázkem přetažení

*ptHotSpot*<br/>
Pozice aktivního bodu v rámci nového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že funkce přetahování používají nový obrázek během operace přetažení, měli byste pomocí funkce Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) skrýt skutečný ukazatel myši po volání `CImageList::SetDragCursorImage`. V opačném případě se může zdát, že systém bude mít po dobu trvání operace přetažení dva ukazatele myši.

##  <a name="setimagecount"></a>Atributu CImageList:: SetImageCount

Zavolejte tuto členskou funkci pro resetování počtu imagí v objektu `CImageList`.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount*<br/>
Hodnota určující nový celkový počet obrázků v seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Pokud zavoláte tuto členskou funkci pro zvýšení počtu obrázků v seznamu obrázků, pak voláním metody [Replace](#replace) pro každý další obrázek přiřadíte nové indexy k platným obrázkům. Pokud nemůžete přiřadit indexy k platným obrázkům, operace vykreslování, které vytvářejí nové image, nebudou předvídatelné.

Pokud zmenšíte velikost seznamu obrázků pomocí této funkce, zkrácené obrázky budou uvolněny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>Atributu CImageList:: SetOverlayImage

Voláním této funkce přidáte index založený na nule obrázku do seznamu obrázků, které mají být použity jako překryté masky.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index založený na nule obrázku, který má být použit jako překryvná maska.

*nOverlay*<br/>
Index překrytí založený na jednom indexu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Do seznamu lze přidat až čtyři indexy.

Překrytí obrázku je obrázek vykreslený transparentně přes jiný obrázek. Nakreslete překryvnou masku na obrázek pomocí funkce [atributu CImageList: in:D holých](#draw) členů s indexem překrytí, který je určený pomocí makra INDEXTOOVERLAYMASK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>Atributu CImageList:: Write

Voláním této funkce zapíšete objekt seznamu obrázků do archivu.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Ukazatel na objekt `CArchive`, ve kterém má být uložen seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)
