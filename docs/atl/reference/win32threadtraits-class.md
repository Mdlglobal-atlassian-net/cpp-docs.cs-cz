---
title: Win32threadtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8b481c917292c672711c308ac39c052ed4ea1d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752118"
---
# <a name="win32threadtraits-class"></a>Win32threadtraits – třída

Tato třída poskytuje funkce pro vytváření pro Windows vlákno. Pokud vlákno nebude používat funkce CRT, použijte tuto třídu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class Win32ThreadTraits
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statické) Voláním této funkce k vytvoření vlákna, která se nesmí používat funkce CRT.|

## <a name="remarks"></a>Poznámky

Vlastnosti vlákna jsou třídy, které poskytují funkce vytváření pro určitý typ vlákna. Vytvoření funkce má stejný podpis a sémantiku jako Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) funkce.

Vlastnosti vlákna jsou používány následující třídy:

- [Cthreadpool –](../../atl/reference/cthreadpool-class.md)

- [Cworkerthread –](../../atl/reference/cworkerthread-class.md)

Pokud vlákno se pomocí funkce CRT, použijte [crtthreadtraits –](../../atl/reference/crtthreadtraits-class.md) místo.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

Voláním této funkce k vytvoření vlákna, která se nesmí používat funkce CRT.

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>Parametry

*lpsa*  
Atributy zabezpečení pro nové vlákno.

*dwStackSize*  
Velikost zásobníku pro nové vlákno.

*pfnThreadProc*  
Procedura vlákna nové vlákno.

*pvParam*  
Parametr, který má být předán procedura vlákna.

*dwCreationFlags*  
Vytváření příznaky (0 nebo CREATE_SUSPENDED).

*pdwThreadId*  
[out] Adresa proměnné DWORD, který v případě úspěchu, přijímá ID vlákna nově vytvořeného vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nově vytvořeného vlákna nebo hodnota NULL při selhání. Volání [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) a získat tak rozšířené informace o chybě.

### <a name="remarks"></a>Poznámky

Zobrazit [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) Další informace o parametrech pro tuto funkci.

Tato funkce volá `CreateThread` k vytvoření vlákna.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
