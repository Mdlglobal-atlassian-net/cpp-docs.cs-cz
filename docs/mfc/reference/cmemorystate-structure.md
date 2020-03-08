---
title: Struktura CMemoryState
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855274"
---
# <a name="cmemorystate-structure"></a>Struktura CMemoryState

Nabízí pohodlný způsob, jak detekovat nevracení paměti v programu.

## <a name="syntax"></a>Syntaxe

```
struct CMemoryState
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Vytvoří strukturu podobnou třídě, která řídí kontrolní body paměti.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Získá snímek (kontrolní bod) aktuálního stavu paměti.|
|[CMemoryState::D ifference](#difference)|Vypočítá rozdíl mezi dvěma objekty typu `CMemoryState`.|
|[CMemoryState::D umpAllObjectsSince](#dumpallobjectssince)|Vypíše souhrn všech aktuálně přidělených objektů od předchozího kontrolního bodu.|
|[CMemoryState::D umpStatistics](#dumpstatistics)|Vytiskne statistiku přidělení paměti pro objekt `CMemoryState`.|

## <a name="remarks"></a>Poznámky

`CMemoryState` je struktura a nemá základní třídu.

K "nevracení paměti dojde v případě, že paměť pro objekt je přidělena haldě, ale není uvolněna, pokud již není vyžadována. Taková nevracení paměti může nakonec vést k chybám při nedostatku paměti. Existuje několik způsobů, jak přidělit a uvolnit paměť v programu:

- Použití `malloc`/ `free` rodinu funkcí z knihovny run-time.

- Pomocí funkcí správy paměti rozhraní Windows API `LocalAlloc`/ `LocalFree` a `GlobalAlloc`/ `GlobalFree`.

- C++ Pomocí operátorů **New** a **Delete** .

Diagnostiku `CMemoryState` jenom napomáhala detekci nevracení paměti, protože paměť přidělená pomocí operátoru **New** není navrácena pomocí **Delete**. Další dvě skupiny funkcí pro správu paměti jsou proC++ neprogramované a jejich kombinování s **novými** a **odstraněnými** ve stejném programu se nedoporučuje. Další makro, DEBUG_NEW, je k dispozici pro nahrazení operátoru **New** , pokud potřebujete sledovat přidělení paměti pro soubor a číslo řádku. DEBUG_NEW se používá vždy, když byste normálně použili operátor **New** .

Stejně jako u jiných diagnostických nástrojů jsou Diagnostika `CMemoryState` k dispozici pouze ve verzi programu pro ladění. Ladicí verze musí mít definovanou _DEBUG konstantou.

Pokud se domníváte, že má váš program nevrácenou paměť, můžete použít funkce `Checkpoint`, `Difference`a `DumpStatistics` k zjištění rozdílu mezi stavem paměti (přidělenými objekty) na dvou různých místech provádění programu. Tyto informace mohou být užitečné při určování, zda funkce čistí všechny objekty, které přiděluje.

Pokud stačí vědět, kde nedochází k nerovnováhě při přidělování a navracení, neposkytuje dostatek informací, můžete použít funkci `DumpAllObjectsSince` k výpisu všech objektů přidělených od předchozího volání `Checkpoint`. Tento výpis zobrazuje pořadí přidělení, zdrojový soubor a řádek, kde byl objekt přidělen (Pokud používáte DEBUG_NEW pro přidělení) a odvození objektu, jeho adresy a jeho velikosti. `DumpAllObjectsSince` také volá `Dump` funkci každého objektu, aby poskytovala informace o jeho aktuálním stavu.

Další informace o použití `CMemoryState` a dalších diagnostických nástrojů naleznete v tématu [DEBUGGING MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Deklarace objektů typu `CMemoryState` a volání členských funkcí by měly být v závorkách direktivami `#if defined(_DEBUG)/#endif`. To způsobí zahrnutí diagnostiky paměti pouze v sestaveních ladění programu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CMemoryState`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="checkpoint"></a>CMemoryState:: Checkpoint

Provede Souhrn snímku paměti a uloží jej do tohoto objektu `CMemoryState`.

```
void Checkpoint();
```

### <a name="remarks"></a>Poznámky

Členské funkce `CMemoryState` [rozdíl](#difference) a [DumpAllObjectsSince](#dumpallobjectssince) používají tato data snímku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro konstruktor [CMemoryState](#cmemorystate) .

##  <a name="cmemorystate"></a>CMemoryState::CMemoryState

Vytvoří prázdný objekt `CMemoryState`, který musí být vyplněn členskou funkcí [kontrolního bodu](#checkpoint) nebo [rozdílu](#difference) .

```
CMemoryState();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState::D ifference

Porovná dva objekty `CMemoryState` a pak tento rozdíl uloží do tohoto objektu `CMemoryState`.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parametry

*oldState*<br/>
Počáteční stav paměti definovaný kontrolním bodem `CMemoryState`.

*newState*<br/>
Nový stav paměti definovaný kontrolním bodem `CMemoryState`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou dva stavy paměti rozdílné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pro každý ze dvou parametrů stavu paměti musí být volán [kontrolní bod](#checkpoint) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro konstruktor [CMemoryState](#cmemorystate) .

##  <a name="dumpallobjectssince"></a>CMemoryState::D umpAllObjectsSince

Volá funkci `Dump` pro všechny objekty typu odvozeného od `CObject` třídy, které byly přiděleny (a jsou stále přiděleny) od posledního volání [kontrolního bodu](#checkpoint) pro tento objekt `CMemoryState`.

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Poznámky

Volání `DumpAllObjectsSince` s neinicializovaným objektem `CMemoryState` vypíše všechny objekty, které jsou aktuálně v paměti.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro konstruktor [CMemoryState](#cmemorystate) .

##  <a name="dumpstatistics"></a>CMemoryState::D umpStatistics

Vytiskne stručnou sestavu statistiky paměti z objektu `CMemoryState`, který je vyplněn členskou funkcí [rozdílu](#difference) .

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Poznámky

Sestava, která je vytištěna na zařízení [afxDump](diagnostic-services.md#afxdump) , zobrazuje následující:

Ukázková sestava obsahuje informace o počtu (nebo množství):

- bezplatné bloky

- normální bloky

- Bloky CRT

- ignorovat bloky

- klientské bloky

- maximální velikost paměti, kterou program v jednom okamžiku využíval (v bajtech)

- Celková paměť, kterou program aktuálně využíval (v bajtech)

Volné bloky jsou počet bloků, jejichž přidělení bylo zpožděno, pokud `afxMemDF` nastaveno na `delayFreeMemDF`. Další informace naleznete v tématu [afxMemDF](diagnostic-services.md#afxmemdf)v části "makra MFC a Globals".

### <a name="example"></a>Příklad

  Následující kód by měl být umístěn v *ProjName*App. cpp. Definujte následující globální proměnné:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Do funkce `InitInstance` přidejte řádek:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Přidejte obslužnou rutinu pro funkci `ExitInstance` a použijte následující kód:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Nyní můžete spustit program v režimu ladění a zobrazit výstup funkce `DumpStatistics`.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
