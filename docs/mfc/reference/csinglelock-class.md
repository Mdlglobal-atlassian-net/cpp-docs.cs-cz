---
title: CSingleLock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 988ade49bb7acbb3bcb759f1bdf3e565e033308f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394137"
---
# <a name="csinglelock-class"></a>CSingleLock – třída

Představuje mechanismus řízení přístupu, který se používá při řízení přístupu k prostředku v programu s více vlákny.

## <a name="syntax"></a>Syntaxe

```
class CSingleLock
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Vytvoří `CSingleLock` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Určuje, pokud je objekt uzamčen.|
|[CSingleLock::Lock](#lock)|Čekání na synchronizační objekt.|
|[CSingleLock::Unlock](#unlock)|Uvolní objekt synchronizace.|

## <a name="remarks"></a>Poznámky

`CSingleLock` nemá základní třídu.

Chcete-li použít synchronizační třídy [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), a [CEvent](../../mfc/reference/cevent-class.md), je nutné vytvořit buď `CSingleLock` nebo [CMultiLock](../../mfc/reference/cmultilock-class.md) objektu pro čekání na a uvolnění objektu synchronizace. Použití `CSingleLock` kdy je potřeba jenom čekat na jeden objekt v čase. Použít `CMultiLock` pokud existuje více objektů, které můžete použít v určitou dobu.

Použití `CSingleLock` objektu, volání konstruktoru uvnitř členské funkce ve třídě řízené prostředků. Zavolejte [uzamčeno](#islocked) členskou funkci k určení, jestli je prostředek k dispozici. Pokud se jedná, pokračujte zbytek členskou funkci. Pokud prostředek není k dispozici, počkejte určenou dobu pro prostředek, který má být všeobecně dostupné nebo vrátí hodnotu neúspěch. Po dokončení použití zdroje buď volat [odemknout](#unlock) fungovat, pokud `CSingleLock` je znovu použít, nebo povolíte `CSingleLock` objekt, který se má zničit.

`CSingleLock` objekty vyžadují existenci objektu odvozeného od [CSyncObject](../../mfc/reference/csyncobject-class.md). To je obvykle datový člen třídy řízené prostředků. Další informace o tom, jak používat `CSingleLock` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CSingleLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

Vytvoří `CSingleLock` objektu.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*odstraněný objekt*<br/>
Odkazuje na objekt synchronizace přístup. Nemůže mít hodnotu NULL.

*bInitialLock*<br/>
Určuje, zda počáteční pokus o přístup k zadaného objektu.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volat v rámci členská funkce přístupu řízeného prostředku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

Určuje, pokud objekt přidružený `CSingleLock` objekt je nonsignaled (není k dispozici).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt uzamčen; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

Voláním této funkce získáte přístup k prostředku řídí synchronizace objekt zadaný do `CSingleLock` konstruktoru.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Určuje dobu čekání na synchronizační objekt k dispozici (signalizován). Pokud je NEKONEČNÉ, `Lock` budou čekat na objekt je signál, před vrácením.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je synchronizační objekt signalizována, `Lock` úspěšně vrátí a vlákno je nyní vlastníkem objektu. Pokud se objekt synchronizace nonsignaled (není k dispozici), `Lock` počká na synchronizační objekt na signálování až číslo zadané v milisekundách *dwTimeOut* parametru. Pokud je synchronizační objekt stát nesignalizováno ve stanoveném čase, `Lock` vrátí chybu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

Uvolní objekt synchronizace vlastněné `CSingleLock`.

```
BOOL Unlock();


BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Počet přístupů k uvolnění. Musí být větší než 0. Pokud zadané by způsobila objektu počet překročí maximální, hodnota tohoto čítače se nemění a funkce vrátí FALSE.

*lPrevCount*<br/>
Odkazuje na proměnnou, která předchozí počet synchronizační objekt přijetí. Pokud má hodnotu NULL, nevrátí se předchozího počtu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je volána `CSingleLock`jeho destruktor.

Pokud potřebujete více než jeden přístup počet semafor verzi, použijte tedy o druhou podobu `Unlock` a určit počet přístupů k uvolnění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock – třída](../../mfc/reference/cmultilock-class.md)
