---
title: Třída CAutoRevertImpersonation
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
ms.openlocfilehash: ea119436fd36d0814c05f1b48380028ad3f63f0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748238"
---
# <a name="cautorevertimpersonation-class"></a>Třída CAutoRevertImpersonation

Tato třída vrátí [CAccessToken](../../atl/reference/caccesstoken-class.md) objekty neztístné stavu, když přejde mimo rozsah.

## <a name="syntax"></a>Syntaxe

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertI](#cautorevertimpersonation)|Vytvoří objekt. `CAutoRevertImpersonation`|
|[CAutoRevertImpersonation::~CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation C](#dtor)|Zničí objekt a vrátí zosobnění přístupového tokenu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAutoRevertImpersonation::Připojit](#attach)|Automatizuje opakování reverze přístupového tokenu.|
|[CAutoRevertImpersonation::Detach](#detach)|Zruší automatickou reverzi zosobnění.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Načte aktuální přístupový token přidružený k tomuto objektu.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/win32/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému k systému Windows NT nebo Windows 2000. Tyto přístupové tokeny mohou `CAccessToken` být reprezentovány třídou.

Někdy je nutné zosobnit přístupové tokeny. Tato třída je k dispozici jako pohodlí, ale neprovádí zosobnění přístupových tokenů; provede pouze automatickou reverzi do neztálého stavu. Důvodem je, že zosobnění přístupu tokenu lze provést několika různými způsoby.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>CAutoRevertImpersonation::Připojit

Automatizuje opakování reverze přístupového tokenu.

```cpp
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*Pat*<br/>
Adresa objektu [CAccessToken,](../../atl/reference/caccesstoken-class.md) který má být automaticky vrácen

### <a name="remarks"></a>Poznámky

Tato metoda by měla být použita pouze v případě, že `CAccessToken` [cautorevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objekt byl vytvořen s ukazatelem NULL, nebo pokud [Odřad](#detach) byl volán dříve. Pro jednoduché případy není nutné používat tuto metodu.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertI

Vytvoří `CAutoRevertImpersonation` objekt.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*Pat*<br/>
Adresa [caccesstoken](../../atl/reference/caccesstoken-class.md) objektu, který má být automaticky vrácen.

### <a name="remarks"></a>Poznámky

Skutečné zosobnění přístupového tokenu by mělo být provedeno odděleně `CAutoRevertImpersonation` od a pokud možno před vytvořením objektu. Toto zosobnění bude vrácena `CAutoRevertImpersonation` automaticky, když objekt přejde mimo rozsah.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>CAutoRevertImpersonation::~CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation CAutoRevertImpersonation C

Zničí objekt a vrátí zosobnění přístupového tokenu.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí všechny zosobnění aktuálně platné pro [CAccessToken](../../atl/reference/caccesstoken-class.md) objektu poskytované buď na konstrukci nebo prostřednictvím [Attach](#attach) metoda. Pokud `CAccessToken` není přidružena, destruktor nemá žádný vliv.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>CAutoRevertImpersonation::Detach

Zruší automatickou reverzi zosobnění.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidruženého [tokenu CAccessToken](../../atl/reference/caccesstoken-class.md)nebo NULL, pokud neexistovalo žádné přidružení.

### <a name="remarks"></a>Poznámky

Volání **oddělovací** zabrání `CAutoRevertImpersonation` objektu vrátit jakékoli zosobnění aktuálně platné pro [caccesstoken](../../atl/reference/caccesstoken-class.md) objekt u tohoto objektu. `CAutoRevertImpersonation`pak může být zničen bez účinku nebo reassociated ke stejnému nebo jinému `CAccessToken` objektu pomocí [Attach](#attach).

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Načte aktuální přístupový token přidružený k tomuto objektu.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Návratová hodnota

Adresa dříve přidruženého [tokenu CAccessToken](../../atl/reference/caccesstoken-class.md)nebo NULL, pokud neexistovalo žádné přidružení.

### <a name="remarks"></a>Poznámky

Pokud tato metoda je volána pro účely, které zahrnují `CAccessToken` reversion zosobnění objektu, [detach](#detach) metoda by měla být použita místo.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení ATL](../../overview/visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/win32/SecAuthZ/access-tokens)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
