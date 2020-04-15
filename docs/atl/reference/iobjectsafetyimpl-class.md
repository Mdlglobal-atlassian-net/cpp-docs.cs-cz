---
title: Třída IObjectSafetyImpl
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
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329654"
---
# <a name="iobjectsafetyimpl-class"></a>Třída IObjectSafetyImpl

Tato třída poskytuje výchozí `IObjectSafety` implementaci rozhraní, která umožňuje klientovi načíst a nastavit úrovně bezpečnosti objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IObjectSafetyImpl`.

*dwSupportedSafety*<br/>
Určuje podporované možnosti zabezpečení ovládacího prvku. Může se na nich vyvěšovat jedna z následujících hodnot:

- INTERFACESAFE_FOR_UNTRUSTED_CALLER Rozhraní identifikované parametrem `riid` [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) by mělo být bezpečné pro skriptování.

- INTERFACESAFE_FOR_UNTRUSTED_DATA Rozhraní identifikované `SetInterfaceSafetyOptions` `riid` parametrem by mělo být bezpečné pro nedůvěryhodná data během inicializace.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Načte možnosti zabezpečení podporované objektem a také možnosti zabezpečení, které jsou aktuálně nastaveny pro objekt.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Umožňuje objekt bezpečné pro inicializaci nebo skriptování.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Ukládá aktuální úroveň bezpečnosti objektu.|

## <a name="remarks"></a>Poznámky

Třída `IObjectSafetyImpl` poskytuje výchozí `IObjectSafety`implementaci aplikace . Rozhraní `IObjectSafety` umožňuje klientovi načíst a nastavit úrovně bezpečnosti objektu. Webový prohlížeč může například `IObjectSafety::SetInterfaceSafetyOptions` volat, aby byl ovládací prvek bezpečný pro inicializaci nebo bezpečný pro skriptování.

Všimněte si, že použití [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) makra s kategoriemi CATID_SafeForScripting a CATID_SafeForInitializing součástí poskytuje alternativní způsob určení, že součást je bezpečná.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>iObjectSafetyImpl::GetInterfaceSafetyOptions

Načte možnosti zabezpečení podporované objektem a také možnosti zabezpečení, které jsou aktuálně nastaveny pro objekt.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Poznámky

Implementace vrátí příslušné hodnoty pro všechny rozhraní podporované implementací objektu `IUnknown::QueryInterface`.

> [!IMPORTANT]
> Každý objekt, `IObjectSafety` který podporuje je zodpovědný za své vlastní zabezpečení a že libovolný objekt, který deleguje. Programátor musí vzít v úvahu problémy vyplývající ze spuštění kódu v kontextu uživatele, skriptování mezi weby a provádění vhodné kontroly zóny.

Viz [IObjectSafety::GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) v sadě Windows SDK.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety

Ukládá aktuální úroveň bezpečnosti objektu.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions

Změní objekt na inicializaci nebo skriptování nastavením [m_dwCurrentSafety](#m_dwcurrentsafety) člena na příslušnou hodnotu.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Poznámky

Implementace vrátí E_NOINTERFACE pro jakékoli rozhraní, které není `IUnknown::QueryInterface`podporováno implementací objektu .

> [!IMPORTANT]
> Každý objekt, `IObjectSafety` který podporuje je zodpovědný za své vlastní zabezpečení a že libovolný objekt, který deleguje. Programátor musí vzít v úvahu problémy vyplývající ze spuštění kódu v kontextu uživatele, skriptování mezi weby a provádění vhodné kontroly zóny.

Viz [IObjectSafety::SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[IObjectSafety Interface](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
