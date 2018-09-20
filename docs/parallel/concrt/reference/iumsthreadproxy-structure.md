---
title: Iumsthreadproxy – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 573bee042788f03278abc78fbc541c933d693907
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417381"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy – struktura

Abstrakce vlákna exekuce. Pokud má váš Plánovač udělit uživatelským režimem plánovatelná vlákna (UMS) nastavte hodnotu pro element zásad plánovače `SchedulerKind` k `UmsThreadDefault`a implementovat `IUMSScheduler` rozhraní. UMS vlákna jsou pouze podporované v 64bitových systémech s verzí Windows 7 a vyšší.

## <a name="syntax"></a>Syntaxe

```
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Iumsthreadproxy::entercriticalregion –](#entercriticalregion)|Volá se, aby bylo možné zadat důležité oblasti. Když uvnitř důležité oblasti, nebudou sledovat Plánovač asynchronní blokující operace, ke kterým dochází při oblast. To znamená, že nebude znovu zadat Plánovač pro stránkování, pozastavení vlákna, volá asynchronní procedury jádra (APCs) a tak dále, UMS vlákna.|
|[Iumsthreadproxy::enterhypercriticalregion –](#enterhypercriticalregion)|Volá se, aby bylo možné zadat hyper důležité oblasti. Když uvnitř hyper důležité oblasti, nebude Plánovač sledovat všechny blokující operace, ke kterým dochází při oblast. To znamená, že plánovač nebude znovu zadat pro blokování volání funkcí, pokusy o získání zámku vlákna pozastavení, volání asynchronní procedury jádra (APCs), který blok, stránkování a tak dále, pro UMS vlákna.|
|[Iumsthreadproxy::exitcriticalregion –](#exitcriticalregion)|Volá se, aby bylo možné ukončit důležité oblasti.|
|[Iumsthreadproxy::exithypercriticalregion –](#exithypercriticalregion)|Volá se, aby bylo možné ukončit hyper důležité oblasti.|
|[Iumsthreadproxy::getcriticalregiontype –](#getcriticalregiontype)|Vrátí druhu kritických proxy vlákna je v rámci oblasti. Protože hyper důležité oblasti jsou nadmnožina o důležitých oblastech, pokud je zadán kód důležité oblasti a pak hyper důležité oblasti, `InsideHyperCriticalRegion` bude vrácen.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

**Namespace:** souběžnosti

##  <a name="entercriticalregion"></a>  Iumsthreadproxy::entercriticalregion – metoda

Volá se, aby bylo možné zadat důležité oblasti. Když uvnitř důležité oblasti, nebudou sledovat Plánovač asynchronní blokující operace, ke kterým dochází při oblast. To znamená, že nebude znovu zadat Plánovač pro stránkování, pozastavení vlákna, volá asynchronní procedury jádra (APCs) a tak dále, UMS vlákna.

```
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka důležité oblasti. Důležité oblasti jsou vícenásobné.

##  <a name="enterhypercriticalregion"></a>  Iumsthreadproxy::enterhypercriticalregion – metoda

Volá se, aby bylo možné zadat hyper důležité oblasti. Když uvnitř hyper důležité oblasti, nebude Plánovač sledovat všechny blokující operace, ke kterým dochází při oblast. To znamená, že plánovač nebude znovu zadat pro blokování volání funkcí, pokusy o získání zámku vlákna pozastavení, volání asynchronní procedury jádra (APCs), který blok, stránkování a tak dále, pro UMS vlákna.

```
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka hyper důležité oblasti. Hyper důležité oblasti jsou vícenásobné.

### <a name="remarks"></a>Poznámky

Plánovači musí být opatrní neobyčejně metody, které volá, a co uzamkne ji proti získá v těchto oblastech. Pokud na zámek, který se nachází použito cokoli, co scheduler je zodpovědná za plánování bloky kódu v těchto oblastech, může následovat zablokování.

##  <a name="exitcriticalregion"></a>  Iumsthreadproxy::exitcriticalregion – metoda

Volá se, aby bylo možné ukončit důležité oblasti.

```
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka důležité oblasti. Důležité oblasti jsou vícenásobné.

##  <a name="exithypercriticalregion"></a>  Iumsthreadproxy::exithypercriticalregion – metoda

Volá se, aby bylo možné ukončit hyper důležité oblasti.

```
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Nová hloubka hyper důležité oblasti. Hyper důležité oblasti jsou vícenásobné.

##  <a name="getcriticalregiontype"></a>  Iumsthreadproxy::getcriticalregiontype – metoda

Vrátí druhu kritických proxy vlákna je v rámci oblasti. Protože hyper důležité oblasti jsou nadmnožina o důležitých oblastech, pokud je zadán kód důležité oblasti a pak hyper důležité oblasti, `InsideHyperCriticalRegion` bude vrácen.

```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Návratová hodnota

Typ důležité oblasti proxy vlákna je v rámci.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[IUMSScheduler – struktura](iumsscheduler-structure.md)
