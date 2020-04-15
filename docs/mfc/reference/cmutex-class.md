---
title: Třída CMutex
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363286"
---
# <a name="cmutex-class"></a>Třída CMutex

Představuje "mutex" – objekt synchronizace, který umožňuje jeden podproces vzájemně se vylučující přístup k prostředku.

## <a name="syntax"></a>Syntaxe

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Vytvoří `CMutex` objekt.|

## <a name="remarks"></a>Poznámky

Objekty Mutex jsou užitečné v případě, že pouze jedno vlákno najednou může být povoleno upravovat data nebo jiný řízený prostředek. Například přidání uzlů do propojeného seznamu je proces, který by měl být povolen pouze jedním vláknem najednou. Pomocí objektu `CMutex` k řízení propojeného seznamu může k seznamu získat přístup pouze jedno vlákno najednou.

Chcete-li `CMutex` použít objekt, vytvořte objekt, `CMutex` když je potřeba. Zadejte název objektu mutex, na který chcete čekat, a že aplikace by ji měla zpočátku vlastnit. Potom můžete přistupovat k objektu mutex, když se vrátí konstruktor. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po dokončení přístupu k řízenému prostředku.

Alternativní metodou pro `CMutex` použití objektů je přidání `CMutex` proměnné typu jako datového člena do třídy, kterou chcete řídit. Během vytváření řízeného objektu volejte konstruktor `CMutex` datového člena určující, zda je objekt mutex původně vlastněn, název objektu mutex (pokud bude použit přes hranice procesu) a požadované atributy zabezpečení.

Chcete-li získat `CMutex` přístup k prostředkům řízenýobjektů tímto způsobem, nejprve vytvořte proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo [cmultilock](../../mfc/reference/cmultilock-class.md) v přístupové členské funkce prostředku. Potom volání `Lock` členské funkce objektu lock (například [CSingleLock::Lock).](../../mfc/reference/csinglelock-class.md#lock) V tomto okamžiku vlákno buď získat přístup k prostředku, počkejte na prostředek, který má být uvolněn a získat přístup, nebo čekat na prostředek, který má být uvolněn a časový režim, nedaří získat přístup k prostředku. V každém případě byl přístup k prostředku přístupným způsobem bezpečným pro přístup z více vláken. Chcete-li uvolnit prostředek, použijte `Unlock` člennou funkci objektu zámku (například [CSingleLock::Unlock)](../../mfc/reference/csinglelock-class.md#unlock)nebo povolte, aby objekt zámku vypadl z oboru.

Další informace o `CMutex` používání objektů naleznete v článku [Vícevláken: Jak používat třídy synchronizace](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex

Vytvoří pojmenovaný nebo nepojmenovaný `CMutex` objekt.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Určuje, zda vlákno `CMutex` vytvářející objekt má zpočátku přístup k prostředku řízenému objektem mutex.

*název lpsz*<br/>
Název objektu. `CMutex` Pokud existuje jiný objekt mutex se stejným názvem, *lpszName* musí být zadán, pokud objekt bude použit přes hranice procesu. Pokud **null**, mutex bude nepojmenovaný. Pokud název odpovídá existující mutex, konstruktor vytvoří `CMutex` nový objekt, který odkazuje na mutex tohoto názvu. Pokud název odpovídá existující objekt synchronizace, který není mutex, konstrukce se nezdaří.

*Atribut lpsa*<br/>
Atributy zabezpečení objektu mutex. Úplný popis této struktury naleznete v [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) sady Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat `CMutex` přístup nebo uvolnit objekt, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho členské funkce [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock) Pokud `CMutex` je objekt používán samostatně, zavolejte jeho členská `Unlock` funkce k jeho uvolnění.

> [!IMPORTANT]
> Po vytvoření `CMutex` objektu použijte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) k zajištění, že mutex ještě neexistoval. Pokud mutex existoval neočekávaně, může to znamenat, že proces rogue je squatting a může být v úmyslu použít mutex zlomyslně. V tomto případě je doporučená procedura s ohledem na zabezpečení zavřít popisovač a pokračovat, jako by došlo k chybě při vytváření objektu.

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
