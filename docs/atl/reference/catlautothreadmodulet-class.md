---
title: Třída CAtlAutoThreadModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321545"
---
# <a name="catlautothreadmodulet-class"></a>Třída CAtlAutoThreadModuleT

Tato třída poskytuje metody pro implementaci serveru COM s družinou s družinou modelu apartment.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída, která bude implementovat server COM.

*ThreadAllocator*<br/>
Třída spravující výběr podprocesu. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Určuje interval časového limitu v milisekundách. Výchozí hodnota je INFINITE, což znamená, že časový limit metody nikdy neuplyne.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE na základě počtu procesorů.|

## <a name="remarks"></a>Poznámky

Třída [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) je `CAtlAutoThreadModuleT` odvozena z k implementaci serveru COM s družné hotence s družinou. Nahrazuje zastaralou třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Tato třída by neměla být použita v dll, jako výchozí *dwWait* hodnota INFINITE způsobí zablokování při uvolnění dll.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE na základě počtu procesorů.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet podprocesů, které mají být vytvořeny v modulu EXE.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu, pokud chcete použít jinou metodu pro výpočet počtu podprocesů. Ve výchozím nastavení je počet podprocesů založen na počtu procesorů.

## <a name="see-also"></a>Viz také

[Třída IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
