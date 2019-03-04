---
title: Cmemorystate – struktura
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288126"
---
# <a name="cmemorystate-structure"></a>Cmemorystate – struktura

Poskytuje pohodlný způsob, jak zjistit, že nevracení paměti v programu.

## <a name="syntax"></a>Syntaxe

```
struct CMemoryState
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Vytvoří strukturu typu třída, která řídí paměti kontrolní body.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMemoryState::Checkpoint](#checkpoint)|Získá snímek aktuálního stavu paměti (kontrolního bodu).|
|[CMemoryState::Difference](#difference)|Vypočítá rozdíl mezi dvěma objekty typu `CMemoryState`.|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Vypíše souhrn všechny aktuálně přidělené objekty od předchozího kontrolního bodu.|
|[CMemoryState::DumpStatistics](#dumpstatistics)|Vypíše statistiky přidělení paměti pro `CMemoryState` objektu.|

## <a name="remarks"></a>Poznámky

`CMemoryState` Struktura a nemá žádné základní třídy.

"Nevracení paměti" nastane, pokud je paměť pro objekt přidělený k haldě, ale ne uvolněna se už nevyžaduje. Takové nevracení paměti může nakonec vést k chybám na více instancí z důvodu nedostatku paměti. Existuje několik způsobů, jak přidělit a uvolnit paměť ve svém programu:

- Použití `malloc` /  `free` řady funkcí z knihovny run-time.

- Pomocí funkce správy paměti rozhraní Windows API, `LocalAlloc` /  `LocalFree` a `GlobalAlloc` /  `GlobalFree`.

- Pomocí jazyka C++ **nové** a **odstranit** operátory.

`CMemoryState` Diagnostiky pouze umožní odhalit paměti nevracení nastává, když je paměť přidělena pomocí **nové** operátor není navrácena pomocí **odstranit**. Další dvě skupiny funkce správy paměti jsou určené pro programy jazyka C++ a jejich kombinování **nové** a **odstranit** ve stejném programu se nedoporučuje. Je k dispozici další makra, DEBUG_NEW, chcete-li nahradit **nové** operátor, když budete potřebovat soubor a číslo řádku sledování přidělování paměti. DEBUG_NEW slouží pokaždé, když se obvykle zřejmě použijete **nové** operátor.

Stejně jako u jiných Diagnostika `CMemoryState` diagnostiky jsou dostupné jenom v ladicí verze aplikace. Ladicí verze musí mít _DEBUG konstanta definovaná.

Pokud máte podezření na nevracení paměti má program, můžete použít `Checkpoint`, `Difference`, a `DumpStatistics` funkce zjišťování rozdílu stavu paměti (přidělené objekty) na dvou různých fázích provádění programu. Tyto informace mohou být užitečné při určování, zda všechny objekty, které přiděluje čistí funkce.

Pokud stačí vědět, kde dochází k nevyrovnanosti přidělování a navracení zpět neposkytuje dostatek informací, můžete použít `DumpAllObjectsSince` funkce pro výpis všech objektů přidělených od předchozího volání `Checkpoint`. Tento výpis zobrazuje pořadí přidělení, zdrojového souboru a řádku, kde byla objektu přidělena (Pokud používáte DEBUG_NEW pro přidělení), a odvození objektu, jeho adresy a její velikost. `DumpAllObjectsSince` volá také každý objekt `Dump` funkce lze zadat informace o aktuálním stavu.

Další informace o tom, jak používat `CMemoryState` a další diagnostiky najdete v článku [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Deklarace objektů typu `CMemoryState` a volání členských funkcí, by měl být uváděn v závorkách `#if defined(_DEBUG)/#endif` direktivy. To způsobí, že Diagnostika paměti mají být zahrnuty pouze v laděných sestaveních programu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CMemoryState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="checkpoint"></a>  CMemoryState::Checkpoint

Pořídí snímek souhrnu paměti a uloží je v tomto `CMemoryState` objektu.

```
void Checkpoint();
```

### <a name="remarks"></a>Poznámky

`CMemoryState` Členské funkce [rozdíl](#difference) a [DumpAllObjectsSince](#dumpallobjectssince) pomocí těchto dat snímku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [cmemorystate –](#cmemorystate) konstruktoru.

##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState

Vytvoří prázdnou `CMemoryState` objekt, který musí být vyplněna objektem [kontrolního bodu](#checkpoint) nebo [rozdíl](#difference) členskou funkci.

```
CMemoryState();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>  CMemoryState::Difference

Porovná dva `CMemoryState` objektů a potom uloží rozdíl do této `CMemoryState` objektu.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*oldState*<br/>
Počáteční paměti stav souladu s definicemi `CMemoryState` kontrolního bodu.

*Nový stav*<br/>
Nový stav paměti podle `CMemoryState` kontrolního bodu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou odlišná dvěma stavy paměti jinak 0.

### <a name="remarks"></a>Poznámky

[Kontrolní bod](#checkpoint) musí volat pro každou z těchto parametrů stavu paměti.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [cmemorystate –](#cmemorystate) konstruktoru.

##  <a name="dumpallobjectssince"></a>  CMemoryState::DumpAllObjectsSince

Volání `Dump` funkce pro všechny objekty typu odvozené od třídy `CObject` , které byly přiděleny (a jsou pořád ještě přidělená) od minulého [kontrolního bodu](#checkpoint) volání pro tuto `CMemoryState` objektu.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Poznámky

Volání `DumpAllObjectsSince` s neinicializované `CMemoryState` objektu se vypsat všechny objekty, které aktuálně v paměti.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [cmemorystate –](#cmemorystate) konstruktoru.

##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics

Vytiskne zprávu Statistika stručné paměti z `CMemoryState` objekt, který vyplní [rozdíl](#difference) členskou funkci.

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Poznámky

Sestava, která je vytištěna na [afxDump](diagnostic-services.md#afxdump) zařízení, zobrazí následující:

Ukázková sestava nabízí informace o číslo (nebo velikost):

- bezplatné bloky

- Normální bloky

- CRT bloky

- bloky ignorovat

- klientské bloky

- maximální velikost paměti, které používá tento program kdykoliv (v bajtech)

- Celková paměť aktuálně používá tento program (v bajtech)

Počet bloků, jehož zrušení přidělení opozdila, pokud jsou zdarma bloky `afxMemDF` byl nastaven na `delayFreeMemDF`. Další informace najdete v tématu [afxmemdf –](diagnostic-services.md#afxmemdf), v části "MFC makra a globální prvky".

### <a name="example"></a>Příklad

  Následující kód musí být umístěné ve *název_projektu*App.cpp. Definujte tyto globální proměnné:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

V `InitInstance` funkci, přidejte řádek:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Přidání obslužné rutiny `ExitInstance` fungovat a použijte následující kód:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Nyní můžete spustit program v režimu ladění, pokud chcete zobrazit výstup `DumpStatistics` funkce.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)
