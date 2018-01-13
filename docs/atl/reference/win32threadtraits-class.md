---
title: "Třída Win32ThreadTraits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf4fd3ffaf2fc4a035fdecf679ab507ebb557f38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits – třída
Tato třída poskytuje funkce vytváření vlákna systému Windows. Tuto třídu používejte, pokud vlákno nebude používat funkce CRT.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class Win32ThreadTraits
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](#createthread)|(Statické) Volání této funkce vytvořit vlákno, který by neměl používat funkce CRT.|  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti vlákna jsou třídy, které poskytují funkce vytváření pro konkrétní typ přístup z více vláken. Vytvoření funkce má stejné podpisu a sémantiku jako Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkce.  
  
 Vlastnosti vlákna používá následující třídy:  
  
- [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
- [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Pokud vlákno budete používat funkce CRT, použijte [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="createthread"></a>Win32ThreadTraits::CreateThread  
 Volání této funkce vytvořit vlákno, který by neměl používat funkce CRT.  
  
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
 `lpsa`  
 Atributy zabezpečení pro nové vlákno.  
  
 `dwStackSize`  
 Velikost zásobníku pro nové vlákno.  
  
 `pfnThreadProc`  
 Vlákno postupu nové vlákno.  
  
 `pvParam`  
 Parametr mají být předány postupu přístup z více vláken.  
  
 `dwCreationFlags`  
 Vytvoření příznaky (0 nebo CREATE_SUSPENDED).  
  
 `pdwThreadId`  
 [out] Adresa DWORD proměnné, která v případě úspěchu přijímá ID vlákna nově vytvořený vlákna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač pro nově vytvořený vlákno nebo hodnotu NULL při selhání. Volání [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) k získání rozšířené informace o chybě.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Další informace o parametry, které chcete tuto funkci.  
  
 Tato funkce volá `CreateThread` vytvořit vlákno.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
