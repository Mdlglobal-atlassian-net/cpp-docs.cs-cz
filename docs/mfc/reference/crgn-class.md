---
title: CRgn – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 66721f34a8ac2b6dac6addcfa04a88b46a37ee60
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916833"
---
# <a name="crgn-class"></a>CRgn – třída

Zapouzdřuje oblast rozhraní grafického zařízení (GDI) systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|`CRgn` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Nastaví objekt tak, aby byl ekvivalentní sjednocení dvou zadaných `CRgn` objektů. `CRgn`|
|[CRgn::CopyRgn](#copyrgn)|Nastaví objekt tak, aby byl kopií zadaného `CRgn` objektu. `CRgn`|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|`CRgn` Inicializuje objekt s eliptickou oblastí.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializuje objekt s eliptickou oblastí definovanou strukturou [Rect.](/windows/desktop/api/windef/ns-windef-tagrect) `CRgn`|
|[CRgn::CreateFromData](#createfromdata)|Vytvoří oblast z dané oblasti a dat transformace.|
|[CRgn::CreateFromPath](#createfrompath)|Vytvoří oblast z cesty, která je vybrána v daném kontextu zařízení.|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|`CRgn` Inicializuje objekt pomocí mnohoúhelníkové oblasti. Systém automaticky uzavře mnohoúhelník, pokud je to nutné, kreslením čáry z posledního vrcholu vrcholu do prvního.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|`CRgn` Inicializuje objekt s oblastí skládající se z řady uzavřených mnohoúhelníků. Mnohoúhelníky mohou být nesouvislé nebo se mohou překrývat.|
|[CRgn::CreateRectRgn](#createrectrgn)|`CRgn` Inicializuje objekt s obdélníkovou oblastí.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializuje objekt s obdélníkovou oblastí definovanou strukturou [Rect.](/windows/desktop/api/windef/ns-windef-tagrect) `CRgn`|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|`CRgn` Inicializuje objekt s obdélníkovou oblastí pomocí zaoblených rohů.|
|[CRgn::EqualRgn](#equalrgn)|Zkontroluje dva `CRgn` objekty a určí, zda jsou ekvivalentní.|
|[CRgn::FromHandle](#fromhandle)|Vrací ukazatel na `CRgn` objekt, pokud je předána obslužná rutina oblasti systému Windows.|
|[CRgn::GetRegionData](#getregiondata)|Vyplní zadanou vyrovnávací paměť daty, která popisují danou oblast.|
|[CRgn::GetRgnBox](#getrgnbox)|Načte souřadnice ohraničujícího obdélníku `CRgn` objektu.|
|[CRgn::OffsetRgn](#offsetrgn)|`CRgn` Přesune objekt o zadané posuny.|
|[CRgn::PtInRegion](#ptinregion)|Určuje, zda je zadaný bod v oblasti.|
|[CRgn::RectInRegion](#rectinregion)|Určuje, zda je část zadaného obdélníku v rámci hranic oblasti.|
|[CRgn::SetRectRgn](#setrectrgn)|`CRgn` Nastaví objekt na určenou obdélníkovou oblast.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|Vrátí popisovač systému Windows obsažený v `CRgn` objektu.|

## <a name="remarks"></a>Poznámky

Oblast je eliptický nebo mnohoúhelníková oblast v rámci okna. Chcete-li použít oblasti, použijte členské funkce třídy `CRgn` s funkcemi oříznutí, které jsou definovány jako členy třídy. `CDC`

Členské funkce `CRgn` vytvořit, změnit a načíst informace o objektu oblasti, pro který jsou volány.

Další informace o použití `CRgn`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="combinergn"></a>CRgn::CombineRgn

Vytvoří novou oblast GDI kombinováním dvou existujících oblastí.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Parametry

*pRgn1*<br/>
Identifikuje existující oblast.

*pRgn2*<br/>
Identifikuje existující oblast.

*nCombineMode*<br/>
Určuje operaci, která se má provést při kombinování dvou zdrojových oblastí. Může to být jedna z následujících hodnot:

- RGN_AND používá překrývající se oblasti obou oblastí (průnik).

- RGN_COPY vytvoří kopii oblasti 1 (identifikovanou *pRgn1*).

- RGN_DIFF vytvoří oblast skládající se z oblastí oblasti 1 (identifikovaných pomocí *pRgn1*), které nejsou součástí oblasti 2 (identifikovaných pomocí *pRgn2*).

- RGN_OR kombinuje obě oblasti v celém rozsahu (sjednocení).

- RGN_XOR kombinuje obě oblasti, ale odebere překrývající se oblasti.

### <a name="return-value"></a>Návratová hodnota

Určuje typ výsledné oblasti. Může to být jedna z následujících hodnot:

- COMPLEXREGION nové oblasti má překrývající se ohraničení.

- Při vytváření nové oblasti došlo k chybě.

- Nová oblast NULLREGION je prázdná.

- SIMPLEREGION nové oblasti nemá žádná překrývající se ohraničení.

### <a name="remarks"></a>Poznámky

Oblasti jsou zkombinovány podle zadání *nCombineMode*.

Dvě zadané oblasti jsou kombinovány a výsledný popisovač oblasti je uložen v `CRgn` objektu. Bez ohledu na to, jaká oblast je `CRgn` uložena v objektu, je nahrazena kombinovanou oblastí.

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Pomocí [CopyRgn](#copyrgn) jednoduše zkopírujte jednu oblast do jiné oblasti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>CRgn::CopyRgn

Zkopíruje oblast definovanou nástrojem *pRgnSrc* do `CRgn` objektu.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parametry

*pRgnSrc*<br/>
Identifikuje existující oblast.

### <a name="return-value"></a>Návratová hodnota

Určuje typ výsledné oblasti. Může to být jedna z následujících hodnot:

- COMPLEXREGION nové oblasti má překrývající se ohraničení.

- Při vytváření nové oblasti došlo k chybě.

- Nová oblast NULLREGION je prázdná.

- SIMPLEREGION nové oblasti nemá žádná překrývající se ohraničení.

### <a name="remarks"></a>Poznámky

Nová oblast nahrazuje oblast dříve uloženou v `CRgn` objektu. Tato funkce je zvláštní případ [CombineRgn](#combinergn) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRgn:: CreateEllipticRgn](#createellipticrgn).

##  <a name="createellipticrgn"></a>CRgn::CreateEllipticRgn

Vytvoří eliptický region.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Určuje logickou souřadnici x levého horního rohu ohraničujícího obdélníku elipsy.

*Y1*<br/>
Určuje logickou souřadnici y levého horního rohu ohraničujícího obdélníku elipsy.

*x2*<br/>
Určuje logickou souřadnici x pravého dolního rohu ohraničujícího obdélníku elipsy.

*y2*<br/>
Určuje logickou souřadnici y pravého dolního rohu ohraničujícího obdélníku elipsy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Oblast je definována ohraničujícím obdélníkem určeným pomocí *x1*, *Y1*, *X2*a *Y2*. Oblast je uložena v `CRgn` objektu.

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Po dokončení použití oblasti vytvořené pomocí `CreateEllipticRgn` funkce by měla aplikace vybrat oblast mimo kontext zařízení a `DeleteObject` pomocí funkce ji odebrat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Vytvoří eliptický region.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který obsahuje logické souřadnice ohraničujícího obdélníku, který je v pravém dolním rohu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Oblast je definována pomocí struktury nebo objektu, na který odkazuje *lpRect* a je uložena v `CRgn` objektu.

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Po dokončení použití oblasti vytvořené pomocí `CreateEllipticRgnIndirect` funkce by měla aplikace vybrat oblast mimo kontext zařízení a `DeleteObject` pomocí funkce ji odebrat.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRgn:: CreateRectRgnIndirect](#createrectrgnindirect).

##  <a name="createfromdata"></a>  CRgn::CreateFromData

Vytvoří oblast z dané oblasti a dat transformace.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parametry

*lpXForm*<br/>
Odkazuje na strukturu dat [Xform –](/windows/desktop/api/wingdi/ns-wingdi-tagxform) , která definuje transformaci, která má být provedena v oblasti. Pokud je tento ukazatel NULL, použije se transformace identity.

*nCount*<br/>
Určuje počet bajtů, na které odkazuje *pRgnData*.

*pRgnData*<br/>
Odkazuje na strukturu dat [rgnData –](/windows/desktop/api/wingdi/ns-wingdi-rgndata) , která obsahuje data oblasti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může načíst data pro oblast voláním `CRgn::GetRegionData` funkce.

##  <a name="createfrompath"></a>CRgn::CreateFromPath

Vytvoří oblast z cesty, která je vybrána v daném kontextu zařízení.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Identifikuje kontext zařízení, který obsahuje uzavřenou cestu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Kontext zařízení identifikovaný parametrem *primárního řadiče domény* musí obsahovat uzavřenou cestu. Když `CreateFromPath` převede cestu do oblasti, Windows zahodí uzavřenou cestu z kontextu zařízení.

##  <a name="createpolygonrgn"></a>CRgn::CreatePolygonRgn

Vytvoří mnohoúhelníkovou oblast.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Odkazuje na pole `POINT` struktury nebo `CPoint` pole objektů. Každá struktura Určuje souřadnici x a y jednoho vrcholu mnohoúhelníku. `POINT` Struktura má následující tvar:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Určuje počet `POINT` struktur nebo `CPoint` objektů v poli, na které odkazuje *lpPoints*.

*nMode*<br/>
Určuje režim vyplňování pro oblast. Tento parametr může být buď ALTERNATIVou, nebo VINUTÍm.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Systém automaticky uzavře mnohoúhelník, pokud je to nutné, kreslením čáry z posledního vrcholu vrcholu do prvního. Výsledná oblast je uložena v `CRgn` objektu.

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Když je režim vyplňování mnohoúhelníku ALTERNATIVně jiný, systém vyplní oblast mezi lichými a sudými mnohoúhelníky na jednotlivých řádcích skenování. To znamená, že systém vyplní oblast mezi první a druhou stranou mezi třetí a čtvrtou stranou atd.

Když je režim vyplňování mnohoúhelníku větru, systém použije směr, ve kterém byl obrázek vykreslen, aby určil, zda má být oblast vyplněna. Každý segment čáry v mnohoúhelníku je vykreslen buď po směru hodinových ručiček, nebo směrem proti směru hodinových ručiček. Pokaždé, když se na imaginární řádek nakreslený z uzavřené oblasti mimo obrázek projde segmentem čáry po směru hodinových ručiček, zvýší se počet. Když řádek projde segmentem čáry proti směru hodinových ručiček, počet se sníží. Oblast je vyplněna, pokud je počet nenulový, když řádek dosáhne mimo obrázek.

Když se aplikace dokončí pomocí oblasti vytvořené `CreatePolygonRgn` funkcí, měla by vybrat oblast mimo kontext zařízení a `DeleteObject` pomocí funkce ji odebrat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn

Vytvoří oblast skládající se z řady uzavřených mnohoúhelníků.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Odkazuje na pole `POINT` struktury nebo `CPoint` pole objektů, které definují vrcholy mnohoúhelníků. Každý mnohoúhelník musí být explicitně uzavřen, protože systém je neuzavře automaticky. Mnohoúhelníky jsou zadány po sobě. `POINT` Struktura má následující tvar:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Odkazuje na pole celých čísel. První celé číslo určuje počet vrcholů v prvním mnohoúhelníku v poli *lpPoints* , druhé celé číslo určuje počet vrcholů v druhém mnohoúhelníku atd.

*nCount*<br/>
Určuje celkový počet celých čísel v poli *lpPolyCounts* .

*nPolyFillMode*<br/>
Určuje režim vyplňování mnohoúhelníku. Tato hodnota může být buď alternativní, nebo vinutí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výsledná oblast je uložena v `CRgn` objektu.

Mnohoúhelníky mohou být nesouvislé nebo se mohou překrývat.

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Když je režim vyplňování mnohoúhelníku ALTERNATIVně jiný, systém vyplní oblast mezi lichými a sudými mnohoúhelníky na jednotlivých řádcích skenování. To znamená, že systém vyplní oblast mezi první a druhou stranou mezi třetí a čtvrtou stranou atd.

Když je režim vyplňování mnohoúhelníku větru, systém použije směr, ve kterém byl obrázek vykreslen, aby určil, zda má být oblast vyplněna. Každý segment čáry v mnohoúhelníku je vykreslen buď po směru hodinových ručiček, nebo směrem proti směru hodinových ručiček. Pokaždé, když se na imaginární řádek nakreslený z uzavřené oblasti mimo obrázek projde segmentem čáry po směru hodinových ručiček, zvýší se počet. Když řádek projde segmentem čáry proti směru hodinových ručiček, počet se sníží. Oblast je vyplněna, pokud je počet nenulový, když řádek dosáhne mimo obrázek.

Když se aplikace dokončí pomocí oblasti vytvořené pomocí `CreatePolyPolygonRgn` funkce, měla by vybrat oblast mimo kontext zařízení a pomocí členské funkce [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) ji odebrat.

##  <a name="createrectrgn"></a>CRgn::CreateRectRgn

Vytvoří obdélníkovou oblast, která je uložena v `CRgn` objektu.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parametry

*x1*<br/>
Určuje logickou souřadnici x levého horního rohu oblasti.

*Y1*<br/>
Určuje logickou souřadnici y v levém horním rohu oblasti.

*x2*<br/>
Určuje logickou souřadnici x v pravém dolním rohu oblasti.

*y2*<br/>
Určuje logickou souřadnici y v pravém dolním rohu oblasti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Po dokončení použití oblasti vytvořené `CreateRectRgn`aplikací by měla aplikace pomocí členské funkce [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) odebrat oblast.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Další příklad naleznete v tématu [CRgn:: CombineRgn](#combinergn).

##  <a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect

Vytvoří obdélníkovou oblast, která je uložena v `CRgn` objektu.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt, který obsahuje logické souřadnice levého horního a pravého dolního rohu oblasti. `RECT` Struktura má následující tvar:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Po dokončení použití oblasti vytvořené `CreateRectRgnIndirect`aplikací by měla aplikace pomocí členské funkce [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) odebrat oblast.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn

Vytvoří obdélníkovou oblast s zaoblenými rohy, které jsou uloženy `CRgn` v objektu.

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

*x1*<br/>
Určuje logickou souřadnici x levého horního rohu oblasti.

*Y1*<br/>
Určuje logickou souřadnici y v levém horním rohu oblasti.

*x2*<br/>
Určuje logickou souřadnici x v pravém dolním rohu oblasti.

*y2*<br/>
Určuje logickou souřadnici y v pravém dolním rohu oblasti.

*x3*<br/>
Určuje šířku elipsy použité k vytvoření zaoblených rohů.

*Y3*<br/>
Určuje výšku elipsy použité k vytvoření zaoblených rohů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud operace byla úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 32 767 logických jednotek nebo 64 kB paměti, podle toho, co je menší.

Když se aplikace dokončí pomocí oblasti vytvořené pomocí `CreateRoundRectRgn` funkce, měla by vybrat oblast mimo kontext zařízení a pomocí členské funkce [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) ji odebrat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>CRgn::CRgn

`CRgn` Vytvoří objekt.

```
CRgn();
```

### <a name="remarks"></a>Poznámky

Datový člen neobsahuje platnou oblast Windows GDI, dokud se objekt neinicializuje s jednou nebo více ostatními `CRgn` členskémi funkcemi. `m_hObject`

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRgn:: CreateRoundRectRgn](#createroundrectrgn).

##  <a name="equalrgn"></a>CRgn::EqualRgn

Určuje, zda je daná oblast ekvivalentní oblasti uložené v `CRgn` objektu.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parametry

*pRgn*<br/>
Identifikuje oblast.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou dvě oblasti ekvivalentní; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>CRgn::FromHandle

Vrací ukazatel na `CRgn` objekt, pokud je předána obslužná rutina oblasti systému Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parametry

*hRgn*<br/>
Určuje popisovač pro oblast systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRgn` objekt. Pokud funkce nebyla úspěšná, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt již není k popisovači připojen, je vytvořen a připojen `CRgn` dočasný objekt. `CRgn` Tento dočasný `CRgn` objekt je platný pouze do příštího okamžiku, kdy aplikace nebude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to vyjádřit, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

##  <a name="getregiondata"></a>CRgn::GetRegionData

Vyplní zadanou vyrovnávací paměť daty, která popisují oblast.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parametry

*lpRgnData*<br/>
Odkazuje na strukturu dat [rgnData –](/windows/desktop/api/wingdi/ns-wingdi-rgndata) , která obdrží informace. Pokud má tento parametr hodnotu NULL, vrácená hodnota obsahuje počet bajtů potřebných pro data oblasti.

*nCount*<br/>
Určuje velikost *lpRgnData* vyrovnávací paměti (v bajtech).

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná a *nCount* určuje dostatečný počet bajtů, návratová hodnota je vždycky *nCount*. Pokud dojde k chybě funkce nebo pokud *nCount* určuje méně než přiměřený počet bajtů, vrácená hodnota je 0 (chyba).

### <a name="remarks"></a>Poznámky

Tato data obsahují rozměry obdélníků, které tvoří oblast. Tato funkce se používá ve spojení s `CRgn::CreateFromData` funkcí.

##  <a name="getrgnbox"></a>CRgn::GetRgnBox

Načte souřadnice ohraničujícího obdélníku `CRgn` objektu.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt pro příjem souřadnic ohraničujícího obdélníku. `RECT` Struktura má následující tvar:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Návratová hodnota

Určuje typ oblasti. Může to být kterákoli z následujících hodnot:

- Oblast COMPLEXREGION má překrývající se ohraničení.

- Oblast NULLREGION je prázdná.

- Objekt `CRgn` Error neurčuje platnou oblast.

- Oblast SIMPLEREGION nemá žádná překrývající se ohraničení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRgn:: CreatePolygonRgn](#createpolygonrgn).

##  <a name="offsetrgn"></a>CRgn::OffsetRgn

Přesune oblast uloženou v `CRgn` objektu o zadané posuny.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Určuje počet jednotek, které mají být přesunuty doleva nebo doprava.

*y*<br/>
Určuje počet jednotek, které se mají přesunout nahoru nebo dolů.

*Vyberte*<br/>
Souřadnice x *bodu* určuje počet jednotek, které mají být přesunuty doleva nebo doprava. Souřadnice y *bodu* určuje počet jednotek, které se mají přesunout nahoru nebo dolů. Parametr *Point* může být buď `POINT` struktura, nebo `CPoint` objekt.

### <a name="return-value"></a>Návratová hodnota

Typ nové oblasti Může to být jedna z následujících hodnot:

- Oblast COMPLEXREGION má překrývající se ohraničení.

- Obslužná rutina chybové oblasti není platná.

- Oblast NULLREGION je prázdná.

- Oblast SIMPLEREGION nemá žádná překrývající se ohraničení.

### <a name="remarks"></a>Poznámky

Funkce přesune jednotky *x* oblasti podél osy x a jednotky *y* podél osy y.

Hodnoty souřadnic v oblasti musí být menší než nebo rovny hodnotě 32 767 a větší nebo rovny hodnotě-32 768. Aby se zabránilo neplatným souřadnicím oblastí, je třeba pečlivě vybrat parametry *x* a *y* .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRgn:: CreateEllipticRgn](#createellipticrgn).

##  <a name="operator_hrgn"></a>CRgn:: operator HRGN

Tento operátor použijte k získání připojené obslužné rutiny `CRgn` Windows GDI objektu.

```
operator HRGN() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač objektu GDI systému Windows reprezentovaný `CRgn` objektem; v opačném případě hodnota null.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HRGN.

Další informace o použití grafických objektů naleznete v článku [grafické objekty](/windows/desktop/gdi/graphic-objects) v Windows SDK.

##  <a name="ptinregion"></a>CRgn::P tInRegion

Kontroluje, zda je bod zadaný *x* a *y* v oblasti `CRgn` uložené v objektu.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parametry

*x*<br/>
Určuje logickou souřadnici x bodu k otestování.

*y*<br/>
Určuje logickou souřadnici y bodu, který se má testovat.

*Vyberte*<br/>
Souřadnice x a y bodu určují souřadnice x a y bodu k otestování hodnoty. Parametr *Point* může být `POINT` buď struktura, nebo `CPoint` objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je bod v oblasti; v opačném případě 0.

##  <a name="rectinregion"></a>CRgn::RectInRegion

Určuje, zda je jakákoli část obdélníku určená parametrem *lpRect* v rámci hranic oblasti uložené v `CRgn` objektu.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt. `RECT` Struktura má následující tvar:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jakákoli část zadaného obdélníku leží v rámci hranic oblasti; v opačném případě 0.

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

*x1*<br/>
Určuje souřadnici x levého horního rohu obdélníkové oblasti.

*Y1*<br/>
Určuje souřadnici y v levém horním rohu obdélníkové oblasti.

*x2*<br/>
Určuje souřadnici x pravého dolního rohu obdélníkové oblasti.

*y2*<br/>
Určuje souřadnici y pravého dolního rohu obdélníkové oblasti.

*lpRect*<br/>
Určuje obdélníkovou oblast. Může být buď ukazatel na `RECT` strukturu, `CRect` nebo objekt.

### <a name="remarks"></a>Poznámky

Na rozdíl od [CreateRectRgn](#createrectrgn)však nealokuje žádnou další paměť z místní haldy aplikace systému Windows. Místo toho používá místo přidělené pro oblast uloženou v `CRgn` objektu. To znamená, že `CRgn` objekt již musí být inicializován s platnou oblastí systému Windows před voláním `SetRectRgn`. Body, které jsou dány *x1*, *Y1*, *X2*a *Y2* , určují minimální velikost přiděleného prostoru.

Použijte tuto funkci namísto `CreateRectRgn` členské funkce, aby se předešlo voláním správce místní paměti.

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
