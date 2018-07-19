---
title: Crtthreadtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c182840ed3592a229b8d6c7b98930ade57a18b25
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883018"
---
# <a name="crtthreadtraits-class"></a>Crtthreadtraits – třída
Tato třída poskytuje funkce vytvoření vlákna CRT. Pokud vlákno použije funkce CRT, použijte tuto třídu.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CRTThreadTraits
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](#createthread)|(Statické) Voláním této funkce k vytvoření vlákna, které můžete použít funkce CRT.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti vlákna jsou třídy, které poskytují funkce vytváření pro určitý typ vlákna. Vytvoření funkce má stejný podpis a sémantiku jako Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce.  
  
 Vlastnosti vlákna jsou používány následující třídy:  
  
- [Cthreadpool –](../../atl/reference/cthreadpool-class.md)  
  
- [Cworkerthread –](../../atl/reference/cworkerthread-class.md)  
  
 Pokud vlákno nebude používat funkce CRT, použijte [win32threadtraits –](../../atl/reference/win32threadtraits-class.md) místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="createthread"></a>  CRTThreadTraits::CreateThread  
 Voláním této funkce k vytvoření vlákna, které můžete použít funkce CRT.  
  
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
 Vrátí popisovač do nově vytvořeného vlákna nebo hodnota NULL při selhání. Volání [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) a získat tak rozšířené informace o chybě.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Další informace o parametrech pro tuto funkci.  
  
 Tato funkce volá [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) k vytvoření vlákna.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
