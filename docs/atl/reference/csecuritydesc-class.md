---
title: Třída CSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330967"
---
# <a name="csecuritydesc-class"></a>Třída CSecurityDesc

Tato třída je obálka `SECURITY_DESCRIPTOR` pro strukturu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor|
|[CSecurityDesc::~CSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Převede popisovač zabezpečení ve formátu řetězce na platný funkční popisovač zabezpečení.|
|[CSecurityDesc::Ovládací prvek GetControl](#getcontrol)|Načte informace o ovládacím prvku z popisovače zabezpečení.|
|[CSecurityDesc::GetDacl](#getdacl)|Načte informace o volitelném seznamu řízení přístupu (DACL) z popisovače zabezpečení.|
|[CSecurityDesc::GetGroup](#getgroup)|Načte informace o primární skupině z popisovače zabezpečení.|
|[CSecurityDesc::GetOwner](#getowner)|Načte vlastníka informaton z popisovače zabezpečení.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.|
|[CSecurityDesc::GetSacl](#getsacl)|Načte informace seznamu řízení přístupu systému (SACL) z popisovače zabezpečení.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Určuje, zda je seznam DACL nakonfigurován tak, aby podporoval automatické šíření.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Určuje, zda je popisovač zabezpečení nakonfigurován s výchozí seznamem DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Určuje, zda je seznam DACL nakonfigurován tak, aby zabránil změnám.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Určuje, zda byl identifikátor zabezpečení popisu zabezpečení (SID) nastaven ve výchozím nastavení.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Určuje, zda byl ve výchozím nastavení nastaven vlastník SID vlastníka popisovače zabezpečení.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Určuje, zda je sacl nakonfigurován tak, aby podporoval automatické šíření.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Určuje, zda je popisovač zabezpečení nakonfigurován s výchozím sacl.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Určuje, zda popisovač zabezpečení obsahuje sacl.|
|[CSecurityDesc::Chráněno](#issaclprotected)|Určuje, zda je sacl nakonfigurován tak, aby zabránil změnám.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Určuje, zda je popisovač zabezpečení v relativním formátu.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Volánítéto metody převést popisovač zabezpečení do absolutního formátu.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Volání této metody převést popisovač zabezpečení na vlastní relativní formát.|
|[CSecurityDesc::Ovládací prvek SetControl](#setcontrol)|Nastaví řídicí bity popisovače zabezpečení.|
|[CSecurityDesc::SetDacl](#setdacl)|Nastaví informace v dacl. Pokud dacl je již k dispozici v popisovači zabezpečení, je nahrazen.|
|[CSecurityDesc::SetGroup](#setgroup)|Nastaví informace o primární skupině popisovače zabezpečení s absolutním formátem a nahradí všechny informace o primární skupině, které již jsou k dispozici.|
|[CSecurityDesc::SetOwner](#setowner)|Nastaví informace vlastníka popisovače zabezpečení v absolutním formátu a nahradí všechny informace o vlastníkovi, které již jsou k dispozici.|
|[CSecurityDesc::SetSacl](#setsacl)|Nastaví informace v sacl. Pokud je v popisovači zabezpečení již k dispozici sacl, je nahrazen.|
|[CSecurityDesc::ToString](#tostring)|Převede popisovač zabezpečení na formát řetězce.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CSecurityDesc::operátor const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.|
|[CSecurityDesc::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Struktura `SECURITY_DESCRIPTOR` obsahuje informace o zabezpečení přidružené k objektu. Aplikace používají tuto strukturu k nastavení a dotazování na stav zabezpečení objektu. Viz také [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikace by neměly `SECURITY_DESCRIPTOR` přímo měnit strukturu a místo toho by měly používat poskytnuté metody třídy.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Konstruktor

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Objekt `CSecurityDesc` nebo `SECURITY_DESCRIPTOR` struktura, které `CSecurityDesc` chcete přiřadit k novému objektu.

### <a name="remarks"></a>Poznámky

Objekt `CSecurityDesc` lze volitelně vytvořit `SECURITY_DESCRIPTOR` pomocí struktury nebo `CSecurityDesc` dříve definovaného objektu.

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc::~CSecurityDesc

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::FromString

Převede popisovač zabezpečení ve formátu řetězce na platný funkční popisovač zabezpečení.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*str.*<br/>
Ukazatel na řetězec s nulovým ukončením, který obsahuje [popisovač zabezpečení ve formátu řetězce,](/windows/win32/SecAuthZ/security-descriptor-string-format) který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true na úspěch. Vyvolá výjimku při selhání.

### <a name="remarks"></a>Poznámky

Řetězec lze vytvořit pomocí [CSecurityDesc::ToString](#tostring). Převod popisovače zabezpečení na řetězec usnadňuje ukládání a přenos.

Tato metoda volá [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::Ovládací prvek GetControl

Načte informace o ovládacím prvku z popisovače zabezpečení.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Ukazatel na `SECURITY_DESCRIPTOR_CONTROL` strukturu, která přijímá informace o ovládacím prvku popisovače zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud se nezdaří.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl

Načte informace o volitelném seznamu řízení přístupu (DACL) z popisovače zabezpečení.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel na `CDacl` strukturu, do které chcete uložit kopii dacl popisovače zabezpečení. Pokud existuje volitelný seznam ACL, metoda nastaví *pDacl* na adresu volitelného acl popisovače zabezpečení. Pokud volitelný seznam ACL neexistuje, není uložena žádná hodnota.

*pbPresent*<br/>
Ukazatel na hodnotu, která označuje přítomnost volitelného acl v zadaném popisovači zabezpečení. Pokud popisovač zabezpečení obsahuje volitelný seznam ACL, je tento parametr nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje volitelný seznam ACL, je tento parametr nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu `SECURITY_DESCRIPTOR_CONTROL` příznaku SE_DACL_DEFAULTED ve struktuře, pokud pro popisovač zabezpečení existuje volitelný seznam ACL. Pokud je tento příznak true, diskreční seznam ACL byl načten výchozí mechanismus; pokud false, diskreční ACL byl výslovně určen uživatelem.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud se nezdaří.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::GetGroup

Načte informace o primární skupině z popisovače zabezpečení.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na [identifikátor CSid](../../atl/reference/csid-class.md) (identifikátor zabezpečení), který obdrží kopii skupiny uložené v CDacl.

*pbDefaulted*<br/>
Ukazatel na příznak nastavenna hodnotu příznaku `SECURITY_DESCRIPTOR_CONTROL` SE_GROUP_DEFAULTED ve struktuře, když metoda vrátí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud se nezdaří.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::GetOwner

Načte vlastníka informaton z popisovače zabezpečení.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na [identifikátor CSid](../../atl/reference/csid-class.md) (identifikátor zabezpečení), který obdrží kopii skupiny uložené v CDacl.

*pbDefaulted*<br/>
Ukazatel na příznak nastavenna hodnotu příznaku `SECURITY_DESCRIPTOR_CONTROL` SE_OWNER_DEFAULTED ve struktuře, když metoda vrátí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud se nezdaří.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na [strukturu SECURITY_DESCRIPTOR.](/windows/win32/api/winnt/ns-winnt-security_descriptor)

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl

Načte informace seznamu řízení přístupu systému (SACL) z popisovače zabezpečení.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl*<br/>
Ukazatel na `CSacl` strukturu, do které chcete uložit kopii sacl s popisovačem popisovače zabezpečení. Pokud systém ACL existuje, metoda nastaví *pSacl* na adresu systému ACL popisovače zabezpečení. Pokud systém ACL neexistuje, není uložena žádná hodnota.

*pbPresent*<br/>
Ukazatel na příznak, který metoda nastaví k označení přítomnosti systémového acl v zadaném popisovači zabezpečení. Pokud popisovač zabezpečení obsahuje systémový seznam Řízení, je tento parametr nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje systémový seznam ACL, je tento parametr nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu `SECURITY_DESCRIPTOR_CONTROL` příznaku SE_SACL_DEFAULTED ve struktuře, pokud pro popisovač zabezpečení existuje systémový acl.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud se nezdaří.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Určuje, zda je volitelný seznam řízení přístupu (DACL) nakonfigurován tak, aby podporoval automatické šíření.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje seznam DACL, který je nastaven tak, aby podporoval automatické šíření dědičných položek řízení přístupu (ACE) na existující podřízené objekty. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém nastaví tento bit při provedení algoritmu automatické dědičnosti pro objekt a jeho existující podřízené objekty.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Určuje, zda je popisovač zabezpečení nakonfigurován s výchozím volitelným seznamem řízení přístupu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje výchozí seznam DACL false, jinak false.

### <a name="remarks"></a>Poznámky

Tento příznak může ovlivnit způsob, jakým systém zachází dacl, s ohledem na dědičnost položky řízení přístupu (ACE). Například pokud tvůrce objektu neurčuje DACL, objekt obdrží výchozí DACL z přístupového tokenu autora. Systém tento příznak ignoruje, pokud není nastaven příznak SE_DACL_PRESENT.

Tento příznak se používá k určení, jak má být vypočítán konečný seznam DACL na objektu a není fyzicky uložen v ovládacím prvku popisovače zabezpečení zabezpečitelného objektu.

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetDacl.](#setdacl)

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Určuje, zda popisovač zabezpečení obsahuje volitelný seznam řízení přístupu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje seznam DACL, false jinak.

### <a name="remarks"></a>Poznámky

Pokud tento příznak není nastaven, nebo pokud je tento příznak nastaven a DACL je NULL, popisovač zabezpečení umožňuje úplný přístup ke všem.

Tento příznak se používá k uložení informací o zabezpečení určených volajícím, dokud popisovač zabezpečení není přidružen k zabezpečitelný objekt. Jakmile je popisovač zabezpečení přidružen k zabezpečitelnému objektu, je příznak SE_DACL_PRESENT vždy nastaven v ovládacím prvku popisovače zabezpečení.

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetDacl.](#setdacl)

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected

Určuje, zda je volitelný seznam řízení přístupu (DACL) nakonfigurován tak, aby zabránil změnám.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je seznam DACL nakonfigurován tak, aby zabránil změně popisovače zabezpečení dědičnými položkami řízení přístupu (ACE). V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetDacl.](#setdacl)

Tato metoda podporuje automatické šíření dědičných ACE.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Určuje, zda byl identifikátor zabezpečení popisu zabezpečení (SID) nastaven ve výchozím nastavení.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud výchozí mechanismus, nikoli původní zprostředkovatel popisovače zabezpečení, za předpokladu, že sid skupiny popisovače zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetGroup.](#setgroup)

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Určuje, zda byl identifikátor zabezpečení popisovače zabezpečení nastaven ve výchozím nastavení.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud výchozí mechanismus, nikoli původní zprostředkovatel popisovače zabezpečení, za předpokladu, že vlastník popisovače zabezpečení sid vlastníka. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetOwner.](#setowner)

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Určuje, zda je seznam řízení přístupu k systému (SACL) nakonfigurován tak, aby podporoval automatické šíření.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje sacl, který je nastaven na podporu automatického šíření dědičných položek řízení přístupu (ACE) na existující podřízené objekty. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém nastaví tento bit při provedení algoritmu automatické dědičnosti pro objekt a jeho existující podřízené objekty.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Určuje, zda je popisovač zabezpečení nakonfigurován s výchozím seznamem řízení přístupu k systému (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje výchozí sacl false jinak.

### <a name="remarks"></a>Poznámky

Tento příznak může ovlivnit, jak systém zachází s sacl, s ohledem na dědičnost položky řízení přístupu (ACE). Systém tento příznak ignoruje, pokud není nastaven příznak SE_SACL_PRESENT.

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetSacl.](#setsacl)

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Určuje, zda popisovač zabezpečení obsahuje seznam řízení přístupu k systému (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje sacl false jinak.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetSacl.](#setsacl)

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::Chráněno

Určuje, zda je seznam řízení přístupu k systému (SACL) nakonfigurován tak, aby zabránil změnám.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je sacl nakonfigurován tak, aby zabránil úpravě popisovače zabezpečení dědičnými položkami řízení přístupu (ACE). V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit tento příznak, použijte metodu [CSecurityDesc::SetSacl.](#setsacl)

Tato metoda podporuje automatické šíření dědičných ACE.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Určuje, zda je popisovač zabezpečení v relativním formátu.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je deskriptor zabezpečení v relativním formátu se všemi informacemi o zabezpečení v souvislém bloku paměti. Vrátí hodnotu false, pokud je popisovač zabezpečení v absolutním formátu. Další informace naleznete [v tématu Absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Volánítéto metody převést popisovač zabezpečení do absolutního formátu.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false otherwise.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, nikoli na informace samotné. Popisovač zabezpečení v relativním formátu obsahuje informace v souvislém bloku paměti. V popisovači zabezpečení relativní k `SECURITY_DESCRIPTOR` sobě, struktura vždy spustí informace, ale ostatní součásti popisovače zabezpečení mohou sledovat strukturu v libovolném pořadí. Namísto použití adres paměti jsou součásti popisovače zabezpečení relativní k sobě označeny posuny od začátku popisovače zabezpečení. Tento formát je užitečný v případě, že popisovač zabezpečení musí být uložen na disku nebo přenášen pomocí komunikačního protokolu. Další informace naleznete [v tématu Absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Volání této metody převést popisovač zabezpečení na vlastní relativní formát.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false otherwise.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, nikoli samotné informace. Popisovač zabezpečení v relativním formátu obsahuje informace v souvislém bloku paměti. V popisovači zabezpečení relativní k `SECURITY_DESCRIPTOR` sobě, struktura vždy spustí informace, ale ostatní součásti popisovače zabezpečení mohou sledovat strukturu v libovolném pořadí. Namísto použití adres paměti jsou součásti popisovače zabezpečení identifikovány posuny od začátku popisovače zabezpečení. Tento formát je užitečný v případě, že popisovač zabezpečení musí být uložen na disku nebo přenášen pomocí komunikačního protokolu. Další informace naleznete [v tématu Absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::operátor =

Operátor přiřazení.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Struktura `SECURITY_DESCRIPTOR` nebo `CSecurityDesc` objekt přiřadit `CSecurityDesc` k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CSecurityDesc` objekt.

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operátor const SECURITY_DESCRIPTOR *

Předává hodnotu ukazatel na `SECURITY_DESCRIPTOR` strukturu.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::Ovládací prvek SetControl

Nastaví řídicí bity popisovače zabezpečení.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parametry

*ControlBitsOfInterest*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, která označuje ovládací bity, které mají být nastaveny. Seznam příznaků, které lze nastavit, naleznete v tématu [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, která označuje nové hodnoty pro řídicí bity určené maskou *ControlBitsOfInterest.* Tento parametr může být kombinací příznaků uvedených pro parametr *ControlBitsOfInterest.*

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl

Nastaví informace v seznamu dispozičního řízení přístupu (DACL). Pokud dacl je již k dispozici v popisovači zabezpečení, je nahrazen.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Dacl*<br/>
Odkaz na `CDacl` objekt určující seznam DACL pro popisovač zabezpečení. Tento parametr nesmí mít hodnotu NULL. Chcete-li nastavit null DACL v popisovači zabezpečení, první forma metody by měla být použita s *bPresent* nastavena na false.

*bSoučasnost*<br/>
Určuje příznak označující přítomnost seznamu DACL v popisovači zabezpečení. Pokud je tento parametr true, metoda nastaví příznak SE_DACL_PRESENT ve `SECURITY_DESCRIPTOR_CONTROL` struktuře a používá hodnoty v *Dacl* a *bDefaulted* parametry. Pokud je false, metoda vymaže příznak SE_DACL_PRESENT a *bDefaulted* je ignorována.

*bVýchozí hodnota*<br/>
Určuje příznak označující zdroj seznamu DACL. Pokud je tento příznak true, dacl byl načten některé výchozí mechanismus. Pokud false, DACL byl explicitně určen uživatelem. Metoda ukládá tuto hodnotu v `SECURITY_DESCRIPTOR_CONTROL` SE_DACL_DEFAULTED příznak struktury. Pokud tento parametr není zadán, SE_DACL_DEFAULTED příznak je vymazána.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Existuje důležitý rozdíl mezi prázdným a neexistujícím seznamem DACL. Pokud dacl je prázdný, neobsahuje žádné položky řízení přístupu a žádná přístupová práva byla explicitně udělena. V důsledku toho je implicitně odepřen přístup k objektu. Pokud objekt nemá žádný seznam DACL, na druhé straně není přiřazena žádná ochrana objektu a je udělena jakákoli žádost o přístup.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup

Nastaví informace o primární skupině popisovače zabezpečení s absolutním formátem a nahradí všechny informace o primární skupině, které již jsou k dispozici.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sid*<br/>
Odkaz na objekt [CSid](../../atl/reference/csid-class.md) pro novou primární skupinu popisovače zabezpečení. Tento parametr nesmí mít hodnotu NULL. Popisovač zabezpečení může být označen jako nemají DACL nebo SACL, ale musí mít skupinu a vlastníka, i když se jedná o NULL SID (což je vestavěný SID se zvláštním významem).

*bVýchozí hodnota*<br/>
Označuje, zda byly informace o primární skupině odvozeny z výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace a metoda ukládá `SECURITY_DESCRIPTOR_CONTROL` tuto hodnotu jako příznak SE_GROUP_DEFAULTED ve struktuře. Pokud je tento parametr nulový, SE_GROUP_DEFAULTED příznak je vymazán.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

Nastaví informace vlastníka popisovače zabezpečení absolutního formátu. Nahrazuje všechny informace vlastníka, které jsou již k dispozici.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt pro nový primární vlastník popisovače zabezpečení. Tento parametr nesmí mít hodnotu NULL.

*bVýchozí hodnota*<br/>
Označuje, zda jsou informace vlastníka odvozeny od výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace. Metoda ukládá tuto hodnotu jako `SECURITY_DESCRIPTOR_CONTROL` příznak SE_OWNER_DEFAULTED ve struktuře. Pokud je tento parametr nulový, SE_OWNER_DEFAULTED příznak je vymazána.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl

Nastaví informace v seznamu řízení přístupu k systému (SACL). Pokud je v popisovači zabezpečení již k dispozici sacl, je nahrazen.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Sacl*<br/>
Ukazatel na `CSacl` objekt určující sacl pro popisovač zabezpečení. Tento parametr nesmí být null a musí být csacl objekt. Na rozdíl od seznamů DACL neexistuje žádný rozdíl mezi hodnotou NULL a prázdným seznamem SACL, protože objekty SACL neurčují přístupová práva, pouze informace o auditování.

*bVýchozí hodnota*<br/>
Určuje příznak označující zdroj seznamu SACL. Pokud je tento příznak true, sacl byl načten některé výchozí mechanismus. Pokud false, sacl byl explicitně určen uživatelem. Metoda ukládá tuto hodnotu do `SECURITY_DESCRIPTOR_CONTROL` příznaku SE_SACL_DEFAULTED struktury. Pokud tento parametr není zadán, příznak SE_SACL_DEFAULTED je vymazán.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

## <a name="csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString

Převede popisovač zabezpečení na formát řetězce.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*str.*<br/>
Ukazatel na řetězec s nulovým ukončením, který obdrží [popisovač zabezpečení ve formátu řetězce](/windows/win32/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Určuje kombinaci příznaků bitů SECURITY_INFORMATION k označení součástí popisovače zabezpečení, které mají být zahrnuty do výstupního řetězce.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Jakmile je popisovač zabezpečení ve formátu řetězce, lze jej snadněji uložit nebo přenést. Pomocí `CSecurityDesc::FromString` metody převeďte řetězec zpět na popisovač zabezpečení.

Parametr *si* může obsahovat následující SECURITY_INFORMATION příznaky:

|Hodnota|Význam|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Zahrňte vlastníka.|
|GROUP_SECURITY_INFORMATION|Zahrňte primární skupinu.|
|DACL_SECURITY_INFORMATION|Zahrňte seznam DACL.|
|SACL_SECURITY_INFORMATION|Zahrňte sacl.|

Pokud je seznam DACL null a řídicí bit SE_DACL_PRESENT je nastaven v popisovači vstupního zabezpečení, metoda se nezdaří.

Pokud je seznam DACL null a řídicí bit SE_DACL_PRESENT není v popisovači vstupního zabezpečení nastaven, výsledný řetězec popisovače zabezpečení nemá komponentu D: . Další podrobnosti naleznete [v tématu Formát řetězce popisovače zabezpečení.](/windows/win32/SecAuthZ/security-descriptor-string-format)

Tato metoda volá [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
