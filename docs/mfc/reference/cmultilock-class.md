---
title: Třída CMultiLock
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319715"
---
# <a name="cmultilock-class"></a>Třída CMultiLock

Představuje mechanismus řízení přístupu používaný při řízení přístupu k prostředkům v programu s více vlákny.

## <a name="syntax"></a>Syntaxe

```
class CMultiLock
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Vytvoří `CMultiLock` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMultilock::Uzamčený](#islocked)|Určuje, zda je uzamčen konkrétní objekt synchronizace v poli.|
|[CMultiLock::Zamknout](#lock)|Čeká na pole objektů synchronizace.|
|[CMultiLock::Odemknout](#unlock)|Uvolní všechny vlastněné objekty synchronizace.|

## <a name="remarks"></a>Poznámky

`CMultiLock`nemá základní třídu.

Chcete-li použít třídy synchronizace [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)a `CMultiLock` [CEvent](../../mfc/reference/cevent-class.md), můžete vytvořit objekt nebo [csinglelock,](../../mfc/reference/csinglelock-class.md) který počká a uvolní objekt synchronizace. Použijte, `CMultiLock` pokud existuje více objektů, které můžete použít v určitém čase. Použijte, `CSingleLock` když potřebujete čekat pouze na jeden objekt najednou.

Chcete-li `CMultiLock` použít objekt, nejprve vytvořte pole objektů synchronizace, na které chcete čekat. Dále volání `CMultiLock` konstruktoru objektu uvnitř členské funkce ve třídě řízeného prostředku. Potom volání [lock](#lock) členské funkce k určení, zda prostředek je k dispozici (signalizováno). Pokud je, pokračujte se zbytkem členské funkce. Pokud není k dispozici žádný prostředek, počkejte na zadané množství času pro uvolnění zdroje nebo vrácení selhání. Po dokončení použití prostředku, volání [Odemknout](#unlock) funkce, pokud `CMultiLock` má být objekt `CMultiLock` znovu použit, nebo povolit zničení objektu.

`CMultiLock`objekty jsou nejužitečnější, když `CEvent` vlákno má velký počet objektů, na které může reagovat. Vytvořte pole obsahující `CEvent` všechny ukazatele a `Lock`volání . To způsobí, že vlákno čekat, dokud je signalizována jedna z událostí.

Další informace o použití `CMultiLock` objektů naleznete v článku [Vícevláken: Jak používat třídy synchronizace](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CMultiLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock

Vytvoří `CMultiLock` objekt.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*ppObjekty*<br/>
Pole ukazatelů na synchronizační objekty, na které se má čekat. Nemůže být null.

*dwCount*<br/>
Počet objektů v *ppObjects*. Musí být větší než 0.

*bInitialLock*<br/>
Určuje, zda se má nejprve pokusit o přístup k některému z dodaných objektů.

### <a name="remarks"></a>Poznámky

Tato funkce je volána po vytvoření pole objektů synchronizace, na které se má čekat. Obvykle se nazývá z v rámci vlákna, který musí čekat na jeden z objektů synchronizace k dispozici.

## <a name="cmultilockislocked"></a><a name="islocked"></a>CMultilock::Uzamčený

Určuje, zda je zadaný objekt nesignalizován (není k dispozici).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parametry

*dwPoložka*<br/>
Index v poli objektů odpovídající objektu, jehož stav je dotazován.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zadaný objekt uzamčen; jinak 0.

## <a name="cmultilocklock"></a><a name="lock"></a>CMultiLock::Zamknout

Volání této funkce získat přístup k jednomu nebo více prostředků řízených `CMultiLock` synchronizační objekty dodávané konstruktoru.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Určuje dobu čekání na dostupnost objektu synchronizace (signalizováno). Pokud INFINITE, bude čekat, `Lock` dokud objekt je signalizován před návratem.

*bWaitForAll*<br/>
Určuje, zda všechny objekty, na které bylo před vrácením čekáno, musí být signalizovány současně. Pokud false, `Lock` vrátí, když některý z objektů čekal na je signalizován.

*dwWakeMask*<br/>
Určuje další podmínky, které mohou přerušit čekání. Úplný seznam dostupných možností pro tento parametr naleznete v [tématu MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Pokud `Lock` se nezdaří, vrátí - 1. Pokud je úspěšná, vrátí jednu z následujících hodnot:

- Mezi WAIT_OBJECT_0 a WAIT_OBJECT_0 + (počet objektů - 1)

   Pokud *je hodnota bWaitForAll* true, jsou signalizovány všechny objekty (k dispozici). Pokud *bWaitForAll* je FALSE, vrácená hodnota - WAIT_OBJECT_0 je index v poli objektů objektu, který je signalizován (k dispozici).

- WAIT_OBJECT_0 + (počet objektů)

   Událost zadaná v *dwWakeMask* je k dispozici ve vstupní frontě vlákna.

- Mezi WAIT_ABANDONED_0 a WAIT_ABANDONED_0 + (počet objektů - 1)

   Pokud *bWaitForAll* je PRAVDA, všechny objekty jsou signalizovány a alespoň jeden z objektů je opuštěný objekt mutex. Pokud *bWaitForAll* je FALSE, vrácená hodnota - WAIT_ABANDONED_0 je index v poli objektů opuštěné mutex objektu, který splnil čekání.

- WAIT_TIMEOUT

   Časový limit zadaný v *dwTimeOut* vypršel bez čekání úspěšné.

### <a name="remarks"></a>Poznámky

Pokud *bWaitForAll* je `Lock` PRAVDA, vrátí úspěšně, jakmile všechny objekty synchronizace se zobrazí současně signalizovat. Pokud *bWaitForAll* je `Lock` FALSE, vrátí, jakmile jeden nebo více objektů synchronizace se stane signalizován.

Pokud `Lock` není schopen vrátit okamžitě, bude čekat na ne více než počet milisekund zadaný v *parametru dwTimeOut* před návratem. Pokud *dwTimeOut* je `Lock` INFINITE, nevrátí, dokud není získán přístup k objektu nebo podmínka zadaná v *dwWakeMask* byla splněna. V opačném `Lock` případě, pokud byl schopen získat objekt synchronizace, vrátí úspěšně; Pokud tomu tak není, vrátí selhání.

## <a name="cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Odemknout

Uvolní objekt synchronizace vlastněný `CMultiLock`společností .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lPočet*<br/>
Počet odkazů, které mají být vydány. Musí být větší než 0. Pokud by zadaná částka způsobila, že počet objektů překročí jeho maximum, počet se nezmění a funkce vrátí hodnotu NEPRAVDA.

*lPrevCount*<br/>
Odkazuje na proměnnou, která získá předchozí počet pro objekt synchronizace. Pokud null, předchozí počet není vrácena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je `CMultiLock`volána destruktorem společnosti.

První forma `Unlock` pokusí odemknout objekt synchronizace `CMultiLock`spravované . Druhá forma `Unlock` pokusí odemknout `CSemaphore` objekty `CMultiLock`vlastněné . Pokud `CMultiLock` nevlastní žádný `CSemaphore` uzamčený objekt, funkce vrátí hodnotu NEPRAVDA. v opačném případě vrátí hodnotu TRUE. *lCount* a *lpPrevCount* jsou přesně stejné jako parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Druhá forma `Unlock` je zřídka použitelné pro multilock situace.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
