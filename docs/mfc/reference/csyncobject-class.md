---
title: CSyncObject – třída
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365974"
---
# <a name="csyncobject-class"></a>CSyncObject – třída

Čistá virtuální třída, která poskytuje funkce společné pro objekty synchronizace v win32.

## <a name="syntax"></a>Syntaxe

```
class CSyncObject : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Vytvoří `CSyncObject` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSyncObject::Zamknout](#lock)|Získá přístup k objektu synchronizace.|
|[CSyncObject::Odemknout](#unlock)|Získá přístup k objektu synchronizace.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CSyncObject::POPISOVAČ operátora](#operator_handle)|Poskytuje přístup k objektu synchronizace.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Popisovač základního objektu synchronizace.|

## <a name="remarks"></a>Poznámky

Knihovna tříd Microsoft Foundation poskytuje `CSyncObject`několik tříd odvozených z aplikace . Jedná se [o CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)a [CSemaphore](../../mfc/reference/csemaphore-class.md).

Informace o použití objektů synchronizace naleznete v článku [Multithreading: How to Use the Synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject

Vytvoří objekt synchronizace s zadaným názvem.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parametry

*název pstr*<br/>
Název objektu. Pokud null, *pstrName* bude null.

## <a name="csyncobjectlock"></a><a name="lock"></a>CSyncObject::Zamknout

Volání této funkce získat přístup k prostředku řízeného objektu synchronizace.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Určuje dobu v milisekundách, po kterou má být k dispozici objekt synchronizace (signalizován). Pokud INFINITE, bude čekat, `Lock` dokud objekt je signalizován před návratem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je signalizován objekt `Lock` synchronizace, úspěšně se vrátí a vlákno nyní vlastní objekt. Pokud je objekt synchronizace nesignalizován `Lock` (není k dispozici), bude čekat, až bude objekt synchronizace signalizován až do počtu milisekund zadaný v parametru *dwTimeOut.* Pokud objekt synchronizace nebyl signalizován v zadaném `Lock` čase, vrátí selhání.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject

Popisovač základního objektu synchronizace.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::POPISOVAČ operátora

Pomocí tohoto operátoru získat `CSyncObject` popisovač objektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač objektu synchronizace; jinak NULL.

### <a name="remarks"></a>Poznámky

Pomocí popisovače můžete volat přímo windows api.

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Odemknout

Deklarace `Unlock` bez parametrů je čistě virtuální funkce a musí být přepsána všemi třídami odvozenými z aplikace `CSyncObject`.

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lPočet*<br/>
Ve výchozím provádění se nepoužívá.

*lpPrevCount*<br/>
Ve výchozím provádění se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Výchozí implementace deklarace se dvěma parametry vždy vrátí hodnotu TRUE. Tato funkce je volána k uvolnění přístupu k objektu synchronizace vlastněného volajícím vláknem. Druhá deklarace je k dispozici pro synchronizační objekty, jako jsou semafory, které umožňují více než jeden přístup řízeného prostředku.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
