---
title: Třída CRTThreadTraits
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: a7cfddc64e8c1b4e192e718d05812e385fbe08ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331019"
---
# <a name="crtthreadtraits-class"></a>Třída CRTThreadTraits

Tato třída poskytuje funkci vytvoření pro vlákno CRT. Tuto třídu použijte, pokud vlákno bude používat funkce CRT.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRTThreadTraits
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|(Statické) Volání této funkce k vytvoření vlákna, které můžete použít funkce CRT.|

## <a name="remarks"></a>Poznámky

Vlastnosti vlákna jsou třídy, které poskytují funkci vytvoření pro určitý typ vlákna. Funkce vytváření má stejný podpis a sémantiku jako funkce Windows [CreateThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

Vlastnosti závitu používají následující třídy:

- [Fond cthreadpoolu](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Pokud vlákno nebude používat funkce CRT, použijte místo toho [Win32ThreadTraits.](../../atl/reference/win32threadtraits-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadTraits::CreateThread

Volání této funkce k vytvoření vlákna, které můžete použít funkce CRT.

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

Tato funkce volá [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) k vytvoření vlákna.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
