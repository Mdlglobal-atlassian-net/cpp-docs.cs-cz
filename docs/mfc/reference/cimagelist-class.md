---
title: Cimagelist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15f021d78158caa6f607be3d68a9666b4ab6d6a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448516"
---
# <a name="cimagelist-class"></a>Cimagelist – třída

Poskytuje funkce pro Windows běžné ovládací prvek seznamu obrázků.

## <a name="syntax"></a>Syntaxe

```
class CImageList : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Vytvoří `CImageList` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CImageList::Add](#add)|Přidá do seznamu obrázků image nebo Image.|
|[CImageList::Attach](#attach)|Připojí se k seznamu obrázků `CImageList` objektu.|
|[CImageList::BeginDrag](#begindrag)|Zahájí přetahování bitovou kopii.|
|[CImageList::Copy](#copy)|Zkopíruje obrázek `CImageList` objektu.|
|[CImageList::Create](#create)|Inicializuje seznamu obrázků a připojí ho k `CImageList` objektu.|
|[CImageList::DeleteImageList](#deleteimagelist)|Odstraní seznamu obrázků.|
|[CImageList::DeleteTempMap](#deletetempmap)|Volá [CWinApp](../../mfc/reference/cwinapp-class.md) doby nečinnosti obslužná rutina se odstranit všechny dočasné `CImageList` objekt vytvořený pomocí `FromHandle`.|
|[CImageList::Detach](#detach)|Odpojí objektu seznamu obrázků z `CImageList` objekt a vrátí popisovač do seznamu obrázků.|
|[CImageList::DragEnter](#dragenter)|Uzamkne aktualizace během operace přetažení a zobrazí obrázek přetáhněte na určené pozici.|
|[CImageList::DragLeave](#dragleave)|Odemkne okna a skryje přetáhnout obrázek tak, že je možné aktualizovat v okně.|
|[CImageList::DragMove](#dragmove)|Přesune obrázku, který je přetažen během operace přetažení myší.|
|[CImageList::DragShowNolock](#dragshownolock)|Zobrazí nebo skryje přetáhnout obrázek během operace přetažení, bez nutnosti používat jenom v okně.|
|[CImageList::Draw](#draw)|Nakreslí obrázek, který je přetažen během operace přetažení myší.|
|[CImageList::DrawEx](#drawex)|Nakreslí obrázek položky seznamu v rámci zadané zařízení. Funkce používá zadané styl vykreslování a prolnutí bitovou kopii určenou barvou.|
|[CImageList::DrawIndirect](#drawindirect)|Kreslení obrázku ze seznamu obrázků.|
|[CImageList::EndDrag](#enddrag)|Ukončí operaci přetažení.|
|[CImageList::ExtractIcon](#extracticon)|Vytvoří ikonu založené na image a maska v seznamu obrázků.|
|[CImageList::FromHandle](#fromhandle)|Vrací ukazatel `CImageList` objektu, když je zadaný popisovač seznamu obrázků. Pokud `CImageList` objekt není připojen ke zpracování, dočasný `CImageList` objekt se vytvoří a připojí.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Vrací ukazatel `CImageList` objektu, když je zadaný popisovač seznamu obrázků. Pokud `CImageList` objekt není připojen ke popisovače, je vrácena hodnota NULL.|
|[CImageList::GetBkColor](#getbkcolor)|Načte aktuální barvu pozadí pro seznam obrázků.|
|[CImageList::GetDragImage](#getdragimage)|Získá seznam dočasných obrázků, který se používá pro přetažení myší.|
|[CImageList::GetImageCount](#getimagecount)|Získá počet obrázků v seznamu obrázků.|
|[CImageList::GetImageInfo](#getimageinfo)|Načte informace o obrázku.|
|[CImageList::GetSafeHandle](#getsafehandle)|Načte `m_hImageList`.|
|[CImageList::Read](#read)|Načte seznam obrázků z archivu.|
|[CImageList::Remove](#remove)|Odebere bitovou kopii ze seznamu obrázků.|
|[CImageList::Replace](#replace)|Nahrazuje obrázek v seznamu obrázků s novou bitovou kopii.|
|[CImageList::SetBkColor](#setbkcolor)|Nastaví barvu pozadí seznamu obrázků.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Vytvoří novou image přetažení.|
|[CImageList::SetImageCount](#setimagecount)|Resetuje počet imagí v seznamu obrázků.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Z nuly vycházející index obrázku přidá do seznamu imagí, které má být použit jako překrytí masky.|
|[CImageList::Write](#write)|Zapíše seznamu obrázků do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Vrátí HIMAGELIST připojené k `CImageList`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Popisovač obsahující seznam obrázků, které jsou připojené k tomuto objektu.|

## <a name="remarks"></a>Poznámky

"Seznamu obrázků" je kolekce obrazů stejné velikosti, z nichž každý lze odkazovat pomocí jeho index založený na nule. Seznamy obrázků se používají k zajištění efektivní správy velkých sad ikony nebo rastrové obrázky. Všechny Image v seznamu obrázků jsou obsaženy v jedné široké rastrového obrázku ve formátu obrazovce zařízení. Seznam obrázků může také zahrnovat monochromatický rastrový obrázek, který obsahuje masky umožňuje transparentně vykreslení obrázků (styl ikon). Microsoft Win32 aplikačního programovacího rozhraní (API) poskytuje funkce seznam obrázků, umožňující vykreslení obrázků, vytvořit a zničit seznamy obrázků, přidat a odebíráním imagí, nahraďte Image, sloučit Image a přetáhněte obrázky.

Tento ovládací prvek (a tedy `CImageList` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Další informace o používání `CImageList`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="add"></a>  CImageList::Add

Voláním této funkce do seznamu obrázků přidat jednu nebo víc imagí nebo ikonu.

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
Ukazatel na rastrový obrázek, který obsahuje image nebo Image. Počet obrázků je odvozen z šířku rastrového obrázku.

*pbmMask*<br/>
Ukazatel na rastrový obrázek s maskou. Pokud se žádná maska se používá s seznam obrázků, tento parametr je ignorován.

*crMask*<br/>
Barva použitá ke generování masky. Každý pixel tato barva v daném rastrového obrázku se změní na černou, a odpovídající bit masky je nastavená na jednu.

*hIcon*<br/>
Popisovač ikony, která obsahuje rastrového obrázku a maska pro nové image.

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index první novou image, v případě úspěchu; jinak - 1.

### <a name="remarks"></a>Poznámky

Zodpovídáte za uvolňuje popisovač ikony, když jste s ním hotovi.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

Voláním této funkce se připojit k seznamu obrázků `CImageList` objektu.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Popisovač pro objekt seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud příloha byla úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

Voláním této funkce začít přetahovat bitovou kopii.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index bitové kopie a přetažením.

*ptHotSpot*<br/>
Souřadnice přetáhněte pozice (obvykle pozice kurzoru). Souřadnice jsou relativní vzhledem k levý horní roh obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce vytvoří seznam dočasných obrázků, který se používá pro přetažení myší. Na obrázku kombinuje zadané bitové kopie a její maska s aktuální kurzor. V odpovědi na následné wm_mousemove a zprávy, může přecházet pomocí přetáhnout obrázek `DragMove` členskou funkci. Chcete-li ukončit operaci přetažení, můžete použít `EndDrag` členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

Vytvoří `CImageList` objektu.

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

Tato členská funkce implementuje chování funkce Win32 [ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy), jak je popsáno v sadě Windows SDK.

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
Index založený na nule obrázek, který se použije jako cíl operace kopírování.

*Kód*<br/>
Index založený na nule obrázek, který se použije jako zdroj kopírování.

*uFlags*<br/>
Hodnota příznaku bit, který určuje typ operace kopírování má být provedeno. Tento parametr může být jeden z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILCF_MOVE|Zdroj obrázku je zkopírován do index bitové kopie cíl. Tato operace vyústí ve více instancích sady danou image. ILCF_MOVE je výchozí nastavení.|
|ILCF_SWAP|Bitové kopie zdrojových a cílových exchange pozice v seznamu obrázků.|

*pSrc*<br/>
Ukazatel `CImageList` objekt, který je cílem operace kopírování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

Inicializuje seznamu obrázků a připojí ho k [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu.

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
Dimenze každého obrázku v pixelech.

*CY*<br/>
Dimenze každého obrázku v pixelech.

*nFlags*<br/>
Určuje typ vytvoření seznamu obrázků. Tento parametr může být kombinací těchto hodnot, ale může obsahovat pouze jeden z `ILC_COLOR` hodnoty.

|Hodnota|Význam|
|-----------|-------------|
|ILC_COLOR|Pokud není zadaný žádný další ILC_COLOR * příznaků, použije se výchozí chování. Výchozí hodnota je obvykle ILC_COLOR4; ale pro starší ovladače displeje, výchozí hodnota je ILC_COLORDDB.|
|ILC_COLOR4|Oddíl 4-bit bitmap nezávislých na zařízení (DIB) (16 barev) použijte jako rastrový obrázek pro seznam obrázků.|
|ILC_COLOR8|Použijte oddíl DIB 8 bitů. Barvy pro tabulku barvy jsou stejné barvy jako polotónování palety.|
|ILC_COLOR16|Použít 16 bitů (32 nebo 64 kB barvu) DIB oddílu.|
|ILC_COLOR24|Použití oddílu DIB 24-bit.|
|ILC_COLOR32|Použití oddílu DIB 32-bit.|
|ILC_COLORDDB|Použijte závislé na zařízení rastrový obrázek.|
|ILC_MASK|Pomocí masky. Seznam obrázků obsahuje dvě rastrové obrázky, z nichž jeden je monochromatický rastrový obrázek používá jako masku. Pokud tato hodnota není zahrnutý, seznam obrázků obsahuje pouze jeden rastrového obrázku. Zobrazit [vykreslování obrázků ze seznamu obrázků](../../mfc/drawing-images-from-an-image-list.md) Další informace o maskované imagí.|

*nInitial*<br/>
Počet imagí, které původně obsahuje seznam obrázků.

*nGrow*<br/>
Počet imagí, podle kterých můžou růst seznam obrázků, když systém potřebuje ke změně velikosti seznamu, aby uvolnil prostor pro nové Image. Tento parametr představuje počet nových imagí, které může obsahovat seznam obrázků se změněnou velikostí.

*nBitmapID*<br/>
ID prostředku rastrového obrázku má být přidružena k seznamu obrázků.

*crMask*<br/>
Barva použitá ke generování masky. Každý pixel tato barva v zadané rastrového obrázku se změní na černou, a odpovídající bit masky je nastavená na jednu.

*lpszBitmapID*<br/>
Řetězec obsahující ID bitové kopie prostředků.

*imagelist1*<br/>
Odkaz na `CImageList` objektu.

*nImage1*<br/>
Index prvního stávající bitovou kopii.

*imagelist2*<br/>
Odkaz na `CImageList` objektu.

*nImage2*<br/>
Index druhého stávající bitovou kopii.

*DX*<br/>
Posun osy x druhý obrázek ve vztahu k první obrázku v pixelech.

*dy*<br/>
Posun osy y druhý obrázek ve vztahu k první obrázku v pixelech.

*pImageList*<br/>
Ukazatel `CImageList` objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CImageList` ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, která vytvoří seznam obrázků a připojí ho k `CImageList` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

