---
title: Csecuritydesc – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 591465ed9c16485498174a710d2d37ff68425058
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116864"
---
# <a name="csecuritydesc-class"></a>Csecuritydesc – třída

Tato třída představuje obálku pro `SECURITY_DESCRIPTOR` struktury.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor|
|[CSecurityDesc::~CSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|Převede formát řetězce popisovače zabezpečení do popisovače zabezpečení platný a funkční.|
|[CSecurityDesc::GetControl](#getcontrol)|Načte ovládací prvek informace z popisovače zabezpečení.|
|[CSecurityDesc::GetDacl](#getdacl)|Načte informace o volitelném řízení přístupu na seznamu (DACL) z popisovače zabezpečení.|
|[CSecurityDesc::GetGroup](#getgroup)|Načte informace o primární skupině z popisovače zabezpečení.|
|[CSecurityDesc::GetOwner](#getowner)|Načte informace vlastníka z popisovače zabezpečení.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Vrací ukazatel `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::GetSacl](#getsacl)|Načte informace o systému řízení přístupu (SACL) seznam z popisovače zabezpečení.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Určuje, jestli seznam DACL je nakonfigurovaný pro podporu automatické šíření.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Určuje, pokud popisovač zabezpečení konfigurován s výchozím seznamem DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Určuje, jestli je nakonfigurovaný seznam DACL zabránit úpravy.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Určuje, zda se ve výchozím nastavení nastaven identifikátor zabezpečení skupiny popisovače zabezpečení (SID).|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Určuje, zda SID vlastníka popisovače zabezpečení byl nastaven ve výchozím nastavení.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Určuje, jestli SACL je nakonfigurovaný pro podporu automatické šíření.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Určuje, pokud popisovač zabezpečení má nakonfigurovanou výchozí SACL.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Určuje, zda SACL je konfigurován pro zabránění úpravy.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Určuje, zda popisovač zabezpečení do seberelativního formátu.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Voláním této metody lze převést popisovač zabezpečení na absolutním formátu.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Volání této metody se převést popisovač zabezpečení do seberelativního formátu.|
|[CSecurityDesc::SetControl](#setcontrol)|Nastaví řídicí bity popisovače zabezpečení.|
|[CSecurityDesc::SetDacl](#setdacl)|Nastaví informace v seznamu DACL. Pokud DACL již existuje v popisovači zabezpečení, se nahradí.|
|[CSecurityDesc::SetGroup](#setgroup)|Nastaví informace o primární skupině absolutním formátu popisovače zabezpečení, nahrazení již k dispozici žádné informace o primární skupině.|
|[CSecurityDesc::SetOwner](#setowner)|Nastaví informace o vlastníka absolutním formátu popisovače zabezpečení, nahradí jakékoli informace o vlastníkovi již existuje.|
|[CSecurityDesc::SetSacl](#setsacl)|Nastaví informace v seznamu SACL. Pokud SACL již existuje v popisovači zabezpečení, se nahradí.|
|[CSecurityDesc::ToString](#tostring)|Převede na formát řetězce popisovače zabezpečení.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Vrací ukazatel `SECURITY_DESCRIPTOR` struktury.|
|[CSecurityDesc::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

`SECURITY_DESCRIPTOR` Struktura obsahuje informace o zabezpečení, které jsou přidružené k objektu. Aplikace tuto strukturu použít pro nastavení a dotazování stavu objektu zabezpečení. Viz také [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikace by neměla změnit `SECURITY_DESCRIPTOR` struktura přímo a místo toho by měla používat metody třídy, které jsou k dispozici.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

Konstruktor

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CSecurityDesc` Objektu nebo `SECURITY_DESCRIPTOR` struktura přiřazena novému `CSecurityDesc` objektu.

### <a name="remarks"></a>Poznámky

`CSecurityDesc` Objektu je volitelně možné vytvořit `SECURITY_DESCRIPTOR` struktury nebo dříve definované `CSecurityDesc` objektu.

##  <a name="dtor"></a>  Csecuritydesc –:: ~ csecuritydesc –

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="fromstring"></a>  CSecurityDesc::FromString

Převede formát řetězce popisovače zabezpečení do popisovače zabezpečení platný a funkční.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje [formát řetězce popisovače zabezpečení](/windows/desktop/SecAuthZ/security-descriptor-string-format) má být převeden.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true v případě úspěchu. Vyvolá výjimku při selhání.

### <a name="remarks"></a>Poznámky

Řetězec je možné vytvořit pomocí [CSecurityDesc::ToString](#tostring). Převod popisovače zabezpečení do řetězce usnadňuje ukládání a přenosu.

Tato metoda volá [funkce ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

Načte ovládací prvek informace z popisovače zabezpečení.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Ukazatel `SECURITY_DESCRIPTOR_CONTROL` struktura, která obdrží informace o řízení popisovač zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud metoda uspěje, false Pokud selže.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa446647).

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

Načte informace o volitelném řízení přístupu na seznamu (DACL) z popisovače zabezpečení.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel `CDacl` strukturu, do kterého chcete uložit kopii DACL popisovače zabezpečení. Pokud volitelný seznam řízení přístupu existuje, metoda nastaví *pDacl* adresu popisovače zabezpečení volitelný seznam řízení přístupu. Pokud volitelný seznam ACL neexistuje, je uložená žádná hodnota.

*pbPresent*<br/>
Ukazatel na hodnotu, která indikuje přítomnost volitelného seznamu řízení přístupu ve Zadaný popisovač zabezpečení. Popisovač zabezpečení obsahuje volitelný seznam řízení přístupu,-li tento parametr je nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje volitelného seznamu řízení přístupu, tento parametr je nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavena na hodnotu příznaku SE_DACL_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury, pokud existuje volitelný seznam řízení přístupu pro popisovač zabezpečení. Pokud tento příznak není true, byla načtena výchozího mechanismu; volitelný seznam řízení přístupu Pokud má hodnotu false, volitelný seznam řízení přístupu explicitně zadaná uživatelem.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud metoda uspěje, false Pokud selže.

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

Načte informace o primární skupině z popisovače zabezpečení.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [identifikační číslo volané stanice](../../atl/reference/csid-class.md) (security identifier), která obdrží kopii skupiny uložená v cdacl –.

*pbDefaulted*<br/>
Ukazatel na příznak nastavena na hodnotu příznaku SE_GROUP_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury po návratu metody.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud metoda uspěje, false Pokud selže.

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

Načte informace vlastníka z popisovače zabezpečení.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [identifikační číslo volané stanice](../../atl/reference/csid-class.md) (security identifier), která obdrží kopii skupiny uložená v cdacl –.

*pbDefaulted*<br/>
Ukazatel na příznak nastavena na hodnotu příznaku SE_OWNER_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury po návratu metody.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud metoda uspěje, false Pokud selže.

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

Vrací ukazatel `SECURITY_DESCRIPTOR` struktury.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) struktury.

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

Načte informace o systému řízení přístupu (SACL) seznam z popisovače zabezpečení.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl*<br/>
Ukazatel `CSacl` strukturu, do kterého chcete uložit kopii SACL popisovače zabezpečení. Pokud systém ACL existuje, metoda nastaví *pSacl* adresu popisovače zabezpečení systému seznamu ACL. Pokud systém ACL neexistuje, je uložená žádná hodnota.

*pbPresent*<br/>
Ukazatel na metodu příznak nastaví udávajících přítomnost systému seznamu ACL v Zadaný popisovač zabezpečení. Obsahuje-li popisovače zabezpečení systému seznamu ACL, tento parametr je nastaven na hodnotu true. Popisovač zabezpečení neobsahuje systém seznamu ACL,-li tento parametr je nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavena na hodnotu příznaku SE_SACL_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury, pokud existuje systém seznamu ACL pro popisovač zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud metoda uspěje, false Pokud selže.

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

Určuje, pokud seznam volitelných řízení přístupu (DACL) je nakonfigurována pro podporu automatické šíření.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud popisovač zabezpečení obsahuje seznam DACL, který je nastaven pro podporu automatické šíření hodnoty záznamů odvoditelný řízení přístupu (ACE) do existující podřízené objekty. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém nastaví tento bit při provádění algoritmu automatické dědičnosti pro objekt a jeho existující podřízených objektů.

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

Určuje, pokud popisovač zabezpečení má nakonfigurovanou výchozí seznam volitelných řízení přístupu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud popisovač zabezpečení obsahuje výchozí seznam DACL, false v opačném případě vrátí hodnotu true.

### <a name="remarks"></a>Poznámky

Tento příznak může ovlivnit, jak systém zpracovává DACL, s ohledem na řízení přístupu položky (ACE) dědičnosti. Pokud tvůrce objektu neurčuje DACL, objekt přijme výchozí seznam DACL z Tvůrce příslušného přístupového tokenu. Systém tento příznak ignoruje, pokud není nastavený příznak SE_DACL_PRESENT.

Tento příznak se používá k určení, jak je konečný seznam DACL na objektu přepočet a není fyzicky uložený v ovládacím prvku popisovače zabezpečení zabezpečitelného objektu.

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetDacl](#setdacl) metody.

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

Určuje, zda popisovač zabezpečení obsahuje seznam volitelných řízení přístupu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud popisovač zabezpečení obsahuje seznam DACL, false v opačném případě.

### <a name="remarks"></a>Poznámky

Pokud tento příznak není nastavený nebo pokud je tento příznak nastaven, a seznam DACL má hodnotu NULL, popisovače zabezpečení umožňuje plný přístup ke všem uživatelům.

Tento příznak se používá k uložení informace o zabezpečení určené volajícího až do popisovače zabezpečení je přidružen zabezpečitelných objektů. Jakmile popisovač zabezpečení je přidružen zabezpečitelných objektů, je vždycky nastavený příznak SE_DACL_PRESENT v ovládacím prvku popisovač zabezpečení.

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetDacl](#setdacl) metody.

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

Určuje, zda seznam volitelných řízení přístupu (DACL) je konfigurován pro zabránění úpravy.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud je nakonfigurovaný seznam DACL zabránit právě upravuje položky odvoditelný řízení přístupu (ACE) popisovače zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetDacl](#setdacl) metody.

Tato metoda podporuje automatické šíření ze dědičné ACE.

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

Určuje, zda se ve výchozím nastavení nastaven identifikátor zabezpečení skupiny popisovače zabezpečení (SID).

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true Pokud výchozího mechanismu namísto původní zprostředkovatele popisovače zabezpečení, k dispozici popisovače zabezpečení SID skupiny. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetGroup](#setgroup) metody.

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

Určuje, zda se ve výchozím nastavení nastaven identifikátor zabezpečení vlastníka popisovače zabezpečení (SID).

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud výchozího mechanismu namísto původní zprostředkovatele popisovače zabezpečení, k dispozici SID vlastníka popisovače zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetOwner](#setowner) metody.

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

Určuje, pokud se systémový seznam řízení přístupu (SACL) je nakonfigurována pro podporu automatické šíření.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud popisovač zabezpečení obsahuje seznam SACL, který je nastaven pro podporu automatické šíření hodnoty záznamů odvoditelný řízení přístupu (ACE) do existující podřízené objekty. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém nastaví tento bit při provádění algoritmu automatické dědičnosti pro objekt a jeho existující podřízených objektů.

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

Určuje, pokud popisovač zabezpečení má nakonfigurovanou seznam výchozí systému řízení přístupu (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud popisovač zabezpečení obsahuje výchozí SACL, false v opačném případě vrátí hodnotu true.

### <a name="remarks"></a>Poznámky

Tento příznak může ovlivnit, jak systém zpracovává SACL, s ohledem na řízení přístupu položky (ACE) dědičnosti. Systém tento příznak ignoruje, pokud není nastavený příznak SE_SACL_PRESENT.

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetSacl](#setsacl) metody.

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

Určuje, zda popisovač zabezpečení obsahuje seznam řízení přístupu (SACL) systému.

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud popisovač zabezpečení obsahuje seznam SACL false v opačném případě.

### <a name="remarks"></a>Poznámky

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetSacl](#setsacl) metody.

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

Určuje, zda systémový seznam řízení přístupu (SACL) je konfigurován pro zabránění úpravy.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud je nakonfigurovaná SACL zabránit právě upravuje položky odvoditelný řízení přístupu (ACE) popisovače zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Chcete-li tento příznak nastavit, použijte [CSecurityDesc::SetSacl](#setsacl) metody.

Tato metoda podporuje automatické šíření ze dědičné ACE.

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

Určuje, zda popisovač zabezpečení do seberelativního formátu.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud je popisovač zabezpečení ve formátu self-relative se všechny informace o zabezpečení v souvislém bloku paměti. Vrátí hodnotu false, pokud je popisovač zabezpečení v absolutním formátu. Další informace najdete v tématu [absolutní a popisovačů zabezpečení Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

Voláním této metody lze převést popisovač zabezpečení na absolutním formátu.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, false v opačném případě vrátí hodnotu true.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, místo samotného informace. Popisovač zabezpečení ve formátu self-relative informacemi v souvislém bloku paměti. V popisovači samorelativní zabezpečení `SECURITY_DESCRIPTOR` struktura vždycky spustí informace, ale popisovače zabezpečení v jiné součásti můžete vycházet ze struktury v libovolném pořadí. Namísto použití adresy paměti, součástí samorelativní popisovače jsou označeny posun od začátku popisovač zabezpečení. Tento formát je užitečný při popisovače zabezpečení musí být uložená na disku nebo přenášet prostřednictvím komunikační protokol. Další informace najdete v tématu [absolutní a popisovačů zabezpečení Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

Volání této metody se převést popisovač zabezpečení do seberelativního formátu.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, false v opačném případě vrátí hodnotu true.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, nikoli obsahující informace o samotné. Popisovač zabezpečení ve formátu self-relative informacemi v souvislém bloku paměti. V popisovači samorelativní zabezpečení `SECURITY_DESCRIPTOR` struktura vždycky spustí informace, ale popisovače zabezpečení v jiné součásti můžete vycházet ze struktury v libovolném pořadí. Místo adresy paměti součásti popisovače zabezpečení jsou označeny posun od začátku popisovač zabezpečení. Tento formát je užitečný při popisovače zabezpečení musí být uložená na disku nebo přenášet prostřednictvím komunikační protokol. Další informace najdete v tématu [absolutní a popisovačů zabezpečení Self-Relative](/windows/desktop/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="operator_eq"></a>  CSecurityDesc::operator =

Operátor přiřazení.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`SECURITY_DESCRIPTOR` Struktury nebo `CSecurityDesc` objekt přiřadit `CSecurityDesc` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CSecurityDesc` objektu.

##  <a name="operator_const_security_descriptor__star"></a>  CSecurityDesc::operator const SECURITY_DESCRIPTOR *

Přetypování na ukazatel na hodnotu `SECURITY_DESCRIPTOR` struktury.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

Nastaví řídicí bity popisovače zabezpečení.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest, 
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parametry

*ControlBitsOfInterest*<br/>
SECURITY_DESCRIPTOR_CONTROL maska, která označuje nastavované řídicí bity. Seznam příznaků, které je možné nastavit, najdete v části [SetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).

*ControlBitsToSet*<br/>
Masku SECURITY_DESCRIPTOR_CONTROL, která určuje nové hodnoty řídicích bitů určených maskou *ControlBitsOfInterest* masky. Tento parametr může být kombinací příznaků uvedených pro *ControlBitsOfInterest* parametru.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [SetSecurityDescriptorControl](https://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

Nastaví informace v seznamu volitelných řízení přístupu (DACL). Pokud DACL již existuje v popisovači zabezpečení, se nahradí.

```
inline void SetDacl(  
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(  
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Seznam DACL*<br/>
Odkaz `CDacl` určující seznam DACL pro popisovač zabezpečení. Tento parametr nesmí mít hodnotu NULL. Nastavení DACL hodnoty NULL v popisovači zabezpečení, by měl použít první formulář metody s *bPresent* nastavena na hodnotu false.

*bPresent*<br/>
Určuje příznak, který udává přítomnost DACL v popisovači zabezpečení. Pokud tento parametr hodnotu true, metoda nastaví příznak SE_DACL_PRESENT `SECURITY_DESCRIPTOR_CONTROL` struktury a používá hodnoty v *Dacl* a *bDefaulted* parametry. Pokud je false, metoda vymaže příznak SE_DACL_PRESENT a *bDefaulted* se ignoruje.

*bDefaulted*<br/>
Určuje příznak, který udává zdrojový DACL. Pokud tento příznak není true, načtou seznam DACL některé výchozího mechanismu. Pokud má hodnotu false, seznam DACL byl explicitně zadán uživatel. Metoda SE_DACL_DEFAULTED příznak uloží tuto hodnotu `SECURITY_DESCRIPTOR_CONTROL` struktury. Pokud není tento parametr zadán, je příznak SE_DACL_DEFAULTED zrušeno.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Je důležité rozdíl mezi prázdná a neexistující DACL. Když DACL je prázdný, neobsahuje žádné položky řízení přístupu a byl výslovně udělen žádné přístupová práva. V důsledku toho je implicitně odepřen přístup k objektu. Když objekt nemá žádné seznamy typu DACL, na druhé straně žádná ochrana je přiřazen objekt a všechny žádosti o přístup je udělen.

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

Nastaví informace o primární skupině absolutním formátu popisovače zabezpečení, nahrazení již k dispozici žádné informace o primární skupině.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*identifikátor SID*<br/>
Odkaz [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekt popisovače zabezpečení nové primární skupiny. Tento parametr nesmí mít hodnotu NULL. Popisovač zabezpečení může být označený jako bez nutnosti DACL nebo SACL, ale musí mít skupinu a vlastníka, i ty jsou NULL SID (která je integrovaná SID zvláštní význam).

*bDefaulted*<br/>
Určuje, zda informace o primární skupině odvozený z výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace a metodu uloží tuto hodnotu jako příznak SE_GROUP_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury. Pokud tento parametr je nula, je příznak SE_GROUP_DEFAULTED zrušeno.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

Nastaví informace o vlastníka popisovače zabezpečení absolutním formátu. Nahradí všechny informace o vlastníkovi již existuje.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*identifikátor SID*<br/>
[Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekt popisovače zabezpečení nového primárního vlastníka. Tento parametr nesmí mít hodnotu NULL.

*bDefaulted*<br/>
Označuje, zda informace o vlastníkovi je odvozena z výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace. Metoda uloží tuto hodnotu jako příznak SE_OWNER_DEFAULTED v `SECURITY_DESCRIPTOR_CONTROL` struktury. Pokud tento parametr je nula, je příznak SE_OWNER_DEFAULTED zrušeno.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

Nastaví informace o systému seznamu řízení přístupu (SACL). Pokud SACL již existuje v popisovači zabezpečení, se nahradí.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*SACL*<br/>
Ukazatel `CSacl` určující SACL popisovače zabezpečení. Tento parametr nesmí mít hodnotu NULL a musí být objekt csacl –. Na rozdíl od DACL není žádný rozdíl mezi hodnotou NULL nebo prázdný seznam SACL, jak objekty SACL nezadávejte přístupová práva, jenom auditování informace.

*bDefaulted*<br/>
Určuje příznak, který udává zdrojový SACL. Pokud tento příznak není true, načtou SACL některé výchozího mechanismu. Pokud má hodnotu false, SACL byl explicitně zadán uživatel. Metoda SE_SACL_DEFAULTED příznak uloží tuto hodnotu `SECURITY_DESCRIPTOR_CONTROL` struktury. Pokud není tento parametr zadán, je příznak SE_SACL_DEFAULTED zrušeno.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="tostring"></a>  CSecurityDesc::ToString

Převede na formát řetězce popisovače zabezpečení.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec zakončený hodnotou null, která se zobrazí [formát řetězce popisovače zabezpečení](/windows/desktop/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Určuje kombinaci SECURITY_INFORMATION bitové příznaky označující součásti popisovače zabezpečení, které chcete zahrnout do výstupního řetězce.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Jakmile popisovač zabezpečení je ve formátu řetězce, ho lze snadněji uložit nebo přenášet. Použití `CSecurityDesc::FromString` způsobů, jak převést řetězec zpět do popisovače zabezpečení.

*Si* parametr může obsahovat následující příznaky SECURITY_INFORMATION:

|Hodnota|Význam|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Zahrnovat vlastníka.|
|GROUP_SECURITY_INFORMATION|Zahrnují primární skupinu.|
|DACL_SECURITY_INFORMATION|Zahrnout DACL.|
|SACL_SECURITY_INFORMATION|Zahrnout SACL.|

Pokud seznam DACL má hodnotu NULL a je nastaven bit ovládací prvek SE_DACL_PRESENT v vstupní popisovač zabezpečení, metoda se nezdaří.

Pokud je DACL hodnoty NULL a bit SE_DACL_PRESENT ovládací prvek kódu není nastavený vstupní popisovač zabezpečení, výsledného řetězce popisovače zabezpečení nemá D: komponenty. Zobrazit [formát řetězce popisovače zabezpečení](/windows/desktop/SecAuthZ/security-descriptor-string-format) další podrobnosti.

Tato metoda volá [funkce ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/desktop/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptora).

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
