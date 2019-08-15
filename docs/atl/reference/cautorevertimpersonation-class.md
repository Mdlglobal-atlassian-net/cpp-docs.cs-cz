---
title: CAutoRevertImpersonation – třída
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
ms.openlocfilehash: f1941bfcd7689ab9d22f5094af0eb833a84dab6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497687"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation – třída

Tato třída vrátí objekty [CAccessToken](../../atl/reference/caccesstoken-class.md) do nezosobněného stavu, pokud se překročí rozsahu.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|`CAutoRevertImpersonation` Vytvoří objekt.|
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](#dtor)|Odstraní objekt a vrátí zosobnění přístupového tokenu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation:: Attach](#attach)|Automatizuje znovu naverzi přístupového tokenu.|
|[CAutoRevertImpersonation::Detach](#detach)|Zruší automatickou reverzi zosobnění.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Načte přístupový token, který je aktuální přidružený k tomuto objektu.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/win32/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému do systému Windows NT nebo Windows 2000. Tyto přístupové tokeny mohou být reprezentovány `CAccessToken` třídou.

Někdy je potřeba zosobnit přístupové tokeny. Tato třída je poskytována jako pohodlí, ale neprovádí zosobnění přístupových tokenů; provádí pouze automatickou novou verzi do nezosobněného stavu. Důvodem je to, že k zosobnění přístupu tokenu se dá použít několik různých způsobů.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="attach"></a>CAutoRevertImpersonation:: Attach

Automatizuje znovu naverzi přístupového tokenu.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*pAT*<br/>
Adresa objektu [CAccessToken](../../atl/reference/caccesstoken-class.md) , který má být vrácen automaticky

### <a name="remarks"></a>Poznámky

Tato metoda by měla být použita pouze v případě, že byl objekt [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) vytvořen `CAccessToken` s ukazatelem s hodnotou null, nebo pokud byl dříve volán příkaz [detach](#detach) . Pro jednoduché případy není nutné používat tuto metodu.

##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

`CAutoRevertImpersonation` Vytvoří objekt.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*pAT*<br/>
Adresa objektu [CAccessToken](../../atl/reference/caccesstoken-class.md) , který má být vrácen automaticky

### <a name="remarks"></a>Poznámky

Vlastní zosobnění přístupového tokenu by mělo být prováděno odděleně od a přednost před vytvořením `CAutoRevertImpersonation` objektu. Tato zosobnění se automaticky vrátí, když se `CAutoRevertImpersonation` objekt stane mimo rozsah.

##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

Odstraní objekt a vrátí zosobnění přístupového tokenu.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí jakékoli zosobnění v současné době pro objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) , který je k dispozici v rámci konstrukce nebo prostřednictvím metody [Attach](#attach) . Pokud není `CAccessToken` k dispozici žádný, destruktor nemá žádný vliv.

##  <a name="detach"></a>CAutoRevertImpersonation::D etach

Zruší automatickou reverzi zosobnění.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidruženého CAccessTokenu [](../../atl/reference/caccesstoken-class.md)nebo hodnota null, pokud žádné přidružení neexistuje.

### <a name="remarks"></a>Poznámky

Volání **detach** zabraňuje `CAutoRevertImpersonation` objektu v současné době vracet jakékoli zosobnění, které je aktuálně platné pro objekt [CAccessToken](../../atl/reference/caccesstoken-class.md) přidružený k tomuto objektu. `CAutoRevertImpersonation`může být zničena bez účinku nebo znovu přidružena ke stejnému nebo `CAccessToken` jinému objektu pomocí [připojení](#attach).

##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Načte přístupový token, který je aktuální přidružený k tomuto objektu.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidruženého CAccessTokenu [](../../atl/reference/caccesstoken-class.md)nebo hodnota null, pokud žádné přidružení neexistuje.

### <a name="remarks"></a>Poznámky

Pokud je tato metoda volána pro účely, které zahrnují reverzi zosobnění `CAccessToken` objektu, je třeba použít metodu [detach](#detach) .

## <a name="see-also"></a>Viz také:

[Ukázka ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/win32/SecAuthZ/access-tokens)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
