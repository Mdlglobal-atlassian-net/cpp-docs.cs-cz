---
title: CPen – – třída
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
ms.openlocfilehash: 952d270acd47b5834a06b731f7875ea2efdd4695
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502941"
---
# <a name="cpen-class"></a>CPen – – třída

Zapouzdřuje pero rozhraní grafického zařízení (GDI) systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CPen : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPen –:: CPen –](#cpen)|`CPen` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|Vytvoří logický kosmetické nebo geometrické pero se zadaným stylem, šířkou a štětcem a připojí ho k `CPen` objektu.|
|[CPen::CreatePenIndirect](#createpenindirect)|Vytvoří pero se stylem, šířkou a barvou zadanou ve struktuře [LOGPEN –](/windows/win32/api/wingdi/ns-wingdi-logpen) a připojí ho k `CPen` objektu.|
|[CPen –:: FromHandle](#fromhandle)|Vrací ukazatel na `CPen` objekt v případě, že je zadán systém Windows HPEN.|
|[CPen::GetExtLogPen](#getextlogpen)|Získá podkladovou strukturu [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) .|
|[CPen::GetLogPen](#getlogpen)|Získá podkladovou strukturu [LOGPEN –](/windows/win32/api/wingdi/ns-wingdi-logpen) .|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CPen –:: operator HPEN](#operator_hpen)|Vrátí popisovač systému Windows připojený k `CPen` objektu.|

## <a name="remarks"></a>Poznámky

Další informace o použití `CPen`naleznete v tématu [Graphics Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cpen"></a>CPen –:: CPen –

`CPen` Vytvoří objekt.

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

- PS_SOLID vytvoří plné pero.

- PS_DASH vytvoří přerušované pero. Platí pouze v případě, že je šířka pera na 1 nebo méně, v jednotkách zařízení.

- PS_DOT vytvoří tečkované pero. Platí pouze v případě, že je šířka pera na 1 nebo méně, v jednotkách zařízení.

- PS_DASHDOT vytvoří pero se střídavými pomlčkami a tečkami. Platí pouze v případě, že je šířka pera na 1 nebo méně, v jednotkách zařízení.

- PS_DASHDOTDOT vytvoří pero se střídavými pomlčkami a dvojitými tečkami. Platí pouze v případě, že je šířka pera na 1 nebo méně, v jednotkách zařízení.

- PS_NULL vytvoří pero s hodnotou null.

- PS_INSIDEFRAME vytvoří pero, které vykreslí čáru uvnitř uzavřených tvarů vytvořených výstupními funkcemi `Ellipse`GDI systému Windows, které určují ohraničující obdélník (například `Rectangle`,, `RoundRect` `Pie`, a `Chord`členské funkce). Pokud se tento styl používá u výstupních funkcí GDI systému Windows, které neurčují ohraničující obdélník (například `LineTo` členské funkce), oblast kreslení pera není omezena rámečkem.

Druhá verze `CPen` konstruktoru určuje kombinaci atributů typ, styl, zakončení a spojení. Hodnoty z každé kategorie by měly být kombinovány pomocí bitového operátoru OR&#124;(). Typ pera může být jedna z následujících hodnot:

- PS_GEOMETRIC vytvoří geometrické pero.

- PS_COSMETIC vytvoří kosmetické pero.

   Druhá verze `CPen` konstruktoru přidává následující styly pera pro *nPenStyle*:

- PS_ALTERNATE vytvoří pero, které nastaví všechny ostatní pixely. (Tento styl se vztahuje pouze na kosmetické pero.)

- PS_USERSTYLE vytvoří pero, které používá pole stylu poskytované uživatelem.

   Koncová hodnota může být jedna z následujících hodnot:

- PS_ENDCAP_ROUND konce jsou zaoblené.

- Zakončení PS_ENDCAP_SQUARE jsou čtvercová.

- Zakončení PS_ENDCAP_FLAT jsou plochá.

   Spojení může být jedna z následujících hodnot:

- Spojení PS_JOIN_BEVEL se zkosí.

- Spojení PS_JOIN_MITER jsou ostrý, pokud jsou v rámci aktuálního limitu nastaveného funkcí [SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) . Pokud spojení tento limit překročí, bude zkosený.

- PS_JOIN_ROUND spojení jsou kulatá.

*nWidth*<br/>
Určuje šířku pera.

- V první verzi konstruktoru, pokud je tato hodnota 0, Šířka v jednotkách zařízení je vždy 1 pixel bez ohledu na režim mapování.

- V případě druhé verze konstruktoru, pokud je *NPENSTYLE* PS_GEOMETRIC, je šířka uvedena v logických jednotkách. Pokud je *NPENSTYLE* PS_COSMETIC, Šířka musí být nastavená na 1.

*crColor*<br/>
Obsahuje barvu RGB pro pero.

*pLogBrush*<br/>
Odkazuje na `LOGBRUSH` strukturu. Pokud je *nPenStyle* PS_COSMETIC, `LOGBRUSH` člen *lbColor* struktury určuje barvu pera `LOGBRUSH` a člen *lbStyle* struktury musí být nastaven na BS_SOLID. Pokud je *NPENSTYLE* PS_GEOMETRIC, musí být pro zadání atributů štětce použity všichni členové.

*nStyleCount*<br/>
Určuje délku pole *lpStyle* v jednotkách doubleword. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyle*<br/>
Odkazuje na pole hodnot doubleword. První hodnota určuje délku první pomlčky v uživatelsky definovaném stylu, druhá hodnota určuje délku prvního prostoru a tak dále. Tento ukazatel musí mít hodnotu NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="remarks"></a>Poznámky

Použijete-li konstruktor bez argumentů, je nutné inicializovat `CPen` výsledný objekt `CreatePen`pomocí funkcí, `CreatePenIndirect`nebo `CreateStockObject` .

Použijete-li konstruktor, který přebírá argumenty, není nutné provádět žádnou další inicializaci. Konstruktor s argumenty může vyvolat výjimku, pokud dojde k chybám, ale konstruktor bez argumentů bude vždy úspěšný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>CPen –:: CreatePen

Vytvoří logický kosmetické nebo geometrické pero se zadaným stylem, šířkou a štětcem a připojí ho k `CPen` objektu.

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
Určuje styl pera. Seznam možných hodnot naleznete v parametru *nPenStyle* v konstruktoru [CPen –](#cpen) .

*nWidth*<br/>
Určuje šířku pera.

- U první verze `CreatePen`nástroje platí, že pokud je tato hodnota 0, Šířka v jednotkách zařízení je vždy 1 pixel bez ohledu na režim mapování.

- V případě druhé verze `CreatePen`nástroje, pokud je *nPenStyle* PS_GEOMETRIC, je šířka uvedena v logických jednotkách. Pokud je *NPENSTYLE* PS_COSMETIC, Šířka musí být nastavená na 1.

*crColor*<br/>
Obsahuje barvu RGB pro pero.

*pLogBrush*<br/>
Odkazuje na strukturu [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) . Pokud *je nPenStyle* PS_COSMETIC, `lbColor` člen `LOGBRUSH` struktury určuje barvu `LOGBRUSH` pera a člen *lbStyle* struktury musí být nastaven na BS_SOLID. Pokud je nPenStyle PS_GEOMETRIC, musí být pro zadání atributů štětce použity všichni členové.

*nStyleCount*<br/>
Určuje délku pole *lpStyle* v jednotkách doubleword. Tato hodnota musí být nula, pokud *nPenStyle* není PS_USERSTYLE.

*lpStyle*<br/>
Odkazuje na pole hodnot doubleword. První hodnota určuje délku první pomlčky v uživatelsky definovaném stylu, druhá hodnota určuje délku prvního prostoru a tak dále. Tento ukazatel musí mít hodnotu NULL, pokud *nPenStyle* není PS_USERSTYLE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je to úspěšné, nebo nula, pokud se metoda nezdařila.

### <a name="remarks"></a>Poznámky

První verze `CreatePen` inicializuje pero se zadaným stylem, šířkou a barvou. Pero lze následně vybrat jako aktuální pero pro libovolný kontext zařízení.

Pro pera, které mají šířku větší než 1 pixel, by měla být vždy buď styl PS_NULL, PS_SOLID, nebo PS_INSIDEFRAME.

Pokud má pero styl PS_INSIDEFRAME a barvu, která se neshoduje s barvou v tabulce logických barev, pero se vykreslí pomocí barevně barvené barvy. Styl pera PS_SOLID nelze použít k vytvoření pera se barevnou barvou. Styl PS_INSIDEFRAME je stejný jako PS_SOLID, pokud je šířka pera menší nebo rovna 1.

Druhá verze `CreatePen` inicializuje logický kosmetické nebo geometrické pero, který má zadaný atribut Style, Width a štětec. Šířka symbolického pera je vždy 1; Šířka geometrického pera je vždy určena v jednotkách světa. Poté, co aplikace vytvoří logické pero, může toto pero vybrat do kontextu zařízení voláním funkce [CDC:: VybratObjekt](../../mfc/reference/cdc-class.md#selectobject) . Po výběru pera do kontextu zařízení lze použít k vykreslení čar a křivek.

- Pokud je *NPENSTYLE* PS_COSMETIC a PS_USERSTYLE, položky v poli *lpStyle* určují délky pomlček a mezer v jednotkách stylu. Jednotka stylu je definována zařízením, ve kterém se pero používá k nakreslení čáry.

- Pokud je *NPENSTYLE* PS_GEOMETRIC a PS_USERSTYLE, položky v poli *lpStyle* určují délky pomlček a mezer v logických jednotkách.

- Pokud je *NPENSTYLE* PS_ALTERNATE, jednotka stylu se ignoruje a nanastaví se všechny ostatní pixely.

Pokud aplikace již nevyžaduje dané pero, měla by zavolat členskou funkci [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) nebo zničit `CPen` objekt, aby se prostředek již nepoužíval. Aplikace by neměla odstranit pero, pokud je pero vybráno v kontextu zařízení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>CPen –:: CreatePenIndirect

Inicializuje pero, který má styl, šířku a barvu určenou ve struktuře, na kterou odkazuje *lpLogPen*.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>Parametry

*lpLogPen*<br/>
Odkazuje na strukturu [LOGPEN –](/windows/win32/api/Wingdi/ns-wingdi-logpen) systému Windows, která obsahuje informace o Peru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pro pera, které mají šířku větší než 1 pixel, by měla být vždy buď styl PS_NULL, PS_SOLID, nebo PS_INSIDEFRAME.

Pokud má pero styl PS_INSIDEFRAME a barvu, která se neshoduje s barvou v tabulce logických barev, pero se vykreslí pomocí barevně barvené barvy. Styl PS_INSIDEFRAME je stejný jako PS_SOLID, pokud je šířka pera menší nebo rovna 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>CPen –:: FromHandle

Vrátí ukazatel na `CPen` objekt s daným popisovačem na objekt pera Windows GDI.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>Parametry

*hPen*<br/>
`HPEN`pořídí pero Windows GDI.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPen` objekt v případě úspěchu; jinak null.

### <a name="remarks"></a>Poznámky

Pokud objekt není připojen k popisovači, je vytvořen a připojen `CPen` dočasný objekt. `CPen` Tento dočasný `CPen` objekt je platný pouze do příštího okamžiku, kdy aplikace nebude mít čas nečinnosti ve smyčce události, kdy jsou odstraněny všechny dočasné grafické objekty. Jinými slovy, dočasný objekt je platný pouze během zpracování jedné zprávy okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>CPen –:: GetExtLogPen

`EXTLOGPEN` Načte podkladovou strukturu.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje na strukturu [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen) , která obsahuje informace o Peru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`EXTLOGPEN` Struktura definuje styl, šířku a atributy štětce pro pero. Například volejte `GetExtLogPen` , aby odpovídalo konkrétnímu stylu pera.

Další informace o atributech pera najdete v následujících tématech Windows SDK.

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN –](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak `GetExtLogPen` zavolat k načtení atributů pera a pak vytvořit nové kosmetické pero se stejnou barvou.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>CPen –:: GetLogPen

`LOGPEN` Získá podkladovou strukturu.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>Parametry

*pLogPen*<br/>
Odkazuje na strukturu [LOGPEN –](/windows/win32/api/wingdi/ns-wingdi-logpen) , aby obsahovala informace o Peru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`LOGPEN` Struktura definuje styl, barvu a vzor pera.

Například volejte `GetLogPen` , aby odpovídalo konkrétnímu stylu pera.

Další informace o atributech pera najdete v následujících tématech Windows SDK.

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN –](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak `GetLogPen` zavolat k načtení znaku pera a pak vytvořit nové, plné pero se stejnou barvou.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>CPen –:: operator HPEN

Získá připojenou obslužnou rutinu `CPen` rozhraní Windows GDI objektu.

```
operator HPEN() const;
```

### <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, popisovač objektu GDI systému Windows reprezentovaný `CPen` objektem; v opačném případě hodnota null.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, který podporuje přímé použití objektu HPEN.

Další informace o použití grafických objektů naleznete v článku [grafické objekty](/windows/win32/gdi/graphic-objects) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>Viz také:

[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CBrush – třída](../../mfc/reference/cbrush-class.md)
