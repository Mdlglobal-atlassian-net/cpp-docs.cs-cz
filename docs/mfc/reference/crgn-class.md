---
title: "Třída CRgn | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57bf810ed1e44ee04b9018da3987c0232fca5e28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crgn-class"></a>Třída CRgn
Zapouzdří oblast Windows zařízení grafické rozhraní (GDI).  
  
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
|[CRgn::CopyRgn](#copyrgn)|Nastaví `CRgn` objektu tak, aby se kopie zadané `CRgn` objektu.|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializuje `CRgn` objekt s eliptické oblast.|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializuje `CRgn` objekt s oblast eliptické definované [Rect –](../../mfc/reference/rect-structure1.md) struktura.|  
|[CRgn::CreateFromData](#createfromdata)|Vytvoří z dané oblasti a transformace dat oblast.|  
|[CRgn::CreateFromPath](#createfrompath)|Vytvoří z cesty, která je do kontextu daného zařízení vybraná oblast.|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|Inicializuje `CRgn` objektu s polygonálních oblastí. Systém mnohoúhelníku automaticky zavře, v případě potřeby podle kreslení na první řádek z poslední vrchol.|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Inicializuje `CRgn` objektu s oblastí, který se skládá z řady uzavřené mnohoúhelníky. Polygonů může být nesouvislý, nebo se překrývají.|  
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializuje `CRgn` objekt s obdélníkovou oblast.|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializuje `CRgn` objekt s obdélníkovou oblast definované [Rect –](../../mfc/reference/rect-structure1.md) struktura.|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Inicializuje `CRgn` objekt s obdélníkovou oblast s zaoblenými hranami.|  
|[CRgn::EqualRgn](#equalrgn)|Kontroluje dva `CRgn` objekty, které chcete určit, jestli jsou ekvivalentní.|  
|[CRgn::FromHandle](#fromhandle)|Vrátí ukazatel na `CRgn` objektu, pokud Zadaný popisovač v oblasti systému Windows.|  
|[CRgn::GetRegionData](#getregiondata)|Vyplní zadanou vyrovnávací paměť data popisující příslušnou oblast.|  
|[CRgn::GetRgnBox](#getrgnbox)|Načte souřadnice ohraničující obdélník `CRgn` objektu.|  
|[CRgn::OffsetRgn](#offsetrgn)|Přesune `CRgn` objektu podle zadaných odsazení.|  
|[CRgn::PtInRegion](#ptinregion)|Určuje, zda zadaný bod nachází v oblasti.|  
|[CRgn::RectInRegion](#rectinregion)|Určuje, zda libovolná součást zadaný obdélníku uvnitř oblasti.|  
|[CRgn::SetRectRgn](#setrectrgn)|Nastaví `CRgn` objekt, který má zadaný obdélníkovou oblast.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRgn::operator HRGN](#operator_hrgn)|Vrátí popisovač Windows, které jsou součástí `CRgn` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Oblast je oblast eliptické nebo polygonálních v rámci časového období. Pokud chcete použít oblasti, můžete použít funkce člena třídy `CRgn` s výstřižek funkce definované členy třídy `CDC`.  
  
 Členské funkce `CRgn` vytvářet, alter a načíst informace o oblast objektu, pro které se nazývají.  
  
 Další informace o používání `CRgn`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="combinergn"></a>CRgn::CombineRgn  
 Vytvoří novou oblast GDI kombinací dvou existující oblastí.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pRgn1`  
 Určuje existující oblasti.  
  
 `pRgn2`  
 Určuje existující oblasti.  
  
 `nCombineMode`  
 Určuje operaci provést, pokud kombinace dvě zdrojových oblastí. Může být některého z následujících hodnot:  
  
- **RGN_AND** používá překrývající se oblasti obou oblastí (průnik).  
  
- **RGN_COPY** vytvoří kopii oblast 1 (identifikovaný `pRgn1`).  
  
- **RGN_DIFF** vytvoří oblasti, které se skládají z oblastí, které oblasti 1 (identifikovaný `pRgn1`), nejsou součástí oblasti 2 (identifikovaný `pRgn2`).  
  
- **RGN_OR** kombinuje obou oblastí jako celek (sjednocení).  
  
- **RGN_XOR** kombinuje obou oblastí, ale odebere překrývajících se oblastí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ výsledné oblasti. Může být jedna z následujících hodnot:  
  
- **COMPLEXREGION** novou oblast má překrývající se hranice.  
  
- **Chyba** žádné nové oblasti vytvořit.  
  
- **NULLREGION** novou oblast je prázdný.  
  
- **SIMPLEREGION** novou oblast nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Oblasti se zkombinují zadané `nCombineMode`.  
  
 Dva zadané oblasti se zkombinují a výsledný popisovač oblast je uložen v `CRgn` objektu. Proto je libovolnou oblast uložený v `CRgn` objektu je nahrazena kombinované oblast.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Použití [CopyRgn](#copyrgn) jedné oblasti jednoduše zkopírovat do jiné oblasti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>CRgn::CopyRgn  
 Zkopíruje oblasti definované `pRgnSrc` do `CRgn` objektu.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pRgnSrc`  
 Určuje existující oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ výsledné oblasti. Může být jedna z následujících hodnot:  
  
- **COMPLEXREGION** novou oblast má překrývající se hranice.  
  
- **Chyba** žádné nové oblasti vytvořit.  
  
- **NULLREGION** novou oblast je prázdný.  
  
- **SIMPLEREGION** novou oblast nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Novou oblast nahradí dříve uložené v oblasti `CRgn` objektu. Tato funkce je zvláštním případem [CombineRgn](#combinergn) – členská funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="createellipticrgn"></a>CRgn::CreateEllipticRgn  
 Vytvoří eliptické oblast.  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Určuje logické souřadnici x levého horního rohu ohraničující obdélník se třemi tečkami.  
  
 `y1`  
 Určuje logické souřadnici y levého horního rohu ohraničující obdélník se třemi tečkami.  
  
 `x2`  
 Určuje logické souřadnici x pravém dolním rohu ohraničující obdélník se třemi tečkami.  
  
 `y2`  
 Určuje logické souřadnici y pravém dolním rohu ohraničující obdélník se třemi tečkami.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Oblast je definována ohraničující obdélník určeného `x1`, `y1`, `x2`, a `y2`. Oblast je uložen v `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Po dokončení pomocí oblast vytvořené pomocí `CreateEllipticRgn` funkce, aplikace by měla vyberte oblast na kontextu zařízení a použití `DeleteObject` funkce jeho odebrání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect  
 Vytvoří eliptické oblast.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který obsahuje logické souřadnice levého a pravého dolního rozích ohraničující obdélník se třemi tečkami.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Oblasti definované struktury nebo na kterou odkazuje objekt `lpRect` a je uložen ve `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Po dokončení pomocí oblast vytvořené pomocí `CreateEllipticRgnIndirect` funkce, aplikace by měla vyberte oblast na kontextu zařízení a použití `DeleteObject` funkce jeho odebrání.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).  
  
##  <a name="createfromdata"></a>CRgn::CreateFromData  
 Vytvoří z dané oblasti a transformace dat oblast.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>Parametry  
 *lpXForm*  
 Odkazuje na [xform –](../../mfc/reference/xform-structure.md) datová struktura, která definuje transformace provádět v oblasti. Pokud je tento ukazatel **NULL**, transformaci identity se používá.  
  
 `nCount`  
 Určuje počet bajtů, na kterou odkazuje `pRgnData`.  
  
 `pRgnData`  
 Odkazuje na [rgndata –](../../mfc/reference/rgndata-structure.md) datová struktura, která obsahuje data oblast.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace může načíst data pro oblast voláním `CRgn::GetRegionData` funkce.  
  
##  <a name="createfrompath"></a>CRgn::CreateFromPath  
 Vytvoří z cesty, která je do kontextu daného zařízení vybraná oblast.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Identifikuje kontextu zařízení, který obsahuje uzavřené cestu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Kontext zařízení se identifikovanou pomocí `pDC` parametr musí obsahovat uzavřené cestu. Po `CreateFromPath` převede cestu do oblasti, Windows zahodí uzavřené cesty z daného kontextu zařízení.  
  
##  <a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn  
 Vytvoří polygonálních oblast.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoints`  
 Odkazuje na pole **bodu** struktury nebo pole `CPoint` objekty. Každá struktura určuje souřadnice x a y souřadnice jednoho vrcholu mnohoúhelníku. **Bodu** struktura má následující formát:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 Určuje počet **bodu** struktury nebo `CPoint` objektů v poli, na kterou odkazuje `lpPoints`.  
  
 `nMode`  
 Určuje režim naplnění pro oblast. Tento parametr může být buď **alternativní** nebo **VINUTÍ**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Systém mnohoúhelníku automaticky zavře, v případě potřeby podle kreslení na první řádek z poslední vrchol. Výsledná oblast je uložen v `CRgn` objektu.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Pokud je režim mnohoúhelníku naplnění **alternativní**, systém vyplní celé oblasti mezi stranách lichých a sudé mnohoúhelníku na každém řádku kontroly. To znamená systém vyplní oblast mezi první a druhé straně, mezi čtvrtý a třetí straně a tak dále.  
  
 Pokud je režim mnohoúhelníku naplnění **VINUTÍ**, používá systém směr, ve kterém obrázek vykreslení k určení, zda vyplnil celou oblast. Každý řádek segmentu v mnohoúhelníku, se vykresluje v po směru hodinových ručiček nebo proti směru hodinových ručiček. Vždy, když čárou čerpají z uzavřené oblasti ven obrázek prochází segment po směru hodinových ručiček řádku, se zvýší počet. Když na řádku prochází segment proti směru hodinových ručiček řádku, se odečte počet. Pokud je počet nenulové hodnoty, když na řádku dosáhne mimo obrázek, naplní oblasti.  
  
 Když aplikace dokončí pomocí oblast vytvořené pomocí `CreatePolygonRgn` funkce, ho měli vyberte oblast na kontextu zařízení a použití `DeleteObject` funkce jeho odebrání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn  
 Vytvoří v oblasti, který se skládá z řady uzavřené mnohoúhelníky.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPoints`  
 Odkazuje na pole **bodu** struktury nebo pole `CPoint` objekty, které definuje vrcholy polygonů. Každého mnohoúhelníku musí explicitně zavřít, protože je systém automaticky nezavře. Polygonů nejsou zadány za sebou. **Bodu** struktura má následující formát:  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 Bodů na pole celých čísel. První celé číslo udává číslo vrcholy v první mnohoúhelníku ve `lpPoints` pole, druhý celé číslo udává číslo vrcholy v druhé mnohoúhelníku a tak dále.  
  
 `nCount`  
 Určuje celkový počet celých čísel v `lpPolyCounts` pole.  
  
 `nPolyFillMode`  
 Určuje režim naplnění mnohoúhelníku. Tato hodnota může být buď **alternativní** nebo **VINUTÍ**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výsledná oblast je uložen v `CRgn` objektu.  
  
 Polygonů může být nesouvislý, nebo se překrývají.  
  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Pokud je režim mnohoúhelníku naplnění **alternativní**, systém vyplní celé oblasti mezi stranách lichých a sudé mnohoúhelníku na každém řádku kontroly. To znamená systém vyplní oblast mezi první a druhé straně, mezi čtvrtý a třetí straně a tak dále.  
  
 Pokud je režim mnohoúhelníku naplnění **VINUTÍ**, používá systém směr, ve kterém obrázek vykreslení k určení, zda vyplnil celou oblast. Každý řádek segmentu v mnohoúhelníku, se vykresluje v po směru hodinových ručiček nebo proti směru hodinových ručiček. Vždy, když čárou čerpají z uzavřené oblasti ven obrázek prochází segment po směru hodinových ručiček řádku, se zvýší počet. Když na řádku prochází segment proti směru hodinových ručiček řádku, se odečte počet. Pokud je počet nenulové hodnoty, když na řádku dosáhne mimo obrázek, naplní oblasti.  
  
 Když aplikace dokončí pomocí oblast vytvořené pomocí `CreatePolyPolygonRgn` funkce, ho měli vyberte oblast na kontextu zařízení a použití [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) – členská funkce jeho odebrání.  
  
##  <a name="createrectrgn"></a>CRgn::CreateRectRgn  
 Vytvoří obdélníkovou oblast, která je uložená v `CRgn` objektu.  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Určuje logické souřadnici x levého horního rohu oblasti.  
  
 `y1`  
 Určuje logické souřadnici y levého horního rohu oblasti.  
  
 `x2`  
 Určuje logické souřadnici x pravém dolním rohu oblasti.  
  
 `y2`  
 Určuje logické souřadnici y pravém dolním rohu oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Po dokončení oblast vytvořené pomocí `CreateRectRgn`, aplikace by měl používat [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) – členská funkce odebrat oblast.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 Další příklad najdete v tématu [CRgn::CombineRgn](#combinergn).  
  
##  <a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect  
 Vytvoří obdélníkovou oblast, která je uložená v `CRgn` objektu.  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který obsahuje logické souřadnice levém horním a pravém dolním rozích oblasti. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Po dokončení oblast vytvořené pomocí `CreateRectRgnIndirect`, aplikace by měl používat [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) – členská funkce odebrat oblast.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn  
 Vytvoří obdélníkovou oblast s zaoblenými hranami, které jsou uloženy v `CRgn` objektu.  
  
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
 `x1`  
 Určuje logické souřadnici x levého horního rohu oblasti.  
  
 `y1`  
 Určuje logické souřadnici y levého horního rohu oblasti.  
  
 `x2`  
 Určuje logické souřadnici x pravém dolním rohu oblasti.  
  
 `y2`  
 Určuje logické souřadnici y pravém dolním rohu oblasti.  
  
 *x3*  
 Určuje šířku se třemi tečkami použít k vytvoření zaoblenými hranami.  
  
 `y3`  
 Určuje výšku se třemi tečkami použít k vytvoření zaoblenými hranami.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se operace úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Velikost oblasti je omezený na 32 767 podle 32 767 logické jednotky nebo 64 kB paměti, než je menší.  
  
 Když aplikace dokončí pomocí oblast vytvořené pomocí `CreateRoundRectRgn` funkce, ho měli vyberte oblast na kontextu zařízení a použití [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) – členská funkce jeho odebrání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>CRgn::CRgn  
 Vytvoří `CRgn` objektu.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hObject` – Datový člen neobsahuje platný oblast GDI systému Windows, dokud se neinicializuje objekt s jedním nebo více dalších `CRgn` členské funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateRoundRectRgn](#createroundrectrgn).  
  
##  <a name="equalrgn"></a>CRgn::EqualRgn  
 Určuje, zda je ekvivalentní pro oblast uložené v dané oblasti `CRgn` objektu.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pRgn`  
 Určuje oblast.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud odpovídají dvou oblastí; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>CRgn::FromHandle  
 Vrátí ukazatel na `CRgn` objektu, pokud Zadaný popisovač v oblasti systému Windows.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>Parametry  
 `hRgn`  
 Určuje popisovač v oblasti systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CRgn` objektu. Pokud funkce nebyla úspěšná, je vrácenou hodnotu **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CRgn` objekt není už připojený k popisovač dočasného `CRgn` objekt se vytvoří a připojené. Toto dočasný `CRgn` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho událostí smyčky, na který čas všechny dočasné obrázek objekty jsou odstraněny. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jeden interval.  
  
##  <a name="getregiondata"></a>CRgn::GetRegionData  
 Zadané vyrovnávací vyplní data popisující oblasti.  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRgnData`  
 Odkazuje na [rgndata –](../../mfc/reference/rgndata-structure.md) datová struktura, která přijímá informace. Pokud tento parametr je **NULL**, počet bajtů, které jsou potřebné pro oblast dat obsahuje návratovou hodnotu.  
  
 `nCount`  
 Určuje velikost v bajtech, a to `lpRgnData` vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud se podaří funkce a `nCount` určuje odpovídající počet bajtů, se vrácená hodnota je vždy `nCount`. Pokud funkce selže, nebo pokud `nCount` určuje menší než odpovídající počet bajtů, vrácená hodnota je 0 (chyba).  
  
### <a name="remarks"></a>Poznámky  
 Tato data zahrnují dimenze obdélníky, které tvoří oblasti. Tato funkce se používá ve spojení s `CRgn::CreateFromData` funkce.  
  
##  <a name="getrgnbox"></a>CRgn::GetRgnBox  
 Načte souřadnice ohraničující obdélník `CRgn` objektu.  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který chcete přijímat souřadnice ohraničující obdélník. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje typ této oblasti. Může být libovolná z následujících hodnot:  
  
- **COMPLEXREGION** oblast má překrývající se hranice.  
  
- **NULLREGION** oblast je prázdný.  
  
- **Chyba** `CRgn` objekt neurčuje platnou oblast.  
  
- **SIMPLEREGION** oblast nemá žádné překrývající se hranice.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreatePolygonRgn](#createpolygonrgn).  
  
##  <a name="offsetrgn"></a>CRgn::OffsetRgn  
 Přesune uložené v oblasti `CRgn` objektu podle zadaných odsazení.  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje počet jednotek přesunout doleva nebo doprava.  
  
 *y*  
 Určuje počet jednotek přesunout nahoru nebo dolů.  
  
 `point`  
 Souřadnici x `point` určuje počet jednotek přesunout doleva nebo doprava. Souřadnici y `point` určuje počet jednotek přesunout nahoru nebo dolů. `point` Parametr může být buď **bodu** struktura nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ nové oblasti. Může být některého z následujících hodnot:  
  
- **COMPLEXREGION** oblast má překrývající se hranice.  
  
- **Chyba** popisovač oblasti je neplatný.  
  
- **NULLREGION** oblast je prázdný.  
  
- **SIMPLEREGION** oblast nemá žádné překrývající se hranice.  
  
### <a name="remarks"></a>Poznámky  
 Funkce přesune oblast *x* jednotky podél osy x a *y* jednotky podél osy y.  
  
 Souřadnice hodnoty oblasti musí být menší než nebo rovna 32 767 a větší než nebo rovna hodnotě-32 768. *x* a *y* parametry musí být pečlivě zvolili aby souřadnice neplatná oblast.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).  
  
##  <a name="operator_hrgn"></a>CRgn::operator HRGN  
 Tento operátor. použijte k získání připojené popisovač GDI systému Windows `CRgn` objektu.  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro objekt Windows GDI reprezentována `CRgn` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití **HRGN** objektu.  
  
 Další informace o použití grafických objektů najdete v článku [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
##  <a name="ptinregion"></a>CRgn::PtInRegion  
 Kontroluje, zda bodu určeného vlastností *x* a *y* v oblasti uložené v `CRgn` objektu.  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Určuje logické souřadnice x bodu k testování.  
  
 *y*  
 Určuje logické souřadnici y bodu k testování.  
  
 `point`  
 X-y souřadnice a `point` zadejte x - a souřadnice y bodu k testování hodnotu. `point` Parametr může být buď **bodu** struktura nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je bod v oblasti; jinak 0.  
  
##  <a name="rectinregion"></a>CRgn::RectInRegion  
 Určuje, zda libovolná součást rámeček určeného `lpRect` nachází uvnitř monitorované geografické oblasti uložené v `CRgn` objektu.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objektu. `RECT` Struktura má následující formát:  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud libovolná součást určeného obdélníku leží v hranicích oblasti; jinak 0.  
  
##  <a name="setrectrgn"></a>CRgn::SetRectRgn  
 Vytvoří obdélníkovou oblast.  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `x1`  
 Určuje souřadnici x levého horního rohu obdélníkovou oblast.  
  
 `y1`  
 Určuje souřadnici y levého horního rohu obdélníkovou oblast.  
  
 `x2`  
 Určuje souřadnici x v pravém dolním rohu obdélníkovou oblast.  
  
 `y2`  
 Určuje souřadnici y pravém dolním rohu obdélníkovou oblast.  
  
 `lpRect`  
 Určuje obdélníkovou oblast. Může být buď ukazatel na `RECT` struktura nebo `CRect` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [CreateRectRgn](#createrectrgn), ale ji není přidělit žádné další paměť z lokální haldy aplikace systému Windows. Místo toho použije místo přidělené pro oblast uložené v `CRgn` objektu. To znamená, že `CRgn` objekt musí již byly inicializovány s platnou oblastí Windows před voláním `SetRectRgn`. Body poskytují `x1`, `y1`, `x2`, a `y2` určit minimální velikost přidělené místo.  
  
 Tato funkce je místo `CreateRectRgn` – členská funkce, aby se zabránilo volání správci místní paměti.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



