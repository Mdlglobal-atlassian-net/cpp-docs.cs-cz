---
title: IUMSThreadProxy – struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368084"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy – struktura

Abstrakce pro vlákno provádění. Pokud chcete, aby byl plánovači udělena vlákna uživatelského režimu (UMS), nastavte hodnotu prvku `SchedulerKind` zásad plánovače na `UmsThreadDefault`aplikaci a implementujte `IUMSScheduler` rozhraní. Vlákna služby UMS jsou podporována pouze v 64bitových operačních systémech s verzí Windows 7 a vyšší.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Volána za účelem vstupu do kritické oblasti. Pokud je uvnitř kritické oblasti, plánovač nebude sledovat operace asynchronního blokování, ke kterým dochází během oblasti. To znamená, že plánovač nebude znovu zadán pro chyby stránky, pozastavení vláken, volání asynchronních procedur jádra (APC) a tak dále pro vlákno UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Volána za účelem vstupu do hyperkritické oblasti. Pokud jsou uvnitř hyperkritické oblasti, plánovač nebude sledovat žádné operace blokování, ke kterým dochází během oblasti. To znamená, že plánovač nebude znovu zadán pro blokování volání funkcí, pokusy o získání zámku, které blokují, chyby stránek, pozastavení vláken, asynchronní volání procedur jádra (APC) a tak dále pro vlákno UMS.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Volána za účelem ukončení kritické oblasti.|
|[IUMSThreadProxy::exithypercriticalregion](#exithypercriticalregion)|Volána za účelem ukončení hyperkritické oblasti.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Vrátí, jaký druh kritické oblasti proxy vlákna je uvnitř. Vzhledem k tomu, že hyperkritické oblasti jsou nadmnožinou kritických oblastí, `InsideHyperCriticalRegion` pokud kód vstoupil do kritické oblasti a potom do hyperkritické oblasti, bude vrácen.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Obor názvů:** souběžnost

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThreadProxy::EnterCriticalRegion Metoda

Volána za účelem vstupu do kritické oblasti. Pokud je uvnitř kritické oblasti, plánovač nebude sledovat operace asynchronního blokování, ke kterým dochází během oblasti. To znamená, že plánovač nebude znovu zadán pro chyby stránky, pozastavení vláken, volání asynchronních procedur jádra (APC) a tak dále pro vlákno UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka kritické oblasti. Kritické oblasti jsou reentrant.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThreadProxy::EnterHyperCriticalRegion Metoda

Volána za účelem vstupu do hyperkritické oblasti. Pokud jsou uvnitř hyperkritické oblasti, plánovač nebude sledovat žádné operace blokování, ke kterým dochází během oblasti. To znamená, že plánovač nebude znovu zadán pro blokování volání funkcí, pokusy o získání zámku, které blokují, chyby stránek, pozastavení vláken, asynchronní volání procedur jádra (APC) a tak dále pro vlákno UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka hyperkritické oblasti. Hyperkritické oblasti jsou reentrant.

### <a name="remarks"></a>Poznámky

Plánovač musí být mimořádně opatrní, jaké metody volá a jaké zámky získá v těchto oblastech. Pokud kód v takové oblasti blokuje na zámek, který je držen něco plánovač je zodpovědný za plánování, může dojít k zablokování.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThreadProxy::Metoda ExitCriticalRegion

Volána za účelem ukončení kritické oblasti.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka kritické oblasti. Kritické oblasti jsou reentrant.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThreadProxy::ExitHyperCriticalRegion Metoda

Volána za účelem ukončení hyperkritické oblasti.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka hyperkritické oblasti. Hyperkritické oblasti jsou reentrant.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThreadProxy::GetCriticalRegionType Metoda

Vrátí, jaký druh kritické oblasti proxy vlákna je uvnitř. Vzhledem k tomu, že hyperkritické oblasti jsou nadmnožinou kritických oblastí, `InsideHyperCriticalRegion` pokud kód vstoupil do kritické oblasti a potom do hyperkritické oblasti, bude vrácen.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Typ kritické oblasti proxy podprocesu je uvnitř.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)
