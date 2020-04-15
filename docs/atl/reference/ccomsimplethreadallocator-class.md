---
title: Třída CComSimpleThreadAllocator
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327347"
---
# <a name="ccomsimplethreadallocator-class"></a>Třída CComSimpleThreadAllocator

Tato třída spravuje výběr podprocesu pro třídu `CComAutoThreadModule`.

## <a name="syntax"></a>Syntaxe

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Vybere vlákno.|

## <a name="remarks"></a>Poznámky

`CComSimpleThreadAllocator`spravuje výběr vláken pro [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`jednoduše prochází každým vláknem a vrátí další v pořadí.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleThreadAllocator::GetThread

Vybere vlákno zadáním dalšího vlákna v sekvenci.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parametry

*pApt*<br/>
Nepoužívá se ve výchozí implementaci atl.

*nVlákna*<br/>
Maximální počet podprocesů v modulu EXE.

### <a name="return-value"></a>Návratová hodnota

Celé číslo mezi nulou a (*nVlákna* - 1). Identifikuje jedno z podprocesů v modulu EXE.

### <a name="remarks"></a>Poznámky

Můžete přepsat `GetThread` poskytnout jinou metodu výběru nebo použít *parametr pApt.*

`GetThread`je volána [modulem CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Viz také

[Třída CComApartment](../../atl/reference/ccomapartment-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
