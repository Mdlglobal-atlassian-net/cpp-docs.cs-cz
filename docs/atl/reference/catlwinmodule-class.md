---
title: CAtlWinModule – třída
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418025"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule – třída

Tato třída poskytuje podporu pro komponenty okna knihovny ATL.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Přidá datový objekt.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Vrátí ukazatel na datový objekt modulu systému Windows.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje podporu pro všechny třídy ATL, které vyžadují funkce oken.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Tato metoda inicializuje a přidá strukturu `_AtlCreateWndData`.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Ukazatel na strukturu `_AtlCreateWndData`, která se má inicializovat a přidat do aktuálního modulu.

*pObject*<br/>
Ukazatel na **Tento** ukazatel objektu.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) , která inicializuje strukturu [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Tato struktura uloží **Tento** ukazatel, který se používá k získání instance třídy v postupech okna.

##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Konstruktor

```
CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Pokud se inicializace nezdařila, je vyvolána výjimka **EXCEPTION_NONCONTINUABLE** .

##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Tato metoda vrací ukazatel na strukturu `_AtlCreateWndData`.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `_AtlCreateWndData` strukturu dříve přidanou pomocí [CAtlWinModule:: AddCreateWndData](#addcreatewnddata)nebo null, pokud není k dispozici žádný objekt.

## <a name="see-also"></a>Viz také

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
