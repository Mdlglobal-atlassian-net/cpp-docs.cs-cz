---
title: Třída CSinglelock
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318275"
---
# <a name="csinglelock-class"></a>Třída CSinglelock

Představuje mechanismus řízení přístupu používaný při řízení přístupu k prostředku v programu s více vlákny.

## <a name="syntax"></a>Syntaxe

```
class CSingleLock
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Vytvoří `CSingleLock` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSingleLock::Zamkne](#islocked)|Určuje, zda je objekt uzamčen.|
|[CSingleLock::Zámek](#lock)|Čeká na objekt synchronizace.|
|[CSingleLock::Odemknout](#unlock)|Uvolní objekt synchronizace.|

## <a name="remarks"></a>Poznámky

`CSingleLock`nemá základní třídu.

Chcete-li použít třídy synchronizace [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)a `CSingleLock` [CEvent](../../mfc/reference/cevent-class.md), musíte vytvořit objekt a nebo [CMultiLock,](../../mfc/reference/cmultilock-class.md) na který chcete počkat a uvolnit objekt synchronizace. Použijte, `CSingleLock` když potřebujete čekat pouze na jeden objekt najednou. Použijte, `CMultiLock` pokud existuje více objektů, které můžete použít v určitém čase.

Chcete-li `CSingleLock` použít objekt, volání jeho konstruktoru uvnitř členské funkce ve třídě řízeného prostředku. Potom volání [islocked](#islocked) členské funkce k určení, zda je k dispozici prostředek. Pokud ano, pokračujte se zbytkem členské funkce. Pokud prostředek není k dispozici, počkejte na zadané množství času pro prostředek, který má být uvolněn, nebo vrátit selhání. Po dokončení použití prostředku, volání [Unlock](#unlock) funkce, `CSingleLock` pokud má být objekt znovu `CSingleLock` použit, nebo povolit zničení objektu.

`CSingleLock`objekty vyžadují přítomnost objektu odvozeného z [CSyncObject](../../mfc/reference/csyncobject-class.md). Obvykle se jedná o datový člen třídy řízeného prostředku. Další informace o použití `CSingleLock` objektů naleznete v článku [Vícevláken: Jak používat třídy synchronizace](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CSingleLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>CSingleLock::CSingleLock

Vytvoří `CSingleLock` objekt.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*pObjekt*<br/>
Odkazuje na objekt synchronizace, ke který má být přístupná. Nemůže být null.

*bInitialLock*<br/>
Určuje, zda se má nejprve pokusit o přístup k zadanému objektu.

### <a name="remarks"></a>Poznámky

Tato funkce je obecně volána z funkce přístupového člena řízeného prostředku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>CSingleLock::Zamkne

Určuje, zda je objekt `CSingleLock` přidružený k objektu nesignalizován (není k dispozici).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt uzamčen; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>CSingleLock::Zámek

Volání této funkce získat přístup k prostředku řízeného objektu synchronizace dodané konstruktoru. `CSingleLock`

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Určuje dobu čekání na dostupnost objektu synchronizace (signalizováno). Pokud INFINITE, bude čekat, `Lock` dokud objekt je signalizován před návratem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je signalizován objekt `Lock` synchronizace, úspěšně se vrátí a vlákno nyní vlastní objekt. Pokud je objekt synchronizace nesignalizován `Lock` (není k dispozici), bude čekat, až bude objekt synchronizace signalizován až do počtu milisekund zadaný v parametru *dwTimeOut.* Pokud objekt synchronizace nebyl signalizován v zadaném `Lock` čase, vrátí selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>CSingleLock::Odemknout

Uvolní objekt synchronizace vlastněný `CSingleLock`společností .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lPočet*<br/>
Počet přístupů k uvolnění. Musí být větší než 0. Pokud by zadaná částka způsobila, že počet objektů překročí jeho maximum, počet se nezmění a funkce vrátí hodnotu NEPRAVDA.

*lPrevCount*<br/>
Odkazuje na proměnnou, která získá předchozí počet objektu synchronizace. Pokud null, předchozí počet není vrácena.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je `CSingleLock`volána destruktorem společnosti.

Pokud potřebujete uvolnit více než jeden počet přístupu semaforu, použijte druhý formulář `Unlock` a zadejte počet přístupů k uvolnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMultiLock](../../mfc/reference/cmultilock-class.md)
