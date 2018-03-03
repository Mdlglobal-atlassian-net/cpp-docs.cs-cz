---
title: "Spojovací bod globální funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce7f6fc3d2a0b51f88952dd720955367b1dfe9d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="connection-point-global-functions"></a>Spojovací bod globální funkce
Tyto funkce poskytuje podporu pro spojovací body a jímky mapy.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.|  
|[AtlUnadvise](#atlunadvise)|Ukončí připojení bylo vytvořeno prostřednictvím `AtlAdvise`.|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|Informuje o tom, nebo unadvises položky v mapě jímky událostí.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 Vytvoří propojení mezi připojovacím bodem objektu a jímkou klienta.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkCP`  
 [v] Ukazatel **IUnknown** objektu se klient pokouší připojit s.  
  
 *pUnk*  
 [v] Ukazatel na klienta **IUnknown**.  
  
 `iid`  
 [v] Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravuje spojovacího bodu.  
  
 `pdw`  
 [out] Ukazatel na souboru cookie, který jednoznačně identifikuje připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Jímky implementuje rozhraní odchozí nepodporuje spojovacího bodu. Klient použije `pdw` soubor cookie k odebrání připojení předáním jeho [AtlUnadvise](#atlunadvise).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 Ukončí připojení bylo vytvořeno prostřednictvím [AtlAdvise](#atladvise).  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkCP`  
 [v] Ukazatel **IUnknown** objektu, který je klient připojen s.  
  
 `iid`  
 [v] Identifikátor GUID spojovacího bodu. Obvykle je to stejné jako odchozí rozhraní spravuje spojovacího bodu.  
  
 `dw`  
 [v] Soubor cookie, který jedinečně identifikuje připojení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 Voláním této funkce vytvoříte nebo zrušíte avízo o všech položkách v mapě událostí jímky objektu.  
  
> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 [v] Ukazatel na objekt obsahující podřízený mapy.  
  
 `bAdvise`  
 [v] **true** všechny položky jímka mají-li být doporučila; **false** všechny položky jímka mají-li být unadvised.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)   
 [Makra bodů připojení](../../atl/reference/connection-point-macros.md)
