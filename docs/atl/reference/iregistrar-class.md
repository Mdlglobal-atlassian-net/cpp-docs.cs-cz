---
title: Rozhraní IRegistrar | Microsoft Docs
ms.custom: ''
ms.date: 2/1/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
dev_langs:
- C++
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89d1e9269536ee28f2c8dd29819ff594c89c186b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="iregistrar-interface"></a>IRegistrar rozhraní
Toto rozhraní je definována v atliface.h a používá se interně pomocí CAtlModule členské funkce, jako [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).   
  
## <a name="syntax"></a>Syntaxe  
  
```
typedef interface IRegistrar IRegistrar;
```  
## <a name="remarks"></a>Poznámky
Podívejte se na téma [pomocí nahraditelné parametry (registrátora Preprocessor)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) další podrobnosti.  

## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Zaregistruje prostředku. |  
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Zruší registraci prostředku.|  
|[IRegistrar::FileRegister](#fileregister)|Zaregistruje soubor.|  
|[IRegistrar::FileUnregister](#fileunregister)|Zruší registraci soubor.|  
|[IRegistrar::StringRegister](#stringregister)|Zaregistruje řetězec.|  
|[IRegistrar::StringUnregister](#stringunregister)|Zruší registraci řetězec|  
|[IRegistrar::ResourceRegister](#resourceregister)|Zaregistruje prostředku.|  
|[IRegistrar::ResourceUnregister](#resourceunregister)|Zruší registraci prostředku.| 
  

 
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlifase.h  
  
##  <a name="resourceregistersz"></a>  IRegistrar::ResourceRegisterSz 
 Zaregistruje prostředku.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
 
  
##  <a name="resourceunregistersz"></a>  IRegistrar::ResourceUnregisterSz  
 Zruší registraci prostředku.
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
  
##  <a name="fileregister"></a>  IRegistrar::FileRegister  
Zaregistruje soubor.
  
```
virtual HRESULT STDMETHODCALLTYPE FileRegister( 
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
  
##  <a name="fileunregister"></a>  IRegistrar::FileUnregister  
Zruší registraci soubor.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister( 
    */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
 
##  <a name="stringregister"></a>  IRegistrar::StringRegister  
  Zaregistruje zadaný řetězec data.
```
virtual HRESULT STDMETHODCALLTYPE StringRegister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  
  
##  <a name="stringunregister"></a>  IRegistrar::StringUnregister
 Zruší registraci data zadaný řetězec.  
  
```
virtualHRESULT STDMETHODCALLTYPE StringUnregister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  

  
##  <a name="resourceregister"></a>  IRegistrar::ResourceRegister  
 Zaregistruje prostředku.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
   
  
##  <a name="resourceunregister"></a>  IRegistrar::ResourceUnregister  
 Zruší registraci prostředku.  
  
```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0; 
```  
 
## <a name="see-also"></a>Viz také  
 [Použití nahraditelných parametrů (preprocesor registrátoru)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)   
 [Komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md)  
