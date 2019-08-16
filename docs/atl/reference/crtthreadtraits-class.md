---
title: CRTThreadTraits – třída
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
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496567"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits – třída

Tato třída poskytuje funkci vytváření pro vlákno CRT. Tuto třídu použijte v případě, že vlákno bude používat funkce CRT.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRTThreadTraits
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRTThreadTraits:: CreateThread](#createthread)|Tras Voláním této funkce vytvoříte vlákno, které může používat funkce CRT.|

## <a name="remarks"></a>Poznámky

Vlastnosti vlákna jsou třídy, které poskytují funkci vytvoření pro konkrétní typ vlákna. Funkce vytváření má stejný podpis a sémantiku jako funkce Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) .

Vlastnosti vlákna jsou používány následujícími třídami:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

Pokud vlákno nebude používat funkce CRT, použijte místo toho [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="createthread"></a>CRTThreadTraits:: CreateThread

Voláním této funkce vytvoříte vlákno, které může používat funkce CRT.

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

Tato funkce volá [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) k vytvoření vlákna.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
