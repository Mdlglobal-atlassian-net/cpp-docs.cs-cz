---
title: Iobjectsafetyimpl – třída
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: e75c52b016fff5bf04fefc86d4289021efc4db8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293274"
---
# <a name="iobjectsafetyimpl-class"></a>Iobjectsafetyimpl – třída

Tato třída poskytuje výchozí implementaci třídy `IObjectSafety` rozhraní umožňující klientská načíst a nastavit úrovně zabezpečení objektu.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IObjectSafetyImpl`.

*dwSupportedSafety*<br/>
Určuje možnosti podporované zabezpečení pro ovládací prvek. Může být jedna z následujících hodnot:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER rozhraní identifikován [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) parametr `riid` třeba bezpečné pro skriptování.

- INTERFACESAFE_FOR_UNTRUSTED_DATA rozhraní identifikován `SetInterfaceSafetyOptions` parametr `riid` by měl být zabezpečeny pro nedůvěryhodná data během inicializace.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Načte bezpečnostní možnosti podporované v objektu, jakož i možnosti zabezpečení pro objekt aktuálně nastaven.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Vytvoří objekt bezpečné inicializace nebo pomocí skriptů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Uloží aktuální úroveň zabezpečení daného objektu.|

## <a name="remarks"></a>Poznámky

Třída `IObjectSafetyImpl` poskytuje výchozí implementaci třídy `IObjectSafety`. `IObjectSafety` Rozhraní umožňuje klientovi načíst a nastavit úrovně zabezpečení objektu. Například můžete volat webový prohlížeč `IObjectSafety::SetInterfaceSafetyOptions` aby ovládací prvek bezpečný pro inicializaci nebo bezpečné pro skriptování.

Všimněte si, že při použití [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) – makro s kategoriemi komponenty CATID_SafeForScripting a CATID_SafeForInitializing poskytuje alternativní způsob určení, že komponenta je bezpečné.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions

Načte bezpečnostní možnosti podporované v objektu, jakož i možnosti zabezpečení pro objekt aktuálně nastaven.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Poznámky

Implementace vrátí příslušné hodnoty pro každé rozhraní, které podporuje implementaci objektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Libovolný objekt, který podporuje `IObjectSafety` je zodpovědná za své vlastní zabezpečení a libovolný objekt, který deleguje. Programátor musí přijímat do účtu problémy vzniklé spouštěním kódu v kontextu uživatele, skriptování napříč weby a provádí kontrolu vhodný zóny.

Zobrazit [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) ve Windows SDK.

##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety

Uloží aktuální úroveň zabezpečení daného objektu.

```
DWORD m_dwCurrentSafety;
```

##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions

Vytvoří objekt bezpečné inicializace nebo skriptování nastavením [m_dwCurrentSafety](#m_dwcurrentsafety) člena na odpovídající hodnotu.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Poznámky

Implementace vrátí E_NOINTERFACE pro libovolné rozhraní nepodporuje implementace objektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  Libovolný objekt, který podporuje `IObjectSafety` je zodpovědná za své vlastní zabezpečení a libovolný objekt, který deleguje. Programátor musí přijímat do účtu problémy vzniklé spouštěním kódu v kontextu uživatele, skriptování napříč weby a provádí kontrolu vhodný zóny.

Zobrazit [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[IObjectSafety rozhraní](https://msdn.microsoft.com/library/aa768224.aspx)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
