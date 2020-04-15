---
title: Třída CCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369368"
---
# <a name="ccriticalsection-class"></a>Třída CCriticalSection

Představuje "kritický oddíl" – objekt synchronizace, který umožňuje jedno vlákno najednou přístup k prostředku nebo části kódu.

## <a name="syntax"></a>Syntaxe

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Vytvoří `CCriticalSection` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCriticalSection::Zamknout](#lock)|Slouží k získání `CCriticalSection` přístupu k objektu.|
|[CCriticalSection::Odemknout](#unlock)|Uvolní `CCriticalSection` objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CCriticalSection::operátor CRITICAL_SECTION*](#operator_critical_section_star)|Načte ukazatel na vnitřní objekt CRITICAL_SECTION.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CCriticalSekce::m_sect](#m_sect)|Objekt CRITICAL_SECTION.|

## <a name="remarks"></a>Poznámky

Kritické oddíly jsou užitečné, pokud pouze jedno vlákno najednou může mít možnost upravovat data nebo jiný řízený prostředek. Například přidání uzlů do propojeného seznamu je proces, který by měl být povolen pouze jedním vláknem najednou. Pomocí objektu `CCriticalSection` k řízení propojeného seznamu může k seznamu získat přístup pouze jedno vlákno najednou.

> [!NOTE]
> Funkce `CCriticalSection` třídy je poskytována skutečný Win32 CRITICAL_SECTION objekt.

Kritické oddíly se používají místo mutexů (viz [CMutex),](../../mfc/reference/cmutex-class.md)když je rychlost kritická a prostředek nebude použit přes hranice procesu.

Existují dvě metody pro `CCriticalSection` použití objektu: samostatné a vložené do třídy.

- Samostatná metoda Chcete-li použít `CCriticalSection` samostatný objekt, vytvořte objekt, `CCriticalSection` když je potřeba. Po úspěšném návratu z konstruktoru explicitně uzamkněte objekt voláním [Lock](#lock). Po dokončení přístupu k kritické části volejte [Unlock.](#unlock) Tato metoda, zatímco jasnější pro někoho čtení zdrojového kódu, je náchylnější k chybě, jak si musíte pamatovat na uzamčení a odemknutí kritické části před a po přístupu.

   Vhodnější metodou je použít třídu [CSingleLock.](../../mfc/reference/csinglelock-class.md) Má také `Lock` metodu a, `Unlock` ale nemusíte se starat o odemknutí prostředku, pokud dojde k výjimce.

- Vložená metoda: Třídu můžete také sdílet s `CCriticalSection`více vlákny přidáním datového člena typu -type do třídy a uzamčením datového člena v případě potřeby.

Další informace o `CCriticalSection` používání objektů naleznete v článku [Vícevláken: Jak používat třídy synchronizace](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection

Vytvoří `CCriticalSection` objekt.

```
CCriticalSection();
```

### <a name="remarks"></a>Poznámky

Chcete-li získat `CCriticalSection` přístup nebo uvolnit objekt, vytvořte objekt [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho členské funkce [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock) Pokud `CCriticalSection` je objekt používán samostatně, zavolejte jeho [unlock](#unlock) členská funkce k jeho uvolnění.

Pokud konstruktor uspěje přidělit požadovanou systémovou paměť, je automaticky vyvolána výjimka paměti (typu [CMemoryException).](../../mfc/reference/cmemoryexception-class.md)

### <a name="example"></a>Příklad

  Viz příklad [ccriticalsection::Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Zamknout

Volání této členské funkce získat přístup k objektu kritické části.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
`Lock`ignoruje tuto hodnotu parametru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

`Lock`je blokující volání, které se nevrátí, dokud není signalizován objekt kritické části (bude k dispozici).

Pokud časované čekání jsou nezbytné, můžete použít [CMutex](../../mfc/reference/cmutex-class.md) objekt namísto objektu. `CCriticalSection`

Pokud `Lock` se nepodaří přidělit potřebnou systémovou paměť, je automaticky vyvolána výjimka paměti (typu [CMemoryException).](../../mfc/reference/cmemoryexception-class.md)

### <a name="example"></a>Příklad

Tento příklad ukazuje vnořený kritický oddíl přístup řízením `_strShared` přístupu ke `CCriticalSection` sdílenému prostředku (statický objekt) pomocí sdíleného objektu. Funkce `SomeMethod` demonstruje bezpečnou aktualizaci sdíleného prostředku.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>CCriticalSekce::m_sect

Obsahuje objekt kritického oddílu, `CCriticalSection` který se používá všechny metody.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>CCriticalSection::operátor CRITICAL_SECTION*

Načte CRITICAL_SECTION objekt.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Poznámky

Volání této funkce načíst ukazatel na vnitřní CRITICAL_SECTION objektu.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Odemknout

Uvolní `CCriticalSection` objekt pro použití jiným vláknem.

```
BOOL Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CCriticalSection` pokud byl objekt vlastněn podprocesem a vydání bylo úspěšné; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud `CCriticalSection` je používán samostatně, `Unlock` musí být volána ihned po dokončení použití prostředku řízeného kritickým oddílem. Pokud [csinglelock](../../mfc/reference/csinglelock-class.md) objekt se `CCriticalSection::Unlock` používá, bude volána `Unlock` členské funkce objektu lock.

### <a name="example"></a>Příklad

  Viz příklad [ccriticalsection::Lock](#lock).

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMutex](../../mfc/reference/cmutex-class.md)
