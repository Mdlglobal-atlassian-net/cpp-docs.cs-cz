---
title: Iaxwinhostwindowlic – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d2d97aa0de61697e31c424c8185c71b06c7dd0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885574"
---
# <a name="iaxwinhostwindowlic-interface"></a>Iaxwinhostwindowlic – rozhraní
Toto rozhraní poskytuje metody pro manipulaci s licencovaného ovládacího prvku a jeho objekt hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|Vytvoří licencovaného ovládacího prvku a připojí ho k objektu hostitele.|  
|[CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaného ovládacího prvku a připojí ho k objektu hostitele volitelně nastaví obslužnou rutinu události.|  
  
## <a name="remarks"></a>Poznámky  
 `IAxWinHostWindowLic` dědí z [iaxwinhostwindow –](../../atl/reference/iaxwinhostwindow-interface.md) a přidá metody, které podporují vytváření licencované ovládací prvky.  
  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá členy tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní není k dispozici jako IDL nebo C++, jak je znázorněno níže.  
  
|Typ definice|Soubor|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (také součástí ATLBase.h)|  
  
##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic  
 Vytvoří licencovaného ovládacího prvku, inicializuje ji a hostuje ji v okně identifikovaný `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Parametry  
 *bstrLic*  
 [in] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) popis zbývající parametry a návratové hodnoty.  
  
 Voláním této metody je ekvivalentní volání [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx  
 Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
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
 *bstrLic*  
 [in] BSTR, který obsahuje licenční klíč pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) popis zbývající parametry a návratové hodnoty.  
  
### <a name="example"></a>Příklad  
 Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `IAxWinHostWindowLic::CreateControlLicEx`.









