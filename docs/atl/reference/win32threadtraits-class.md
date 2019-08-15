---
title: Win32ThreadTraits – třída
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
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495478"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits – třída

Tato třída poskytuje funkci vytváření pro vlákno systému Windows. Tuto třídu použijte v případě, že vlákno nebude používat funkce CRT.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class Win32ThreadTraits
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[Win32ThreadTraits:: CreateThread](#createthread)|Tras Voláním této funkce vytvoříte vlákno, které by nemělo používat funkce CRT.|

## <a name="remarks"></a>Poznámky

Vlastnosti vlákna jsou třídy, které poskytují funkci vytvoření pro konkrétní typ vlákna. Funkce vytváření má stejný podpis a sémantiku jako funkce Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Vlastnosti vlákna jsou používány následujícími třídami:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Pokud vlákno bude používat funkce CRT, použijte místo toho [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="createthread"></a>Win32ThreadTraits:: CreateThread

Voláním této funkce vytvoříte vlákno, které by nemělo používat funkce CRT.

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
Procedura vlákna nového vlákna.

*pvParam*<br/>
Parametr, který má být předán proceduře vlákna.

*dwCreationFlags*<br/>
Příznaky vytváření (0 nebo CREATE_SUSPENDED).

*pdwThreadId*<br/>
mimo Adresa proměnné DWORD, která po úspěchu obdrží ID vlákna nově vytvořeného vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač nově vytvořeného vlákna nebo hodnotu NULL při selhání. Zavolejte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) a získejte rozšířené informace o chybě.

### <a name="remarks"></a>Poznámky

Další informace o parametrech této funkce naleznete v tématu [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Tato funkce volá `CreateThread` vytvoření vlákna.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
