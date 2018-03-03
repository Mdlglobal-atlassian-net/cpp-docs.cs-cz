---
title: "Rozhraní IAxWinAmbientDispatchEx | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3fd212417a00335bfc02699cf5e38eeacc6451ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx rozhraní
Toto rozhraní implementuje dodatečné vedlejším vlastnostem hostované ovládacího prvku.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|Tato metoda je volána doplníte rozhraní – vedlejší vlastnost výchozí uživatelské rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Zahrňte toto rozhraní ATL aplikace, které jsou staticky propojené do knihovny ATL a hostitelských ovládacích prvků ActiveX, zejména ovládací prvky ActiveX, které mají vedlejším vlastnostem. Toto rozhraní není včetně vygeneruje tento kontrolní výraz součásti: "Zapomněli jste ID KNIHOVNY předat CComModule::Init"  
  
 Toto rozhraní je zveřejněný prostřednictvím ovládacího prvku ActiveX knihovny ATL pro hostování objekty. Odvozené z [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md), `IAxWinAmbientDispatchEx` přidá metoda, která umožňuje doplnit rozhraní – vedlejší vlastnost poskytované ATL s vlastním.  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx) se pokusí načíst informace o typu o `IAxWinAmbientDispatch` a `IAxWinAmbientDispatchEx` z knihovny typů, který obsahuje kód.  
  
 Pokud se připojujete k ATL90.dll, **AXHost** načte informace o typu z knihovny typů v knihovně DLL.  
  
 V tématu [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) další podrobnosti.  
  
## <a name="requirements"></a>Požadavky  
 Definice toto rozhraní je k dispozici v různých formách, jak je znázorněno v následující tabulce.  
  
|Definice typu|Soubor|  
|---------------------|----------|  
|IDL|atliface.IDL|  
|Knihovny typů|ATL.|  
|C++|atliface.h (také obsaženy v ATLBase.h)|  
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 Tato metoda je volána doplníte rozhraní – vedlejší vlastnost výchozí uživatelské rozhraní.  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pDispatch*  
 Ukazatel na nové rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Když `SetAmbientDispatch` je volána s ukazatel na nové rozhraní, toto nové rozhraní se použije k vyvolání jakékoli vlastnosti nebo metody žádali hostované ovládacím prvkem, pokud tyto vlastnosti nejsou obsaženy ve [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>Viz také  
 [IAxWinAmbientDispatch – rozhraní](../../atl/reference/iaxwinambientdispatch-interface.md)
