---
title: CImageList – třída | Microsoft Docs
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
ms.openlocfilehash: 54804ff4c6b2410aa47ea4d7cf5f5d3ab48316f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cimagelist-class"></a>CImageList – třída
Poskytuje funkci Windows ovládací prvek běžné seznamu obrázků.  
  
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
|[CImageList::Add](#add)|Přidá do seznamu obrázků bitovou kopii nebo bitové kopie.|  
|[CImageList::Attach](#attach)|Připojí k seznamu obrázků `CImageList` objektu.|  
|[CImageList::BeginDrag](#begindrag)|Zahájí přetahování bitovou kopii.|  
|[CImageList::Copy](#copy)|Zkopíruje bitovou kopii v rámci `CImageList` objektu.|  
|[CImageList::Create](#create)|Inicializuje seznamu obrázků a připojí jej k `CImageList` objektu.|  
|[CImageList::DeleteImageList](#deleteimagelist)|Odstraní seznamu obrázků.|  
|[CImageList::DeleteTempMap](#deletetempmap)|Volá [CWinApp](../../mfc/reference/cwinapp-class.md) doby nečinnosti obslužná rutina se odstranit všechny dočasné `CImageList` objekt vytvořený `FromHandle`.|  
|[CImageList::Detach](#detach)|Umožňuje odpojit objekt seznamu bitové kopie z `CImageList` objektu a vrátí popisovač do seznamu obrázků.|  
|[CImageList::DragEnter](#dragenter)|Uzamkne aktualizace během operace přetažení a zobrazí obrázek přetáhněte na zadané pozici.|  
|[CImageList::DragLeave](#dragleave)|Odemkne okna a skryje bitovou kopii přetažení, aby bylo možné aktualizovat okna.|  
|[CImageList::DragMove](#dragmove)|Přesune bitové kopie, který je právě přetáhli během operace přetažení myší.|  
|[CImageList::DragShowNolock](#dragshownolock)|Zobrazí nebo skryje bitovou kopii přetažení během operace přetažení, bez blokování okna.|  
|[CImageList::Draw](#draw)|Nakreslí obrázek, který je právě přetáhli během operace přetažení myší.|  
|[CImageList::DrawEx](#drawex)|Nakreslí obrázek položky seznamu v kontextu zadané zařízení. Funkce používá zadaný styl vykreslování a smíchá bitovou kopii určenou barvou.|  
|[CImageList::DrawIndirect](#drawindirect)|Nakreslí obrázek ze seznamu obrázků.|  
|[CImageList::EndDrag](#enddrag)|Ukončí operaci přetažení.|  
|[CImageList::ExtractIcon](#extracticon)|Vytvoří ikonu založené na bitové kopie a maska v seznamu obrázků.|  
|[CImageList::FromHandle](#fromhandle)|Vrátí ukazatel na `CImageList` objektu, pokud Zadaný popisovač do seznamu obrázků. Pokud `CImageList` objektu není připojený k popisovač dočasného `CImageList` objekt se vytvoří a připojené.|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Vrátí ukazatel na `CImageList` objektu, pokud Zadaný popisovač do seznamu obrázků. Pokud `CImageList` objektu není připojený k popisovač, **NULL** je vrácen.|  
|[CImageList::GetBkColor](#getbkcolor)|Načte aktuální barva pozadí pro seznamu obrázků.|  
|[CImageList::GetDragImage](#getdragimage)|Získá seznam dočasné bitové kopie, který se používá pro přetažení myší.|  
|[CImageList::GetImageCount](#getimagecount)|Načte množství obrázků v seznamu obrázků.|  
|[CImageList::GetImageInfo](#getimageinfo)|Načte informace o bitovou kopii.|  
|[CImageList::GetSafeHandle](#getsafehandle)|Načte **m_hImageList**.|  
|[CImageList::Read](#read)|Čte seznam obrázků z archivu.|  
|[CImageList::Remove](#remove)|Odebere bitovou kopii ze seznamu obrázků.|  
|[CImageList::Replace](#replace)|Nahrazuje obrázek v seznamu obrázků s novou bitovou kopii.|  
|[CImageList::SetBkColor](#setbkcolor)|Nastaví barvu pozadí seznamu obrázků.|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Vytvoří novou bitovou kopii přetažení.|  
|[CImageList::SetImageCount](#setimagecount)|Resetuje počet obrázků v seznamu obrázků.|  
|[CImageList::SetOverlayImage](#setoverlayimage)|Index založený na nule bitové kopie se přidá do seznamu obrázků má být použit jako masek překrytí.|  
|[CImageList::Write](#write)|Zapíše seznamu obrázků do archivu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Vrátí `HIMAGELIST` připojené k `CImageList`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|Obslužná rutina obsahující seznamu obrázků, který je připojen k tomuto objektu.|  
  
## <a name="remarks"></a>Poznámky  
 "Seznamu obrázků" je kolekce stejnou velikost bitové kopie, z nichž každý lze odkazovat jejím indexem. Seznamy obrázků umožňují efektivně spravovat velké sady ikony nebo bitmapy. Všechny Image v seznamu obrázků jsou obsažené v jednom široké rastrový obrázek ve formátu obrazovky zařízení. Seznam obrázků může také zahrnovat černobílý rastrového obrázku, který obsahuje masek použitý k vykreslení obrázků transparentně (ikona styl). Aplikace Microsoft Win32 programovací rozhraní (API), poskytuje funkce seznamu bitové kopie, které vám umožní kreslení bitové kopie, vytvořit destroy seznamů obrázků, přidat, odebrat bitové kopie, nahradit Image, sloučení bitové kopie a přetáhněte bitové kopie.  
  
 Tento ovládací prvek (a proto `CImageList` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Další informace o používání `CImageList`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí ovládacího prvku CImageList](../../mfc/using-cimagelist.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="add"></a>  CImageList::Add  
 Volání této funkce můžete přidat jeden nebo více bitových kopií nebo ikonu do seznamu obrázků.  
  
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
 `pbmImage`  
 Ukazatel na rastrový obrázek obsahující bitové kopie nebo bitové kopie. Počet bitových kopií je odvozeno z šířka rastrového obrázku.  
  
 `pbmMask`  
 Ukazatel na rastrový obrázek s maskou. Pokud žádné maska používá s seznamu obrázků, tento parametr je ignorován.  
  
 `crMask`  
 Barva použitá ke generování maska. Každý pixel tato barva v dané rastrového obrázku se změní na černé a příslušné bity maska nastaven na jednu.  
  
 `hIcon`  
 Popisovač ikonu, která obsahuje rastrového obrázku a maska pro novou bitovou kopii.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nule první novou bitovou kopii v případě úspěšného; jinak - 1.  
  
### <a name="remarks"></a>Poznámky  
 Jste zodpovědní za uvolnění popisovač ikonu, když jste hotovi s ním.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="attach"></a>  CImageList::Attach  
 Volání této funkce pro připojení k seznamu obrázků `CImageList` objektu.  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Popisovač pro objekt seznamu bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud přílohu byla úspěšná. jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="begindrag"></a>  CImageList::BeginDrag  
 Volání této funkce zahájíte přetahování bitovou kopii.  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie a přetáhněte nule.  
  
 `ptHotSpot`  
 Souřadnice přetáhněte pozice (obvykle pozice kurzoru). Souřadnice jsou relativní vzhledem k levém horním rohu bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vytvoří seznam dočasné bitové kopie, který se používá pro přetažení myší. Obrázek kombinuje zadanou bitovou kopii a maska s aktuální kurzor. V odpovědi na následné `WM_MOUSEMOVE` zprávy, přetáhněte image můžete přesouvat pomocí `DragMove` – členská funkce. Pro ukončení operace přetažení, můžete použít `EndDrag` – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="cimagelist"></a>  CImageList::CImageList  
 Vytvoří `CImageList` objektu.  
  
```  
CImageList();
```  
  
##  <a name="copy"></a>  CImageList::Copy  
 Tato funkce člen implementuje chování funkce Win32 [ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520), jak je popsáno v sadě Windows SDK.  
  
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
 *iDst*  
 Index založený na nule bitové kopie, který se má použít jako cíl operace kopírování.  
  
 `iSrc`  
 Index založený na nule bitové kopie má být použit jako zdroj kopírování.  
  
 `uFlags`  
 Bitová hodnota příznak, který určuje typ operace kopírování má být provedeno. Tento parametr může být jedna z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`ILCF_MOVE`|Zdrojová bitová kopie se zkopíruje na cílový obrázek indexu. Tato operace má za následek více instancí danou bitovou kopii. `ILCF_MOVE` je výchozí.|  
|`ILCF_SWAP`|Bitové kopie zdrojové a cílové exchange pozice v seznamu obrázků.|  
  
 `pSrc`  
 Ukazatel na `CImageList` objekt, který je cílem operace kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="create"></a>  CImageList::Create  
 Inicializuje seznamu obrázků a připojí jej k [CImageList](../../mfc/reference/cimagelist-class.md) objektu.  
  
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
 `cx`  
 Dimenze každý obrázku v pixelech.  
  
 `cy`  
 Dimenze každý obrázku v pixelech.  
  
 `nFlags`  
 Určuje typ seznamu obrázků k vytvoření. Tento parametr může být kombinací těchto hodnot, ale může obsahovat pouze jeden z `ILC_COLOR` hodnoty.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`ILC_COLOR`|Použije výchozí chování, pokud žádná z dalších `ILC_COLOR`* příznaky je zadán. Výchozí hodnota je obvykle `ILC_COLOR4`; ale pro starší ovladače zobrazení, výchozí hodnota je `ILC_COLORDDB`.|  
|`ILC_COLOR4`|Použijte oddíl 4-bit (16 barevný) device independent bitmap (DIB) jako bitové mapy pro seznamu obrázků.|  
|`ILC_COLOR8`|Pomocí 8bitové DIB části. Barvy používané pro tabulky barev jsou stejné barvy jako palety polotónování.|  
|`ILC_COLOR16`|Použít 16 bitů (32/64 tisíc barvu) DIB části.|  
|`ILC_COLOR24`|Použijte oddíl DIB 24 bitů.|  
|`ILC_COLOR32`|Použijte oddíl DIB 32-bit.|  
|`ILC_COLORDDB`|Použijte bitovou mapu závislé na zařízení.|  
|`ILC_MASK`|Používá masku. Seznam obrázků obsahuje dvě bitové mapy, z nichž jeden je Černobílý rastr použít jako masku. Pokud tuto hodnotu nezadáte, seznamu obrázků obsahuje pouze jeden rastrového obrázku. V tématu [vykreslování obrázků ze seznamu obrázků](../../mfc/drawing-images-from-an-image-list.md) Další informace o maskované bitové kopie.|  
  
 `nInitial`  
 Počet bitové kopie, které původně obsahuje seznamu obrázků.  
  
 `nGrow`  
 Počet obrázků, které můžou růst seznamu obrázků, když je potřeba změnit velikost seznamu, aby uvolnil prostor pro nové bitové kopie systému. Tento parametr představuje počet nových bitových kopií, které může obsahovat seznam změněnou obrázků.  
  
 `nBitmapID`  
 ID prostředků bitmapy přidruženou seznamu obrázků.  
  
 `crMask`  
 Barva použitá ke generování masku. Každý pixel tato barva v zadaný rastrový obrázek se změní na černé a příslušné bity maska nastaven na jednu.  
  
 `lpszBitmapID`  
 Řetězec obsahující ID obrazů prostředků.  
  
 `imagelist1`  
 Odkaz na `CImageList` objektu.  
  
 `nImage1`  
 Index prvního existující bitová kopie.  
  
 `imagelist2`  
 Odkaz na `CImageList` objektu.  
  
 `nImage2`  
 Index druhý existující bitová kopie.  
  
 `dx`  
 Posun osy x druhý bitové kopie ve vztahu k první obrázku v pixelech.  
  
 `dy`  
 Posun osy y druhý bitové kopie ve vztahu k první obrázku v pixelech.  
  
 `pImageList`  
 Ukazatel na `CImageList` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CImageList` ve dvou krocích. Nejprve volat konstruktor a pak zavolají `Create`, který vytvoří seznamu obrázků a připojí jej k `CImageList` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList  
 Volání této funkce se odstranit seznamu obrázků.  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap  
 Volá se automaticky `CWinApp` doby nečinnosti obslužnou rutinu, `DeleteTempMap` odstraní všechny dočasné `CImageList` objekty vytvořené [FromHandle](#fromhandle), ale nezničí všechny popisovače ( `hImageList`) dočasně přidružené pomocí **ImageList** objekty.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="detach"></a>  CImageList::Detach  
 Volání této funkce se odpojit objekt seznamu bitové kopie z `CImageList` objektu.  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt seznamu bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vrací popisovač objektu seznamu bitové kopie.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::Attach](#attach).  
  
##  <a name="dragenter"></a>  CImageList::DragEnter  
 Během operace přetažení, zamkne aktualizace do okna určeného `pWndLock` a zobrazí obrázek přetáhněte na pozici určeného `point`.  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndLock`  
 Ukazatel na okno vlastní obrázek přetažení.  
  
 `point`  
 Pozice, kdy má být umožňuje zobrazit obrázek přetažení. Souřadnice jsou relativní vzhledem k levém horním rohu okna (ne klientské oblasti).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou relativní vzhledem k okně na levém horním rohu, takže šířek okno prvky, jako jsou například ohraničení, záhlaví a řádku nabídek musí kompenzovat při zadávání souřadnice.  
  
 Pokud `pWndLock` je **NULL**, tato funkce nakreslí obrázek v kontextu zobrazení související s okně plochy a souřadnice jsou relativní vzhledem k levém horním rohu obrazovky.  
  
 Tato funkce zamkne všechny další aktualizace do daného okna během operace přetažení. Pokud je potřeba udělat všechny kreslení během operace přetažení, jako je například zvýraznění cíl operace přetahování myší, dočasně můžete skrýt taženou bitové kopie, pomocí [CImageList::DragLeave](#dragleave) funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::BeginDrag](#begindrag).  
  
##  <a name="dragleave"></a>  CImageList::DragLeave  
 Odemkne okna určeného `pWndLock` a skryje obrázek přetažení, povolení okno na aktualizovat.  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndLock`  
 Ukazatel na okno vlastní obrázek přetažení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::EndDrag](#enddrag).  
  
##  <a name="dragmove"></a>  CImageList::DragMove  
 Volání této funkce přesunout bitovou kopii, která je právě přetáhli během operace přetažení myší.  
  
```  
static BOOL PASCAL DragMove(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Nové přetáhněte pozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle v reakci `WM_MOUSEMOVE` zprávy. Chcete-li zahájit operaci přetažení, použijte `BeginDrag` – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="dragshownolock"></a>  CImageList::DragShowNolock  
 Zobrazí nebo skryje bitovou kopii přetažení během operace přetažení, bez blokování okna.  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Určuje, jestli přetažení obrázku je zobrazený.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 [CImageList::DragEnter](#dragenter) funkce zamkne všechny aktualizace do okna během operace přetažení. Tuto funkci však nezamyká okna.  
  
##  <a name="draw"></a>  CImageList::Draw  
 Volání této funkce kreslení obrázku, který je právě přetáhli během operace přetažení myší.  
  
```  
BOOL Draw(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext cílové zařízení.  
  
 `nImage`  
 Index bitové kopie k vykreslení nule.  
  
 `pt`  
 Umístění, kam chcete kreslení v rámci zadaného zařízení.  
  
 `nStyle`  
 Příznak určující styl vykreslování. Může být jeden nebo více z těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`ILD_BLEND25`, **ILD_FOCUS**|Nakreslí obrázek, prolnutí 25 procent barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznamu obrázků neobsahuje masku.|  
|`ILD_BLEND50`, **ILD_SELECTED**, **ILD_BLEND**|Nakreslí obrázek, prolnutí 50 procent barvou zvýraznění systému. Tato hodnota nemá žádný vliv, pokud seznamu obrázků neobsahuje masku.|  
|**ILD_MASK**|Nakreslí maska.|  
|`ILD_NORMAL`|Nakreslí obrázek pomocí barvu pozadí pro seznamu obrázků. Pokud je barva pozadí `CLR_NONE` hodnotu, bitovou kopii je vykresleno transparentně pomocí masky.|  
|`ILD_TRANSPARENT`|Nakreslí obrázek transparentně pomocí maska, bez ohledu na barvu pozadí.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::SetOverlayImage](#setoverlayimage).  
  
##  <a name="drawex"></a>  CImageList::DrawEx  
 Nakreslí obrázek položky seznamu v kontextu zadané zařízení.  
  
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
 `pDC`  
 Ukazatel na kontext cílové zařízení.  
  
 `nImage`  
 Index bitové kopie k vykreslení nule.  
  
 `pt`  
 Umístění, kam chcete kreslení v rámci zadaného zařízení.  
  
 `sz`  
 Velikost část bitovou kopii k vykreslení relativně k levém horním rohu bitové kopie. V tématu `dx` a *dy* v [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) ve Windows SDK.  
  
 *clrBk*  
 Barva pozadí bitovou kopii. V tématu *rgbBk* v [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) ve Windows SDK.  
  
 *clrFg*  
 Barvu popředí bitové kopie. V tématu *rgbFg* v [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) ve Windows SDK.  
  
 `nStyle`  
 Příznak určující styl vykreslování. V tématu *fStyle* v [ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce používá zadaný styl vykreslování a smíchá bitovou kopii určenou barvou.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="drawindirect"></a>  CImageList::DrawIndirect  
 Volání této funkce člen kreslení obrázku ze seznamu obrázků.  
  
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
 *pimldp*  
 Ukazatel na [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktura, která obsahuje informace o operaci kreslení.  
  
 `pDC`  
 Ukazatel na kontext cílové zařízení. To je nutné odstranit [CDC](../../mfc/reference/cdc-class.md) objektu až skončíte s ním.  
  
 `nImage`  
 Index založený na nule bitové kopie, které se mají vykreslovat.  
  
 `pt`  
 A [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura obsahující souřadnic x a y-místo, kde bude vykreslovat bitovou kopii.  
  
 `sz`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která určuje velikost bitové kopie, které se mají vykreslovat.  
  
 *ptOrigin*  
 A [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura obsahující souřadnic x a y-zadání levém horním rohu kreslení operace s ohledem na bitovou kopii sám sebe. Nejsou vykresluje pixelů bitové kopie, které jsou vlevo souřadnice x a výše souřadnici y.  
  
 `fStyle`  
 Příznak určující styl vykreslování a volitelně bitovou kopii překrytí. Najdete v části poznámky informace na bitovou kopii překrytí. Výchozí implementace MFC `ILD_NORMAL`, nakreslí obrázek pomocí barvu pozadí pro seznamu obrázků. Pokud je barva pozadí `CLR_NONE` hodnotu, bitovou kopii je vykresleno transparentně pomocí masky.  
  
 Další možné styly jsou popsané v části **fStyle** členem [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury.  
  
 *dwRop*  
 Hodnota, která určuje kód rastrové operace. Tyto kódy definovat, jak data barvu pro rámeček zdroj bude sloučen s barva data pro cílové rámeček k dosažení konečného barvu. MFC pro výchozí implementace, **SRCCOPY**, zkopíruje rámeček zdroj přímo do cílového rámeček. Tento parametr je ignorována, pokud `fStyle` parametr nezahrnuje **ILD_ROP** příznak.  
  
 Další možné hodnoty jsou popsané v části **dwRop** členem [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury.  
  
 *rgbBack*  
 Barva pozadí obrázku, ve výchozím nastavení `CLR_DEFAULT`. Tento parametr může být hodnotu RGB definované aplikací nebo jeden z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`CLR_DEFAULT`|Výchozí barvu pozadí. Bitovou kopii jsou vykresleny barvou pozadí seznamu bitové kopie.|  
|`CLR_NONE`|Žádné barvu pozadí. Obrázek se vykresluje transparentně.|  
  
 *rgbFore*  
 Obrázek barvu popředí, ve výchozím nastavení `CLR_DEFAULT`. Tento parametr může být hodnotu RGB definované aplikací nebo jeden z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`CLR_DEFAULT`|Výchozí barvu popředí. Obrázek je vykreslovány pomocí Barva zvýraznění systému jako barvu popředí.|  
|`CLR_NONE`|Barva žádné blend. Obrázek je smíšení barvou kontextu cílové zařízení.|  
  
 Tento parametr se používá pouze v případě `fStyle` zahrnuje `ILD_BLEND25` nebo `ILD_BLEND50` příznak.  
  
 *fState*  
 Příznak určující kreslení stavu. Tento člen může obsahovat jeden nebo více příznaků stavu seznamu bitové kopie.  
  
 *Rámec*  
 Má vliv na chování saturate a prolnutí alfa účinky.  
  
 Při použití s **ILS_SATURATE**, tento člen obsahuje hodnotu, která je přičtena ke každé barva součást trojdílná RGB pro každý pixelů v ikonu.  
  
 Při použití s **ILS_APLHA**, tento člen obsahuje hodnotu pro alfa kanálu. Tato hodnota může být od 0 do 255, kde 0 je zcela transparentní a 255 se zcela neprůhledný.  
  
 *crEffect*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnota používaná pro záře a stínové účinky.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud bitová kopie je úspěšně vykresleného; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k vyplnění strukturu Win32 sami, použijte první verzi. Druhá verze použijte, pokud chcete využít výhod jeden nebo více argumentů výchozí knihovny MFC nebo zabránění jejímu provedení Správa strukturu.  
  
 Překrytí obrázek je obrázek, který je vykreslen nad primární bitovou kopii, zadaný ve funkci tento člen ve `nImage` parametr. Kreslení pomocí masky překrytí [kreslení](#draw) – členská funkce s index na základě jedné zadaná pomocí maska překrytí [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) – makro.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="enddrag"></a>  CImageList::EndDrag  
 Volání této funkce pro ukončení operace přetažení.  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zahájit operaci přetažení, použijte `BeginDrag` – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="extracticon"></a>  CImageList::ExtractIcon  
 Volání této funkce vytváření ikony na základě image a její související maska v seznamu obrázků.  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač na ikonu v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je založena na chování [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) makro vytvořit ikonu. Odkazovat [ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401) makro Další informace o vytváření ikonu a čištění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="fromhandle"></a>  CImageList::FromHandle  
 Vrátí ukazatel na `CImageList` objektu, pokud Zadaný popisovač do seznamu obrázků.  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Určuje seznam obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CImageList` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CImageList` již není připojen k popisovač dočasného `CImageList` objekt se vytvoří a připojené. Toto dočasný `CImageList` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho smyčky událostí, které během všechny dočasné objekty jsou odstraněny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent  
 Vrátí ukazatel na `CImageList` objektu, pokud Zadaný popisovač do seznamu obrázků.  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `hImageList`  
 Určuje seznam obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CImageList` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CImageList` objektu není připojený k popisovač, **NULL** je vrácen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="getbkcolor"></a>  CImageList::GetBkColor  
 Volání této funkce načíst aktuální barva pozadí pro seznamu obrázků.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota Barva RGB `CImageList` objektu barvu pozadí.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::SetBkColor](#setbkcolor).  
  
##  <a name="getdragimage"></a>  CImageList::GetDragImage  
 Získá seznam dočasné bitové kopie, který se používá pro přetažení myší.  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoint`  
 Adresa [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) přetáhněte struktura, která přijímá aktuální pozici.  
  
 *lpPointHotSpot*  
 Adresa **bodu** struktura, která přijímá posun bitovou kopii přetáhněte vzhledem ke přetáhněte pozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, ukazatel na bitovou kopii dočasný seznam, který se používá pro přetažení; v opačném **NULL**.  
  
##  <a name="getimagecount"></a>  CImageList::GetImageCount  
 Volání této funkce se načíst počet obrázků v seznamu obrázků.  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet obrázků.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::ExtractIcon](#extracticon).  
  
##  <a name="getimageinfo"></a>  CImageList::GetImageInfo  
 Volání této funkce k načtení informací o bitovou kopii.  
  
```  
BOOL GetImageInfo(
    int nImage,  
    IMAGEINFO* pImageInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie nule.  
  
 *pImageInfo*  
 Ukazatel na [IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393) struktura, která přijímá informace o bitové kopii. Informace v této struktuře lze přímo upravit bitmap pro bitovou kopii.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `IMAGEINFO` Struktura obsahuje informace o obrázku v seznamu obrázků.  
  
##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle  
 Volání této funkce můžete získat **m_hImageList** – datový člen.  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro připojené image seznamu; v opačném případě **NULL** Pokud je připojen žádný objekt.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="m_himagelist"></a>  CImageList::m_hImageList  
 Popisovač seznamu obrázků, který je připojen k tomuto objektu.  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>Poznámky  
 **M_hImageList** – datový člen je veřejné proměnné typu `HIMAGELIST`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST  
 Tento operátor. použijte k získání připojené popisovač `CImageList` objektu.  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro seznamu obrázků reprezentována `CImageList` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití `HIMAGELIST` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="read"></a>  CImageList::Read  
 Volání této funkce čtení seznamu obrázků z archivu.  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parametry  
 `pArchive`  
 Ukazatel na `CArchive` objekt, ze kterého má být čtení seznamu obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
##  <a name="remove"></a>  CImageList::Remove  
 Volání této funkce můžete odebrat bitovou kopii z objektu seznamu bitové kopie.  
  
```  
BOOL Remove(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie k odebrání nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Všechny položky následující `nImage` nyní přesunout o jednu pozici dolů. Například pokud seznamu obrázků obsahuje dvě položky, odstranění první položka způsobí, že zbývající položka, která má být nyní v první pozici. `nImage`= 0 pro položky v první pozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="replace"></a>  CImageList::Replace  
 Volání této funkce můžete nahradit novou bitovou kopii obrázku v seznamu obrázků.  
  
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
 `nImage`  
 Index bitové kopie a nahraďte nule.  
  
 `pbmImage`  
 Ukazatel na rastrový obrázek, který obsahuje bitovou kopii.  
  
 `pbmMask`  
 Ukazatel na rastrový obrázek s maskou. Pokud žádné maska používá s seznamu obrázků, tento parametr je ignorován.  
  
 `hIcon`  
 Popisovač pro ikonu, která obsahuje rastrového obrázku a maska pro novou bitovou kopii.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácení verze **BOOL** vrátí nenulové hodnoty, pokud úspěšná, jinak hodnota 0.  
  
 Vrácení verze `int` vrátí index o základu 0 bitové kopie, pokud úspěšná, jinak hodnota - 1.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen po volání [SetImageCount](#setimagecount) přiřadit nový, platný bitové kopie na zástupný symbol obrázku čísla indexů.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CImageList::SetImageCount](#setimagecount).  
  
##  <a name="setbkcolor"></a>  CImageList::SetBkColor  
 Volejte tuto funkci nastavit barvu pozadí seznamu obrázků.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 `cr`  
 Barva pozadí nastavit. Může být `CLR_NONE`. V takovém případě bitové kopie jsou vykreslovány transparentně pomocí masky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí barva pozadí v případě úspěšného; v opačném případě `CLR_NONE`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage  
 Vytvoří novou bitovou kopii přetáhněte kombinací bitovou kopii daného (obvykle bitové kopie kurzor myši) s aktuální image přetažení.  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>Parametry  
 *nDrag*  
 Index novou bitovou kopii a nelze jej zkombinovat s bitovou kopií přetažení.  
  
 `ptHotSpot`  
 Pozice aktivního bodu v rámci novou bitovou kopii.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Protože přetahování funkce nový image používala během operace přetažení, měli byste používat Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) funkce skrytí skutečné myší po volání `CImageList::SetDragCursorImage`. Jinak systému může pravděpodobně dva ukazatele myši po dobu trvání operace přetažení.  
  
##  <a name="setimagecount"></a>  CImageList::SetImageCount  
 Volání této funkce člen resetovat počet obrázků v `CImageList` objektu.  
  
```  
BOOL SetImageCount(UINT uNewCount);
```  
  
### <a name="parameters"></a>Parametry  
 *uNewCount*  
 Hodnota určující nové celkový počet bitové kopie v seznamu obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je volání této funkce člen a zvýšit počet obrázků v seznamu obrázků, zavolejte [nahradit](#replace) každé další bitové kopie přiřadit nové indexy platný bitové kopie. Pokud žádnou indexy přiřadit platný bitové kopie, budou kreslení operace, které vytvoříte nové bitové nepředvídatelné.  
  
 Pokud snížit velikost seznamu obrázků s použitím této funkce jsou uvolněny zkrácený bitové kopie.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage  
 Volání této funkce můžete přidat index založený na nule bitové kopie do seznamu obrázků má být použit jako masek překrytí.  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie a použít jako masku překrytí nule.  
  
 *nOverlay*  
 Na základě jeden index maska překrytí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Až čtyři indexy, které lze přidat do seznamu.  
  
 Překrytí maska je obrázek, který vykresluje transparentně přes jiné image. Zakreslit masku překrytí nad bitovou kopii pomocí [CImageList::Draw](#draw) – členská funkce s index na základě jedné zadaná pomocí maska překrytí **INDEXTOOVERLAYMASK** – makro.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="write"></a>  CImageList::Write  
 Volání této funkce k zápisu objektu seznamu bitové kopie do archivu.  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>Parametry  
 `pArchive`  
 Ukazatel na `CArchive` objektu, ve kterém má být uložena seznamu obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CListCtrl – třída](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)
