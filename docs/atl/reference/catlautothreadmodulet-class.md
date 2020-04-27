---
title: CAtlAutoThreadModuleT – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 7308e3a51c531fbe942e2df326c03273eeb326e2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168720"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT – třída

Tato třída poskytuje metody pro implementaci serveru modelu COM s více vlákny ve fondu.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída, která bude implementovat server COM.

*ThreadAllocator*<br/>
Třída, která spravuje výběr vlákna. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Určuje časový limit (v milisekundách). Výchozí hodnota je INFINITá, což znamená, že interval časového limitu metody nikdy neuplynul.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE na základě počtu procesorů.|

## <a name="remarks"></a>Poznámky

Třída [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) je odvozena z `CAtlAutoThreadModuleT` , aby mohla implementovat Server modelu COM ve fondu vláken. Nahrazuje zastaralou třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Tato třída by se neměla používat v knihovně DLL, protože výchozí hodnota *DWWAIT* nekonečné způsobí zablokování při uvolnění knihovny DLL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE na základě počtu procesorů.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet vláken, která mají být vytvořena v modulu EXE.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete použít jinou metodu pro výpočet počtu vláken. Ve výchozím nastavení je počet vláken založen na počtu procesorů.

## <a name="see-also"></a>Viz také

[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
