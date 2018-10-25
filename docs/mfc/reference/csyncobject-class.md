---
title: CSyncObject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a3978b83be0cc1bc85d57cbde87d17eb4cc6d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082798"
---
# <a name="csyncobject-class"></a>CSyncObject – třída

Čistě virtuální třída, která poskytuje funkčnost běžnou pro synchronizaci objektů v systému Win32.

## <a name="syntax"></a>Syntaxe

```
class CSyncObject : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Vytvoří `CSyncObject` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSyncObject::Lock](#lock)|Získáte přístup k synchronizační objekt.|
|[CSyncObject::Unlock](#unlock)|Získáte přístup k synchronizační objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSyncObject::operator POPISOVAČ](#operator_handle)|Poskytuje přístup k objektu synchronizace.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Popisovač na základní objekt synchronizace.|

## <a name="remarks"></a>Poznámky

Knihovny Microsoft Foundation Class poskytuje několik tříd odvozených z `CSyncObject`. Jedná se o [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), a [CSemaphore](../../mfc/reference/csemaphore-class.md).

Informace o tom, jak používat objekty synchronizace, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

Vytvoří objekt synchronizace se zadaným názvem.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Název objektu. Pokud má hodnotu NULL, *pstrName* bude mít hodnotu null.

##  <a name="lock"></a>  CSyncObject::Lock

Voláním této funkce získáte přístup k prostředku řídí synchronizační objekt.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Určuje dobu v milisekundách pro čekání synchronizační objekt k dispozici (signalizován). Pokud je NEKONEČNÉ, `Lock` budou čekat na objekt je signál, před vrácením.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je synchronizační objekt signalizována, `Lock` úspěšně vrátí a vlákno je nyní vlastníkem objektu. Pokud se objekt synchronizace nonsignaled (není k dispozici), `Lock` počká na synchronizační objekt na signálování až číslo zadané v milisekundách *dwTimeOut* parametru. Pokud je synchronizační objekt stát nesignalizováno ve stanoveném čase, `Lock` vrátí chybu.

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

Popisovač na základní objekt synchronizace.

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator POPISOVAČ

Tento operátor se získat popisovač `CSyncObject` objektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu popisovač objekt synchronizace. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Popisovač můžete použít pro volání rozhraní API Windows přímo.

##  <a name="unlock"></a>  CSyncObject::Unlock

Deklarace `Unlock` bez parametrů je čistě virtuální funkce a musí se přepsat všechny třídy odvozené od `CSyncObject`.

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Výchozí implementace není používána.

*lpPrevCount*<br/>
Výchozí implementace není používána.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Výchozí implementace deklarace se dvěma parametry vždy vrátí hodnotu TRUE. Tato funkce je volána k uvolnění přístup k synchronizační objekt ve vlastnictví volajícího vlákna. Druhý deklarace se poskytuje pro synchronizaci objektů například semafory, která umožňují více než jeden přístup řízené prostředku.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

