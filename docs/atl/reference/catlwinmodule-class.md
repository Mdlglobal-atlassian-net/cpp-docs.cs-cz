---
title: Catlwinmodule – třída
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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269458"
---
# <a name="catlwinmodule-class"></a>Catlwinmodule – třída

Tato třída poskytuje podporu pro komponenty ATL časová okna.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Přidá datového objektu.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Vrací ukazatel na datový objekt okna modul.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje podporu pro všechny třídy ATL, které vyžadují oddílová funkce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="addcreatewnddata"></a>  CAtlWinModule::AddCreateWndData

Tato metoda inicializuje a přidá `_AtlCreateWndData` struktury.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Ukazatel `_AtlCreateWndData` struktura bude inicializována a přidán do aktuální modul.

*pObject*<br/>
Ukazatel na objekt **to** ukazatele.

### <a name="remarks"></a>Poznámky

Tato metoda volá [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) které inicializuje [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury. Tato struktura bude uložený **to** ukazatel, použít k získání instance třídy v procedury okna.

##  <a name="catlwinmodule"></a>  CAtlWinModule::CAtlWinModule

Konstruktor

```
CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Jestliže se inicializace nezdaří, **EXCEPTION_NONCONTINUABLE** je vyvolána výjimka.

##  <a name="dtor"></a>  Catlwinmodule –:: ~ catlwinmodule –

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="extractcreatewnddata"></a>  CAtlWinModule::ExtractCreateWndData

Tato metoda vrací ukazatel na `_AtlCreateWndData` struktury.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `_AtlCreateWndData` struktura přidali dříve, pomocí [CAtlWinModule::AddCreateWndData](#addcreatewnddata), nebo hodnota NULL, pokud je k dispozici žádný objekt.

## <a name="see-also"></a>Viz také:

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
