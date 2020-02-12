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
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139964"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy – struktura

Abstrakce pro vlákno provádění. Pokud chcete, aby váš Plánovač měl udělená vlákna v uživatelském režimu plánovatelná (UMS), nastavte hodnotu pro element Scheduler Policy `SchedulerKind` na `UmsThreadDefault`a implementujte rozhraní `IUMSScheduler`. UMS vlákna jsou podporována pouze v 64 operačních systémech s verzí Windows 7 a vyšší.

## <a name="syntax"></a>Syntaxe

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IUMSThreadProxy:: Entercriticalregion –](#entercriticalregion)|Volá se, aby se zadala kritická oblast. V případě nepostradatelné oblasti Plánovač nebude sledovat asynchronní blokující operace, ke kterým dojde během dané oblasti. To znamená, že Plánovač nebude znovu zadán pro chyby stránky, pozastavení vlákna, volání asynchronních procedur v jádru (APCs) a tak dále pro vlákno UMS.|
|[IUMSThreadProxy:: Enterhypercriticalregion –](#enterhypercriticalregion)|Volá se, aby se zadal region kritická pro Hyper-v. V případě kritické oblasti technologie Hyper nebude Plánovač sledovat žádné blokující operace, ke kterým dojde během dané oblasti. To znamená, že Plánovač nebude znovu zadán pro blokující volání funkcí, uzamknout pokusy o získání, které blok, chyby stránkování, pozastavení vlákna, volání asynchronní procedury jádra (APCs) a tak dále, pro vlákno UMS.|
|[IUMSThreadProxy:: Exitcriticalregion –](#exitcriticalregion)|Volá se, aby se ukončila kritická oblast.|
|[IUMSThreadProxy:: Exithypercriticalregion –](#exithypercriticalregion)|Volá se, aby se ukončila oblast kritická pro Hyper-v.|
|[IUMSThreadProxy:: Getcriticalregiontype –](#getcriticalregiontype)|Vrátí typ kritické oblasti, v rámci které je umístěn proxy vlákna. Vzhledem k tomu, že kritické oblasti technologie Hyper-v jsou nadmnožině kritických oblastí, pokud kód zadal kritickou oblast a pak je kritická oblast technologie Hyper-v, `InsideHyperCriticalRegion` se vrátí.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

**Obor názvů:** souběžnost

## <a name="entercriticalregion"></a>IUMSThreadProxy:: Entercriticalregion – – metoda

Volá se, aby se zadala kritická oblast. V případě nepostradatelné oblasti Plánovač nebude sledovat asynchronní blokující operace, ke kterým dojde během dané oblasti. To znamená, že Plánovač nebude znovu zadán pro chyby stránky, pozastavení vlákna, volání asynchronních procedur v jádru (APCs) a tak dále pro vlákno UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka kritické oblasti. Kritické oblasti se připravují.

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy:: Enterhypercriticalregion – – metoda

Volá se, aby se zadal region kritická pro Hyper-v. V případě kritické oblasti technologie Hyper nebude Plánovač sledovat žádné blokující operace, ke kterým dojde během dané oblasti. To znamená, že Plánovač nebude znovu zadán pro blokující volání funkcí, uzamknout pokusy o získání, které blok, chyby stránkování, pozastavení vlákna, volání asynchronní procedury jádra (APCs) a tak dále, pro vlákno UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová Hloubka oblasti kritické pro technologii Hyper-v. V oblastech kritických pro technologii Hyper se přecházejí.

### <a name="remarks"></a>Poznámky

Plánovač musí být neobyčejně uvážlivě o tom, jaké metody volá a co v těchto oblastech získává. Pokud se kód v takové oblasti zablokuje na zámek, který je držený něco, co Plánovač zodpovídá za plánování, může se zablokování následovat.

## <a name="exitcriticalregion"></a>IUMSThreadProxy:: Exitcriticalregion – – metoda

Volá se, aby se ukončila kritická oblast.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka kritické oblasti. Kritické oblasti se připravují.

## <a name="exithypercriticalregion"></a>IUMSThreadProxy:: Exithypercriticalregion – – metoda

Volá se, aby se ukončila oblast kritická pro Hyper-v.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová Hloubka oblasti kritické pro technologii Hyper-v. V oblastech kritických pro technologii Hyper se přecházejí.

## <a name="getcriticalregiontype"></a>IUMSThreadProxy:: Getcriticalregiontype – – metoda

Vrátí typ kritické oblasti, v rámci které je umístěn proxy vlákna. Vzhledem k tomu, že kritické oblasti technologie Hyper-v jsou nadmnožině kritických oblastí, pokud kód zadal kritickou oblast a pak je kritická oblast technologie Hyper-v, `InsideHyperCriticalRegion` se vrátí.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Typ kritické oblasti, v rámci které je umístěn proxy vlákna.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)
