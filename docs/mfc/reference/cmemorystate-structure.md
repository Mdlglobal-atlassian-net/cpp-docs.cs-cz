---
title: Struktura stavu CMemoryState
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 8f49a9faf70673c62167deeaa1bef33e4882378f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369987"
---
# <a name="cmemorystate-structure"></a>Struktura stavu CMemoryState

Poskytuje pohodlný způsob, jak zjistit nevracení paměti v programu.

## <a name="syntax"></a>Syntaxe

```
struct CMemoryState
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Vytvoří strukturu třídy, která řídí kontrolní body paměti.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMemoryState::Kontrolní bod](#checkpoint)|Získá snímek (kontrolní bod) aktuálního stavu paměti.|
|[CMemoryState::Difference](#difference)|Vypočítá rozdíl mezi dvěma `CMemoryState`objekty typu .|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Vypíše souhrn všech aktuálně přidělených objektů od předchozího kontrolního bodu.|
|[CMemoryState::DumpStatistika](#dumpstatistics)|Vytiskne statistiku `CMemoryState` přidělení paměti pro objekt.|

## <a name="remarks"></a>Poznámky

`CMemoryState`je struktura a nemá základní třídu.

"Nevracení paměti" dochází, když je paměť pro objekt přidělena na haldě, ale není přidělena, když již není vyžadována. Takové nevracení paměti může nakonec vést k chybám nedostatku paměti. Existuje několik způsobů, jak přidělit a navrátit paměť v programu:

- /  `free` Použití rodiny funkcí z knihovny `malloc` run-time.

- `LocalAlloc` /  `LocalFree` Pomocí funkcí správy paměti rozhraní `GlobalAlloc` / API systému Windows a `GlobalFree`.

- Použití c++ **nové** a **odstranit** operátory.

Diagnostika `CMemoryState` pouze pomoci zjistit nevracení paměti způsobené při paměti přidělené pomocí **nového** operátoru není deallocated pomocí **delete**. Další dvě skupiny funkcí správy paměti jsou určeny pro programy bez jazyka C++ a jejich smíchání s **novým** a **odstraněníve** stejném programu se nedoporučuje. Další makro, DEBUG_NEW, je k dispozici nahradit **nový** operátor, když potřebujete soubor a číslo řádku sledování přidělení paměti. DEBUG_NEW se používá vždy, když byste normálně používali **nový** operátor.

Stejně jako u `CMemoryState` jiných diagnostiky, diagnostika jsou k dispozici pouze v ladicí verze programu. Ladicí verze musí mít _DEBUG konstantu definována.

Pokud máte podezření, že program má nevracení paměti, můžete použít `Checkpoint`, `Difference`a `DumpStatistics` funkce zjistit rozdíl mezi stav paměti (přidělené objekty) ve dvou různých bodech při provádění programu. Tyto informace mohou být užitečné při určování, zda funkce čistí všechny objekty, které přiděluje.

Pokud jednoduše vědět, kde dojde k nerovnováze v přidělení a `DumpAllObjectsSince` deallocation neposkytuje dostatek informací, můžete `Checkpoint`použít funkci k výpisu všechny objekty přidělené od předchozího volání . Tento výpis zobrazuje pořadí přidělení, zdrojový soubor a řádek, kde byl objekt přidělen (pokud používáte DEBUG_NEW pro přidělení) a odvození objektu, jeho adresu a jeho velikost. `DumpAllObjectsSince`také volá `Dump` funkce každého objektu poskytnout informace o jeho aktuálním stavu.

Další informace o použití `CMemoryState` a další diagnostiky naleznete [v tématu Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Deklarace objektů typu `CMemoryState` a volání členských funkcí by `#if defined(_DEBUG)/#endif` měly být v závorkách podle směrnic. To způsobí, že diagnostika paměti, které mají být zahrnuty pouze v ladění sestavení programu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CMemoryState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Kontrolní bod

Pořídí souhrn snímků paměti a `CMemoryState` uloží jej do tohoto objektu.

```
void Checkpoint();
```

### <a name="remarks"></a>Poznámky

Člen `CMemoryState` funkce [Difference](#difference) a [DumpAllObjectsSince](#dumpallobjectssince) použít tento snímek data.

### <a name="example"></a>Příklad

  Viz příklad konstruktoru [CMemoryState.](#cmemorystate)

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Vytvoří prázdný `CMemoryState` objekt, který musí být vyplněn [kontrolním bodem](#checkpoint) nebo [rozdíl](#difference) členské funkce.

```
CMemoryState();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::Difference

Porovná dva `CMemoryState` objekty a pak `CMemoryState` uloží rozdíl do tohoto objektu.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*oldState*<br/>
Počáteční stav paměti, jak `CMemoryState` je definován kontrolním bodem.

*newState*<br/>
Nový stav paměti, jak `CMemoryState` je definován kontrolním bodem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se dva stavy paměti liší; jinak 0.

### <a name="remarks"></a>Poznámky

[Kontrolní bod](#checkpoint) musí být volána pro každý ze dvou parametrů stavu paměti.

### <a name="example"></a>Příklad

  Viz příklad konstruktoru [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince

Volá `Dump` funkci pro všechny objekty typu `CObject` odvozené z třídy, které byly přiděleny (a `CMemoryState` jsou stále přiděleny) od [posledního volání Checkpoint](#checkpoint) pro tento objekt.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Poznámky

Volání `DumpAllObjectsSince` s neinicializovaný `CMemoryState` objekt vypíše všechny objekty aktuálně v paměti.

### <a name="example"></a>Příklad

  Viz příklad konstruktoru [CMemoryState.](#cmemorystate)

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistika

Vytiskne stručnou sestavu `CMemoryState` statistiky paměti z objektu, který je vyplněn členovou funkcí [Rozdíl.](#difference)

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Poznámky

Sestava, která je vytištěna na zařízení [afxDump,](diagnostic-services.md#afxdump) zobrazuje následující:

Ukázková sestava poskytuje informace o počtu (nebo množství) :

- volné bloky

- normální bloky

- CRT bloky

- ignorovat bloky

- klientské bloky

- maximální paměť používaná programem v jednom okamžiku (v bajtech)

- celková paměť aktuálně používaná programem (v bajtech)

Volné bloky jsou počet bloků, jejichž `afxMemDF` deallocation `delayFreeMemDF`byl zpožděn, pokud byl nastaven na . Další informace naleznete [v části AfxMemDF](diagnostic-services.md#afxmemdf)v části MFC MFC MMacros and Globals .

### <a name="example"></a>Příklad

  Následující kód by měl být umístěn v *projname*App.cpp. Definujte následující globální proměnné:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Do `InitInstance` funkce přidejte řádek:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Přidejte obslužnou rutinu `ExitInstance` funkce a použijte následující kód:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Nyní můžete spustit program v režimu ladění pro `DumpStatistics` zobrazení výstupu funkce.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
