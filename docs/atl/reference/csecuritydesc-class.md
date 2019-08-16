---
title: CSecurityDesc – třída
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
ms.openlocfilehash: 90f8cfd66fbab88bfa29c39ff27189f02447a7c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496492"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc – třída

Tato třída je obálkou pro `SECURITY_DESCRIPTOR` strukturu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityDesc
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Konstruktor|
|[CSecurityDesc::~CSecurityDesc](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSecurityDesc:: FromString](#fromstring)|Převede popisovač zabezpečení formátu String na platný, funkční popisovač zabezpečení.|
|[CSecurityDesc:: GetControl](#getcontrol)|Načte informace o ovládacím prvku z popisovače zabezpečení.|
|[CSecurityDesc::GetDacl](#getdacl)|Načte volitelné informace o seznamu řízení přístupu (DACL) z popisovače zabezpečení.|
|[CSecurityDesc::GetGroup](#getgroup)|Načte informace o primární skupině z popisovače zabezpečení.|
|[CSecurityDesc::GetOwner](#getowner)|Načte vlastníka informace z popisovače zabezpečení.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.|
|[CSecurityDesc:: getsacl](#getsacl)|Načte z popisovače zabezpečení informace o seznamu řízení přístupu (SACL) systému.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Určuje, jestli je seznam DACL nakonfigurovaný tak, aby podporoval automatické šíření.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Určuje, jestli je popisovač zabezpečení nakonfigurovaný s výchozím seznamem DACL.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Určuje, jestli je seznam DACL nakonfigurovaný tak, aby se zabránilo změnám.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Určuje, zda byl ve výchozím nastavení nastaven identifikátor zabezpečení (SID) popisovače zabezpečení.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Určuje, zda byl ve výchozím nastavení nastaven identifikátor SID vlastníka popisovače zabezpečení.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Určuje, jestli je seznam SACL nakonfigurovaný tak, aby podporoval automatické šíření.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Určuje, jestli je popisovač zabezpečení nakonfigurovaný s výchozím SACL.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam SACL.|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Určuje, jestli je seznam SACL nakonfigurovaný tak, aby se zabránilo změnám.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Určuje, zda je popisovač zabezpečení ve formátu samostatného vztahu.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Voláním této metody převedete popisovač zabezpečení na absolutní formát.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Voláním této metody můžete převést popisovač zabezpečení na formát relativní vzhledem k samostatnému formátu.|
|[CSecurityDesc::SetControl](#setcontrol)|Nastaví řídicí bity popisovače zabezpečení.|
|[CSecurityDesc::SetDacl](#setdacl)|Nastaví informace v seznamu DACL. Pokud je seznam DACL v popisovači zabezpečení již přítomen, je nahrazen.|
|[CSecurityDesc::SetGroup](#setgroup)|Nastaví informace o primární skupině pro popisovač zabezpečení absolutního formátu a nahradí již existující informace o primární skupině.|
|[CSecurityDesc::SetOwner](#setowner)|Nastaví informace o vlastníkovi popisovače zabezpečení absolutního formátu a nahradí již existující informace o vlastníkovi.|
|[CSecurityDesc::SetSacl](#setsacl)|Nastaví informace v SACL. Pokud je seznam SACL již přítomen v popisovači zabezpečení, je nahrazen.|
|[CSecurityDesc:: ToString](#tostring)|Převede popisovač zabezpečení na formát řetězce.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.|
|[CSecurityDesc:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

`SECURITY_DESCRIPTOR` Struktura obsahuje informace o zabezpečení přidružené k objektu. Aplikace tuto strukturu používají k nastavení a dotazování na stav zabezpečení objektu. Viz také [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Aplikace by neměly měnit `SECURITY_DESCRIPTOR` strukturu přímo a místo toho by měly používat poskytnuté metody třídy.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Konstruktor

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Objekt nebo `SECURITY_DESCRIPTOR` struktura, které chcete přiřadit k novému `CSecurityDesc` objektu. `CSecurityDesc`

### <a name="remarks"></a>Poznámky

Objekt lze volitelně vytvořit `SECURITY_DESCRIPTOR` pomocí struktury nebo dříve definovaného `CSecurityDesc` objektu. `CSecurityDesc`

##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc

Destruktor.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny přidělené prostředky.

##  <a name="fromstring"></a>CSecurityDesc:: FromString

Převede popisovač zabezpečení formátu String na platný, funkční popisovač zabezpečení.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje [popisovač zabezpečení formátu řetězce](/windows/win32/SecAuthZ/security-descriptor-string-format) , který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true při úspěchu. Vyvolá výjimku při selhání.

### <a name="remarks"></a>Poznámky

Řetězec lze vytvořit pomocí [CSecurityDesc:: ToString](#tostring). Převod popisovače zabezpečení na řetězec usnadňuje ukládání a přenos.

Tato metoda volá [funkce ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

##  <a name="getcontrol"></a>CSecurityDesc:: GetControl

Načte informace o ovládacím prvku z popisovače zabezpečení.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Parametry

*psdc*<br/>
Ukazatel na `SECURITY_DESCRIPTOR_CONTROL` strukturu, která obdrží informace o ovládacím prvku popisovače zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud selže.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

##  <a name="getdacl"></a>CSecurityDesc:: getdacl

Načte volitelné informace o seznamu řízení přístupu (DACL) z popisovače zabezpečení.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel na `CDacl` strukturu, do které se uloží kopie seznamu DACL popisovače zabezpečení. Pokud existuje volitelný seznam řízení přístupu (ACL), metoda nastaví *pDacl* na adresu VOLITELNÉHO seznamu ACL popisovače zabezpečení. Pokud neexistuje volitelný seznam řízení přístupu (ACL), není uložena žádná hodnota.

*pbPresent*<br/>
Ukazatel na hodnotu, která indikuje přítomnost volitelného seznamu ACL v zadaném popisovači zabezpečení. Pokud popisovač zabezpečení obsahuje volitelný seznam řízení přístupu (ACL), je tento parametr nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje volitelný seznam řízení přístupu (ACL), je tento parametr nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu příznaku SE_DACL_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře, pokud pro popisovač zabezpečení existuje volitelný seznam řízení přístupu (ACL). Pokud má tento příznak hodnotu true, volitelné řízení přístupu bylo načteno pomocí výchozího mechanismu; Pokud má hodnotu false, je volitelný seznam řízení přístupu výslovně zadaný uživatelem.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud selže.

##  <a name="getgroup"></a>CSecurityDesc:: getgroup

Načte informace o primární skupině z popisovače zabezpečení.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na identifikátor [CSID](../../atl/reference/csid-class.md) (identifikátor zabezpečení), který obdrží kopii skupiny uloženou v CDacl.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu příznaku SE_GROUP_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře, když se metoda vrátí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud selže.

##  <a name="getowner"></a>CSecurityDesc:: GetOwner

Načte vlastníka informace z popisovače zabezpečení.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na identifikátor [CSID](../../atl/reference/csid-class.md) (identifikátor zabezpečení), který obdrží kopii skupiny uloženou v CDacl.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu příznaku SE_OWNER_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře, když se metoda vrátí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud selže.

##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Vrátí ukazatel na `SECURITY_DESCRIPTOR` strukturu.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na strukturu [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) .

##  <a name="getsacl"></a>CSecurityDesc:: getsacl

Načte z popisovače zabezpečení informace o seznamu řízení přístupu (SACL) systému.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSacl*<br/>
Ukazatel na `CSacl` strukturu, do které se uloží kopie seznamu SACL popisovače zabezpečení. Pokud existuje seznam řízení přístupu (ACL) systému, metoda nastaví *pSacl* na adresu seznamu ACL systému popisovače zabezpečení. Pokud seznam řízení přístupu systému neexistuje, není uložena žádná hodnota.

*pbPresent*<br/>
Ukazatel na příznak, který nastaví metodu, aby označoval přítomnost seznamu ACL systému v zadaném popisovači zabezpečení. Pokud popisovač zabezpečení obsahuje seznam řízení přístupu (ACL) systému, je tento parametr nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje seznam ACL systému, je tento parametr nastaven na hodnotu false.

*pbDefaulted*<br/>
Ukazatel na příznak nastavený na hodnotu příznaku SE_SACL_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře, pokud pro popisovač zabezpečení existuje seznam ACL systému.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, false, pokud selže.

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

Určuje, jestli je seznam DACL (Discretionary Access Control List) nakonfigurovaný tak, aby podporoval automatické šíření.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje seznam DACL, který je nastaven tak, aby podporoval automatickou šíření dědičných položek řízení přístupu (ACE) do existujících podřízených objektů. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém tento bit nastaví, když provede algoritmus automatické dědičnosti pro objekt a jeho existující podřízené objekty.

##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Určuje, jestli je popisovač zabezpečení nakonfigurovaný s výchozím volitelným seznamem řízení přístupu (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje výchozí seznam DACL, jinak false.

### <a name="remarks"></a>Poznámky

Tento příznak může mít vliv na to, jak systém pracuje se seznamem DACL, s ohledem na dědičnost vstupu řízení přístupu (ACE). Pokud například tvůrce objektu neurčí seznam DACL, objekt dostane výchozí seznam DACL z přístupového tokenu autora. Systém tento příznak ignoruje, pokud není nastaven příznak SE_DACL_PRESENT.

Tento příznak se používá k určení toho, jak se má výsledný seznam DACL na objektu vypočítat a který není fyzicky uložen v ovládacím prvku popisovač zabezpečení zabezpečitelné objektu.

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetDacl –](#setdacl) .

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

Určuje, jestli popisovač zabezpečení obsahuje volitelný seznam řízení přístupu (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje DACL, jinak false.

### <a name="remarks"></a>Poznámky

Pokud tento příznak není nastavený nebo pokud je tento příznak nastavený a DACL má hodnotu NULL, popisovač zabezpečení umožňuje úplný přístup všem.

Tento příznak se používá k uložení informací o zabezpečení určených volajícím, dokud popisovač zabezpečení není přidružen k zabezpečitelné objektu. Jakmile je popisovač zabezpečení přidružen k zabezpečitelné objektu, příznak SE_DACL_PRESENT je vždy nastaven v ovládacím prvku popisovač zabezpečení.

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetDacl –](#setdacl) .

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

Určuje, jestli je seznam volitelných řízení přístupu (DACL) nakonfigurovaný tak, aby se zabránilo změnám.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud je seznam DACL nakonfigurován tak, aby zabránil změně popisovače zabezpečení dědičnými položkami řízení přístupu (ACE). V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetDacl –](#setdacl) .

Tato metoda podporuje automatické šíření dědičných ACE.

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

Určuje, zda byl ve výchozím nastavení nastaven identifikátor zabezpečení (SID) popisovače zabezpečení.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud výchozí mechanismus místo původního poskytovatele popisovače zabezpečení poskytl identifikátor SID skupiny popisovačů zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetGroup](#setgroup) .

##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Určuje, zda byl ve výchozím nastavení nastaven identifikátor zabezpečení SID vlastníka popisovače zabezpečení.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud výchozí mechanismus místo původního poskytovatele popisovače zabezpečení poskytl identifikátor SID vlastníka popisovače zabezpečení. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetOwner](#setowner) .

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

Určuje, jestli je seznam řízení přístupu (SACL) systému nakonfigurovaný tak, aby podporoval automatické šíření.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje seznam SACL, který je nastaven tak, aby podporoval automatickou šíření dědičných položek řízení přístupu (ACE) do existujících podřízených objektů. V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Systém tento bit nastaví, když provede algoritmus automatické dědičnosti pro objekt a jeho existující podřízené objekty.

##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Určuje, jestli je popisovač zabezpečení nakonfigurovaný s výchozím seznamem SACL (System Access Control).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje výchozí seznam SACL, jinak false.

### <a name="remarks"></a>Poznámky

Tento příznak může ovlivnit způsob, jakým systém pracuje s SACL, s ohledem na dědičnost položky přístupu (ACE). Systém tento příznak ignoruje, pokud není nastaven příznak SE_SACL_PRESENT.

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Určuje, zda popisovač zabezpečení obsahuje seznam řízení přístupu (SACL) systému.

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud popisovač zabezpečení obsahuje v opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetSacl](#setsacl) .

##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected

Určuje, jestli je seznam řízení přístupu k systému (SACL) nakonfigurovaný tak, aby se zabránilo změnám.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je seznam SACL nakonfigurován tak, aby zabránil tomu, aby byl popisovač zabezpečení upravován dědičnými položkami řízení přístupu (ACE). V opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

K nastavení tohoto příznaku použijte metodu [CSecurityDesc:: SetSacl](#setsacl) .

Tato metoda podporuje automatické šíření dědičných ACE.

##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Určuje, zda je popisovač zabezpečení ve formátu samostatného vztahu.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je popisovač zabezpečení v samostatném formátu se všemi informacemi o zabezpečení v souvislém bloku paměti. Vrátí hodnotu false, pokud je popisovač zabezpečení v absolutním formátu. Další informace najdete v tématu [absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Voláním této metody převedete popisovač zabezpečení na absolutní formát.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, jinak false.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, nikoli informace samotné. Popisovač zabezpečení v samostatném formátu obsahuje informace v souvislém bloku paměti. V samostatném popisovači zabezpečení, `SECURITY_DESCRIPTOR` struktura vždy spouští tyto informace, ale ostatní komponenty popisovače zabezpečení mohou strukturu sledovat v libovolném pořadí. Místo používání adres paměti jsou součásti samostatného popisovače zabezpečení identifikovány posuny od začátku popisovače zabezpečení. Tento formát je užitečný, když popisovač zabezpečení musí být uložený na disku nebo předaný prostřednictvím komunikačního protokolu. Další informace najdete v tématu [absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Voláním této metody můžete převést popisovač zabezpečení na formát relativní vzhledem k samostatnému formátu.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je metoda úspěšná, jinak false.

### <a name="remarks"></a>Poznámky

Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, místo toho, aby obsahovaly samotné informace. Popisovač zabezpečení v samostatném formátu obsahuje informace v souvislém bloku paměti. V samostatném popisovači zabezpečení, `SECURITY_DESCRIPTOR` struktura vždy spouští tyto informace, ale ostatní komponenty popisovače zabezpečení mohou strukturu sledovat v libovolném pořadí. Místo používání adres paměti jsou součásti popisovače zabezpečení identifikovány posuny od začátku popisovače zabezpečení. Tento formát je užitečný, když popisovač zabezpečení musí být uložený na disku nebo předaný prostřednictvím komunikačního protokolu. Další informace najdete v tématu [absolutní a relativní popisovače zabezpečení](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

##  <a name="operator_eq"></a>CSecurityDesc:: operator =

Operátor přiřazení

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
`SECURITY_DESCRIPTOR` Struktura nebo `CSecurityDesc` objekt`CSecurityDesc` , který má být přiřazen objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CSecurityDesc` objekt.

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

Přetypování hodnoty na ukazatel na `SECURITY_DESCRIPTOR` strukturu.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>CSecurityDesc::SetControl

Nastaví řídicí bity popisovače zabezpečení.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Parametry

*ControlBitsOfInterest*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, která označuje bity ovládacího prvku, které se mají nastavit. Seznam příznaků, které lze nastavit, naleznete v tématu [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Maska SECURITY_DESCRIPTOR_CONTROL, která označuje nové hodnoty pro bity ovládacího prvku určené maskou *ControlBitsOfInterest* . Tento parametr může být kombinací příznaků uvedených pro parametr *ControlBitsOfInterest* .

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Tato metoda volá [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

##  <a name="setdacl"></a>CSecurityDesc:: SetDacl –

Nastaví informace v volitelném seznamu řízení přístupu (DACL). Pokud je seznam DACL v popisovači zabezpečení již přítomen, je nahrazen.

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
Odkaz na `CDacl` objekt určující DACL pro popisovač zabezpečení. Tento parametr nesmí mít hodnotu NULL. Chcete-li nastavit seznam DACL s hodnotou NULL v popisovači zabezpečení, je třeba použít první tvar metody s *bPresent* nastavenou na hodnotu false.

*bPresent*<br/>
Určuje příznak označující přítomnost seznamu DACL v popisovači zabezpečení. Pokud je tento parametr true, metoda nastaví příznak SE_DACL_PRESENT ve `SECURITY_DESCRIPTOR_CONTROL` struktuře a použije hodnoty v parametrech *DACL* a *bDefaulted* . Pokud je hodnota false, metoda vymaže příznak SE_DACL_PRESENT a *bDefaulted* se ignoruje.

*bDefaulted*<br/>
Určuje příznak označující zdroj seznamu DACL. Pokud má tento příznak hodnotu true, seznam DACL byl načten nějakým výchozím mechanismem. Pokud je hodnota false, seznam DACL byl explicitně zadán uživatelem. Metoda uloží tuto hodnotu do příznaku `SECURITY_DESCRIPTOR_CONTROL` SE_DACL_DEFAULTED struktury. Pokud tento parametr není zadán, příznak SE_DACL_DEFAULTED je vymazán.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Existuje důležitý rozdíl mezi prázdným a neexistujícím seznamem DACL. Pokud je seznam DACL prázdný, neobsahuje žádné položky řízení přístupu a nebyla explicitně udělena žádná přístupová práva. V důsledku toho je přístup k objektu implicitně odepřen. Pokud objekt nemá žádný DACL, k objektu se nepřiřazuje žádná ochrana a je udělená kterákoli žádost o přístup.

##  <a name="setgroup"></a>CSecurityDesc::SetGroup

Nastaví informace o primární skupině pro popisovač zabezpečení absolutního formátu a nahradí již existující informace o primární skupině.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*ID*<br/>
Odkazuje na objekt [CSID](../../atl/reference/csid-class.md) pro novou primární skupinu popisovače zabezpečení. Tento parametr nesmí mít hodnotu NULL. Popisovač zabezpečení je možné označit jako neobsahující DACL nebo SACL, ale musí mít skupinu a vlastníka, i když se jedná o identifikátor SID s hodnotou NULL (což je předdefinovaný identifikátor SID se speciálním významem).

*bDefaulted*<br/>
Určuje, zda byly informace o primární skupině odvozeny od výchozího mechanismu. Pokud je tato hodnota true, jedná se o výchozí informace a metoda uloží tuto hodnotu jako příznak SE_GROUP_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře. Pokud má tento parametr hodnotu nula, příznak SE_GROUP_DEFAULTED se vymaže.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="setowner"></a>CSecurityDesc::SetOwner

Nastaví informace o vlastníkovi pro popisovač zabezpečení absolutního formátu. Nahrazuje již existující informace o vlastníkovi.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*ID*<br/>
Objekt [CSID](../../atl/reference/csid-class.md) pro nového primárního vlastníka popisovače zabezpečení Tento parametr nesmí mít hodnotu NULL.

*bDefaulted*<br/>
Určuje, zda jsou informace o vlastníkovi odvozeny z výchozího mechanismu. Pokud je tato hodnota true, jedná se o výchozí informace. Metoda uloží tuto hodnotu jako příznak SE_OWNER_DEFAULTED ve `SECURITY_DESCRIPTOR_CONTROL` struktuře. Pokud má tento parametr hodnotu nula, příznak SE_OWNER_DEFAULTED se vymaže.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="setsacl"></a>CSecurityDesc::SetSacl

Nastaví informace v seznamu řízení přístupu (SACL) systému. Pokud je seznam SACL již přítomen v popisovači zabezpečení, je nahrazen.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Parametry

*Seznamy*<br/>
Ukazatel na `CSacl` objekt určující seznam SACL pro popisovač zabezpečení. Tento parametr nesmí mít hodnotu NULL a musí se jednat o objekt CSacl. Na rozdíl od seznamů DACL není rozdíl mezi hodnotou NULL a prázdným SACL, protože objekty SACL neurčují přístupová práva, pouze informace o auditování.

*bDefaulted*<br/>
Určuje příznak označující zdroj seznamu SACL. Pokud má tento příznak hodnotu true, seznam SACL byl načten nějakým výchozím mechanismem. Pokud je hodnota false, seznam SACL byl explicitně zadán uživatelem. Metoda uloží tuto hodnotu do příznaku `SECURITY_DESCRIPTOR_CONTROL` SE_SACL_DEFAULTED struktury. Pokud tento parametr není zadán, příznak SE_SACL_DEFAULTED je vymazán.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

##  <a name="tostring"></a>CSecurityDesc:: ToString

Převede popisovač zabezpečení na formát řetězce.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec zakončený hodnotou null, který získá [popisovač zabezpečení formátu řetězce](/windows/win32/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Určuje kombinaci SECURITY_INFORMATION bitových příznaků, které označují součásti popisovače zabezpečení, které mají být zahrnuty do výstupního řetězce.

### <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.

### <a name="remarks"></a>Poznámky

Jakmile je popisovač zabezpečení ve formátu řetězce, může být snáze uložený nebo přenesený. `CSecurityDesc::FromString` Použijte metodu pro převod řetězce zpět na popisovač zabezpečení.

Parametr *si* může obsahovat následující příznaky SECURITY_INFORMATION:

|Value|Význam|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Zahrňte vlastníka.|
|GROUP_SECURITY_INFORMATION|Zahrňte primární skupinu.|
|DACL_SECURITY_INFORMATION|Zahrňte DACL.|
|SACL_SECURITY_INFORMATION|Zahrňte seznam SACL.|

Pokud je DACL NULL a řídicí bit SE_DACL_PRESENT je nastaven ve vstupní popisovač zabezpečení, metoda se nezdařila.

Pokud je DACL NULL a řídicí bit SE_DACL_PRESENT není nastaven ve vstupním popisovači zabezpečení, výsledný řetězec popisovače zabezpečení nemá komponentu D:. Další podrobnosti najdete v tématu [formát řetězce popisovače zabezpečení](/windows/win32/SecAuthZ/security-descriptor-string-format) .

Tato metoda volá [funkce ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
