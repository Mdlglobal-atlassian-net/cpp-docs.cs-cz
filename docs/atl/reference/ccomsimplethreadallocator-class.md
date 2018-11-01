---
title: Ccomsimplethreadallocator – třída
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
ms.openlocfilehash: 1644014048b27b7ab6076783c5025140527a7ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637538"
---
# <a name="ccomsimplethreadallocator-class"></a>Ccomsimplethreadallocator – třída

Tato třída spravuje výběr vlákna pro třídu `CComAutoThreadModule`.

## <a name="syntax"></a>Syntaxe

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Vybere vlákno.|

## <a name="remarks"></a>Poznámky

`CComSimpleThreadAllocator` spravuje výběr vlákna pro [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` jednoduše projde každé vlákno a vrátí dalším objektem v sekvenci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

Vybere vlákna tak, že zadáte další vlákno v sekvenci.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parametry

*pApt*<br/>
Nepoužívá se v ATL výchozí implementaci.

*nThreads*<br/>
Maximální počet vláken v modulu souboru EXE.

### <a name="return-value"></a>Návratová hodnota

Celé číslo mezi nulou a (*nThreads* – 1). Určuje jedno z vláken v modulu souboru EXE.

### <a name="remarks"></a>Poznámky

Můžete přepsat `GetThread` nabízejí jiný způsob výběru a vytvoříte využívání *pApt* parametru.

`GetThread` je volán [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Viz také

[CComApartment – třída](../../atl/reference/ccomapartment-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
