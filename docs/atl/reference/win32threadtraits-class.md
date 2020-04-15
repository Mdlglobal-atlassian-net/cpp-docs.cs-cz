---
title: Třída Win32ThreadTraits
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
ms.openlocfilehash: 64f02293508894a70f36c29d5032c9ba8f250c38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325797"
---
# <a name="win32threadtraits-class"></a>Třída Win32ThreadTraits

Tato třída poskytuje funkci vytváření pro podproces systému Windows. Tuto třídu použijte, pokud vlákno nebude používat funkce CRT.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class Win32ThreadTraits
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|(Statické) Volání této funkce k vytvoření podprocesu, který by neměl používat funkce CRT.|

## <a name="remarks"></a>Poznámky

Vlastnosti vlákna jsou třídy, které poskytují funkci vytvoření pro určitý typ vlákna. Funkce vytváření má stejný podpis a sémantiku jako funkce Windows [CreateThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Vlastnosti závitu používají následující třídy:

- [Fond cthreadpoolu](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Pokud vlákno bude používat funkce CRT, použijte místo toho [CRTThreadTraits.](../../atl/reference/crtthreadtraits-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="win32threadtraitscreatethread"></a><a name="createthread"></a>Win32ThreadTraits::CreateThread

Volání této funkce k vytvoření podprocesu, který by neměl používat funkce CRT.

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

*LPSA*<br/>
Atributy zabezpečení pro nové vlákno.

*dwStackVelikost*<br/>
Velikost zásobníku pro nové vlákno.

*pfnThreadProc*<br/>
Procedura podprocesu nového vlákna.

*pvParam*<br/>
Parametr, který má být předán postupu podprocesu.

*dwCreationFlags*<br/>
Příznaky vytvoření (0 nebo CREATE_SUSPENDED).

*pdwThreadId*<br/>
[out] Adresa proměnné DWORD, která při úspěchu obdrží ID vlákna nově vytvořeného vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač nově vytvořenévlákno nebo NULL při selhání. Volání [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) získat rozšířené informace o chybě.

### <a name="remarks"></a>Poznámky

Další informace o parametrech této funkce naleznete v tématu [CreateThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Tato funkce `CreateThread` volá k vytvoření vlákna.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
