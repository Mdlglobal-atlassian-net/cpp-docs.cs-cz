---
title: Třída ISupportErrorInfoImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e226f66d6ddd20181f083f723568acb1cc647c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364578"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl – třída
Tato třída poskytuje výchozí implementaci třídy [ISupportErrorInfo rozhraní](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) a je možné použít při pouze jedno rozhraní generuje chyby na objekt.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<const IID* piid>  
class ATL_NO_VTABLE ISupportErrorInfoImpl 
   : public ISupportErrorInfo
```  
  
#### <a name="parameters"></a>Parametry  
 `piid`  
 Ukazatel na identifikátory IID rozhraní, které podporuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447).  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 [ISupportErrorInfo rozhraní](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32) zajistí, že informace o chybě můžete vrácen do klienta. Objekty, které používají **IErrorInfo** musí implementovat **ISupportErrorInfo**.  
  
 Třída `ISupportErrorInfoImpl` poskytuje výchozí implementaci třídy **ISupportErrorInfo** a je možné použít při pouze jedno rozhraní generuje chyby na objekt. Příklad:  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo  
 Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) rozhraní.  
  
```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [ISupportErrorInfo::InterfaceSupportsErrorInfo](http://msdn.microsoft.com/en-us/a54ef18d-ee3f-4483-ac4a-99d758f0960a) ve Windows SDK.  
  
##  <a name="getsize"></a>  IThreadPoolConfig::GetSize  
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
 [!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]  
  
##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout  
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
  
##  <a name="setsize"></a>  IThreadPoolConfig::SetSize  
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
  
##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout  
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
 [Přehled třídy](../../atl/atl-class-overview.md)
