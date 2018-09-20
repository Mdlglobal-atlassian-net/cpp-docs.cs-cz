---
title: CCriticalSection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e5147faaf0170a10295006f12d7e95f5dfd3e8d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380695"
---
# <a name="ccriticalsection-class"></a>CCriticalSection – třída

Představuje "kritický oddíl" – synchronizační objekt umožňující vždy jednomu vláknu postupně, aby přístup k prostředku nebo části kódu.

## <a name="syntax"></a>Syntaxe

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Vytvoří `CCriticalSection` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|Použít k získání přístupu k `CCriticalSection` objektu.|
|[CCriticalSection::Unlock](#unlock)|Verze `CCriticalSection` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CCriticalSection::operator critical_section – *](#operator_critical_section_star)|Načte ukazatel na vnitřní objekt critical_section –.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Critical_section – objekt.|

## <a name="remarks"></a>Poznámky

Kritické oddíly jsou užitečné, pokud najednou pouze jedno vlákno může být povoleno upravovat data nebo jiný řízené prostředek. Například přidání uzlů do propojený seznam je proces, který pouze by měl být povoleno jedno vlákno najednou. Pomocí `CCriticalSection` objekt pro řízení seznamu propojených pouze jedno vlákno najednou můžete získat přístup k seznamu.

> [!NOTE]
>  Funkce `CCriticalSection` třída poskytuje skutečný objekt critical_section – Win32.

Kritické oddíly se používají místo vzájemně vyloučené přístupy (viz [CMutex](../../mfc/reference/cmutex-class.md)) při rychlost je klíčová a zdroje nesmí použít přes hranice procesu.

Existují dvě metody pro použití `CCriticalSection` objektu: samostatné a vložené v třídě.

- Samostatné metodu použít samostatný `CCriticalSection` objektu, vytvořit `CCriticalSection` objektu, když ho nepotřebují. Po úspěšném návrat z konstruktoru explicitně zamknout objekt voláním [Zámek](#lock). Volání [odemknout](#unlock) po dokončení přístupu k kritický oddíl. Tato metoda při přesnější někomu čtení zdrojového kódu, je více náchylné k chybám jako nesmíte zapomenout při zamykání a odemykání kritický oddíl před a za přístup.

     Vhodnější metodou je použít [CSingleLock](../../mfc/reference/csinglelock-class.md) třídy. Má také `Lock` a `Unlock` metody, ale nemusíte starat o odemknutí prostředku, pokud dojde k výjimce.

- Vložené metody třídy můžete také sdílet s více vlákny tak, že přidáte `CCriticalSection`– datový člen typu třídy a zamykání datový člen v případě potřeby.

Další informace o používání `CCriticalSection` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

Vytvoří `CCriticalSection` objektu.

```
CCriticalSection();
```

### <a name="remarks"></a>Poznámky

Přístup nebo vydání `CCriticalSection` objektu, vytvořit [CSingleLock](../../mfc/reference/csinglelock-class.md) objektu a volání jeho [Zámek](../../mfc/reference/csinglelock-class.md#lock) a [odemknout](../../mfc/reference/csinglelock-class.md#unlock) členské funkce. Pokud `CCriticalSection` objektu používá samostatné, zavolejte jeho [odemknout](#unlock) členskou funkci pro uvolnění.

Pokud selže přidělování požadované systémové paměti, s výjimkou paměti konstruktoru (typu [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md)) je automaticky vyvolána.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CCriticalSection::Lock](#lock).

##  <a name="lock"></a>  CCriticalSection::Lock

Zavolejte tuto členskou funkci získat přístup k objektu kritický oddíl.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
`Lock` Tento parametr ignoruje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

`Lock` je blokovacího hovoru, který nebude vracet, dokud je signalizována objekt kritický oddíl (k dispozici).

Pokud vypršel časový limit čekání jsou nezbytné, můžete použít [CMutex](../../mfc/reference/cmutex-class.md) místo objektu `CCriticalSection` objektu.

Pokud `Lock` selže přidělování nezbytné systémové paměti, s výjimkou paměti (typu [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md)) je automaticky vyvolána.

### <a name="example"></a>Příklad

Tento příklad ukazuje postup vnořené kritický oddíl, řízení přístupu ke sdílenému prostředku (statické `_strShared` objektů) pomocí sdíleného `CCriticalSection` objektu. `SomeMethod` Funkce ukazuje aktualizaci sdíleného prostředku bezpečným způsobem.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

Obsahuje objekt kritický oddíl, který se používá ve všech `CCriticalSection` metody.

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator critical_section – *

Načte objekt critical_section –.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce načtete ukazatel na vnitřní objekt critical_section –.

##  <a name="unlock"></a>  CCriticalSection::Unlock

Verze `CCriticalSection` objektu používá jiné vlákno.

```
BOOL Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CCriticalSection` byl vlastníkem objektu vlákna a vydání bylo úspěšné; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud `CCriticalSection` používá samostatné, `Unlock` musí být volána ihned po dokončení používání prostředků řídí kritický oddíl. Pokud [CSingleLock](../../mfc/reference/csinglelock-class.md) objektu se používá, `CCriticalSection::Unlock` zavolá se zamknout objekt `Unlock` členskou funkci.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMutex – třída](../../mfc/reference/cmutex-class.md)
