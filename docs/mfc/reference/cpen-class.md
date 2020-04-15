---
title: CPen – třída
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364073"
---
# <a name="cpen-class"></a>CPen – třída

Zapouzdřuje pero rozhraní grafického zařízení (Windows) (GDI).

## <a name="syntax"></a>Syntaxe

```
class CPen : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CPen::CPen](#cpen)|Vytvoří `CPen` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPen::Vytvořit pero](#createpen)|Vytvoří logické kosmetické nebo geometrické pero se zadaným stylem, šířkou a atributy stopy a připojí je k objektu. `CPen`|
|[CPen::CreatePenIndirect](#createpenindirect)|Vytvoří pero se stylem, šířkou a barvou danou ve struktuře `CPen` [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen) a připojí je k objektu.|
|[Cpen::FromHandle](#fromhandle)|Vrátí ukazatel na `CPen` objekt při dané Windows HPEN.|
|[CPen::GetExtLogPen](#getextlogpen)|Získá základní strukturu [EXTLOGPEN.](/windows/win32/api/wingdi/ns-wingdi-extlogpen)|
|[CPen::GetLogPen](#getlogpen)|Získá základní strukturu [LOGPEN.](/windows/win32/api/wingdi/ns-wingdi-logpen)|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CPen::operátor HPEN](#operator_hpen)|Vrátí popisovač systému `CPen` Windows připojený k objektu.|

## <a name="remarks"></a>Poznámky

Další informace o `CPen`použití naleznete v [tématu Grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CGdi](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen::CPen

Vytvoří `CPen` objekt.

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parametry

*nPenStyle*<br/>
Určuje styl pera. Tento parametr v první verzi konstruktoru může být jedna z následujících hodnot:

- PS_SOLID Vytvoří plné pero.

- PS_DASH Vytvoří přerušované pero. Platí pouze v případě, že šířka pera je 1 nebo méně, v jednotkách zařízení.

- PS_DOT Vytvoří tečkované pero. Platí pouze v případě, že šířka pera je 1 nebo méně, v jednotkách zařízení.

- PS_DASHDOT Vytvoří pero se střídavými pomlčkami a tečkami. Platí pouze v případě, že šířka pera je 1 nebo méně, v jednotkách zařízení.

- PS_DASHDOTDOT Vytvoří pero se střídavými pomlčkami a dvojitými tečkami. Platí pouze v případě, že šířka pera je 1 nebo méně, v jednotkách zařízení.

- PS_NULL Vytvoří pero s nulou.

- PS_INSIDEFRAME Vytvoří pero, které nakreslí čáru uvnitř rámečku uzavřených tvarů vytvořených výstupními funkcemi `Ellipse` `Rectangle`Windows `RoundRect` `Pie`GDI, které určují ohraničující obdélník (například , , , a `Chord` členské funkce). Pokud se tento styl používá s výstupními funkcemi GDI systému `LineTo` Windows, které neurčují ohraničující obdélník (například členská funkce), není kreslicí plocha pera omezena rámečkem.

Druhá verze konstruktoru `CPen` určuje kombinaci atributů typu, stylu, zakončení a spojení. Hodnoty z každé kategorie by měly být kombinovány pomocí bitového operátoru OR (&#124;). Typ pera může být jedna z následujících hodnot:

- PS_GEOMETRIC Vytvoří geometrické pero.

- PS_COSMETIC Vytvoří kosmetické pero.

   Druhá verze konstruktoru `CPen` přidá následující styly pera pro *nPenStyle*:

- PS_ALTERNATE Vytvoří pero, které nastaví každý druhý obrazový bod. (Tento styl je použitelný pouze pro kosmetická pera.)

- PS_USERSTYLE Vytvoří pero, které používá stylové pole dodané uživatelem.

   Koncová víčka může být jedna z následujících hodnot:

- PS_ENDCAP_ROUND Koncová čepička jsou kulatá.

- PS_ENDCAP_SQUARE Koncová čepička jsou čtvercová.

- PS_ENDCAP_FLAT Koncová víčka jsou plochá.

   Spojení může být jedna z následujících hodnot:

- PS_JOIN_BEVEL spojení jsou zužována.

- PS_JOIN_MITER Spojení jsou posety, pokud jsou v rámci aktuálního limitu nastaveného funkcí [SetMiterLimit.](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) Pokud spojení překročí tento limit, je znečaleno.

- PS_JOIN_ROUND spojení jsou kulatá.

*nŠířka*<br/>
Určuje šířku pera.

- Pro první verzi konstruktoru, pokud je tato hodnota 0, šířka v jednotkách zařízení je vždy 1 pixel, bez ohledu na režim mapování.

- Pro druhou verzi konstruktoru, pokud *nPenStyle* je PS_GEOMETRIC, šířka je uvedena v logických jednotkách. Pokud *nPenStyle* je PS_COSMETIC, šířka musí být nastavena na 1.

*crColor*<br/>
Obsahuje barvu RGB pro pero.

*pLogBrush*<br/>
Ukazuje na `LOGBRUSH` strukturu. Pokud *nPenStyle* je PS_COSMETIC, člen `LOGBRUSH` struktury *lbColor* určuje barvu pera a člen `LOGBRUSH` *lbStyle* struktury musí být nastavena na BS_SOLID. Pokud *nPenStyle* je PS_GEOMETRIC, všechny členy musí být použity k určení atributy stopy pera.

*nPočet stylů*<br/>
Určuje délku pole *lpStyle* v jednotkách doubleword. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyl*<br/>
Odkazuje na pole doubleword hodnoty. První hodnota určuje délku první pomlčky v uživatelem definovaném stylu, druhá hodnota určuje délku první mezery a tak dále. Tento ukazatel musí být NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="remarks"></a>Poznámky

Pokud používáte konstruktor bez argumentů, je nutné inicializovat `CPen` výsledný objekt pomocí `CreatePen`funkcí , `CreatePenIndirect`nebo `CreateStockObject` členské.

Pokud použijete konstruktor, který přebírá argumenty, není nutné žádné další inicializace. Konstruktor s argumenty může vyvolat výjimku, pokud dojde k chybám, zatímco konstruktor bez argumentů bude vždy úspěšné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::Vytvořit pero

Vytvoří logické kosmetické nebo geometrické pero se zadaným stylem, šířkou a atributy stopy a připojí je k objektu. `CPen`

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>Parametry

*nPenStyle*<br/>
Určuje styl pera. Seznam možných hodnot naleznete v parametru *nPenStyle* v konstruktoru [CPen.](#cpen)

*nŠířka*<br/>
Určuje šířku pera.

- Pro první verzi `CreatePen`aplikace , pokud je tato hodnota 0, šířka v jednotkách zařízení je vždy 1 pixel, bez ohledu na režim mapování.

- Pro druhou verzi `CreatePen`, pokud *nPenStyle* je PS_GEOMETRIC, šířka je uvedena v logických jednotkách. Pokud *nPenStyle* je PS_COSMETIC, šířka musí být nastavena na 1.

*crColor*<br/>
Obsahuje barvu RGB pro pero.

*pLogBrush*<br/>
Odkazuje na strukturu [LOGBRUSH.](/windows/win32/api/wingdi/ns-wingdi-logbrush) Pokud *nPenStyle* je `lbColor` PS_COSMETIC, `LOGBRUSH` člen struktury určuje barvu pera a člen `LOGBRUSH` *lbStyle* struktury musí být nastavena na BS_SOLID. Pokud nPenStyle je PS_GEOMETRIC, všechny členy musí být použity k určení atributy stopy pera.

*nPočet stylů*<br/>
Určuje délku pole *lpStyle* v jednotkách doubleword. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyl*<br/>
Odkazuje na pole doubleword hodnoty. První hodnota určuje délku první pomlčky v uživatelem definovaném stylu, druhá hodnota určuje délku první mezery a tak dále. Tento ukazatel musí být NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, nebo nula, pokud se metoda nezdaří.

### <a name="remarks"></a>Poznámky

První verze `CreatePen` inicializuje pero se zadaným stylem, šířkou a barvou. Pero lze následně vybrat jako aktuální pero pro libovolný kontext zařízení.

Pera, která mají šířku větší než 1 obrazový bod, by měla mít vždy styl PS_NULL, PS_SOLID nebo PS_INSIDEFRAME.

Pokud má pero PS_INSIDEFRAME styl a barvu, která neodpovídá barvě v tabulce logických barev, je pero nakresleno barvou s rozlišenou barvou. Styl PS_SOLID pera nelze použít k vytvoření pera s rozlišenou barvou. Styl PS_INSIDEFRAME je shodný s PS_SOLID, pokud je šířka pera menší nebo rovna 1.

Druhá verze `CreatePen` inicializuje logické kosmetické nebo geometrické pero, které má zadaný styl, šířku a atributy stopy. Šířka kosmetického pera je vždy 1; šířka geometrického pera je vždy specifikována ve světových jednotkách. Poté, co aplikace vytvoří logické pero, může vybrat toto pero do kontextu zařízení voláním funkce [CDC::SelectObject.](../../mfc/reference/cdc-class.md#selectobject) Po výběru pera do kontextu zařízení jej lze použít k nakreslení čar a křivek.

- Pokud *nPenStyle* je PS_COSMETIC a PS_USERSTYLE, položky v *poli lpStyle* určit délky pomlčky a mezery v jednotkách stylu. Jednotka stylu je definována zařízením, ve kterém se pero používá k nakreslení čáry.

- Pokud *nPenStyle* je PS_GEOMETRIC a PS_USERSTYLE, položky v *poli lpStyle* určit délky pomlčky a mezery v logických jednotkách.

- Pokud *nPenStyle* je PS_ALTERNATE, jednotka stylu je ignorována a každý jiný pixel je nastaven.

Pokud aplikace již nevyžaduje dané pero, měla by volat členskou funkci [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) nebo `CPen` zničit objekt, takže prostředek se již nepoužívá. Aplikace by neměla odstranit pero, pokud je pero vybráno v kontextu zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen::CreatePenIndirect

Inicializuje pero, které má styl, šířku a barvu danou ve struktuře, na kterou poukazuje *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parametry

*lpLogPen*<br/>
Odkazuje na strukturu Windows [LOGPEN,](/windows/win32/api/Wingdi/ns-wingdi-logpen) která obsahuje informace o peru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pera, která mají šířku větší než 1 obrazový bod, by měla mít vždy styl PS_NULL, PS_SOLID nebo PS_INSIDEFRAME.

Pokud má pero PS_INSIDEFRAME styl a barvu, která neodpovídá barvě v tabulce logických barev, je pero nakresleno barvou s rozlišenou barvou. Styl PS_INSIDEFRAME je shodný s PS_SOLID, pokud je šířka pera menší nebo rovna 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>Cpen::FromHandle

Vrátí ukazatel na `CPen` objekt s popisovačem pro objekt pera GDI systému Windows.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parametry

*hPero*<br/>
`HPEN`na pero GDI systému Windows.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPen` objekt, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud `CPen` objekt není připojen k popisovač, `CPen` dočasný objekt je vytvořen a připojen. Tento `CPen` dočasný objekt je platný pouze do příště aplikace má nečinnosti čas ve smyčce událostí, kdy jsou odstraněny všechny dočasné grafické objekty. Jinými slovy dočasný objekt je platný pouze během zpracování jedné zprávy okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen::GetExtLogPen

