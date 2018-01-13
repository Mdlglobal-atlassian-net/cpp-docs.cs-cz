---
title: "Rozhraní IAxWinHostWindowLic | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs: C++
helpviewer_keywords: IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61bd50d5602812cc70ccc3201e9df255f469604a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic rozhraní
Toto rozhraní poskytuje metody pro manipulaci s licencované ovládací prvek a jeho objekt hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|Vytvoří licencované ovládací prvek a připojí jej k objektu hostitele.|  
|[CreateControlLicEx](#createcontrollicex)|Vytvoří licencované ovládací prvek, připojí k objektu hostitele a volitelně nastaví obslužnou rutinu události.|  
  
## <a name="remarks"></a>Poznámky  
 `IAxWinHostWindowLic`dědí z [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) a přidá metody, které podporují vytváření licencované ovládací prvky.  
  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá členů tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní je k dispozici jako IDL nebo C++, jak je uvedeno níže.  
  
|Definice typu|Soubor|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (také obsaženy v ATLBase.h)|  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 Vytvoří licencované ovládací prvek, inicializuje ji a hostuje v okně identifikovaný `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [v] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) popis zbývající parametry a návratové hodnoty.  
  
 Voláním této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 Vytvoří licencované ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrLic`  
 [v] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) popis zbývající parametry a návratové hodnoty.  
  
### <a name="example"></a>Příklad  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) příklad, který používá `IAxWinHostWindowLic::CreateControlLicEx`.









