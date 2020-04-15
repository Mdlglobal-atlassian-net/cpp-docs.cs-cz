---
title: WinModule globální funkce
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329364"
---
# <a name="winmodule-global-functions"></a>WinModule globální funkce

Tyto funkce poskytují `_AtlCreateWndData` podporu pro operace struktury.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Tato funkce se používá k inicializaci a přidání `_AtlCreateWndData` struktury.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Volání této funkce extrahovat existující `_AtlCreateWndData` strukturu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

Tato funkce se používá k inicializaci a přidání `_AtlCreateWndData` struktury.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parametry

*pWinModul*<br/>
Ukazatel na strukturu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) modulu.

*Pdata*<br/>
Ukazatel na [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) strukturu, která má být inicializována a přidána do aktuálního modulu.

*pObjekt*<br/>
Ukazatel na objekt je **tento** ukazatel.

### <a name="remarks"></a>Poznámky

Inicializuje `_AtlCreateWndData` strukturu, která se používá k uložení **tohoto** ukazatele, který slouží k odkazování na instance `_ATL_WIN_MODULE70` třídy, a přidá ji do seznamu, na který odkazuje struktura modulu. Volal [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

Volání této funkce extrahovat existující `_AtlCreateWndData` strukturu.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parametry

*pWinModul*<br/>
Ukazatel na strukturu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) modulu.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury.

### <a name="remarks"></a>Poznámky

Tato funkce extrahuje existující `_AtlCreateWndData` strukturu ze seznamu, `_ATL_WIN_MODULE70` na který odkazuje struktura modulu.

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
