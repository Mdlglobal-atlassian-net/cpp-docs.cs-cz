---
title: "Rozhraní IThreadPoolConfig | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d967720778305eace4eff9ad8b2163456fb4bb46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig rozhraní
Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Getsize –](#getsize)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|  
|[GetTimeout](#gettimeout)|Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.|  
|[SetSize](#setsize)|Volejte tuto metodu a nastavit počet vláken ve fondu.|  
|[SetTimeout](#settimeout)|Volejte tuto metodu a nastavit maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je implementováno modulem [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="getsize"></a>IThreadPoolConfig::GetSize  
 Volejte tuto metodu za účelem získání počet vláken ve fondu.  
  
```
STDMETHOD(GetSize)(int* pnNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `pnNumThreads`  
 [out] Adresa proměnné, která v případě úspěchu obdrží počet vláken ve fondu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]  
  
##  <a name="gettimeout"></a>IThreadPoolConfig::GetTimeout  
 Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 `pdwMaxWait`  
 [out] Adresa proměnné, která v případě úspěchu obdrží maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="example"></a>Příklad  
 V tématu [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="setsize"></a>IThreadPoolConfig::SetSize  
 Volejte tuto metodu a nastavit počet vláken ve fondu.  
  
```
STDMETHOD(SetSize)int nNumThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `nNumThreads`  
 Požadovaný počet vláken ve fondu.  
  
 Pokud `nNumThreads` je záporná, jeho absolutní hodnota vynásobeny počet procesorů v počítači získat celkový počet vláken.  
  
 Pokud `nNumThreads` rovná nule, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) vynásobeny počet procesorů v počítači získat celkový počet vláken.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="example"></a>Příklad  
 V tématu [IThreadPoolConfig::GetSize](#getsize).  
  
##  <a name="settimeout"></a>IThreadPoolConfig::SetTimeout  
 Volejte tuto metodu a nastavit maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```  
  
### <a name="parameters"></a>Parametry  
 `dwMaxWait`  
 Požadovaný maximální dobu v milisekundách, fondu vláken způsobí čekání vlákno a ukončí se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="example"></a>Příklad  
 V tématu [IThreadPoolConfig::GetSize](#getsize).  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../atl/reference/atl-classes.md)   
 [CThreadPool – třída](../../atl/reference/cthreadpool-class.md)
