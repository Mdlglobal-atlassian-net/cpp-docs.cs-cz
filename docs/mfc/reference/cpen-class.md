---
title: "CPen – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c06467c49c4b1d3013a69fdc749b8acb17cae0dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cpen-class"></a>CPen – třída
Zapouzdří pera Windows zařízení grafické rozhraní (GDI).  
  
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
|[CPen::CreatePen](#createpen)|Vytvoří logickou kosmetické nebo geometrickou pera s určený styl, šířku a atributy štětce a připojí jej k `CPen` objektu.|  
|[CPen::CreatePenIndirect](#createpenindirect)|Vytvoří pera styl, šířku a barvu uvedené v [logpen –](http://msdn.microsoft.com/library/windows/desktop/dd145041) struktury a připojí jej k `CPen` objektu.|  
|[CPen::FromHandle](#fromhandle)|Vrátí ukazatel `CPen` objektu při zadané Windows `HPEN`.|  
|[CPen::GetExtLogPen](#getextlogpen)|Získá [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) základní struktura.|  
|[CPen::GetLogPen](#getlogpen)|Získá [logpen –](http://msdn.microsoft.com/library/windows/desktop/dd145041) základní struktura.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|Vrátí popisovač Windows připojené k `CPen` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o používání `CPen`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cpen"></a>CPen::CPen  
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
 `nPenStyle`  
 Určuje styl pera. Tento parametr v první verzi konstruktor může být jedna z následujících hodnot:  
  
- **PS_SOLID** vytvoří pera plnou.  
  
- **PS_DASH** vytvoří pera přerušovanou. Platné jenom v případě, že šířku pera je jednotky 1 nebo méně, v zařízení.  
  
- **PS_DOT** vytvoří pera s tečkou. Platné jenom v případě, že šířku pera je jednotky 1 nebo méně, v zařízení.  
  
- **PS_DASHDOT** vytvoří pera s různými pomlčky a tečky. Platné jenom v případě, že šířku pera je jednotky 1 nebo méně, v zařízení.  
  
- **PS_DASHDOTDOT** vytvoří pera s různými pomlčky a tečky double. Platné jenom v případě, že šířku pera je jednotky 1 nebo méně, v zařízení.  
  
- **PS_NULL** vytvoří pera hodnotu null.  
  
- **PS_INSIDEFRAME** vytvoří pera, který se vykreslí řádku uvnitř rámečku uzavřené obrazce vytvořeného pomocí funkcí výstup GDI systému Windows, které určují ohraničující obdélník (například **elipsy**, **obdélníku** , `RoundRect`, `Pie`, a `Chord` členské funkce). Když tento styl se používá s funkcemi výstup GDI systému Windows, které neurčují ohraničující obdélník (například `LineTo` – členská funkce), oblasti výkresu pera není omezeno rámečku.  
  
 Druhá verze `CPen` konstruktor Určuje kombinaci typu, stylu, zakončení a atributy spojení. Hodnoty z každé kategorie by měl společně s použitím bitový operátor OR (&#124;). Typ pera může být jedna z následujících hodnot:  
  
- **PS_GEOMETRIC** vytvoří pera geometrickou.  
  
- **PS_COSMETIC** vytvoří pera kosmetická.  
  
     Druhá verze `CPen` konstruktor přidá následující styly pera pro `nPenStyle`:  
  
- **PS_ALTERNATE** vytvoří pera, který nastaví všechny ostatní pixelů. (Tento styl lze použít pouze u kosmetické pera.)  
  
- **PS_USERSTYLE** vytvoří pera používá pole stylů zadané uživatelem.  
  
     Krytky end může být jedna z následujících hodnot:  
  
- **PS_ENDCAP_ROUND** se zaokrouhlí zakončení.  
  
- **PS_ENDCAP_SQUARE** jsou odmocnina zakončení.  
  
- **PS_ENDCAP_FLAT** jsou ploché zakončení.  
  
     Spojení, může být jedna z následujících hodnot:  
  
- **PS_JOIN_BEVEL** jsou zkosené spojení.  
  
- **PS_JOIN_MITER** spojení jsou ostrého když jsou v rámci aktuální limit nastaven [SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076) funkce. Pokud připojení k překračuje tento limit, je zkosené.  
  
- **PS_JOIN_ROUND** spojení se zaokrouhlí.  
  
 `nWidth`  
 Určuje šířku pera.  
  
-   Pro první verze součásti konstruktoru Pokud je tato hodnota 0, je vždy 1 pixel, bez ohledu na režim mapování šířku v jednotkách zařízení.  
  
-   Pro druhou verzi konstruktoru Pokud `nPenStyle` je **PS_GEOMETRIC**, šířka je uveden v logické jednotky. Pokud `nPenStyle` je **PS_COSMETIC**, šířka musí být nastavena na hodnotu 1.  
  
 `crColor`  
 Obsahuje barva RGB pro pero.  
  
 `pLogBrush`  
 Odkazuje na `LOGBRUSH` struktury. Pokud `nPenStyle` je **PS_COSMETIC**, `lbColor` členem `LOGBRUSH` struktura Určuje barvu pera a `lbStyle` členem `LOGBRUSH` struktury musí být nastavena na **BS_ PLNOU**. Pokud `nPenStyle` je **PS_GEOMETRIC**, všechny členy, musí se použít k zadání atributy štětce pera.  
  
 `nStyleCount`  
 Určuje délku v jednotkách doubleword z `lpStyle` pole. Tato hodnota musí být nula v případě `nPenStyle` není **PS_USERSTYLE**.  
  
 `lpStyle`  
 Bodů na pole hodnot doubleword. První hodnota určuje první čárka ve stylu definovaný uživatelem, druhá hodnota udává délku první místa a tak dále. Musí být tento ukazatel **NULL** Pokud `nPenStyle` není **PS_USERSTYLE**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte konstruktor bez argumentů, musí inicializovat výsledná `CPen` objektu s `CreatePen`, `CreatePenIndirect`, nebo `CreateStockObject` členské funkce.  
  
 Pokud chcete použít konstruktor, který přebírá argumenty, žádné další inicializaci je nezbytné. Konstruktor bez argumentů může vyvolat výjimku, pokud dojde k chybám, když bude vždy úspěšné konstruktor bez argumentů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>CPen::CreatePen  
 Vytvoří logickou kosmetické nebo geometrickou pera s určený styl, šířku a atributy štětce a připojí jej k `CPen` objektu.  
  
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
 `nPenStyle`  
 Určuje styl pro pero. Seznam možných hodnot najdete v tématu `nPenStyle` parametr ve [CPen](#cpen) konstruktor.  
  
 `nWidth`  
 Určuje šířku pera.  
  
-   Pro první verze součásti `CreatePen`, pokud je tato hodnota je 0, šířka v jednotkách zařízení je vždy 1 pixel, bez ohledu na režim mapování.  
  
-   Pro druhou verzi `CreatePen`, pokud `nPenStyle` je **PS_GEOMETRIC**, šířka je uveden v logické jednotky. Pokud `nPenStyle` je **PS_COSMETIC**, šířka musí být nastavena na hodnotu 1.  
  
 `crColor`  
 Obsahuje barva RGB pro pero.  
  
 `pLogBrush`  
 Odkazuje na [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura. Pokud `nPenStyle` je **PS_COSMETIC**, **lbColor** členem `LOGBRUSH` struktura Určuje barvu pera a `lbStyle` členem `LOGBRUSH` musí být struktura Nastavte na **BS_SOLID**. Pokud **nPenStyle** je **PS_GEOMETRIC**, všechny členy, musí se použít k zadání atributy štětce pera.  
  
 `nStyleCount`  
 Určuje délku v jednotkách doubleword z `lpStyle` pole. Tato hodnota musí být nula v případě `nPenStyle` není **PS_USERSTYLE**.  
  
 `lpStyle`  
 Bodů na pole hodnot doubleword. První hodnota určuje první čárka ve stylu definovaný uživatelem, druhá hodnota udává délku první místa a tak dále. Musí být tento ukazatel **NULL** Pokud `nPenStyle` není **PS_USERSTYLE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, nebo nula, pokud metoda selže.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti `CreatePen` inicializuje pera s určený styl, šířku a barvu. Pera lze následně vybrat jako aktuální pero pro jakýkoli kontext zařízení.  
  
 Pera, které mají větší než 1 pixel by měl mít vždy buď šířku **PS_NULL**, **PS_SOLID**, nebo **PS_INSIDEFRAME** stylu.  
  
 Pokud má pera **PS_INSIDEFRAME** stylu a barvy, která neodpovídá barvu v tabulce barev logické pera vykreslením s tónovaná barva. **PS_SOLID** styl pera nelze použít k vytvoření pera s tónovaná barva. Styl **PS_INSIDEFRAME** je stejný jako **PS_SOLID** Pokud šířku pera je menší než nebo rovna 1.  
  
 Druhá verze `CreatePen` inicializuje logické kosmetické nebo geometrickou pera, který má zadaný styl, šířku a zdokonalit atributy. Šířka pera kosmetické je vždy 1; Šířka pera geometrickou je vždy určen v jednotkách world. Jakmile aplikace vytvoří logické pera, můžete ho vybrat pera v kontextu zařízení voláním [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkce. Po výběru pera se v kontextu zařízení, můžete použít k vykreslení čar a křivek.  
  
-   Pokud `nPenStyle` je **PS_COSMETIC** a **PS_USERSTYLE**, položky v `lpStyle` pole zadejte délky čárek a mezer v jednotkách stylu. Styl jednotka je definována podle zařízení, ve kterém se používá pera kreslení čáry.  
  
-   Pokud `nPenStyle` je **PS_GEOMETRIC** a **PS_USERSTYLE**, položky v `lpStyle` pole zadejte délky čárek a mezer v logické jednotky.  
  
-   Pokud `nPenStyle` je **PS_ALTERNATE**, styl jednotky je ignorována a bude nastavena každých dalších pixelů.  
  
 Pokud aplikace vyžaduje už danou pera, by měly volat [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) členské funkce nebo zničení `CPen` objektu, prostředek je již používán. Aplikace by neměl odstranit pera, když pera je vybraný v kontextu zařízení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>CPen::CreatePenIndirect  
 Inicializuje pera, který má styl, šířku a barvu uvedené ve struktuře, na kterou odkazuje `lpLogPen`.  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPen`  
 Odkazuje na Windows [logpen –](../../mfc/reference/logpen-structure.md) struktura, která obsahuje informace o pera.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pera, které mají větší než 1 pixel by měl mít vždy buď šířku **PS_NULL**, **PS_SOLID**, nebo **PS_INSIDEFRAME** stylu.  
  
 Pokud má pera **PS_INSIDEFRAME** stylu a barvy, která neodpovídá barvu v tabulce barev logické pera vykreslením s tónovaná barva. **PS_INSIDEFRAME** styl je stejný jako **PS_SOLID** Pokud šířku pera je menší než nebo rovna 1.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>CPen::FromHandle  
 Vrátí ukazatel na `CPen` objekt daný popisovač na objekt pera GDI systému Windows.  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>Parametry  
 *hPen*  
 `HPEN`Popisovač pera GDI systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPen` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CPen` objektu není připojený k popisovač dočasného `CPen` objekt se vytvoří a připojené. Toto dočasný `CPen` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho událostí smyčky, na který čas všechny dočasné obrázek objekty jsou odstraněny. Jinými slovy dočasný objekt je platná pouze během zpracování zprávy jeden interval.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>CPen::GetExtLogPen  
 Získá **EXTLOGPEN** základní struktura.  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogPen`  
 Odkazuje na [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) struktura, která obsahuje informace o pera.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 **EXTLOGPEN** struktura definuje styl, šířky a pera štětce atributy. Například volání `GetExtLogPen` tak, aby odpovídala konkrétním styl pera.  
  
 Najdete v následujících tématech v sadě Windows SDK pro informace o atributech pera:  
  
- [Funkce GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN –](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání `GetExtLogPen` načíst atributy pera a pak vytvořit nové, kosmetické pera stejné barvy.  
  
 [!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>CPen::GetLogPen  
 Získá `LOGPEN` základní struktura.  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogPen`  
 Odkazuje na [logpen –](http://msdn.microsoft.com/library/windows/desktop/dd145041) struktura bude obsahovat informace o pera.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `LOGPEN` Struktura definuje styl, barvu a vzor pera.  
  
 Například volání `GetLogPen` tak, aby odpovídala konkrétním styl pera.  
  
 Najdete v následujících tématech v sadě Windows SDK pro informace o atributech pera:  
  
- [Funkce GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN –](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání `GetLogPen` k načtení znak pera a pak vytvořte nové, plnou pera stejné barvy.  
  
 [!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>CPen::operator HPEN  
 Získá popisovač Windows GDI připojených `CPen` objektu.  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro objekt Windows GDI reprezentována `CPen` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití `HPEN` objektu.  
  
 Další informace o použití grafických objektů najdete v článku [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CBrush – třída](../../mfc/reference/cbrush-class.md)
