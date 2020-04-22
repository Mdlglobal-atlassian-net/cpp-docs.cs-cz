---
title: Třída CAtlWinModule
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
ms.openlocfilehash: e131ca1b4eb6e320d533ad1292c23add6ffa46e5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748550"
---
# <a name="catlwinmodule-class"></a>Třída CAtlWinModule

Tato třída poskytuje podporu pro součásti oken ATL.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor|
|[CAtlWinModule::~CAtlWinModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Přidá datový objekt.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Vrátí ukazatel datového objektu modulu okna.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje podporu pro všechny třídy ATL, které vyžadují funkce okna.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Tato metoda inicializuje `_AtlCreateWndData` a přidá strukturu.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Ukazatel na `_AtlCreateWndData` strukturu, která má být inicializována a přidána do aktuálního modulu.

*pObjekt*<br/>
Ukazatel na objekt je **tento** ukazatel.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlWinModuleAddCreateWndData,](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) která inicializuje [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury. Tato struktura bude ukládat **tento** ukazatel, který se používá k získání instance třídy v procedurách okna.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Konstruktor

```
CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Pokud se inicializace nezdaří, je vyvolána **výjimka EXCEPTION_NONCONTINUABLE.**

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule::~CAtlWinModule

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Tato metoda vrátí ukazatel `_AtlCreateWndData` na strukturu.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `_AtlCreateWndData` strukturu dříve přidanou pomocí [CAtlWinModule::AddCreateWndData](#addcreatewnddata)nebo NULL, pokud není k dispozici žádný objekt.

## <a name="see-also"></a>Viz také

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
