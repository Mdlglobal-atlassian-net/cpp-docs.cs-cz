---
title: "Třída IDataObjectImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 644f498a491605fb69b18ec53afee689f5f90a26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idataobjectimpl-class"></a>IDataObjectImpl – třída
Tato třída poskytuje metody pro podporu Uniform přenos dat a správě připojení.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IDataObjectImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|Naváže připojení mezi datový objekt a jímky doporučení. To umožňuje jímky doporučení k přijímání oznámení o změny v objektu.|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|Ukončí připojení dříve vytvořené prostřednictvím `DAdvise`.|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Vytvoří enumerátor k iteraci v rámci aktuální poradní připojení.|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Vytvoří enumerátor k iteraci v rámci **FORMATETC** struktury datový objekt nepodporuje. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|Odešle upozornění na změnu zpět do každé doporučení jímky.|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Načte logicky ekvivalentní **FORMATETC** struktura na takový, který je složitější. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IDataObjectImpl::GetData](#getdata)|Přenáší data z datového objektu do klienta. Data je popsaná v **FORMATETC** struktury a se přenáší prostřednictvím **STGMEDIUM** struktury.|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobně jako `GetData`, s výjimkou přidělíte klienta **STGMEDIUM** struktury. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|Určuje, zda datový objekt podporuje konkrétní **FORMATETC** strukturu pro přenos dat. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IDataObjectImpl::SetData](#setdata)|Datový objekt přenáší data z klienta. Implementace ATL vrátí **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Poznámky  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) rozhraní poskytuje metody pro podporu Uniform přenášet Data. `IDataObject`používá standardní formát struktury [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) a [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) načíst a ukládat data.  
  
 `IDataObject`spravuje taky připojení k poradit jímky pro zpracování oznámení o změnách dat. V pořadí pro klienta k přijímání oznámení o změnách dat z datový objekt musí implementovat klienta [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) rozhraní na objektu s názvem jímky doporučení. Když klient pak zavolá **IDataObject::DAdvise**, připojení mezi datový objekt a jímka doporučení.  
  
 Třída `IDataObjectImpl` poskytuje výchozí implementaci třídy `IDataObject` a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="dadvise"></a>IDataObjectImpl::DAdvise  
 Naváže připojení mezi datový objekt a jímky doporučení.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Poznámky  
 To umožňuje jímky doporučení k přijímání oznámení o změny v objektu.  
  
 Chcete-li ukončit připojení, volejte [DUnadvise](#dunadvise).  
  
 V tématu [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) ve Windows SDK.  
  
##  <a name="dunadvise"></a>IDataObjectImpl::DUnadvise  
 Ukončí připojení dříve vytvořené prostřednictvím [DAdvise](#dadvise).  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) ve Windows SDK.  
  
##  <a name="enumdadvise"></a>IDataObjectImpl::EnumDAdvise  
 Vytvoří enumerátor k iteraci v rámci aktuální poradní připojení.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) ve Windows SDK.  
  
##  <a name="enumformatetc"></a>IDataObjectImpl::EnumFormatEtc  
 Vytvoří enumerátor k iteraci v rámci **FORMATETC** struktury datový objekt nepodporuje.  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
##  <a name="firedatachange"></a>IDataObjectImpl::FireDataChange  
 Odešle upozornění na změnu zpět do každé podřízený doporučení, která je aktuálně spravován.  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="getcanonicalformatetc"></a>IDataObjectImpl::GetCanonicalFormatEtc  
 Načte logicky ekvivalentní **FORMATETC** struktura na takový, který je složitější.  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) ve Windows SDK.  
  
##  <a name="getdata"></a>IDataObjectImpl::GetData  
 Přenáší data z datového objektu do klienta.  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>Poznámky  
 *PformatetcIn* parametr musí určovat střední typ úložiště **TYMED_MFPICT**.  
  
 V tématu [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) ve Windows SDK.  
  
##  <a name="getdatahere"></a>IDataObjectImpl::GetDataHere  
 Podobně jako `GetData`, s výjimkou přidělíte klienta **STGMEDIUM** struktury.  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::GetDataHere](http://msdn.microsoft.com/library/windows/desktop/ms687266) ve Windows SDK.  
  
##  <a name="querygetdata"></a>IDataObjectImpl::QueryGetData  
 Určuje, zda datový objekt podporuje konkrétní **FORMATETC** strukturu pro přenos dat.  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) ve Windows SDK.  
  
##  <a name="setdata"></a>IDataObjectImpl::SetData  
 Datový objekt přenáší data z klienta.  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDataObject::SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
