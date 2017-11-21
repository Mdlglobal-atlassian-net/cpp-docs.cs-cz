---
title: "Třída CAtlComModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs: C++
helpviewer_keywords: CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8a0d0e240e1c830763b5b7781fb3a1e536d4672
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catlcommodule-class"></a>CAtlComModule – třída
Tato třída implementuje modul COM serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|Volejte tuto metodu za účelem aktualizace registru systému pro každý objekt v mapování objektu.|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Voláním této metody lze zaregistrovat knihovnu typů.|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|Volejte tuto metodu zrušení registrace každý objekt v mapování objektu.|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Volejte tuto metodu za účelem zrušit registraci knihovny typů.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlComModule`implementuje modul server COM, umožňuje klientům přístup k součástem modulu.  
  
 Nahradí tato třída zastaralá [CComModule](../../atl/reference/ccommodule-class.md) třída používaná v dřívějších verzích ATL. V tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule  
 Konstruktor  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje modul.  
  
##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule  
 Destruktor.  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny objekty pro vytváření tříd.  
  
##  <a name="registerserver"></a>CAtlComModule::RegisterServer  
 Volejte tuto metodu za účelem aktualizace registru systému pro každý objekt v mapování objektu.  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 TRUE, pokud je typ knihovna k registraci. Výchozí hodnota je FALSE.  
  
 `pCLSID`  
 Body CLSID objekt, který má být zaregistrován. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapování objektu bude zaregistrována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volá funkci globální [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).  
  
##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib  
 Voláním této metody lze zaregistrovat knihovnu typů.  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 Řetězec ve formátu "\\\N", kde N je celé číslo indexu TYPELIB prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Informace o typu knihovny se přidá do registru systému. Pokud instance modulu obsahuje více knihovny typů, použijte k určení, které knihovny typů by měl používat první verzi této metody.  
  
##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 Volejte tuto metodu zrušení registrace každý objekt v mapování objektu.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 Hodnota TRUE, pokud se zrušit registraci knihovny typů. Výchozí hodnota je FALSE.  
  
 `pCLSID`  
 Body CLSID objekt, který má neregistrované. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapování objektu bude zrušena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volá funkci globální [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).  
  
##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib  
 Volejte tuto metodu za účelem zrušit registraci knihovny typů.  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 Řetězec ve formátu "\\\N", kde N je celé číslo indexu TYPELIB prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Informace o typu knihovny se odebere z registru systému. Pokud instance modulu obsahuje více knihovny typů, použijte k určení, které knihovny typů by měl používat první verzi této metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
## <a name="see-also"></a>Viz také  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [Přehled třídy](../../atl/atl-class-overview.md)
