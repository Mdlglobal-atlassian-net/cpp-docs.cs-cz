---
title: Třída CRgn
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
ms.openlocfilehash: e84526eec8f4fd4b1935fa39bc7f4ed3c4d5dd71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754488"
---
# <a name="crgn-class"></a>Třída CRgn

Zapouzdřuje oblast rozhraní grafického zařízení systému Windows (GDI).

## <a name="syntax"></a>Syntaxe

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Vytvoří `CRgn` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Nastaví `CRgn` objekt tak, aby byl ekvivalentní `CRgn` sjednocení dvou zadaných objektů.|
|[CRgn::CopyRgn](#copyrgn)|Nastaví `CRgn` objekt tak, aby se `CRgn` jedná o kopii zadaného objektu.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Inicializuje `CRgn` objekt s eliptickou oblastí.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Inicializuje `CRgn` objekt s eliptickou oblastí definovanou strukturou [RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::CreateFromData](#createfromdata)|Vytvoří oblast z dané oblasti a data transformace.|
|[CRgn::CreateFromPath](#createfrompath)|Vytvoří oblast z cesty, která je vybrána do kontextu daného zařízení.|
|[CRgn::VytvořitPolygonRgn](#createpolygonrgn)|Inicializuje `CRgn` objekt s polygonové oblasti. Systém v případě potřeby automaticky uzavře polygon nakreslením čáry od posledního vrcholu k prvnímu.|
|[CRgn::VytvořitPolyPolygonRgn](#createpolypolygonrgn)|Inicializuje `CRgn` objekt s oblastí skládající se z řady uzavřených polygonů. Polygony mohou být nesouvislé nebo se mohou překrývat.|
|[CRgn::CreateRectRgn](#createrectrgn)|Inicializuje `CRgn` objekt s obdélníkovou oblastí.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Inicializuje `CRgn` objekt s obdélníkovou oblastí definovanou [tructure RECT.](/windows/win32/api/windef/ns-windef-rect)|
|[CRgn::VytvořitRoundRectRgn](#createroundrectrgn)|Inicializuje `CRgn` objekt s obdélníkovou oblastí se zaoblenými rohy.|
|[CRgn::EqualRgn](#equalrgn)|Zkontroluje `CRgn` dva objekty k určení, zda jsou rovnocenné.|
|[CRgn::FromHandle](#fromhandle)|Vrátí ukazatel na `CRgn` objekt při dané popisovač oblasti systému Windows.|
|[CRgn::GetRegionData](#getregiondata)|Vyplní zadanou vyrovnávací paměť daty popisujícími danou oblast.|
|[CRgn::GetRgnBox](#getrgnbox)|Načte souřadnice ohraničujícího obdélníku objektu. `CRgn`|
|[CRgn::OffsetRgn](#offsetrgn)|Přesune `CRgn` objekt o zadané posuny.|
|[CRgn::PtInRegion](#ptinregion)|Určuje, zda je zadaný bod v oblasti.|
|[CRgn::RectInRegion](#rectinregion)|Určuje, zda je libovolná část zadaného obdélníku v rámci hranic oblasti.|
|[CRgn::SetRectRgn](#setrectrgn)|Nastaví `CRgn` objekt na zadanou obdélníkovou oblast.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CRgn::operátor HRGN](#operator_hrgn)|Vrátí popisovač systému `CRgn` Windows obsažený v objektu.|

## <a name="remarks"></a>Poznámky

Oblast je eliptická nebo polygonalní oblast v okně. Chcete-li použít oblasti, použijte `CRgn` členské funkce třídy s ořezové funkce definované jako členy třídy `CDC`.

Členské funkce `CRgn` vytvořit, změnit a načíst informace o objektu oblasti, pro které jsou volány.

Další informace o `CRgn`použití naleznete v [tématu Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::CombineRgn

Vytvoří novou oblast GDI kombinací dvou existujících oblastí.

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
Určuje operaci, která má být provedena při kombinování dvou zdrojových oblastí. Může to být některá z následujících hodnot:

- RGN_AND Používá překrývající se oblasti obou oblastí (průsečík).

- RGN_COPY Vytvoří kopii oblasti 1 (identifikované *pRgn1*).

- RGN_DIFF Vytvoří oblast skládající se z oblastí oblasti 1 (identifikované *pRgn1*), které nejsou součástí oblasti 2 (identifikované *pomocí pRgn2).*

- RGN_OR Kombinuje oba regiony jako celek (unie).

- RGN_XOR Kombinuje obě oblasti, ale odstraní překrývající se oblasti.

### <a name="return-value"></a>Návratová hodnota

Určuje typ výsledné oblasti. Může to být jedna z následujících hodnot:

- COMPLEXREGION Nová oblast má překrývající se ohraničení.

- CHYBA Nebyla vytvořena žádná nová oblast.

- NULLREGION Nová oblast je prázdná.

- SIMPLEREGION Nová oblast nemá žádné překrývající se hranice.

### <a name="remarks"></a>Poznámky

Oblasti jsou kombinovány podle specifikace *nCombineMode*.

Dvě zadané oblasti jsou kombinovány a výsledný popisovač `CRgn` oblasti je uložen v objektu. Proto bez ohledu na `CRgn` oblast je uložena v objektu je nahrazen kombinované oblasti.

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

[CopyRgn](#copyrgn) slouží k jednoduše zkopírování jedné oblasti do jiné oblasti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::CopyRgn

Zkopíruje oblast definovanou *pRgnSrc* do objektu. `CRgn`

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parametry

*pRgnSrc*<br/>
Identifikuje existující oblast.

### <a name="return-value"></a>Návratová hodnota

Určuje typ výsledné oblasti. Může to být jedna z následujících hodnot:

- COMPLEXREGION Nová oblast má překrývající se ohraničení.

- CHYBA Nebyla vytvořena žádná nová oblast.

- NULLREGION Nová oblast je prázdná.

- SIMPLEREGION Nová oblast nemá žádné překrývající se hranice.

### <a name="remarks"></a>Poznámky

Nová oblast nahradí oblast dříve uložená `CRgn` v objektu. Tato funkce je zvláštní případ [combinergn](#combinergn) členské funkce.

### <a name="example"></a>Příklad

  Viz příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::CreateEllipticRgn

Vytvoří eliptickou oblast.

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

*y1*<br/>
Určuje logickou souřadnici y levého horního rohu ohraničujícího obdélníku elipsy.

*x2*<br/>
Určuje logickou souřadnici x pravého dolního rohu ohraničovacího obdélníku elipsy.

*y2*<br/>
Určuje logickou souřadnici y pravého dolního rohu ohraničovacího obdélníku elipsy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Oblast je definována ohraničujícím obdélníkem určeným *parametry x1*, *y1*, *x2*a *y2*. Oblast je uložena `CRgn` v objektu.

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Po dokončení pomocí oblasti vytvořené s `CreateEllipticRgn` funkcí by aplikace měla vybrat oblast mimo kontext `DeleteObject` zařízení a použít funkci k jeho odebrání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Vytvoří eliptickou oblast.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který obsahuje logické souřadnice levého horního a pravého dolního rohu ohraničujícího obdélníku elipsy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Oblast je definována strukturou nebo objektem, na který `CRgn` poukazuje *lpRect,* a je uložena v objektu.

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Po dokončení pomocí oblasti vytvořené s `CreateEllipticRgnIndirect` funkcí by aplikace měla vybrat oblast mimo kontext `DeleteObject` zařízení a použít funkci k jeho odebrání.

### <a name="example"></a>Příklad

  Viz příklad pro [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::CreateFromData

Vytvoří oblast z dané oblasti a data transformace.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parametry

*lpXForm*<br/>
Odkazuje na strukturu [Ata XFORM,](/windows/win32/api/wingdi/ns-wingdi-xform)která definuje transformaci, která má být provedena v oblasti. Pokud tento ukazatel je NULL, transformace identity se používá.

*nCount*<br/>
Určuje počet bajtů, na které je odkazováno *pomocí pRgnData*.

*pRgnData*<br/>
Odkazuje na datovou strukturu [RGNDATA,](/windows/win32/api/wingdi/ns-wingdi-rgndata) která obsahuje data oblasti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace může načíst data pro `CRgn::GetRegionData` oblast voláním funkce.

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::CreateFromPath

Vytvoří oblast z cesty, která je vybrána do kontextu daného zařízení.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Identifikuje kontext zařízení, který obsahuje uzavřenou cestu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Kontext zařízení identifikovaný parametrem *pDC* musí obsahovat uzavřenou cestu. Po `CreateFromPath` převedení cesty do oblasti, systém Windows zahodí uzavřenou cestu z kontextu zařízení.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::VytvořitPolygonRgn

Vytvoří polygonovou oblast.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Odkazuje na pole `POINT` struktur nebo pole `CPoint` objektů. Každá struktura určuje souřadnice x a y jednoho vrcholu polygonu. Struktura `POINT` má následující tvar:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Určuje počet `POINT` struktur nebo `CPoint` objektů v poli, na které odkazuje *lpPoints*.

*nRežim*<br/>
Určuje režim plnění pro oblast. Tento parametr může být buď ALTERNATE nebo WINDING.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Systém v případě potřeby automaticky uzavře polygon nakreslením čáry od posledního vrcholu k prvnímu. Výsledná oblast je uložena v objektu. `CRgn`

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Pokud je režim plnění mnohostranných spojů ALTERNATE, systém vyplní oblast mezi lichými a sudými polygonovými stranami na každé linii skenování. To znamená, že systém vyplňuje oblast mezi první a druhou stranou, mezi třetí a čtvrtou stranou a tak dále.

Pokud je režim plnění polygonů winding, systém používá směr, ve kterém byl obrázek nakreslena k určení, zda má být vyplnit oblast. Každý segment čáry v polygonu je nakreslen buď ve směru hodinových ručiček, nebo proti směru hodinových ručiček. Kdykoli pomyslná čára nakreslená z uzavřené oblasti na vnější stranu polymeje prochází segmentem čáry ve směru hodinových ručiček, poroste se počet. Když čára prochází segmentem čáry proti směru hodinových ručiček, počet se sníží. Oblast je vyplněna, pokud je počet nenulový, když čára dosáhne vnější strany obrázku.

Po dokončení aplikace pomocí oblasti vytvořené `CreatePolygonRgn` s funkcí, by měla vybrat oblast z `DeleteObject` kontextu zařízení a použít funkci k jeho odebrání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::VytvořitPolyPolygonRgn

Vytvoří oblast skládající se z řady uzavřených polygonů.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parametry

*lpPoints*<br/>
Odkazuje na pole `POINT` struktur nebo pole `CPoint` objektů, které definuje vrcholy polygonů. Každý polygon musí být explicitně uzavřen, protože systém je nezavře automaticky. Polygony jsou určeny postupně. Struktura `POINT` má následující tvar:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Odkazuje na pole celá čísla. První celé číslo určuje počet vrcholů v prvním mnohonolu v poli *lpPoints,* druhé celé číslo určuje počet vrcholů v druhém mnohonolu a tak dále.

*nCount*<br/>
Určuje celkový počet celá čísla v poli *lpPolyCounts.*

*nPolyFillMode*<br/>
Určuje režim plnění polygonů. Tato hodnota může být buď ALTERNATE nebo WINDING.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Výsledná oblast je uložena v objektu. `CRgn`

Polygony mohou být nesouvislé nebo se mohou překrývat.

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Pokud je režim plnění mnohostranných spojů ALTERNATE, systém vyplní oblast mezi lichými a sudými polygonovými stranami na každé linii skenování. To znamená, že systém vyplňuje oblast mezi první a druhou stranou, mezi třetí a čtvrtou stranou a tak dále.

Pokud je režim plnění polygonů winding, systém používá směr, ve kterém byl obrázek nakreslena k určení, zda má být vyplnit oblast. Každý segment čáry v polygonu je nakreslen buď ve směru hodinových ručiček, nebo proti směru hodinových ručiček. Kdykoli pomyslná čára nakreslená z uzavřené oblasti na vnější stranu polymeje prochází segmentem čáry ve směru hodinových ručiček, poroste se počet. Když čára prochází segmentem čáry proti směru hodinových ručiček, počet se sníží. Oblast je vyplněna, pokud je počet nenulový, když čára dosáhne vnější strany obrázku.

Po dokončení aplikace pomocí oblasti vytvořené `CreatePolyPolygonRgn` s funkcí, by měla vybrat oblast z kontextu zařízení a použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci odebrat.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::CreateRectRgn

Vytvoří obdélníkovou oblast, která `CRgn` je uložena v objektu.

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

*y1*<br/>
Určuje logickou souřadnici y levého horního rohu oblasti.

*x2*<br/>
Určuje logickou souřadnici x pravého dolního rohu oblasti.

*y2*<br/>
Určuje logickou souřadnici y pravého dolního rohu oblasti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Po dokončení použití oblasti vytvořené `CreateRectRgn`aplikace by měla použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci k odebrání oblasti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Další příklad naleznete v tématu [CRgn::CombineRgn](#combinergn).

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect

Vytvoří obdélníkovou oblast, která `CRgn` je uložena v objektu.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který obsahuje logické souřadnice levého horního a pravého dolního rohu oblasti. Struktura `RECT` má následující tvar:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Po dokončení použití oblasti vytvořené `CreateRectRgnIndirect`aplikace by měla použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci k odebrání oblasti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::VytvořitRoundRectRgn

Vytvoří obdélníkovou oblast se zaoblenými `CRgn` rohy, která je uložena v objektu.

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

*y1*<br/>
Určuje logickou souřadnici y levého horního rohu oblasti.

*x2*<br/>
Určuje logickou souřadnici x pravého dolního rohu oblasti.

*y2*<br/>
Určuje logickou souřadnici y pravého dolního rohu oblasti.

*x3*<br/>
Určuje šířku elipsy použité k vytvoření zaoblených rohů.

*y3*<br/>
Určuje výšku elipsy použité k vytvoření zaoblených rohů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla operace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Velikost oblasti je omezena na 32 767 podle 32 767 logických jednotek nebo 64 kM paměti, podle toho, která hodnota je menší.

Po dokončení aplikace pomocí oblasti vytvořené `CreateRoundRectRgn` s funkcí, by měla vybrat oblast z kontextu zařízení a použít [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členskou funkci odebrat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn::CRgn

Vytvoří `CRgn` objekt.

```
CRgn();
```

### <a name="remarks"></a>Poznámky

Datový `m_hObject` člen neobsahuje platnou oblast GDI systému Windows, dokud není `CRgn` objekt inicializován s jednou nebo více dalšími členskými funkcemi.

### <a name="example"></a>Příklad

  Viz příklad pro [CRgn::CreateRoundRectRgn](#createroundrectrgn).

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::EqualRgn

Určuje, zda je daná oblast ekvivalentní `CRgn` oblasti uložené v objektu.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parametry

*pRgn*<br/>
Identifikuje oblast.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou oba regiony rovnocenné; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::FromHandle

Vrátí ukazatel na `CRgn` objekt při dané popisovač oblasti systému Windows.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parametry

*hRgn*<br/>
Určuje popisovač oblasti systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRgn` objekt. Pokud funkce nebyla úspěšná, vrácená hodnota je NULL.

### <a name="remarks"></a>Poznámky

Pokud `CRgn` objekt ještě není připojen k popisovač, dočasný `CRgn` objekt je vytvořen a připojen. Tento `CRgn` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Dalším způsobem, jak to říct, je, že dočasný objekt je platný pouze během zpracování jedné zprávy okna.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn::GetRegionData

Vyplní zadanou vyrovnávací paměť daty popisujícími oblast.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parametry

*lpRgnData*<br/>
Odkazuje na datovou strukturu [RGNDATA,](/windows/win32/api/wingdi/ns-wingdi-rgndata) která přijímá informace. Pokud je tento parametr NULL, vrácená hodnota obsahuje počet bajtů potřebných pro data oblasti.

*nCount*<br/>
Určuje velikost vyrovnávací paměti *lpRgnData* v bajtech.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce úspěšné a *nCount* určuje dostatečný počet bajtů, vrácená hodnota je vždy *nCount*. Pokud funkce selže nebo pokud *nCount* určuje menší než dostatečný počet bajtů, vrácená hodnota je 0 (chyba).

### <a name="remarks"></a>Poznámky

Tato data zahrnují rozměry obdélníky, které tvoří oblast. Tato funkce se používá `CRgn::CreateFromData` ve spojení s funkcí.

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

Načte souřadnice ohraničujícího obdélníku objektu. `CRgn`

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, aby získal souřadnice ohraničovacího obdélníku. Struktura `RECT` má následující tvar:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Návratová hodnota

Určuje typ oblasti. Může to být některá z následujících hodnot:

- COMPLEXREGION Region má překrývající se hranice.

- NullREGION oblast je prázdný.

- Objekt `CRgn` ERROR neurčuje platnou oblast.

- SIMPLEREGION Region nemá žádné překrývající se hranice.

### <a name="example"></a>Příklad

  Viz příklad pro [CRgn::CreatePolygonRgn](#createpolygonrgn).

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::OffsetRgn

Přesune oblast uloženou `CRgn` v objektu o zadané posuny.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Určuje počet jednotek, které mají být posunuty doleva nebo doprava.

*Y*<br/>
Určuje počet jednotek, které se mají pohybovat nahoru nebo dolů.

*Bod*<br/>
Souřadnice *x bodu* určuje počet jednotek, které mají být posunuty doleva nebo doprava. Souřadnice *y bodu* určuje počet jednotek, které se mají pohybovat nahoru nebo dolů. Parametrem *bodu* může `POINT` být buď `CPoint` struktura, nebo objekt.

### <a name="return-value"></a>Návratová hodnota

Nový typ regionu. Může to být některá z následujících hodnot:

- COMPLEXREGION Region má překrývající se hranice.

- Popisovač oblasti chyby není platný.

- NullREGION oblast je prázdný.

- SIMPLEREGION Region nemá žádné překrývající se hranice.

### <a name="remarks"></a>Poznámky

Funkce přesune jednotky oblasti *x* podél osy x a *jednotek y* podél osy y.

Souřadnicové hodnoty oblasti musí být menší nebo rovny 32 767 a větší nebo rovny -32 768. Parametry *x* a *y* musí být pečlivě vybrány, aby se zabránilo neplatným souřadnicím oblasti.

### <a name="example"></a>Příklad

  Viz příklad pro [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::operátor HRGN

Pomocí tohoto operátoru získáte připojený popisovač GDI systému Windows objektu. `CRgn`

```
operator HRGN() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu GDI systému Windows reprezentovaný objektem; `CRgn` jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor lití, který podporuje přímé použití objektu HRGN.

Další informace o používání grafických objektů naleznete v článku [Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::PtInRegion

Zkontroluje, zda bod daný *x* a *y* `CRgn` je v oblasti uložené v objektu.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parametry

*X*<br/>
Určuje logickou souřadnici x bodu, který má být testován.

*Y*<br/>
Určuje logickou souřadnici y bodu, který má být testován.

*Bod*<br/>
Souřadnice x a y *bodu* určují souřadnice x a y bodu, který má být otestována hodnota. Parametrem *bodu* může `POINT` být buď `CPoint` struktura, nebo objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je bod v oblasti; jinak 0.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::RectInRegion

Určuje, zda je jakákoli část obdélníku určená *lpRect* v `CRgn` rámci hranic oblasti uložené v objektu.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt. Struktura `RECT` má následující tvar:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud některá část zadaného obdélníku leží uvnitř hranic oblasti; jinak 0.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::SetRectRgn

Vytvoří obdélníkovou oblast.

```cpp
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

*y1*<br/>
Určuje souřadnici y levého horního rohu obdélníkové oblasti.

*x2*<br/>
Určuje souřadnici x pravého dolního rohu obdélníkové oblasti.

*y2*<br/>
Určuje souřadnici y pravého dolního rohu obdélníkové oblasti.

*lpRect*<br/>
Určuje obdélníkovou oblast. Může být buď ukazatel `RECT` na `CRect` strukturu nebo objekt.

### <a name="remarks"></a>Poznámky

Na rozdíl od [CreateRectRgn](#createrectrgn)však nepřiděluje žádné další paměti z haldy místní aplikace systému Windows. Místo toho používá místo přidělené pro oblast `CRgn` uloženou v objektu. To znamená, `CRgn` že objekt již musí být inicializován s platnou oblastí systému Windows před voláním `SetRectRgn`. Body dané *x1*, *y1*, *x2*a *y2* určují minimální velikost přiděleného prostoru.

Pomocí této funkce `CreateRectRgn` namísto členské funkce se vyhnete volání správce místní paměti.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
