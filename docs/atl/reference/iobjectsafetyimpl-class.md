---
title: Třída IObjectSafetyImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 592a23286ad6592bc0ce6faab999cb362aac42f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl – třída
Tato třída poskytuje výchozí implementaci třídy `IObjectSafety` rozhraní a tak dovolit klientským k načtení a nastavení úrovně zabezpečení objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T,DWORD dwSupportedSafety>  
class IObjectSafetyImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IObjectSafetyImpl`.  
  
 *dwSupportedSafety*  
 Určuje podporovaná bezpečnostní možnosti pro ovládací prvek. Může být jedna z následujících hodnot:  
  
- **INTERFACESAFE_FOR_UNTRUSTED_CALLER** rozhraní identifikovaný [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parametr `riid` by měl být provedeny bezpečné pro skriptování.  
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA** rozhraní identifikovaný `SetInterfaceSafetyOptions` parametr `riid` by měl být provedené bezpečné pro přístup z nedůvěryhodných dat během inicializace.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Načte bezpečnostní možnosti podporované objektem, jakož i možnosti zabezpečení aktuálně nastavit pro objekt.|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Vytvoří objekt bezpečné pro přístup z inicializace nebo skriptování.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Uloží aktuální úroveň zabezpečení objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Třída `IObjectSafetyImpl` poskytuje výchozí implementaci třídy `IObjectSafety`. `IObjectSafety` Rozhraní umožňuje klientům k načtení a nastavení úrovně zabezpečení objektu. Například můžete volat webový prohlížeč **IObjectSafety::SetInterfaceSafetyOptions** k vytvoření ovládacího prvku inicializaci nebo bezpečné pro skriptování.  
  
 Všimněte si, že pomocí [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) makro s **CATID_SafeForScripting** a **CATID_SafeForInitializing** součást kategorie představuje alternativní způsob určení, že součást je bezpečné.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions  
 Načte bezpečnostní možnosti podporované objektem, jakož i možnosti zabezpečení aktuálně nastavit pro objekt.  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace vrátí odpovídající hodnoty pro všechny rozhraní nepodporuje implementace objektu **IUnknown::QueryInterface**.  
  
> [!IMPORTANT]
>  Libovolný objekt, který podporuje `IObjectSafety` zodpovídá za vlastní zabezpečení a u všech objektů, dojde k delegaci. Programátorů musí vzít v účtu problémy vyplývající z spuštění kódu v uživatelském kontextu, skriptování mezi a provádí kontrolu vhodný zóny.  
  
 V tématu [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) ve Windows SDK.  
  
##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety  
 Uloží aktuální úroveň zabezpečení objektu.  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions  
 Umožňuje bezpečné pro přístup z inicializace nebo skriptování nastavení objektu [m_dwCurrentSafety](#m_dwcurrentsafety) člena na odpovídající hodnotu.  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace vrátí **E_NOINTERFACE** pro všechny rozhraní nepodporuje implementace objektu **IUnknown::QueryInterface**.  
  
> [!IMPORTANT]
>  Libovolný objekt, který podporuje `IObjectSafety` zodpovídá za vlastní zabezpečení a u všech objektů, dojde k delegaci. Programátorů musí vzít v účtu problémy vyplývající z spuštění kódu v uživatelském kontextu, skriptování mezi a provádí kontrolu vhodný zóny.  
  
 V tématu [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IObjectSafety rozhraní](https://msdn.microsoft.com/library/aa768224.aspx)   
 [Přehled třídy](../../atl/atl-class-overview.md)