Voláním této funkce se odstranit seznamu obrázků.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

Automaticky volána `CWinApp` doby nečinnosti obslužnou rutinu, `DeleteTempMap` odstraní všechny dočasné `CImageList` objekty vytvořené [FromHandle](#fromhandle), ale nezničí všechny obslužné rutiny ( `hImageList`) dočasně související s `ImageList` objekty.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

Voláním této funkce se odpojit objektu seznamu obrázků z `CImageList` objektu.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro objekt seznamu obrázků.

### <a name="remarks"></a>Poznámky

Tato funkce vrací popisovač objektu seznamu obrázků.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::Attach](#attach).

##  <a name="dragenter"></a>  CImageList::DragEnter

Během operace přetažení, uzamkne aktualizace v okně určeného *pWndLock* a přetáhnout obrázek se zobrazí na určené pozici *bodu*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno vlastní obrázek přetažení.

*Bod*<br/>
Pozice, na který chcete zobrazit přetáhnout obrázek. Souřadnice jsou relativní vzhledem k levém horním rohu okna (ne klientské oblasti).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Souřadnice jsou relativní vzhledem k výšce levého horního rohu, takže šířku okna prvky, jako je například ohraničení, záhlaví a řádek nabídek, musí kompenzovat při zadávání souřadnice.

Pokud *pWndLock* má hodnotu NULL, tato funkce nakreslí obrázek v rámci zobrazení související s oknem klasické pracovní plochy a souřadnice jsou relativní vzhledem k levém horním rohu obrazovky.

Tato funkce uzamkne všechny aktualizace v daném okně během operace přetažení. Pokud je třeba provést jakékoli kreslení během operace přetažení, jako je například zvýraznění cíl operace přetažení myší, můžete dočasně skrýt Přetahované image pomocí [CImageList::DragLeave](#dragleave) funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::BeginDrag](#begindrag).

##  <a name="dragleave"></a>  CImageList::DragLeave

Odemkne v okně určeného *pWndLock* a skryje přetáhnout obrázek, což okna k aktualizaci.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parametry

*pWndLock*<br/>
Ukazatel na okno vlastní obrázek přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::EndDrag](#enddrag).

##  <a name="dragmove"></a>  CImageList::DragMove

Voláním této funkce přesunout obrázku, který je přetažen během operace přetažení myší.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
Nové umístění přetažení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána v reakci na zprávu wm_mousemove a. Chcete-li spustit operaci přetažení, použijte `BeginDrag` členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

Zobrazí nebo skryje přetáhnout obrázek během operace přetažení, bez nutnosti používat jenom v okně.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
Určuje, zda má být zobrazen přetáhnout obrázek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

[CImageList::DragEnter](#dragenter) funkce uzamkne všechny aktualizace v okně během operace přetažení. Tuto funkci, ale nepoužívejte zámky okno.

##  <a name="draw"></a>  CImageList::Draw

Voláním této funkce pro kreslení obrázku, který je přetažen během operace přetažení myší.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Ukazatel na kontextu cílového zařízení.

*nvybrán Nobrázek*<br/>
Z nuly vycházející index obrázku pro kreslení.

*PT*<br/>
Umístění, kam chcete-li nakreslit v rámci zadané zařízení.

*nStyle*<br/>
Příznak určující styl vykreslování. Může být jeden nebo více z těchto hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ILD_BLEND25 ILD_FOCUS|Nakreslí obrázek, prolnutí 25 procent barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masky.|
|ILD_BLEND50 ILD_SELECTED, ILD_BLEND|Nakreslí obrázek, prolnutí 50 procent barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznam obrázků neobsahuje masky.|
|ILD_MASK|Nakreslí masce.|
|ILD_NORMAL|Nakreslí obrázek barvou pozadí pro seznam obrázků. Pokud je barva pozadí CLR_NONE hodnotu, na obrázku je vykreslen transparentně masce.|
|ILD_TRANSPARENT|Nakreslí obrázek transparentně pomocí masky, bez ohledu na barvu pozadí.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>  CImageList::DrawEx

Nakreslí obrázek položky seznamu v rámci zadané zařízení.

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

*primární řadič domény*<br/>
Ukazatel na kontextu cílového zařízení.

*nvybrán Nobrázek*<br/>
Z nuly vycházející index obrázku pro kreslení.

*PT*<br/>
Umístění, kam chcete-li nakreslit v rámci zadané zařízení.

*Sz*<br/>
Velikost část obrázku, nakreslete vzhledem k levého horního rohu obrázku. Zobrazit *dx* a *dy* v [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*clrBk*<br/>
Barva pozadí bitové kopie. Zobrazit *rgbBk* v [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*clrFg*<br/>
Barva popředí bitové kopie. Zobrazit *rgbFg* v [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

*nStyle*<br/>
Příznak určující styl vykreslování. Zobrazit *fStyle* v [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Funkce používá zadané styl vykreslování a prolnutí bitovou kopii určenou barvou.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

Voláním této členské funkce vykreslení obrázku ze seznamu obrázků.

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
Ukazatel [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) strukturu, která obsahuje informace o operaci příkazu pro vykreslení.

*primární řadič domény*<br/>
Ukazatel na kontextu cílového zařízení. Je to nutné odstranit [CDC](../../mfc/reference/cdc-class.md) objektu, jakmile budete hotovi s ním.

*nvybrán Nobrázek*<br/>
Z nuly vycházející index image, které chcete kreslit.

*PT*<br/>
A [bodu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury obsahující souřadnic x a y – kde bude vykreslen na obrázku.

*Sz*<br/>
A [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktura určující velikost bitové kopie, které chcete kreslit.

*ptOrigin*<br/>
A [bodu](https://msdn.microsoft.com/library/windows/desktop/dd162805) struktury obsahující souřadnic x a y-zadání levý horní roh kreslení s ohledem na samotný obrázek. Nejsou vykreslit pixelů bitové kopie, které jsou nalevo souřadnice x a nad souřadnice na ose y.

*fStyle*<br/>
Příznak určující styl vykreslování a volitelně obrázků překrytí. V části poznámky informace na imagi překrytí. Výchozí implementace MFC ILD_NORMAL, kreslení obrázku barvou pozadí pro seznam obrázků. Pokud je barva pozadí CLR_NONE hodnotu, na obrázku je vykreslen transparentně masky.

Další možné styly jsou popsány v části *fStyle* člena [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury.

*dwRop*<br/>
Hodnota, která určuje rastrovou operaci kódu. Tyto kódy definovat, jak se budou kombinovat data o barvách pro zdrojového obdélníku barev dat pro cílového obdélníku k dosažení konečnou barvu. Výchozí implementace MFC, SRCCOPY, zkopíruje zdrojového obdélníku přímo do cílového obdélníku. Tento parametr se ignoruje, pokud *fStyle* parametr neobsahuje příznak ILD_ROP.

Další možné hodnoty jsou popsány v části *dwRop* člena [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury.

*rgbBack*<br/>
Obrázek barvu pozadí, ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaného aplikací nebo jednu z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva pozadí. Na obrázku je vykreslen barvu pozadí seznamu obrázků.|
|CLR_NONE|Bez barvy pozadí. Na obrázku je znázorněna transparentně.|

*rgbFore*<br/>
Barva popředí obrázku, ve výchozím nastavení CLR_DEFAULT. Tento parametr může být hodnota RGB definovaného aplikací nebo jednu z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|CLR_DEFAULT|Výchozí barva popředí. Na obrázku je vykreslen barvu zvýraznění systému jako barvu popředí.|
|CLR_NONE|Žádná blend. Na obrázku je v kombinaci s barvou kontextu cílového zařízení.|

Tento parametr se používá jenom v případě *fStyle* zahrnuje příznak ILD_BLEND25 nebo ILD_BLEND50.

*fState*<br/>
Příznak určující výkresu stavu. Tento člen může obsahovat jeden nebo více příznaků stav seznamu obrázků.

*Rámec*<br/>
Má vliv na chování saturate a alfa blending účinky.

Při použití s ILS_SATURATE, tento člen obsahuje hodnotu, která se přidá na každou komponentu barva RGB trojici pro každý pixel v ikonu.

Při použití s ILS_APLHA, tento člen obsahuje hodnotu alfa kanálu. Tato hodnota může být od 0 do 255, kde 0 je zcela transparentní a 255 se stane zcela neprůhledný.

*crEffect*<br/>
A [COLORREF](/windows/desktop/gdi/colorref) hodnota používaná pro efekty záře a stínu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud úspěšně vykreslením obrázku; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Použijte první verze, pokud chcete vyplnit struktura Win32 sami. Pokud chcete využít výhod jedné nebo více výchozích argumentů knihovny MFC nebo vyhnout Správa strukturu, použijte druhou verzi.

Překrytí image je obrázek, který je vykreslen na primární image zadanou v této členské funkce pomocí *nvybrán Nobrázek* parametru. Kreslení pomocí masky překrytí [nakreslit](#draw) členské funkce s indexem založen na jedničce masky překrytí určené vlastností [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) – makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

Voláním této funkce pro ukončení operace přetažení.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Poznámky

Chcete-li spustit operaci přetažení, použijte `BeginDrag` členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

Voláním této funkce vytváření ikony na základě bitovou kopii a její související maska v seznamu obrázků.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index bitové kopie.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony v případě úspěchu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato metoda závisí na chování [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) – makro vytvořit ikonu. Odkazovat [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) – makro pro další informace o vytvoření ikony a čištění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

Vrací ukazatel `CImageList` objektu, když je zadaný popisovač seznamu obrázků.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CImageList` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CImageList` už není připojen ke zpracování, dočasný `CImageList` objekt se vytvoří a připojí. Tento dočasný `CImageList` objektu je platný pouze dokud příště má aplikace čas nečinnosti v jeho smyčkou událostí, po kterém všechny dočasné objekty budou odstraněny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

Vrací ukazatel `CImageList` objektu, když je zadaný popisovač seznamu obrázků.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parametry

*hImageList*<br/>
Určuje seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CImageList` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CImageList` objekt není připojen ke popisovače, je vrácena hodnota NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

Volání této funkce načtete aktuální barvu pozadí pro seznam obrázků.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB `CImageList` objektu barvu pozadí.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>  CImageList::GetDragImage

Získá seznam dočasných obrázků, který se používá pro přetažení myší.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parametry

*lppoint –*<br/>
Adresa [bodu](https://msdn.microsoft.com/library/windows/desktop/dd162805) přetáhněte struktura, která přijímá aktuální pozici.

*lpPointHotSpot*<br/>
Adresa `POINT` struktura, která přijímá posun přetáhnout obrázek umístění přetažení.

### <a name="return-value"></a>Návratová hodnota

Pokud úspěšná, ukazatel na dočasných obrázků seznamu, který se používá pro přetažení myší; v opačném případě hodnota NULL.

##  <a name="getimagecount"></a>  CImageList::GetImageCount

Voláním této funkce načtete počet obrázků v seznamu obrázků.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet obrázků.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

Volání této funkce načtete informace o obrázku.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index bitové kopie.

*pImageInfo*<br/>
Ukazatel [IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo) struktura, která obdrží informace o imagi. Informace v této struktuře je možné přímo manipulovat s rastrové obrázky pro bitovou kopii.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

`IMAGEINFO` Struktura obsahuje informace o obrázku v seznamu obrázků.

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

Voláním této funkce načtete `m_hImageList` datový člen.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač seznamu přiloženého obrázku jinak hodnota NULL, pokud je připojen žádný objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

Popisovač seznamu obrázků, které jsou připojené k tomuto objektu.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Poznámky

`m_hImageList` Datový člen je veřejná proměnná typu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

Použití tohoto operátoru získat připojený popisovač `CImageList` objektu.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud úspěchu popisovač pro seznam obrázků reprezentována `CImageList` objektu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, která podporuje přímému použití objektu HIMAGELIST.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

Voláním této funkce pro čtení seznamu obrázků z archivu.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Ukazatel `CArchive` objektu, ze kterého je seznam obrázků pro čtení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

Voláním této funkce odeberte image z objektu seznamu obrázků.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index Image, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Všechny položky následující *nvybrán Nobrázek* teď přejít o jednu pozici dolů. Například pokud seznamu obrázků obsahuje dvě položky, odstranění první položky způsobí zbývající položky, která má být nyní na první pozici. *nvybrán Nobrázek*= 0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

Voláním této funkce k nahrazení obrázku v seznamu obrázků s novou bitovou kopii.

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

*nvybrán Nobrázek*<br/>
Z nuly vycházející index obrázku pro nahrazení.

*pbmImage*<br/>
Ukazatel na rastrový obrázek, který obsahuje bitovou kopii.

*pbmMask*<br/>
Ukazatel na rastrový obrázek s maskou. Pokud se žádná maska se používá s seznam obrázků, tento parametr je ignorován.

*hIcon*<br/>
Popisovač na ikonu, která obsahuje rastrového obrázku a maska pro nové image.

### <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, v případě úspěchu; verze vrácení BOOL jinak 0.

Verze vrácení **int** vrátí index založený na nule image případě úspěchu; jinak - 1.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce po volání [SetImageCount](#setimagecount) přiřadit nový, platný bitové kopie na zástupný symbol image čísla indexů.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CImageList::SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

Voláním této funkce nastavíte barvu pozadí pro seznam obrázků.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*znak CR*<br/>
Nastavit barvu pozadí. Může být CLR_NONE. V takovém případě bitové kopie jsou vykreslovány transparentně pomocí masky.

### <a name="return-value"></a>Návratová hodnota

Předchozí barva pozadí v případě úspěchu; jinak CLR_NONE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

Vytvoří novou image přetáhněte kombinací danou image (obvykle bitové kopie kurzoru myši) aktuální přetáhnout obrázek.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parametry

*nPokud*<br/>
Index novou bitovou kopii a nelze jej zkombinovat s přetáhnout obrázek.

*ptHotSpot*<br/>
Pozice aktivního bodu v rámci nové image.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, aby nový image používala přetahování funkce během operace přetažení, byste měli použít Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) skrýt skutečné myší po volání funkce `CImageList::SetDragCursorImage`. V opačném případě systém pravděpodobně mají dva ukazatele myši po dobu trvání operace přetažení.

##  <a name="setimagecount"></a>  CImageList::SetImageCount

Voláním této členské funkce resetování počet imagí v `CImageList` objektu.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parametry

*uNewCount*<br/>
Hodnota určující nové celkový počet imagí v seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Při volání této členské funkce lze zvýšit počet obrázků v seznamu obrázků, zavolejte [nahradit](#replace) pro každou další bitovou kopii nové indexy přiřadit platnou Image. Pokud indexy přiřadit platnou imagí, bude operace příkazu pro vykreslení, které vytvoření nových imagí nepředvídatelné.

Pokud snížení velikosti seznamu obrázků s použitím této funkce, jsou uvolněny zkrácený bitové kopie.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

Voláním této funkce z nuly vycházející index image přidat do seznamu imagí, které má být použit jako překrytí masky.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index Image, který se použije jako masku překrytí.

*nOverlay*<br/>
Index založený na jeden masky překrytí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Až čtyři indexů lze přidat do seznamu.

Masku překrytí je obrázek transparentně zaškrtnutí nakreslit přes jiný obrázek. Vykreslení masku překrytí přes bitovou kopii pomocí [CImageList::Draw](#draw) členské funkce s indexem založen na jedničce zadaná pomocí makra INDEXTOOVERLAYMASK maska překrytí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

Voláním této funkce k zápisu objektu seznamu image do archivu.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parametry

*pArchive*<br/>
Ukazatel `CArchive` objektu, ve kterém má být uložen seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)
