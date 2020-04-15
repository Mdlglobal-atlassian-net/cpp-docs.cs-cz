---
title: CEvent – třída
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373961"
---
# <a name="cevent-class"></a>CEvent – třída

Představuje událost, což je objekt synchronizace, který umožňuje jednomu vláknu upozornit jiné, že došlo k události.

## <a name="syntax"></a>Syntaxe

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Vytvoří `CEvent` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Nastaví událost na dostupnou (signalizovanou), uvolní čekající vlákna a nastaví událost na nedostupnou (nesignalizovanou).|
|[CEvent::ResetEvent](#resetevent)|Nastaví událost na nedostupnou (nesignalizovanou).|
|[CEvent::SetEvent](#setevent)|Nastaví událost na dostupnou (signalizovanou) a uvolní všechna čekající vlákna.|
|[CEvent::Odemknout](#unlock)|Uvolní objekt události.|

## <a name="remarks"></a>Poznámky

Události jsou užitečné, když vlákno musí vědět, kdy má provést svůj úkol. Například vlákno, které kopíruje data do archivu dat, musí být upozorněno, když jsou k dispozici nová data. Pomocí objektu `CEvent` upozornit vlákno kopie, když jsou k dispozici nová data, může vlákno provést svůj úkol co nejdříve.

`CEvent`objekty mají dva typy: ruční a automatické.

Automatický `CEvent` objekt se automaticky vrátí do nesignalizovaného (nedostupného) stavu po uvolnění alespoň jednoho vlákna. Ve výchozím `CEvent` nastavení je objekt `TRUE` automatický, pokud nepředáte parametr *bManualReset* během výstavby.

Ruční `CEvent` objekt zůstane ve stavu nastaveném [setEvent](#setevent) nebo [ResetEvent,](#resetevent) dokud nebude volána druhá funkce. Chcete-li `CEvent` vytvořit ruční `TRUE` objekt, předajte `bManualReset` parametr během výstavby.

Chcete-li `CEvent` použít objekt, vytvořte objekt, `CEvent` pokud je požadován. Zadejte název události, na kterou chcete čekat, a také určete, že aplikace by ji měla zpočátku vlastnit. Potom můžete získat přístup k události, když se vrátí konstruktor. Volání [SetEvent](#setevent) signál (zpřístupnit) objekt události a pak volat [Odemknout](#unlock) po dokončení přístupu k řízenému prostředku.

Alternativní metodou pro `CEvent` použití objektů je přidání `CEvent` proměnné typu jako datového člena do třídy, kterou chcete řídit. Během vytváření řízeného objektu zavolejte `CEvent` konstruktor datového člena a určete, zda je událost původně signalizována, a také určete požadovaný typ objektu události, název události (pokud bude použita přes hranice procesu) a všechny požadované atributy zabezpečení.

Chcete-li získat přístup `CEvent` k prostředku řízenému objektem tímto způsobem, nejprve vytvořte proměnnou typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo [cmultilock](../../mfc/reference/cmultilock-class.md) v metodě přístupu vašeho prostředku. Potom volání `Lock` metody objektu lock (například [CMultiLock::Lock).](../../mfc/reference/cmultilock-class.md#lock) V tomto okamžiku vlákno buď získat přístup k prostředku, počkejte na prostředek, který má být uvolněn a získat přístup, nebo čekat na prostředek, který má být uvolněn, časový režim a nepodaří získat přístup k prostředku. V každém případě byl přístup k prostředku přístupným způsobem bezpečným pro přístup z více vláken. Chcete-li uvolnit `SetEvent` prostředek, volání signál objektu `Unlock` události a potom použijte metodu objektu lock (například [CMultiLock::Unlock)](../../mfc/reference/cmultilock-class.md#unlock)nebo nechte objekt zámku vypadnout z oboru.

Další informace o použití `CEvent` objektů naleznete v [tématu Multithreading: How to Use the Synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>CEvent::CEvent

Vytvoří pojmenovaný nebo nepojmenovaný `CEvent` objekt.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Pokud true, vlákno `CMultilock` pro `CSingleLock` objekt nebo je povolena. V opačném případě musí čekat všechna vlákna, která chtějí získat přístup k prostředku.

*bManualReset*<br/>
Pokud true, určuje, že objekt události je ruční událost, jinak objekt události je automatická událost.

*název lpsz*<br/>
Název objektu. `CEvent` Musí být zadán, pokud bude objekt použit přes hranice procesu. Pokud název odpovídá existující události, konstruktor vytvoří `CEvent` nový objekt, který odkazuje na událost tohoto názvu. Pokud název odpovídá existující musynchronizační objekt, který není událostí, konstrukce se nezdaří. Pokud null, název bude null.

*Atribut lpsa*<br/>
Atributy zabezpečení pro objekt události. Úplný popis této struktury naleznete v [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) sady Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat `CEvent` přístup nebo uvolnit objekt, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho členské funkce [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

Chcete-li změnit `CEvent` stav objektu na signalizované (vlákna nemusí čekat), volání [SetEvent](#setevent) nebo [PulseEvent](#pulseevent). Chcete-li nastavit `CEvent` stav objektu na nesignalizované (vlákna musí počkat), volejte [ResetEvent](#resetevent).

> [!IMPORTANT]
> Po vytvoření `CEvent` objektu použijte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) k zajištění, že mutex ještě neexistoval. Pokud mutex existoval neočekávaně, může to znamenat, že proces rogue je squatting a může být v úmyslu použít mutex zlomyslně. V tomto případě je doporučená procedura s ohledem na zabezpečení zavřít popisovač a pokračovat, jako by došlo k chybě při vytváření objektu.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>CEvent::PulseEvent

Nastaví stav události na signalizované (k dispozici), uvolní všechny čekající vlákna a automaticky ji obnoví na nesignalizovanou (nedostupnou).

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je událost ruční, jsou uvolněny všechny čekající podprocesy, `PulseEvent` událost je nastavena na nesignalizované a vrátí. Pokud je událost automatická, je uvolněno jedno vlákno, událost je `PulseEvent` nastavena na nesignalizovanou a vrátí se.

Pokud žádné podprocesy čekají nebo žádná vlákna `PulseEvent` mohou být uvolněny okamžitě, nastaví stav události na nesignalizované a vrátí.

`PulseEvent`používá základní funkci `PulseEvent` Win32, která může být na okamžik odebrána ze stavu čekání voláním asynchronní procedury v režimu jádra. Proto `PulseEvent` je nespolehlivé a by neměly být používány nové aplikace. Další informace naleznete v [tématu PulseEvent funkce](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a>CEvent::ResetEvent

Nastaví stav události na nesignalizovanou, dokud není explicitně nastavena na signalizovanou členovou funkcí [SetEvent.](#setevent)

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

To způsobí, že všechna vlákna, kteří chtějí získat přístup k této události čekat.

Tato členská funkce není používána automatickými událostmi.

## <a name="ceventsetevent"></a><a name="setevent"></a>CEvent::SetEvent

Nastaví stav události signalizované, uvolnění všech čekajících podprocesů.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je událost ruční, událost zůstane signalizována, dokud nebude volána [resetevent.](#resetevent) V tomto případě lze uvolnit více než jedno vlákno. Pokud je událost automatická, událost zůstane signalizována, dokud nebude uvolněno jedno vlákno. Systém pak nastaví stav události na nesignalizovanou. Pokud žádné podprocesy čekají, stav zůstane signalizován, dokud je uvolněno jedno vlákno.

## <a name="ceventunlock"></a><a name="unlock"></a>CEvent::Odemknout

Uvolní objekt události.

```
BOOL Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud vlákno vlastnilo objekt události a událost je automatická událost; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána vlákny, které aktuálně vlastní automatickou událost, aby ji uvolnily po dokončení, pokud má být jejich objekt zámku znovu použit. Pokud objekt zámku není znovu použít, bude tato funkce volána destruktorem objektu zámku.

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
