---
title: _Atl_base_module70 – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7218d7fc8886cffdcce13f09a682fdc635f84f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759925"
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

`cbSize`  
Velikost struktury, použít pro správu verzí.

`m_hInst`  
`hInstance` Pro tento modul (exe nebo dll).

`m_hInstResource`  
Výchozí instance prostředků popisovač.

`m_bNT5orWin98`  
Informace o verzi operačního systému. Vnitřně jej používá knihovnu ATL.

`dwAtlBuildVer`  
Obsahuje verzi knihovny ATL. Aktuálně 0x0700.

`pguidVer`  
ATL interní identifikátor GUID.

`m_csResource`  
Používá k synchronizaci přístupu k `m_rgResourceInstance` pole. Vnitřně jej používá knihovnu ATL.

`m_rgResourceInstance`  
Pole použitá k vyhledání prostředků ve všech instancích prostředků, které ATL je vědět. Vnitřně jej používá knihovnu ATL.

## <a name="remarks"></a>Poznámky

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) je definován jako typedef _atl_base_module70 –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

