---
title: Struktura CMemoryState | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20f4c2d7d33d07a5eca5a980c376056c3fe68e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmemorystate-structure"></a>Struktura CMemoryState
Nabízí pohodlný způsob, jak zjistit, že nevracení paměti v programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Vytvoří strukturu jako třída, která řídí paměti kontrolní body.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|Získá snímek aktuální stav paměti (kontrolního bodu).|  
|[CMemoryState::Difference](#difference)|Vypočítá rozdíl mezi dvěma objekty typu `CMemoryState`.|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Vypíše souhrn všechny aktuálně přidělené objekty od předchozího kontrolního bodu.|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|Zobrazí statistiku přidělení paměti pro `CMemoryState` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CMemoryState`je struktura a nemá základní třídu.  
  
 "Nevrácené paměti" nastane, když je paměti pro objekt přidělené v haldě, ale není navrácena, pokud se už nevyžaduje. Takové nevracení paměti může nakonec vést k nedostatku paměti chyby. Alokace a zrušit přidělení paměti v programu několika způsoby:  
  
-   Pomocí `malloc` /  **volné** rodiny funkcí z knihovny běhu.  
  
-   Pomocí funkce správy paměti rozhraní API systému Windows, **LocalAlloc**/ **LocalFree** a **GlobalAlloc**/ **GlobalFree** .  
  
-   Pomocí C++ **nové** a **odstranit** operátory.  
  
 `CMemoryState` Diagnostiky pouze pomůže zjistit paměti nevracení nastat, když pomocí přidělit paměť **nové** operátor není navrácena pomocí **odstranit**. Jsou dalších dvou skupin funkce správy paměti pro programy mimo jazyk C++ a kombinování je s **nové** a **odstranit** ve stejném programu se nedoporučuje. Další makro, `DEBUG_NEW`, je určena k nahrazení **nové** operátor až budete potřebovat soubor a číslo řádku sledování přidělování paměti. `DEBUG_NEW`se používá při každém běžně používáte **nové** operátor.  
  
 Stejně jako u jiných diagnostiky `CMemoryState` diagnostiky jsou dostupné jenom v ladicí verze vašeho programu. Ladicí verze musí mít **_DEBUG –** konstanta definované.  
  
 Pokud máte podezření na nevracení paměti má program, můžete použít `Checkpoint`, **rozdíl**, a `DumpStatistics` funkce ke zjištění rozdílu mezi je stav paměti (objekty přidělené) na dva různé body v programu provádění. Tato informace může být užitečné při určování, zda je funkce vyčistit všechny objekty, které přiděluje.  
  
 Pokud jednoduše zároveň budete vědět, kde dochází k nevyváženosti v přidělené a odebrané nenabízí dostatek informací, můžete použít `DumpAllObjectsSince` funkce vypsat všechny objekty přidělené od předchozího volání `Checkpoint`. Tento výpis zobrazuje pořadí přidělení, zdrojový soubor a řádku, kde byl přidělen objektu (Pokud používáte `DEBUG_NEW` pro přidělení) a odvození objektu, jeho adresy a jeho velikost. `DumpAllObjectsSince`také voláním každý objekt `Dump` funkce lze zadat informace o aktuálním stavu.  
  
 Další informace o tom, jak používat `CMemoryState` a najdete v části Další diagnostiky [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Deklarace objektů typu `CMemoryState` a volání členské funkce by měla být bracketed podle `#if defined(_DEBUG)/#endif` direktivy. To způsobí, že diagnostiky paměti mají být zahrnuty pouze při ladění sestavení vašeho programu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CMemoryState`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="checkpoint"></a>CMemoryState::Checkpoint  
 Pořídí snímek souhrnné paměti a ukládá je v tomto `CMemoryState` objektu.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Poznámky  
 `CMemoryState` Členské funkce [rozdíl](#difference) a [DumpAllObjectsSince](#dumpallobjectssince) používat tato data snímku.  
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [CMemoryState](#cmemorystate) konstruktor.  
  
##  <a name="cmemorystate"></a>CMemoryState::CMemoryState  
 Vytvoří prázdnou `CMemoryState` objekt, který musí být vyplněna objektem [kontrolního bodu](#checkpoint) nebo [rozdíl](#difference) – členská funkce.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>CMemoryState::Difference  
 Porovná dva `CMemoryState` objekty a pak uloží rozdíl do této `CMemoryState` objektu.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Parametry  
 *oldState*  
 Stav počáteční paměti podle definice `CMemoryState` kontrolního bodu.  
  
 *Nový stav*  
 Nový stav paměti, jak je definována `CMemoryState` kontrolního bodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se dva paměti stavy liší; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 [Kontrolní bod](#checkpoint) musí mít zavolána pro každou z těchto parametrů stav paměti.  
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [CMemoryState](#cmemorystate) konstruktor.  
  
##  <a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince  
 Volání `Dump` funkce pro všechny objekty typu odvozené od třídy `CObject` které byly přiděleny (a jsou pořád ještě přidělená) od minulého [kontrolního bodu](#checkpoint) volání pro tento `CMemoryState` objektu.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Poznámky  
 Volání metody `DumpAllObjectsSince` s Neinicializovaný `CMemoryState` objektu bude vypsat všechny objekty, které aktuálně v paměti.  
  
### <a name="example"></a>Příklad  
  Podívejte se příklad [CMemoryState](#cmemorystate) konstruktor.  
  
##  <a name="dumpstatistics"></a>CMemoryState::DumpStatistics  
 Vytiskne sestavu statistiky stručným paměti ze `CMemoryState` objekt, který vyplní [rozdíl](#difference) – členská funkce.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Poznámky  
 Zprávu, která je vytištěno na [afxdump –](diagnostic-services.md#afxdump) zařízení, zobrazí následující:  
  
 Ukázková sestava nabízí informace o číslo (nebo velikost):  
  
-   volné bloky  
  
-   Normální bloky  
  
-   Bloky CRT  
  
-   Ignorovat bloky  
  
-   klientské bloky  
  
-   maximální velikost paměti, které používá program v jednom okamžiku (v bajtech)  
  
-   celkové paměti aktuálně používá program (v bajtech)  
  
 Počet bloků, jejichž navrácení byla zpožděna, pokud jsou volné bloky `afxMemDF` byla nastavena na **delayfreememdf –**. Další informace najdete v tématu [afxmemdf –](diagnostic-services.md#afxmemdf), v části "MFC makra a globální prvky". V tématu [typy bloky v haldě ladění](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5) pro další informace o těchto blokovat typy.  
  
### <a name="example"></a>Příklad  
  Následující kód musí být umístěny v *projname*App.cpp. Definujte tyto globální proměnné:  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 V `InitInstance` fungovat, přidejte řádek:  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Přidání obslužné rutiny `ExitInstance` funkce a použít následující kód:  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Teď můžete spustit program v režimu ladění zobrazíte výstup `DumpStatistics` funkce.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



