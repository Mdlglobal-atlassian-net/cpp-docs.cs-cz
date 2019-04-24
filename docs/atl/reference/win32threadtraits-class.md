---
title: Win32threadtraits – třída
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: da4b8b3d5a41ab16dc2027fd632c56158afd3b97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275935"
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

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

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

*lpsa*<br/>
Atributy zabezpečení pro nové vlákno.

*dwStackSize*<br/>
Velikost zásobníku pro nové vlákno.

*pfnThreadProc*<br/>
Procedura vlákna nové vlákno.

*pvParam*<br/>
Parametr, který má být předán procedura vlákna.

*dwCreationFlags*<br/>
Vytváření příznaky (0 nebo CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adresa proměnné DWORD, který v případě úspěchu, přijímá ID vlákna nově vytvořeného vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do nově vytvořeného vlákna nebo hodnota NULL při selhání. Volání [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) a získat tak rozšířené informace o chybě.

### <a name="remarks"></a>Poznámky

Zobrazit [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) Další informace o parametrech pro tuto funkci.

Tato funkce volá `CreateThread` k vytvoření vlákna.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
