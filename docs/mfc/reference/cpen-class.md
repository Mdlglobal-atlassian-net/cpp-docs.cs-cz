---
title: Cpen – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6e8f448d4b6bee4b301fc567cc8e8e857747a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440287"
---
# <a name="cpen-class"></a>Cpen – třída

Zapouzdřuje pero rozhraní GDI systému Windows grafiky zařízení.

## <a name="syntax"></a>Syntaxe

```
class CPen : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPen::CPen](#cpen)|Vytvoří `CPen` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Vytvoří logický kosmetické nebo geometrické pera určený styl, šířku a atributy štětce a připojí ho k `CPen` objektu.|
|[CPen::CreatePenIndirect](#createpenindirect)|Vytvoří pera s styl, šířku a barvu podle [logpen –](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) struktury a připojí ho k `CPen` objektu.|
|[CPen::FromHandle](#fromhandle)|Vrací ukazatel `CPen` objektu při Windows HPEN.|
|[CPen::GetExtLogPen](#getextlogpen)|Získá [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) základní struktury.|
|[CPen::GetLogPen](#getlogpen)|Získá [logpen –](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) základní struktury.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CPen::operator HPEN](#operator_hpen)|Vrátí popisovač Windows připojené k `CPen` objektu.|

## <a name="remarks"></a>Poznámky

Další informace o používání `CPen`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cgdiobject –](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cpen"></a>  CPen::CPen

Vytvoří `CPen` objektu.

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
Určuje styl psaní perem. Tento parametr v první verzi konstruktoru může být jeden z následujících hodnot:

- PS_SOLID vytvoří solid pera.

- PS_DASH vytváří čárkovanou pera. Platné pouze v případě, že šířka pera je 1 nebo žádnou skupinou, v zařízení jednotky.

- PS_DOT vytvoří tečkovaná pera. Platné pouze v případě, že šířka pera je 1 nebo žádnou skupinou, v zařízení jednotky.

- Vytvoří PS_DASHDOT pera s různými pomlčky a tečky. Platné pouze v případě, že šířka pera je 1 nebo žádnou skupinou, v zařízení jednotky.

- PS_DASHDOTDOT vytvoří a psaní perem s různými pomlčky a tečky double. Platné pouze v případě, že šířka pera je 1 nebo žádnou skupinou, v zařízení jednotky.

- PS_NULL vytvoří null pera.

- Funkce, které určují ohraničující obdélník PS_INSIDEFRAME vytvoří pera nakreslí čáru uvnitř rámečku uzavřených obrazců vytvořený ve Windows GDI výstup (například `Ellipse`, `Rectangle`, `RoundRect`, `Pie`a `Chord`členské funkce). Při použití tohoto stylu s Windows GDI výstup funkce, které neurčují ohraničující obdélník (například `LineTo` členská funkce), oblasti pro kreslení pera není omezeno rámečkem.

Druhá verze `CPen` konstruktor Určuje kombinaci typu, styl, zakončení a atributy spojení. Hodnoty z jednotlivých kategorií by měly být kombinované pomocí bitového operátoru OR (&#124;). Psaní perem typ může být jeden z následujících hodnot:

- PS_GEOMETRIC vytvoří geometrické pera.

- PS_COSMETIC vytvoří kosmetické pera.

     Druhá verze `CPen` konstruktor přidá následující styly pero *nPenStyle*:

- PS_ALTERNATE vytvoří pera, který nastaví každý pixel. (Tento styl je možné použít pouze kosmetické pera.)

- Vytvoří PS_USERSTYLE pera, která používá pole stylu zadaných uživatelem.

     Zakončení může být jedna z následujících hodnot:

- Zakončení PS_ENDCAP_ROUND jsou kola.

- Zakončení PS_ENDCAP_SQUARE jsou čtvereček.

- Zakončení PS_ENDCAP_FLAT jsou bez stromové struktury.

     Připojení může být jedna z následujících hodnot:

- Jsou sený PS_JOIN_BEVEL připojí.

- Připojí PS_JOIN_MITER jsou zkosené když jsou v rámci aktuální limit nastavil [SetMiterLimit](/windows/desktop/api/wingdi/nf-wingdi-setmiterlimit) funkce. Pokud připojení překročí tento limit, je sený.

- Připojí PS_JOIN_ROUND jsou kola.

*nWidth*<br/>
Určuje šířku pera.

- Pro první verzi konstruktoru Pokud je tato hodnota 0, je vždy 1 pixelu, bez ohledu na režim mapování šířku v jednotkách zařízení.

- Pro druhý verze konstruktoru Pokud *nPenStyle* je PS_GEOMETRIC, šířku je uveden v logických jednotkách. Pokud *nPenStyle* je PS_COSMETIC, šířka musí být nastavena na hodnotu 1.

*crColor*<br/>
Obsahuje barva RGB pro pero.

*pLogBrush*<br/>
Odkazuje `LOGBRUSH` struktury. Pokud *nPenStyle* PS_COSMETIC, je *lbColor* člena `LOGBRUSH` struktura Určuje barvu pera a *lbStyle* člena `LOGBRUSH` struktura musí být nastavena na BS_SOLID. Pokud *nPenStyle* PS_GEOMETRIC, je třeba zadat všechny členy pro zadání atributů štětce, pera.

*nStyleCount*<br/>
Určuje délku v jednotkách doubleword *lpStyle* pole. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyle*<br/>
Odkazuje na pole hodnot dvojitého slova. První hodnota určuje první dash ve stylu definovaný uživatelem, druhá hodnota udává délku první místo a tak dále. This – ukazatel musí mít hodnotu NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="remarks"></a>Poznámky

Pokud použijete konstruktor bez argumentů, musí inicializovat výsledný `CPen` objektu `CreatePen`, `CreatePenIndirect`, nebo `CreateStockObject` členské funkce.

Pokud použijete konstruktor, který přebírá argumenty, žádné další inicializaci je nezbytné. Konstruktor s argumenty může vyvolat výjimku, pokud nedojde k chybám, když bude vždy úspěšné konstruktor bez argumentů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>  CPen::CreatePen

Vytvoří logický kosmetické nebo geometrické pera určený styl, šířku a atributy štětce a připojí ho k `CPen` objektu.

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
Určuje styl pera. Seznam možných hodnot, najdete v článku *nPenStyle* parametr [cpen –](#cpen) konstruktoru.

*nWidth*<br/>
Určuje šířku pera.

- Pro první verzi `CreatePen`, pokud je tato hodnota 0, šířku v jednotkách zařízení je vždy 1 pixelu, bez ohledu na režim mapování.

- Pro druhou verzi `CreatePen`, pokud *nPenStyle* je PS_GEOMETRIC, šířku je uveden v logických jednotkách. Pokud *nPenStyle* je PS_COSMETIC, šířka musí být nastavena na hodnotu 1.

*crColor*<br/>
Obsahuje barva RGB pro pero.

*pLogBrush*<br/>
Odkazuje [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) struktury. Pokud *nPenStyle* PS_COSMETIC, je `lbColor` člena `LOGBRUSH` struktura Určuje barvu pera a *lbStyle* člena `LOGBRUSH` struktura musí být nastaveno na BS_ PLNÁ. Je-li nPenStyle PS_GEOMETRIC, všichni členové musí využívat pro zadání atributů štětce, pera.

*nStyleCount*<br/>
Určuje délku v jednotkách doubleword *lpStyle* pole. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyle*<br/>
Odkazuje na pole hodnot dvojitého slova. První hodnota určuje první dash ve stylu definovaný uživatelem, druhá hodnota udává délku první místo a tak dále. This – ukazatel musí mít hodnotu NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, nebo nula, pokud metoda selže.

### <a name="remarks"></a>Poznámky

První verze `CreatePen` inicializuje s určený styl, šířku a barvu pera. Pera je následně vybrat jako aktuální pero pro jakýkoli kontext zařízení.

Pera, které mají větší než 1 pixelu šířku by měl mít vždy PS_NULL, PS_SOLID nebo PS_INSIDEFRAME style.

Pokud pera PS_INSIDEFRAME styl a barvy, který neodpovídá barvu v tabulce barev logické, pera je vykreslen s tónovaná barva. Styl psaní perem PS_SOLID nelze použít k vytvoření pera dithered pro bitové barvou. Styl PS_INSIDEFRAME se shoduje s PS_SOLID, pokud je šířka pera menší než nebo rovno 1.

Druhá verze `CreatePen` inicializuje logické kosmetické nebo geometrické pera, který má zadaný styl, šířku a štětce atributy. Šířka pera kosmetické je vždy 1; Šířka pera geometrické je vždy určena v celém světě jednotkách. Jakmile aplikace vytvoří logické pera, ho vyberte pera kontextu zařízení voláním [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkce. Po výběru pera kontextu zařízení, můžete použít k vykreslení čar a křivek.

- Pokud *nPenStyle* PS_COSMETIC a PS_USERSTYLE položky *lpStyle* pole zadejte délku pomlčky a mezery v jednotkách style. Styl jednotka je definována zařízení, ve kterém se pera používá k nakreslení čáry.

- Pokud *nPenStyle* PS_GEOMETRIC a PS_USERSTYLE položky *lpStyle* pole zadejte délku pomlčky a mezery v logických jednotkách.

- Pokud *nPenStyle* PS_ALTERNATE, ignorován styl jednotky a nastavit každý pixel.

Když aplikace již nevyžaduje dané pera, měla by volat [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členské funkce nebo zničit `CPen` objektu, prostředek se už používá. Aplikace by neměl odstranit pera, při výběru pera v kontextu zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect

Inicializuje pera, který má styl, šířku a barvu uvedené ve struktuře, na které odkazuje *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parametry

*lpLogPen*<br/>
Odkazuje Windows [logpen –](../../mfc/reference/logpen-structure.md) strukturu, která obsahuje informace o pera.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pera, které mají větší než 1 pixelu šířku by měl mít vždy PS_NULL, PS_SOLID nebo PS_INSIDEFRAME style.

Pokud pera PS_INSIDEFRAME styl a barvy, který neodpovídá barvu v tabulce barev logické, pera je vykreslen s tónovaná barva. Pokud šířka pera je menší než nebo rovno 1 se shoduje s PS_SOLID PS_INSIDEFRAME style.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>  CPen::FromHandle

Vrací ukazatel `CPen` objekt daný popisovač pro objekt pen Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parametry

*hPen*<br/>
`HPEN` Popisovač Windows GDI pera.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CPen` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CPen` objekt není připojen ke zpracování, dočasný `CPen` objekt se vytvoří a připojí. Tento dočasný `CPen` objektu je platná pouze v až při příštím má aplikace čas nečinnosti v jeho smyčkou událostí, na které čas všechny dočasné obrázek objekty budou odstraněny. Jinými slovy dočasný objekt je platná pouze při zpracování zprávy jedno okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>  CPen::GetExtLogPen

Získá `EXTLOGPEN` základní struktury.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje na [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen) strukturu, která obsahuje informace o pera.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

`EXTLOGPEN` Struktury definuje styl, šířku a atributy štětce, pera. Například volání `GetExtLogPen` tak, aby odpovídaly konkrétního stylu pera.

Naleznete v následujících tématech v sadě Windows SDK informace o psaní perem atributy:

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)

- [LOGPEN –](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

- [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje volání `GetExtLogPen` načtení atributů na pero a potom vytvořit nové, kosmetické pera stejné barvy.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

Získá `LOGPEN` základní struktury.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje [logpen –](/windows/desktop/api/wingdi/ns-wingdi-taglogpen) struktura bude obsahovat informace o pera.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

`LOGPEN` Struktury definuje styl, barvu a vzor pera.

Například volání `GetLogPen` tak, aby odpovídaly konkrétní styl psaní perem.

Naleznete v následujících tématech v sadě Windows SDK informace o psaní perem atributy:

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [LOGPEN –](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje volání `GetLogPen` načtení pera znak, a pak vytvoříte novou, solid pera se stejnou barvu.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>  CPen::operator HPEN

Získá popisovač Windows GDI připojené `CPen` objektu.

```
operator HPEN() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud úspěchu popisovač objektů Windows GDI reprezentována `CPen` objektu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, která podporuje přímému použití objektu HPEN.

Další informace o použití grafických objektů najdete v článku [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Viz také

[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBrush – třída](../../mfc/reference/cbrush-class.md)
