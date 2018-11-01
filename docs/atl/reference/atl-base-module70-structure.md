---
title: _Atl_base_module70 – struktura
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 806ed86076d8b27662bcd9a328d43cabf5df5c86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667542"
---
# <a name="atlbasemodule70-structure"></a>_Atl_base_module70 – struktura

Používat jakýkoli projekt, který používá knihovnu ATL.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>Členové

`cbSize`<br/>
Velikost struktury, použít pro správu verzí.

`m_hInst`<br/>
`hInstance` Pro tento modul (exe nebo dll).

`m_hInstResource`<br/>
Výchozí instance prostředků popisovač.

`m_bNT5orWin98`<br/>
Informace o verzi operačního systému. Vnitřně jej používá knihovnu ATL.

`dwAtlBuildVer`<br/>
Obsahuje verzi knihovny ATL. Aktuálně 0x0700.

`pguidVer`<br/>
ATL interní identifikátor GUID.

`m_csResource`<br/>
Používá k synchronizaci přístupu k `m_rgResourceInstance` pole. Vnitřně jej používá knihovnu ATL.

`m_rgResourceInstance`<br/>
Pole použitá k vyhledání prostředků ve všech instancích prostředků, které ATL je vědět. Vnitřně jej používá knihovnu ATL.

## <a name="remarks"></a>Poznámky

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) je definován jako typedef _atl_base_module70 –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

