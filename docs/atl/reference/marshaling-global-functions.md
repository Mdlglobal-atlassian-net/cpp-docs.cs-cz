---
title: "Zařazování globální funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a12f719d2cb893a5d2989a80f5fe09a5b49aeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="marshaling-global-functions"></a>Zařazování globální funkce
Tyto funkce poskytuje podporu pro zařazování a převodu zařazování dat na ukazatele rozhraní.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Uvolní data zařazování a `IStream` ukazatel.|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Vytvoří nový objekt datového proudu a zařazuje ukazatel zadaný rozhraní.|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|Převede datový proud zařazování dat ukazatele rozhraní.|  

## <a name="requirements"></a>Požadavky:
**Záhlaví:** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 Uvolní zařazování dat ve streamu a následně uvolní ukazatel streamu.  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel `IStream` rozhraní na datový proud použitý pro zařazování.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
##  <a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 Vytvoří nový objekt streamu, zapíše do tohoto streamu identifikátor CLSID proxy a zařadí zadaný ukazatel rozhraní tím, že do streamu zapíše data potřebná k inicializaci proxy.  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel rozhraní být zařazena.  
  
 `iid`  
 [v] Identifikátor GUID rozhraní se zařazené.  
  
 `ppStream`  
 [out] Ukazatel `IStream` rozhraní na nový datový proud objekt použitý pro zařazování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 **MSHLFLAGS_TABLESTRONG** je příznak nastaven tak ukazatele může být zařazen do různých datových proudů. Ukazatele může být také zařazeny vícekrát.  
  
 Pokud zařazování selže, je vydala ukazatele datového proudu.  
  
 `AtlMarshalPtrInProc`můžete použít pouze v ukazatel na objekt v procesu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 Převede zařazovaná data streamu na ukazatel rozhraní, který může použít klient.  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel na datový proud se zařazeny.  
  
 `iid`  
 [v] Identifikátor GUID rozhraní se zařazeny.  
  
 `ppUnk`  
 [out] Ukazatel rozhraní zařazeny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