Získá `EXTLOGPEN` základní strukturu.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje na [strukturu EXTLOGPEN,](/windows/win32/api/wingdi/ns-wingdi-extlogpen) která obsahuje informace o peru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Struktura `EXTLOGPEN` definuje atributy stylu, šířky a stopy pera. Volání například `GetExtLogPen` odpovídá konkrétnímu stylu pera.

Informace o atributech pera naleznete v následujících tématech sady Windows SDK:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetExtLogPen` volání načíst atributy pera a potom vytvořit nové kosmetické pero se stejnou barvou.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen::GetLogPen

Získá `LOGPEN` základní strukturu.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje na [strukturu LOGPEN,](/windows/win32/api/wingdi/ns-wingdi-logpen) která obsahuje informace o peru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Struktura `LOGPEN` definuje styl, barvu a vzorek pera.

Například volání, `GetLogPen` aby odpovídaly konkrétní styl pera.

Informace o atributech pera naleznete v následujících tématech sady Windows SDK:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetLogPen` volání načíst znak pera a potom vytvořte nové, plné pero se stejnou barvou.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::operátor HPEN

Získá připojené popisovače GDI `CPen` systému Windows objektu.

```
operator HPEN() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu GDI systému Windows reprezentovaný objektem; `CPen` jinak NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HPEN.

Další informace o používání grafických objektů naleznete v článku [Grafické objekty](/windows/win32/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Viz také

[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBrush – třída](../../mfc/reference/cbrush-class.md)
