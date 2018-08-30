---
title: Třída CRgn | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
dev_langs:
- C++
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ac334221f22dcd80434c1be2f59998709aae5e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204877"
---
# <a name="crgn-class"></a>Crgn – třída
Zapouzdřuje oblast rozhraní GDI systému Windows grafiky zařízení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn)|Vytvoří `CRgn` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRgn::CombineRgn](#combinergn)|Nastaví `CRgn` objektu tak, aby je ekvivalentní k sjednocení dvou zadaný `CRgn` objekty.|  
|[CRgn::CopyRgn](#copyrgn)|Nastaví `CRgn` objektu tak, že jde o kopii zadaného `CRgn` objektu.|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializuje `CRgn` objektu s elipsy oblastí.|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializuje `CRgn` objekt elipsy oblast určené [RECT](../../mfc/reference/rect-structure1.md) struktury.|  
|[CRgn::CreateFromData](#createfromdata)|Vytvoří z dané oblasti a transformace dat v oblasti.|  
|[CRgn::CreateFromPath](#createfrompath)|Vytvoří oblast cesty, který je vybraný v kontextu daného zařízení.|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializuje `CRgn` objektu s mnohoúhelníkové oblastí. Systém mnohoúhelníku se automaticky zavře, v případě potřeby kreslením řádku od posledního vrcholu první.|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializuje `CRgn` objektu s oblastí, který se skládá z řady uzavřené mnohoúhelníky. Může být polygonů nesouvislý, nebo mohou překrývat.|  
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializuje `CRgn` objekt s obdélníková oblast.|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializuje `CRgn` objekt s obdélníková oblast určené [RECT](../../mfc/reference/rect-structure1.md) struktury.|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializuje `CRgn` objekt s oblasti obdélníkový zaoblené rohy.|  
|[CRgn::EqualRgn](#equalrgn)|Zkontroluje dvě `CRgn` objekty k určení, zda jsou ekvivalentní.|  
|[CRgn::FromHandle](#fromhandle)|Vrací ukazatel `CRgn` objektu, když je zadaný popisovač do oblasti Windows.|  
|[CRgn::GetRegionData](#getregiondata)|Vyplní zadané vyrovnávací paměti dat popisující příslušnou oblast.|  
|[CRgn::GetRgnBox](#getrgnbox)|Načte souřadnice ohraničující obdélník `CRgn` objektu.|  
|[CRgn::OffsetRgn](#offsetrgn)|Přesune `CRgn` objektu zadaných odsazení.|  
|[CRgn::PtInRegion](#ptinregion)|Určuje, zda zadaný bod nachází v oblasti.|  
|[CRgn::RectInRegion](#rectinregion)|Určuje, zda jakékoliv části obdélníku zadaného v rámci hranic vytyčených oblast.|  
|[CRgn::SetRectRgn](#setrectrgn)|Nastaví `CRgn` objekt do zadané oblasti obdélníkový.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRgn::operator HRGN](#operator_hrgn)|Vrátí popisovač Windows, součástí `CRgn` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Oblast je oblast elipsy nebo mnohoúhelníku v rámci časového období. Použití oblastí pomocí členské funkce třídy `CRgn` s funkcí oříznutí definovaných jako členy třídy `CDC`.  
  
 Členské funkce `CRgn` vytvářet, měnit a načítání informací o objektu oblasti, pro které se nazývají.  
  
 Další informace o používání `CRgn`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cgdiobject –](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="combinergn"></a>  CRgn::CombineRgn  
 Vytvoří novou oblast GDI kombinací dvou stávajících oblastí.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>Parametry  
 *pRgn1*  
 Určuje existující oblasti.  
  
 *pRgn2*  
 Určuje existující oblasti.  
  
 *nCombineMode*  
 Určuje operaci, která mají být provedeny při sloučení dvou zdrojových oblastí. To může být jedna z následujících hodnot:  
  
- RGN_AND používá překrývajících se oblastí obě oblasti (průnik).  
  
- RGN_COPY vytvoří kopii oblast 1 (identifikovaný *pRgn1*).  
  
- Vytvoří RGN_DIFF oblasti skládající se z oblasti oblast 1 (identifikovaný *pRgn1*), které nejsou součástí oblasti 2 (identifikovaný *pRgn2*).  
  
- RGN_OR kombinuje obě oblasti v plné výši (sjednocení).  
  
- RGN_XOR kombinuje obě oblasti, ale odebere překrývající se oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ výsledný oblasti. Může být jeden z následujících hodnot:  
  
- COMPLEXREGION nové oblasti obsahuje překrývající se hranice.  
  
- Došlo k CHYBĚ vytvořeny žádné nové oblasti.  
  
- NULLREGION nové oblasti je prázdný.  
  
- SIMPLEREGION novou oblast nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Jsou zkombinované v oblastech podle *nCombineMode*.  
  
 Dvě zadané oblasti jsou zkombinované a výsledné popisovač oblast je uložen v `CRgn` objektu. Díky tomu se jakékoli oblasti je uložen v `CRgn` objekt je nahrazen kombinované oblasti.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Použití [CopyRgn](#copyrgn) jednoduše zkopírovat jedné oblasti do jiné oblasti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>  CRgn::CopyRgn  
 Zkopíruje oblasti definované *pRgnSrc* do `CRgn` objektu.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *pRgnSrc*  
 Určuje existující oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ výsledný oblasti. Může být jeden z následujících hodnot:  
  
- COMPLEXREGION nové oblasti obsahuje překrývající se hranice.  
  
- Došlo k CHYBĚ vytvořeny žádné nové oblasti.  
  
- NULLREGION nové oblasti je prázdný.  
  
- SIMPLEREGION novou oblast nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Nahradí oblasti dříve uložené v nové oblasti `CRgn` objektu. Tato funkce je zvláštním případem [CombineRgn](#combinergn) členskou funkci.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn  
 Vytvoří elipsy oblasti.  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 *x1*  
 Určuje logickou souřadnici x levého horního rohu ohraničující obdélník na tři tečky.  
  
 *Y1*  
 Určuje logickou souřadnici y levého horního rohu ohraničující obdélník na tři tečky.  
  
 *x2*  
 Určuje logickou souřadnici x pravého dolního rohu ohraničující obdélník na tři tečky.  
  
 *y2*  
 Určuje logickou souřadnici y pravého dolního rohu ohraničující obdélník na tři tečky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Oblast je definován ohraničující obdélník určené *x1*, *y1*, *x2*, a *y2*. Oblast je uložen v `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Po dokončení použít oblast vytvořené pomocí `CreateEllipticRgn` funkce, aplikace by měla vyberte oblast si tohoto kontextu zařízení a `DeleteObject` funkce jeho odstranění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect  
 Vytvoří elipsy oblasti.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje `RECT` struktury nebo `CRect` objekt, který obsahuje logické souřadnice levého a pravého dolního rohu ohraničující obdélník na tři tečky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V oblasti určené struktury nebo objekt, na které odkazuje *lprect –* a je uložen v `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Po dokončení použít oblast vytvořené pomocí `CreateEllipticRgnIndirect` funkce, aplikace by měla vyberte oblast si tohoto kontextu zařízení a `DeleteObject` funkce jeho odstranění.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).  
  
##  <a name="createfromdata"></a>  CRgn::CreateFromData  
 Vytvoří z dané oblasti a transformace dat v oblasti.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpXForm*  
 Odkazuje na [xform –](../../mfc/reference/xform-structure.md) datová struktura, která definuje transformaci provést v oblasti. Pokud tento ukazatel je NULL, použije se identita transformaci.  
  
 *nCount*  
 Určuje počet bajtů, na které odkazuje *pRgnData*.  
  
 *pRgnData*  
 Odkazuje [rgndata –](../../mfc/reference/rgndata-structure.md) datová struktura, která obsahuje data oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace může načíst data pro určitou oblast voláním `CRgn::GetRegionData` funkce.  
  
##  <a name="createfrompath"></a>  CRgn::CreateFromPath  
 Vytvoří oblast cesty, který je vybraný v kontextu daného zařízení.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 *primární řadič domény*  
 Určuje kontext zařízení, který obsahuje uzavřené cestu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Kontext zařízení identifikován *primárního řadiče domény* parametr musí obsahovat uzavřené cestu. Po `CreateFromPath` převede cestu do oblasti, Windows zahodí uzavřené cestu z kontextu zařízení.  
  
##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn  
 Vytvoří mnohoúhelníkové oblasti.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>Parametry  
 *lpPoints*  
 Odkazuje na pole `POINT` struktury nebo pole `CPoint` objekty. Každá struktura určuje souřadnice x a y jednoho vrcholu mnohoúhelníku. `POINT` Struktura má následující formát:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 *nCount*  
 Určuje počet `POINT` struktury nebo `CPoint` objektů v poli odkazované *lpPoints*.  
  
 *nMode*  
 Určuje režim vyplnění oblasti. Tento parametr může být alternativní nebo zrušení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Systém mnohoúhelníku se automaticky zavře, v případě potřeby kreslením řádku od posledního vrcholu první. Výsledný oblasti je uložen v `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 ALTERNATIVNÍ při vyplňování mnohoúhelníku režimu systému vyplní oblast mezi stran lichými čísly a sudým číslem mnohoúhelníku na každém řádku kontroly. To znamená, že systém vyplní oblast mezi první a druhé straně, mezi třetí a čtvrtá straně a tak dále.  
  
 Když je režim vyplnění mnohoúhelníku zrušení, systém použije směr, ve kterém byl nakreslen elementu figure k určení, jestli k vyplnění oblasti. Každý úsek čáry v mnohoúhelník je vykreslen v po směru nebo proti směru hodinových ručiček. Pokaždé, když se z uzavřených oblasti vykreslit vnější elementu figure čárou prochází po směru hodinových ručiček čárového segmentu, počet se zvýší. Když řádku prochází proti směru hodinových ručiček čárového segmentu, je snížen počet. Oblast je vyplněna, pokud je počet nenulové dosáhne řádku mimo na obrázku.  
  
 Když aplikace dokončí použít oblast vytvořené pomocí `CreatePolygonRgn` funkce, ji by měl vyberte oblast si tohoto kontextu zařízení a `DeleteObject` funkce jeho odstranění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn  
 Vytvoří oblasti, který se skládá z řady uzavřené mnohoúhelníky.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parametry  
 *lpPoints*  
 Odkazuje na pole `POINT` struktury nebo pole `CPoint` objekty, které definuje vrcholy polygonů. Každého mnohoúhelníku musí explicitně ukončeno, protože je systém automaticky nezavře. Polygonů zadávají postupně. `POINT` Struktura má následující formát:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 *lpPolyCounts*  
 Odkazuje na pole celých čísel. První celé číslo určuje počet vrcholů v první mnohoúhelníku ve *lpPoints* pole, druhý celé číslo určuje počet vrcholů v druhé mnohoúhelníků a tak dále.  
  
 *nCount*  
 Určuje celkový počet celých čísel v *lpPolyCounts* pole.  
  
 *nPolyFillMode*  
 Určuje režim vyplnění mnohoúhelníku. Tato hodnota může být alternativní nebo zrušení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výsledný oblasti je uložen v `CRgn` objektu.  
  
 Může být polygonů nesouvislý, nebo mohou překrývat.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 ALTERNATIVNÍ při vyplňování mnohoúhelníku režimu systému vyplní oblast mezi stran lichými čísly a sudým číslem mnohoúhelníku na každém řádku kontroly. To znamená, že systém vyplní oblast mezi první a druhé straně, mezi třetí a čtvrtá straně a tak dále.  
  
 Když je režim vyplnění mnohoúhelníku zrušení, systém použije směr, ve kterém byl nakreslen elementu figure k určení, jestli k vyplnění oblasti. Každý úsek čáry v mnohoúhelník je vykreslen v po směru nebo proti směru hodinových ručiček. Pokaždé, když se z uzavřených oblasti vykreslit vnější elementu figure čárou prochází po směru hodinových ručiček čárového segmentu, počet se zvýší. Když řádku prochází proti směru hodinových ručiček čárového segmentu, je snížen počet. Oblast je vyplněna, pokud je počet nenulové dosáhne řádku mimo na obrázku.  
  
 Když aplikace dokončí použít oblast vytvořené pomocí `CreatePolyPolygonRgn` funkce, ji by měl vyberte oblast si tohoto kontextu zařízení a [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci jeho odstranění.  
  
##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn  
 Vytvoří obdélníkovou oblast, která je uložena v `CRgn` objektu.  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 *x1*  
 Určuje logickou souřadnici x levého horního rohu oblasti.  
  
 *Y1*  
 Určuje logickou souřadnici y levého horního rohu oblasti.  
  
 *x2*  
 Určuje logickou souřadnici x pravém dolním rohu oblasti.  
  
 *y2*  
 Určuje logickou souřadnici y pravého dolního rohu oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Když se dokončí oblasti vytvořené využitím `CreateRectRgn`, by měla aplikace použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci odebrat oblasti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 Další příklad naleznete v tématu [CRgn::CombineRgn](#combinergn).  
  
##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect  
 Vytvoří obdélníkovou oblast, která je uložena v `CRgn` objektu.  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje `RECT` struktury nebo `CRect` objekt, který obsahuje logické souřadnice levého a pravého dolního rohu oblasti. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Když se dokončí oblasti vytvořené využitím `CreateRectRgnIndirect`, by měla aplikace použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci odebrat oblasti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn  
 Vytvoří oblasti obdélníkový zaoblené rohy, která je uložena v `CRgn` objektu.  
  
```  
BOOL CreateRoundRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);
```  
  
### <a name="parameters"></a>Parametry  
 *x1*  
 Určuje logickou souřadnici x levého horního rohu oblasti.  
  
 *Y1*  
 Určuje logickou souřadnici y levého horního rohu oblasti.  
  
 *x2*  
 Určuje logickou souřadnici x pravém dolním rohu oblasti.  
  
 *y2*  
 Určuje logickou souřadnici y pravého dolního rohu oblasti.  
  
 *x3*  
 Určuje šířku použitý k vytvoření oblých rohů elipsy.  
  
 *Y3*  
 Určuje výšku elipsy použitý k vytvoření zaoblené rohy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je operace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, která je menší.  
  
 Když aplikace dokončí použít oblast vytvořené pomocí `CreateRoundRectRgn` funkce, ji by měl vyberte oblast si tohoto kontextu zařízení a [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci jeho odstranění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>  CRgn::CRgn  
 Vytvoří `CRgn` objektu.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hObject` Datový člen neobsahuje platný oblasti Windows GDI, dokud nebude objekt je inicializován s jednou nebo více z nich `CRgn` členské funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateRoundRectRgn](#createroundrectrgn).  
  
##  <a name="equalrgn"></a>  CRgn::EqualRgn  
 Určuje, zda je ekvivalentní k oblasti uložených v dané oblasti `CRgn` objektu.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pRgn*  
 Identifikuje oblast.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud tyto dvě oblasti jsou ekvivalentní; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>  CRgn::FromHandle  
 Vrací ukazatel `CRgn` objektu, když je zadaný popisovač do oblasti Windows.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>Parametry  
 *hRgn*  
 Určuje popisovač do oblasti Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CRgn` objektu. Pokud funkce nebyla úspěšná, vrácená hodnota je NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CRgn` objekt už není připojen ke zpracování, dočasný `CRgn` objekt se vytvoří a připojí. Tento dočasný `CRgn` objektu je platná pouze v až při příštím má aplikace čas nečinnosti v jeho smyčkou událostí, na které čas všechny dočasné obrázek objekty budou odstraněny. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jedno okno.  
  
##  <a name="getregiondata"></a>  CRgn::GetRegionData  
 Vyplní data popisující oblast zadané vyrovnávací paměti.  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpRgnData*  
 Odkazuje [rgndata –](../../mfc/reference/rgndata-structure.md) datová struktura, která přijímá informace. Pokud má parametr hodnotu NULL, návratová hodnota obsahuje počet bajtů potřebných pro datové oblasti.  
  
 *nCount*  
 Určuje velikost v bajtech, *lpRgnData* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je funkce úspěšná a *nCount* určuje odpovídající počet bajtů, vrácená hodnota je vždy *nCount*. Pokud funkce selže nebo pokud *nCount* určuje menší než odpovídající počet bajtů, vrácená hodnota je 0 (chyba).  
  
### <a name="remarks"></a>Poznámky  
 Tato data zahrnují dimenze obdélníky, které tvoří oblast. Tato funkce se používá ve spojení s `CRgn::CreateFromData` funkce.  
  
##  <a name="getrgnbox"></a>  CRgn::GetRgnBox  
 Načte souřadnice ohraničující obdélník `CRgn` objektu.  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje na `RECT` struktury nebo `CRect` objektu získat souřadnice ohraničujícího rámečku. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ oblasti. Může být některý z následujících hodnot:  
  
- Oblast COMPLEXREGION obsahuje překrývající se hranice.  
  
- Oblast NULLREGION je prázdný.  
  
- Chyba `CRgn` objekt neurčuje platnou oblast.  
  
- Oblast SIMPLEREGION nemá žádné překrývající se hranice.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreatePolygonRgn](#createpolygonrgn).  
  
##  <a name="offsetrgn"></a>  CRgn::OffsetRgn  
 Přesune uložené v oblasti `CRgn` objektu zadaných odsazení.  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje počet jednotek na doleva nebo doprava.  
  
 *y*  
 Určuje počet jednotek, aby se přesuňte směrem nahoru nebo dolů.  
  
 *Bod*  
 Souřadnici x *bodu* určuje počet jednotek na doleva nebo doprava. Souřadnici y *bodu* určuje počet jednotek, aby se přesuňte směrem nahoru nebo dolů. *Bodu* parametr může být buď `POINT` struktury nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ nové oblasti. To může být jedna z následujících hodnot:  
  
- Oblast COMPLEXREGION obsahuje překrývající se hranice.  
  
- Chyba oblasti popisovač je neplatný.  
  
- Oblast NULLREGION je prázdný.  
  
- Oblast SIMPLEREGION nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Funkce přesune oblast *x* jednotky podél osy x a *y* jednotky podél osy y.  
  
 Hodnoty souřadnic oblasti musí být menší než nebo rovna 32 767 a větší než nebo rovna hodnotě-32 768. *x* a *y* parametry musí být pečlivě zvolili zabránit souřadnice neplatnou oblast.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="operator_hrgn"></a>  CRgn::operator HRGN  
 Tento operátor se získat popisovač Windows GDI připojené `CRgn` objektu.  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěchu popisovač objektů Windows GDI reprezentována `CRgn` objektu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor je operátor přetypování, která podporuje přímému použití objektu HRGN.  
  
 Další informace o použití grafických objektů najdete v článku [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.  
  
##  <a name="ptinregion"></a>  CRgn::PtInRegion  
 Kontroluje, zda bodu *x* a *y* je v oblasti uložené v `CRgn` objektu.  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje logickou souřadnici x bodu k testování.  
  
 *y*  
 Určuje logickou souřadnici y bodu k testování.  
  
 *Bod*  
 X-y souřadnice a *bodu* zadejte x - a souřadnice y bodu pro testování hodnot. *Bodu* parametr může být buď `POINT` struktury nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je bod je v oblasti; jinak 0.  
  
##  <a name="rectinregion"></a>  CRgn::RectInRegion  
 Určuje, zda jakékoliv části obdélníku určené *lprect –* nachází uvnitř uložené v oblasti `CRgn` objektu.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje `RECT` struktury nebo `CRect` objektu. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud libovolné části obdélníku zadaného leží v hranicích oblasti; jinak 0.  
  
##  <a name="setrectrgn"></a>  CRgn::SetRectRgn  
 Vytvoří obdélníková oblast.  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *x1*  
 Určuje souřadnice x levého horního rohu oblasti obdélníkový.  
  
 *Y1*  
 Určuje souřadnici y levého horního rohu oblasti obdélníkový.  
  
 *x2*  
 Určuje souřadnici x v pravém dolním rohu oblasti obdélníkový.  
  
 *y2*  
 Určuje souřadnici y pravého dolního rohu oblasti obdélníkový.  
  
 *lprect –*  
 Určuje obdélníkovou oblast. Může být buď ukazatel `RECT` struktury nebo `CRect` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [CreateRectRgn](#createrectrgn), ale ho nepřidělí další paměti z haldy místní aplikace Windows. Místo toho používá místo přidělené oblasti uložená ve `CRgn` objektu. To znamená, že `CRgn` objektu musí již byly inicializovány s platnou oblast Windows před voláním `SetRectRgn`. Body Dal *x1*, *y1*, *x2*, a *y2* zadat minimální velikost přidělené místo.  
  
 Pomocí této funkce místo `CreateRectRgn` členskou funkci, aby se zabránilo volání do paměti místního správce.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



