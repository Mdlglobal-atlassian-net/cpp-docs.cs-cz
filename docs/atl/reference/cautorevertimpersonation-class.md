---
title: Cautorevertimpersonation – třída
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 78488fba080e397b06eb67ebe8039fb3e8d5e035
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779375"
---
# <a name="cautorevertimpersonation-class"></a>Cautorevertimpersonation – třída

Tato třída se vrátí [caccesstoken –](../../atl/reference/caccesstoken-class.md) objekty do nonimpersonating stavu, když dostane mimo rozsah.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Vytvoří `CAutoRevertImpersonation` objektu|
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](#dtor)|Odstraní objekt a vrátí token zosobnění přístup.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|Automatizuje k zosobnění obnovení tokenu přístupu.|
|[CAutoRevertImpersonation::Detach](#detach)|Zruší k obnovení automatické zosobnění.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Načte aktuální token přístupu asociovaném s tímto objektem.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje proces nebo vlákno kontextu zabezpečení a přidělené každému uživateli přihlášení systému Windows NT nebo Windows 2000. Tyto tokeny přístupu lze znázornit pomocí `CAccessToken` třídy.

Někdy je nezbytné k zosobnění přístupové tokeny. Tato třída je k dispozici pro zjednodušení, ale neprovádí zosobnění přístupové tokeny; provádí pouze k automatické obnovení do nonimpersonated stavu. Je to proto, že přístup pomocí tokenu zosobnění lze provést několika různými způsoby.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="attach"></a>  CAutoRevertImpersonation::Attach

Automatizuje k zosobnění obnovení tokenu přístupu.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*pAT*<br/>
Adresa [caccesstoken –](../../atl/reference/caccesstoken-class.md) objektu se mají zrušit změny automaticky

### <a name="remarks"></a>Poznámky

Tato metoda by měla použít pouze v případě [cautorevertimpersonation –](../../atl/reference/cautorevertimpersonation-class.md) s hodnotou NULL byl vytvořen objekt `CAccessToken` ukazatele, nebo pokud [odpojit](#detach) dříve byla volána. Pro jednoduché případy není nutné použít tuto metodu.

##  <a name="cautorevertimpersonation"></a>  CAutoRevertImpersonation::CAutoRevertImpersonation

Vytvoří `CAutoRevertImpersonation` objektu.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*pAT*<br/>
Adresa [caccesstoken –](../../atl/reference/caccesstoken-class.md) objektu se automaticky vrátí zpátky.

### <a name="remarks"></a>Poznámky

Skutečné zosobnění přístupového tokenu by měl provést samostatně z a pokud možno před vytvořením `CAutoRevertImpersonation` objektu. Tato zosobnění se vrátí zpět automaticky při `CAutoRevertImpersonation` objekt dostane mimo rozsah.

##  <a name="dtor"></a>  Cautorevertimpersonation –:: ~ cautorevertimpersonation –

Odstraní objekt a vrátí token zosobnění přístup.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí všechny zosobnění aktuálně v platnosti [caccesstoken –](../../atl/reference/caccesstoken-class.md) objekt Poskytnutý při konstrukci nebo prostřednictvím [připojit](#attach) metoda. Pokud ne `CAccessToken` je spojené, destruktor nemá žádný vliv.

##  <a name="detach"></a>  CAutoRevertImpersonation::Detach

Zruší k obnovení automatické zosobnění.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidružené [caccesstoken –](../../atl/reference/caccesstoken-class.md), nebo hodnota NULL, pokud žádné přidružení.

### <a name="remarks"></a>Poznámky

Volání **odpojit** brání `CAutoRevertImpersonation` objekt z jakékoli zosobnění aktuálně používána pro návrat [caccesstoken –](../../atl/reference/caccesstoken-class.md) objekt přidružený k tomuto objektu. `CAutoRevertImpersonation` Můžete pak zničit pomocí žádný účinek nebo naimportován do stejného nebo jiného `CAccessToken` pomocí [připojit](#attach).

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

Načte aktuální token přístupu asociovaném s tímto objektem.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidružené [caccesstoken –](../../atl/reference/caccesstoken-class.md), nebo hodnota NULL, pokud žádné přidružení.

### <a name="remarks"></a>Poznámky

Pokud tato metoda je volána pro účely, které patří k obnovení zosobnění `CAccessToken` objektu, [odpojit](#detach) metoda by místo toho používá.

## <a name="see-also"></a>Viz také:

[Ukázka ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
