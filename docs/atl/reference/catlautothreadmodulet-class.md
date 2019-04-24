---
title: Catlautothreadmodulet – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 63f1c8dbe3c752773fd64c6e339a9a3b67051d35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247164"
---
# <a name="catlautothreadmodulet-class"></a>Catlautothreadmodulet – třída

Tato třída poskytuje metody pro implementaci serveru ve fondu vláken, apartment model modelu COM.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída, která implementuje serveru COM.

*ThreadAllocator*<br/>
Třídy správy výběr vlákna. Výchozí hodnota je [ccomsimplethreadallocator –](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Určuje interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, což znamená, že interval časového limitu metody nikdy vypaří.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE, na základě počtu procesorů.|

## <a name="remarks"></a>Poznámky

Třída [catlautothreadmodule –](../../atl/reference/catlautothreadmodule-class.md) je odvozena z `CAtlAutoThreadModuleT` kvůli implementaci ve fondu vláken, apartment model modelu COM serveru. Nahradí zastaralou třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
>  Tato třída by neměl v knihovně DLL použít jako výchozí *dwWait* hodnoty NEKONEČNÉ způsobí zablokování při uvolnění knihovny DLL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads

Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE, na základě počtu procesorů.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet vláken v modulu souboru EXE.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu, pokud chcete použít jinou metodu pro výpočet počtu vláken. Ve výchozím nastavení počet vláken vychází z počtu procesorů.

## <a name="see-also"></a>Viz také:

[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
