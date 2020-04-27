---
title: Struktura _ATL_BASE_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168641"
---
# <a name="_atl_base_module70-structure"></a>Struktura _ATL_BASE_MODULE70

Používáno jakýmkoli projektem, který používá ATL.

## <a name="syntax"></a>Syntaxe

```cpp
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
Velikost struktury, která se používá pro správu verzí.

`m_hInst`<br/>
`hInstance` Pro tento modul (buď exe nebo DLL).

`m_hInstResource`<br/>
Výchozí popisovač prostředku instance

`m_bNT5orWin98`<br/>
Informace o verzi operačního systému. Interně používá ATL.

`dwAtlBuildVer`<br/>
Ukládá verzi knihovny ATL. Aktuálně se 0x0700.

`pguidVer`<br/>
Vnitřní identifikátor GUID knihovny ATL

`m_csResource`<br/>
Slouží k synchronizaci přístupu k `m_rgResourceInstance` poli. Interně používá ATL.

`m_rgResourceInstance`<br/>
Pole, které slouží k hledání prostředků ve všech instancích prostředků, na kterých je aplikace ATL vědoma. Interně používá ATL.

## <a name="remarks"></a>Poznámky

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) je definován jako definice typu _ATL_BASE_MODULE70.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)
