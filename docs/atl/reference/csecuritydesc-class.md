---
title: "Třída CSecurityDesc | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 64f286a02729a5fd39885a449056973381e52611
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="csecuritydesc-class"></a>CSecurityDesc – třída
Tato třída je obálka pro **SECURITY_DESCRIPTOR** struktura.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
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
|[CSecurityDesc::FromString](#fromstring)|Převede popisovač zabezpečení formát řetězce popisovače zabezpečení platné, funkční.|  
|[CSecurityDesc::GetControl](#getcontrol)|Načte řídit informace z popisovač zabezpečení.|  
|[CSecurityDesc::GetDacl](#getdacl)|Načte volitelný řízení přístupu (DACL) seznamu informace z popisovač zabezpečení.|  
|[CSecurityDesc::GetGroup](#getgroup)|Načte informace o primární skupině z popisovač zabezpečení.|  
|[CSecurityDesc::GetOwner](#getowner)|Načte informace vlastníka z popisovač zabezpečení.|  
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Vrátí ukazatel **SECURITY_DESCRIPTOR** struktura.|  
|[CSecurityDesc::GetSacl](#getsacl)|Načte informace o systému řízení přístupu seznam (SACL) z popisovač zabezpečení.|  
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Určuje, pokud je seznam DACL nakonfigurován pro podporu automatického šíření.|  
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Určuje, jestli popisovač zabezpečení je nakonfigurovaná s výchozím DACL.|  
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam DACL.|  
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Určuje, jestli je nakonfigurovaný seznam DACL VBA.|  
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Určuje, pokud se ve výchozím nastavení popisovač zabezpečení skupiny identifikátor zabezpečení (SID).|  
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Určuje, pokud se ve výchozím nastavení SID vlastníka popisovač zabezpečení.|  
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Určuje, jestli SACL je nakonfigurovaná pro podporu automatického šíření.|  
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Určuje, jestli popisovač zabezpečení je nakonfigurovaná s výchozím SACL.|  
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Určuje, zda popisovač zabezpečení obsahuje seznam SACL.|  
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|Určuje, zda SACL je konfigurována pro zabránit úpravy.|  
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Určuje, zda popisovač zabezpečení do seberelativního formátu.|  
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Voláním této metody lze převést popisovač zabezpečení na absolutním formátu.|  
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Voláním této metody se převést popisovač zabezpečení do seberelativního formátu.|  
|[CSecurityDesc::SetControl](#setcontrol)|Nastaví řídicí bity popisovače zabezpečení.|  
|[CSecurityDesc::SetDacl](#setdacl)|Nastaví informace v seznamu DACL. Pokud seznam DACL se již nachází ve popisovač zabezpečení, je nahradit.|  
|[CSecurityDesc::SetGroup](#setgroup)|Nastaví informace o primární skupině absolutním formátu popisovače zabezpečení, nahraďte všechny informace o primární skupině již existuje.|  
|[CSecurityDesc::SetOwner](#setowner)|Nastaví informace vlastníka absolutním formátu popisovače zabezpečení, nahraďte všechny informace vlastníka již existuje.|  
|[CSecurityDesc::SetSacl](#setsacl)|Nastaví informace v seznamu SACL. Pokud seznam SACL se již nachází ve popisovač zabezpečení, je nahradit.|  
|[CSecurityDesc::ToString](#tostring)|Převede na formát řetězce popisovače zabezpečení.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSecurityDesc::operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Vrátí ukazatel **SECURITY_DESCRIPTOR** struktura.|  
|[CSecurityDesc::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 **SECURITY_DESCRIPTOR** struktura obsahuje informace o zabezpečení, které jsou přidružené k objektu. Aplikace použijte tuto strukturu nastavení a dotazovat se stav objektu zabezpečení. Viz také [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).  
  
 Neměli upravovat aplikace **SECURITY_DESCRIPTOR** struktura přímo a místo toho by měl používat metody třídy poskytované.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc  
 Konstruktor  
  
```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );  
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CSecurityDesc` Objekt nebo **SECURITY_DESCRIPTOR** struktura přiřadit nové `CSecurityDesc` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CSecurityDesc` Můžete volitelně vytvořit objekt pomocí **SECURITY_DESCRIPTOR** struktura nebo dříve definovaném `CSecurityDesc` objektu.  
  
##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc  
 Destruktor.  
  
```
virtual ~CSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny přidělené prostředky.  
  
##  <a name="fromstring"></a>CSecurityDesc::FromString  
 Převede popisovač zabezpečení formát řetězce popisovače zabezpečení platné, funkční.  
  
```
bool FromString(LPCTSTR pstr) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje [formát řetězce popisovače zabezpečení](http://msdn.microsoft.com/library/windows/desktop/aa379570) má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA v případě úspěchu. Vyvolá výjimku při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec lze vytvořit pomocí [CSecurityDesc::ToString](#tostring). Převádění na řetězce popisovače zabezpečení usnadňuje ukládání a přenosu.  
  
 Tato metoda volá [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
##  <a name="getcontrol"></a>CSecurityDesc::GetControl  
 Načte řídit informace z popisovač zabezpečení.  
  
```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *psdc*  
 Ukazatel na **SECURITY_DESCRIPTOR_CONTROL** struktura, která přijímá informace o řízení popisovač zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false Pokud selže.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [GetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa446647).  
  
##  <a name="getdacl"></a>  CSecurityDesc::GetDacl  
 Načte volitelný řízení přístupu (DACL) seznamu informace z popisovač zabezpečení.  
  
```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDacl`  
 Ukazatel na `CDacl` strukturu, do které chcete uložit kopii DACL popisovač zabezpečení. Pokud volitelného **seznamu ACL** existuje, nastaví metoda `pDacl` na adresu zabezpečení je volitelný popisovač **seznamu ACL**. Pokud volitelného **seznamu ACL** neexistuje, není uložena žádná hodnota.  
  
 `pbPresent`  
 Ukazatel na hodnotu, která indikuje přítomnost volitelné **seznamu ACL** v Zadaný popisovač zabezpečení. Pokud obsahuje popisovač zabezpečení volitelného **seznamu ACL**, tento parametr je nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje volitelné **seznamu ACL**, tento parametr je nastaven na hodnotu false.  
  
 `pbDefaulted`  
 Ukazatel na příznak nastaven na hodnotu příznak SE_DACL_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury, pokud volitelný **seznamu ACL** existuje pro popisovač zabezpečení. Pokud tento příznak má hodnotu true, volitelný **seznamu ACL** byla načtena výchozího mechanismu; Pokud je hodnota false, volitelný **seznamu ACL** explicitně zadaná uživatelem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false Pokud selže.  
  
##  <a name="getgroup"></a>  CSecurityDesc::GetGroup  
 Načte informace o primární skupině z popisovač zabezpečení.  
  
```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice](../../atl/reference/csid-class.md) (security identifier), obdrží kopii skupině uložené v CDacl.  
  
 `pbDefaulted`  
 Ukazatel na příznak nastaven na hodnotu příznak SE_GROUP_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury po návratu metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false Pokud selže.  
  
##  <a name="getowner"></a>CSecurityDesc::GetOwner  
 Načte informace vlastníka z popisovač zabezpečení.  
  
```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice](../../atl/reference/csid-class.md) (security identifier), obdrží kopii skupině uložené v CDacl.  
  
 `pbDefaulted`  
 Ukazatel na příznak nastaven na hodnotu příznak SE_OWNER_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury po návratu metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false Pokud selže.  
  
##  <a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR  
 Vrátí ukazatel **SECURITY_DESCRIPTOR** struktura.  
  
```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) struktura.  
  
##  <a name="getsacl"></a>CSecurityDesc::GetSacl  
 Načte informace o systému řízení přístupu seznam (SACL) z popisovač zabezpečení.  
  
```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSacl`  
 Ukazatel na `CSacl` strukturu, do které chcete uložit kopii SACL popisovač zabezpečení. Pokud systém **seznamu ACL** existuje, nastaví metoda `pSacl` na adresu popisovač zabezpečení systému **seznamu ACL**. Pokud systém **seznamu ACL** neexistuje, není uložena žádná hodnota.  
  
 `pbPresent`  
 Ukazatel na příznak Nastaví metodu udávající přítomnost systému **seznamu ACL** v Zadaný popisovač zabezpečení. Pokud popisovač zabezpečení obsahuje systém **seznamu ACL**, tento parametr je nastaven na hodnotu true. Pokud popisovač zabezpečení neobsahuje systému **seznamu ACL**, tento parametr je nastaven na hodnotu false.  
  
 `pbDefaulted`  
 Ukazatel na příznak nastaven na hodnotu příznak SE_SACL_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury, pokud systém **seznamu ACL** existuje pro popisovač zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false Pokud selže.  
  
##  <a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited  
 Určuje, zda seznamu volitelného řízení přístupu (DACL) je konfigurována pro podporu automatického šíření.  
  
```
bool IsDaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud popisovač zabezpečení obsahuje seznam DACL, který je nastaven pro podporu automatického propagace položky zděditelné řízení přístupu (ACE) pro stávající podřízený objekt. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Systém nastaví tento bit při provádění algoritmus automatického dědičnosti pro objekt a jeho existující podřízených objektů.  
  
##  <a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted  
 Určuje, pokud popisovač zabezpečení konfigurován s výchozím seznamu volitelného řízení přístupu (DACL).  
  
```
bool IsDaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud popisovač zabezpečení obsahuje výchozí seznam DACL ho ZAMEZUJE, false v opačném případě vrátí hodnotu true.  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak může ovlivnit jak systém zpracovává seznam DACL ho ZAMEZUJE, s ohledem na řízení přístupu (ACE) položka dědičnosti. Například pokud tvůrce objektu neurčuje seznam DACL, objekt přijímá výchozí seznam DACL ho ZAMEZUJE ze nástroj creator přístupový token. Tento příznak systém ignoruje, pokud není nastaven příznak SE_DACL_PRESENT.  
  
 Tento příznak se používá k určení, jak konečné seznam DACL u objektu je počítaný a není fyzicky uložené v ovládacím prvku popisovače zabezpečení zabezpečitelného objektu.  
  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetDacl](#setdacl) metoda.  
  
##  <a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent  
 Určuje, zda popisovač zabezpečení obsahuje seznam volitelného řízení přístupu (DACL).  
  
```
bool IsDaclPresent() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud popisovač zabezpečení obsahuje seznam DACL, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tento příznak není nastavený, nebo pokud je nastavený tento příznak a seznam DACL má hodnotu NULL, popisovač zabezpečení umožňuje úplný přístup ke všem uživatelům.  
  
 Tento příznak se používá k uložení informace o zabezpečení určeného volající, dokud popisovač zabezpečení je přidružen zabezpečitelných objektů. Jakmile popisovač zabezpečení je přidružen zabezpečitelných objektů, je vždycky nastavený příznak SE_DACL_PRESENT v ovládacím prvku popisovač zabezpečení.  
  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetDacl](#setdacl) metoda.  
  
##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected  
 Určuje, zda seznamu volitelného řízení přístupu (DACL) je konfigurována pro zabránit úpravy.  
  
```
bool IsDaclProtected() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud je nakonfigurovaný seznam DACL upravuje v položek zděditelné řízení přístupu (ACE), aby popisovač zabezpečení. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetDacl](#setdacl) metoda.  
  
 Tato metoda podporuje automatické šíření zděditelné položky řízení přístupu.  
  
##  <a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted  
 Určuje, pokud se ve výchozím nastavení popisovač zabezpečení skupiny identifikátor zabezpečení (SID).  
  
```
bool IsGroupDefaulted() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud výchozí mechanismus, nikoli původní zprostředkovatele popisovače zabezpečení Zadaný popisovač zabezpečení skupiny SID. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetGroup](#setgroup) metoda.  
  
##  <a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted  
 Určuje, pokud se ve výchozím nastavení popisovač zabezpečení vlastníka identifikátor zabezpečení (SID).  
  
```
bool IsOwnerDefaulted() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud výchozí mechanismus, nikoli původní zprostředkovatele popisovače zabezpečení SID vlastníka popisovač zabezpečení. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetOwner](#setowner) metoda.  
  
##  <a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited  
 Určuje, pokud systémový seznam řízení přístupu (SACL) je nakonfigurován pro podporu automatického šíření.  
  
```
bool IsSaclAutoInherited() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud popisovač zabezpečení obsahuje seznam SACL, který je nastaven pro podporu automatického propagace položky zděditelné řízení přístupu (ACE) pro stávající podřízený objekt. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Systém nastaví tento bit při provádění algoritmus automatického dědičnosti pro objekt a jeho existující podřízených objektů.  
  
##  <a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted  
 Určuje, pokud popisovač zabezpečení je nakonfigurované výchozím seznamu řízení přístupu systému (SACL).  
  
```
bool IsSaclDefaulted() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud popisovač zabezpečení obsahuje výchozí SACL, false v opačném případě vrátí hodnotu true.  
  
### <a name="remarks"></a>Poznámky  
 Tento příznak může ovlivnit jak systém zpracovává SACL, s ohledem na řízení přístupu (ACE) položka dědičnosti. Tento příznak systém ignoruje, pokud není nastaven příznak SE_SACL_PRESENT.  
  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetSacl](#setsacl) metoda.  
  
##  <a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent  
 Určuje, zda popisovač zabezpečení obsahuje seznam řízení přístupu systému (SACL).  
  
```
bool IsSaclPresent() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud popisovač zabezpečení obsahuje seznam SACL false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetSacl](#setsacl) metoda.  
  
##  <a name="issaclprotected"></a>CSecurityDesc::IsSaclProtected  
 Určuje, pokud systémový seznam řízení přístupu (SACL) je nakonfigurována pro zabránit úpravy.  
  
```
bool IsSaclProtected() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud je nakonfigurovaný SACL upravuje v položek zděditelné řízení přístupu (ACE), aby popisovač zabezpečení. V opačném případě vrátí hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete nastavit tento příznak, použijte [CSecurityDesc::SetSacl](#setsacl) metoda.  
  
 Tato metoda podporuje automatické šíření zděditelné položky řízení přístupu.  
  
##  <a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative  
 Určuje, zda popisovač zabezpečení do seberelativního formátu.  
  
```
bool IsSelfRelative() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud popisovač zabezpečení ve formátu self-relative všechny informace zabezpečení v bloku souvislé paměti. Vrátí hodnotu false, pokud je popisovač zabezpečení v absolutním formátu. Další informace najdete v tématu [absolutní a popisovače zabezpečení Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute  
 Voláním této metody lze převést popisovač zabezpečení na absolutním formátu.  
  
```
bool MakeAbsolute() throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, místo informace samotné. Popisovač zabezpečení ve formátu self-relative obsahuje informace v blok souvislé paměti. V popisovači samorelativní zabezpečení **SECURITY_DESCRIPTOR** struktura vždycky spustí informace, ale popisovač zabezpečení je jiné součásti můžete vycházet ze struktury v libovolném pořadí. Místo použití adresy paměti, jsou součástí popisovač zabezpečení samorelativní identifikovaný posun od začátku popisovač zabezpečení. Tento formát je užitečné, když popisovač zabezpečení musí být uložená na disku nebo odeslány prostřednictvím komunikační protokol. Další informace najdete v tématu [absolutní a popisovače zabezpečení Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative  
 Voláním této metody se převést popisovač zabezpečení do seberelativního formátu.  
  
```
bool MakeSelfRelative() throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud metoda úspěšné, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač zabezpečení v absolutním formátu obsahuje odkazy na informace, které obsahuje, nikoli obsahujícího informace o sám sebe. Popisovač zabezpečení ve formátu self-relative obsahuje informace v blok souvislé paměti. V popisovači samorelativní zabezpečení **SECURITY_DESCRIPTOR** struktura vždycky spustí informace, ale popisovač zabezpečení je jiné součásti můžete vycházet ze struktury v libovolném pořadí. Místo použití adresy paměti, jsou součástí popisovač zabezpečení identifikovaný posun od začátku popisovač zabezpečení. Tento formát je užitečné, když popisovač zabezpečení musí být uložená na disku nebo odeslány prostřednictvím komunikační protokol. Další informace najdete v tématu [absolutní a popisovače zabezpečení Self-Relative](http://msdn.microsoft.com/library/windows/desktop/aa374807).  
  
##  <a name="operator_eq"></a>CSecurityDesc::operator =  
 Operátor přiřazení.  
  
```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);  
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 **SECURITY_DESCRIPTOR** struktura nebo `CSecurityDesc` objekt, který chcete přiřadit `CSecurityDesc` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CSecurityDesc` objektu.  
  
##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc::operator const SECURITY_DESCRIPTOR *  
 Vrhá hodnotu na ukazatel **SECURITY_DESCRIPTOR** struktura.  
  
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
 `ControlBitsOfInterest`  
 A **SECURITY_DESCRIPTOR_CONTROL** maska určující ovládací bity nastavit. Seznam příznaky, které lze nastavit, naleznete v části [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
 `ControlBitsToSet`  
 A `SECURITY_DESCRIPTOR_CONTROL` maska, který označuje nové hodnoty pro službu bits řízení určeného `ControlBitsOfInterest` masky. Tento parametr může být kombinace příznaků pro uvedené `ControlBitsOfInterest` parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [SetSecurityDescriptorControl](http://msdn.microsoft.com/library/windows/desktop/aa379582\(v=vs.85\).aspx).  
  
##  <a name="setdacl"></a>  CSecurityDesc::SetDacl  
 Nastaví informace v seznamu volitelného řízení přístupu (DACL). Pokud seznam DACL se již nachází ve popisovač zabezpečení, je nahradit.  
  
```
inline void SetDacl(  
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(  
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Seznam DACL ho zamezuje*  
 Odkaz na `CDacl` zadání DACL pro popisovač zabezpečení objektu. Tento parametr nesmí mít hodnotu NULL. Pokud chcete nastavit hodnotu NULL DACL v popisovači zabezpečení, musí být první formulář metody použit s `bPresent` nastavena na hodnotu false.  
  
 `bPresent`  
 Určuje příznak, který udává přítomnost DACL v popisovači zabezpečení. Je-li tento parametr hodnotu true, metodu nastavuje příznak SE_DACL_PRESENT **SECURITY_DESCRIPTOR_CONTROL** struktury a používá hodnoty *Dacl* a `bDefaulted` parametry. Pokud je třeba nastavit metodu vymaže příznak SE_DACL_PRESENT a `bDefaulted` je ignorována.  
  
 `bDefaulted`  
 Určuje příznak, který udává zdroj seznam DACL. Je-li tento příznak hodnotu true, má seznam DACL načteny pomocí některé výchozího mechanismu. Když má hodnotu false, seznam DACL byla explicitně zadané uživatelem. Metoda ukládá tato hodnota v příznak SE_DACL_DEFAULTED **SECURITY_DESCRIPTOR_CONTROL** struktury. Pokud není tento parametr zadán, je příznak SE_DACL_DEFAULTED vymazán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Není k dispozici důležitý rozdíl mezi prázdná a neexistující DACL. Pokud seznam DACL je prázdná, neobsahuje žádné položky řízení přístupu a byl výslovně udělen žádné přístupová práva. V důsledku toho je implicitně odepřen přístup k objektu. Objekt se žádný seznam DACL ho ZAMEZUJE, na druhé straně žádná ochrana je přiřazena k objektu, a všechny žádosti o přístup je povolen.  
  
##  <a name="setgroup"></a>  CSecurityDesc::SetGroup  
 Nastaví informace o primární skupině absolutním formátu popisovače zabezpečení, nahraďte všechny informace o primární skupině již existuje.  
  
```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `Sid`  
 Odkaz na [identifikační číslo volané stanice](../../atl/reference/csid-class.md) nové primární skupiny popisovač zabezpečení objektu. Tento parametr nesmí mít hodnotu NULL. Popisovač zabezpečení, může být označen jako nemají seznam DACL nebo seznam SACL, ale musí mít skupina a vlastníka, i ty jsou NULL SID (což je předdefinovaný SID zvláštní význam).  
  
 `bDefaulted`  
 Určuje, zda informace o primární skupině odvozený z výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace a metoda ukládá hodnotu jako příznak SE_GROUP_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury. Pokud má parametr hodnotu nula, je příznak SE_GROUP_DEFAULTED vymazán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="setowner"></a>CSecurityDesc::SetOwner  
 Nastaví vlastníka informací popisovače zabezpečení v absolutním formátu. Nahradí všechny informace vlastníka již existuje.  
  
```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `Sid`  
 [Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekt pro nový primární vlastník popisovač zabezpečení. Tento parametr nesmí mít hodnotu NULL.  
  
 `bDefaulted`  
 Určuje, zda vlastníka informací je odvozené z výchozího mechanismu. Pokud je tato hodnota true, je výchozí informace. Metoda ukládá hodnotu jako příznak SE_OWNER_DEFAULTED v **SECURITY_DESCRIPTOR_CONTROL** struktury. Pokud má parametr hodnotu nula, je příznak SE_OWNER_DEFAULTED vymazán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="setsacl"></a>CSecurityDesc::SetSacl  
 Nastaví informace v seznamu řízení přístupu (SACL) systému. Pokud seznam SACL se již nachází ve popisovač zabezpečení, je nahradit.  
  
```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *Sacl*  
 Ukazatel na `CSacl` zadání SACL pro popisovač zabezpečení objektu. Tento parametr nesmí mít hodnotu NULL a musí být objekt CSacl. Na rozdíl od seznamů DACL není žádný rozdíl mezi hodnotu NULL a prázdný SACL, jako objekty SACL nezadávejte přístupová práva, jenom auditování informace.  
  
 `bDefaulted`  
 Určuje příznak, který udává zdroj SACL. Je-li tento příznak hodnotu true, načtení SACL pomocí některé výchozího mechanismu. Když má hodnotu false, SACL byla explicitně zadané uživatelem. Metoda ukládá tato hodnota v příznak SE_SACL_DEFAULTED **SECURITY_DESCRIPTOR_CONTROL** struktury. Pokud není tento parametr zadán, je příznak SE_SACL_DEFAULTED vymazán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="tostring"></a>CSecurityDesc::ToString  
 Převede na formát řetězce popisovače zabezpečení.  
  
```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Ukazatel na řetězce ukončené hodnotou null, který se zobrazí [formát řetězce popisovače zabezpečení](http://msdn.microsoft.com/library/windows/desktop/aa379570).  
  
 `si`  
 Určuje kombinaci SECURITY_INFORMATION bitové příznaky k označení součásti popisovač zabezpečení, které chcete zahrnout do výstupního řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Jakmile popisovač zabezpečení ve formátu řetězce, může být snadněji uložené či přenášených. Použití `CSecurityDesc::FromString` způsobů, jak převést řetězec zpět do popisovače zabezpečení.  
  
 `si` Parametru může obsahovat následující příznaky SECURITY_INFORMATION:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|OWNER_SECURITY_INFORMATION|Zahrnovat vlastníka.|  
|GROUP_SECURITY_INFORMATION|Zahrnují primární skupinu.|  
|DACL_SECURITY_INFORMATION|Zahrnout seznam DACL.|  
|SACL_SECURITY_INFORMATION|Zahrnout SACL.|  
  
 Pokud seznam DACL je NULL a je v popisovači zabezpečení vstupní nastaven bit Řízení SE_DACL_PRESENT, metoda se nezdaří.  
  
 Pokud seznam DACL má hodnotu NULL a v vstupní popisovač zabezpečení není nastaven bit Řízení SE_DACL_PRESENT, výsledný řetězec popisovač zabezpečení nemá D: součásti. V tématu [formát řetězce popisovače zabezpečení](http://msdn.microsoft.com/library/windows/desktop/aa379570) další podrobnosti.  
  
 Tato metoda volá [ConvertStringSecurityDescriptorToSecurityDescriptor](http://msdn.microsoft.com/library/windows/desktop/aa376401).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
