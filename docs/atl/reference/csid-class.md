---
title: "Identifikační číslo volané stanice třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38c2cff0cb9bd99a70e142d16ee5e7d38e82d8d0
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="csid-class"></a>Identifikační číslo volané stanice – třída
Tato třída je obálka pro `SID` struktury (security identifier).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSid
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CSid::CSidArray](#csidarray)|Pole `CSid` objekty.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSid::CSid](#csid)|Konstruktor|  
|[Identifikační číslo volané stanice:: ~ identifikační číslo volané stanice](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSid::AccountName](#accountname)|Vrací název účet přidružený ke `CSid` objektu.|  
|[CSid::Domain](#domain)|Vrací název domény přidružené k `CSid` objektu.|  
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` předpony (security identifier) rovnosti.|  
|[CSid::GetLength](#getlength)|Vrátí délku `CSid` objektu.|  
|[CSid::GetPSID](#getpsid)|Vrátí ukazatel na `SID` struktury.|  
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Vrátí ukazatel **SID_IDENTIFIER_AUTHORITY** struktury.|  
|[CSid::GetSubAuthority](#getsubauthority)|Vrátí zadaný podautority v **SID** struktura.|  
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Vrátí počet podautority.|  
|[CSid::IsValid](#isvalid)|Testy `CSid` objekt pro platnosti.|  
|[CSid::LoadAccount](#loadaccount)|Aktualizace `CSid` objekt daný název účtu a doménu nebo existující `SID` struktura.|  
|[CSid::Sid](#sid)|Vrátí řetězec ID.|  
|[CSid::SidNameUse](#sidnameuse)|Vrátí popis stavu `CSid` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator_eq)|Operátor přiřazení.|  
|[const SID operátor *](#operator_const_sid__star)|Přetypování `CSid` objekt, který má ukazatel na `SID` struktury.|  
  
### <a name="global-operators"></a>Globální operátory  
  
|||  
|-|-|  
|[Operator ==](#operator_eq_eq)|Testy dva objekty popisovače zabezpečení rovnosti|  
|[Operator! =](#operator_neq)|Testy dva objekty popisovače zabezpečení pro nerovnosti|  
|[operátor\<](#operator_lt_)|Porovná relativní hodnota dva objekty popisovač zabezpečení.|  
|[operátor >](#operator_gt_)|Porovná relativní hodnota dva objekty popisovač zabezpečení.|  
|[operátor\<=](#operator_lt__eq)|Porovná relativní hodnota dva objekty popisovač zabezpečení.|  
|[Operator > =](#operator_gt__eq)|Porovná relativní hodnota dva objekty popisovač zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 `SID` Struktura je struktura proměnlivou délkou použít k jednoznačné identifikaci uživatele nebo skupiny.  
  
 Neměli upravovat aplikace `SID` struktura přímo, ale místo toho použít metody uvedené v této obálkové třídy. Viz také [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), a [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="accountname"></a>CSid::AccountName  
 Vrací název účet přidružený ke `CSid` objektu.  
  
```
LPCTSTR AccountName() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `LPCTSTR` přejdete na název účtu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se pokusí najít název zadaný `SID` (security identifier). Úplné podrobnosti najdete v tématu [funkce LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Pokud žádný název účtu pro `SID` najdete, `AccountName` vrátí prázdný řetězec. Tato situace může nastat, pokud časový limit sítě brání hledání názvu této metody. Může také nastat pro identifikátory zabezpečení bez odpovídající názvu účtu, jako je například přihlášení k `SID` identifikující relace přihlášení.  
  
##  <a name="csid"></a>CSid::CSid  
 Konstruktor  
  
```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 Existující `CSid` objekt nebo `SID` struktury (security identifier).  
  
 *IdentifierAuthority*  
 Oprávnění.  
  
 *nSubAuthorityCount*  
 Počet podautority.  
  
 `pszAccountName`  
 Název účtu.  
  
 `pszSystem`  
 Název systému. Tento řetězec může být název vzdáleného počítače. Pokud tento řetězec hodnotu NULL, použije se místo místního systému.  
  
 `pSid`  
 Ukazatel na `SID` struktury.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor inicializuje `CSid` objektu, nastavení na člena interních datových *SidTypeInvalid*, nebo zkopírováním nastavení z existující `CSid`, `SID`, nebo existující účet.  
  
 Pokud se inicializace nezdaří, vyvolá výjimku konstruktoru [CAtlException třída](../../atl/reference/catlexception-class.md).  
  
##  <a name="dtor"></a>Identifikační číslo volané stanice:: ~ identifikační číslo volané stanice  
 Destruktor.  
  
```
virtual ~CSid() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny prostředky získali objektem.  
  
##  <a name="csidarray"></a>CSid::CSidArray  
 Pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.  
  
```
typedef CAtlArray<CSid> CSidArray;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato typedef Určuje typ pole, které je možné načíst identifikátory zabezpečení z ACL (seznam řízení přístupu). V tématu [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).  
  
##  <a name="domain"></a>CSid::Domain  
 Vrací název domény přidružené k `CSid` objektu.  
  
```
LPCTSTR Domain() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `LPCTSTR` odkazující na doménu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se pokusí najít název zadaný `SID` (security identifier). Úplné podrobnosti najdete v tématu [funkce LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166).  
  
 Pokud žádný název účtu pro `SID` najdete, **domény** vrátí do domény jako prázdný řetězec. Tato situace může nastat, pokud časový limit sítě brání hledání názvu této metody. Může také nastat pro identifikátory zabezpečení bez odpovídající názvu účtu, jako je například přihlášení k `SID` identifikující relace přihlášení.  
  
##  <a name="equalprefix"></a>  CSid::EqualPrefix  
 Testy `SID` předpony (security identifier) rovnosti.  
  
```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `SID` Struktury (security identifier) nebo `CSid` objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěchu **false** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [EqualPrefixSid](http://msdn.microsoft.com/library/windows/desktop/aa446621) ve Windows SDK pro další podrobnosti.  
  
##  <a name="getlength"></a>CSid::GetLength  
 Vrátí délku `CSid` objektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délku v bajtech `CSid` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CSid` struktura není platný, není definován návratovou hodnotu. Před voláním `GetLength`, použijte [CSid::IsValid](#isvalid) – členská funkce ověřit, jestli `CSid` je platný.  
  
> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.  
  
##  <a name="getpsid"></a>CSid::GetPSID  
 Vrátí ukazatel na `SID` struktury (security identifier).  
  
```
const SID* GetPSID() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu `CSid` je základní objekt `SID` struktura.  
  
##  <a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY  
 Vrátí ukazatel **SID_IDENTIFIER_AUTHORITY** struktury.  
  
```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí adresu **SID_IDENTIFIER_AUTHORITY** struktury. Pokud se nezdaří, není definován návratovou hodnotu. Selhání může dojít, pokud `CSid` objekt není platný, v takovém případě [CSid::IsValid](#isvalid) metoda vrátí **false**. Funkce `GetLastError` lze volat pro rozšířené informace o chybě.  
  
> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.  
  
##  <a name="getsubauthority"></a>CSid::GetSubAuthority  
 Vrátí zadaný podautority v `SID` struktury (security identifier).  
  
```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nSubAuthority*  
 Podautority.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí podautority odkazuje *nSubAuthority.* Hodnota podautority je relativních identifikátorů (RID).  
  
### <a name="remarks"></a>Poznámky  
 *NSubAuthority* parametr určuje hodnotu indexu identifikace elementu pole podautority, metoda vrátí. Metoda provádí žádné ověřovací testy na této hodnotě. Aplikace může volat [CSid::GetSubAuthorityCount](#getsubauthoritycount) ke zjištění rozsahu přijatelných hodnot.  
  
> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.  
  
##  <a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount  
 Vrátí počet podautority.  
  
```
UCHAR GetSubAuthorityCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu počtu podautority.  
  
 Pokud metoda selže, není definován návratovou hodnotu. Metoda selže, pokud `CSid` objekt je neplatný. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.  
  
> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.  
  
##  <a name="isvalid"></a>CSid::IsValid  
 Testy `CSid` objekt pro platnosti.  
  
```
bool IsValid() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud `CSid` je objekt platný, **false** není-li. Nejsou žádné podrobné informace o chybě informace pro tuto metodu; Nevolejte `GetLastError`.  
  
### <a name="remarks"></a>Poznámky  
 `IsValid` Metoda ověřuje `CSid` objektu podle ověření, že číslo revize je v rozsahu známé a že počet subauthorities je menší než maximální.  
  
##  <a name="loadaccount"></a>CSid::LoadAccount  
 Aktualizace `CSid` objekt daný název účtu a doménu nebo existující strukturu SID (security identifier).  
  
```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszAccountName`  
 Název účtu.  
  
 `pszSystem`  
 Název systému. Tento řetězec může být název vzdáleného počítače. Pokud tento řetězec hodnotu NULL, použije se místo místního systému.  
  
 `pSid`  
 Ukazatel [SID](http://msdn.microsoft.com/library/windows/desktop/aa379594\(v=vs.85\).aspx) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěchu **false** při selhání. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.  
  
### <a name="remarks"></a>Poznámky  
 `LoadAccount`pokusí se najít identifikátor zabezpečení pro zadaný název. V tématu [funkce LookupAccountSid](http://msdn.microsoft.com/library/windows/desktop/aa379166\(v=vs.85\).aspx) další podrobnosti.  
  
##  <a name="operator_eq"></a>CSid::operator =  
 Operátor přiřazení.  
  
```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` přiřadit `CSid` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizaci `CSid` objektu.  
  
##  <a name="operator_eq_eq"></a>CSid::operator ==  
 Testy dva objekty popisovače zabezpečení z hlediska rovnosti.  
  
```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně == – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně == – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud popisovače zabezpečení jsou stejné, jinak **false**.  
  
##  <a name="operator_neq"></a>CSid::operator! =  
 Testy dva objekty popisovače zabezpečení nerovnost.  
  
```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně! = – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně! = – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud popisovače zabezpečení nejsou stejné, jinak **false**.  
  
##  <a name="operator_lt"></a>CSid::operator&lt;  
 Porovná relativní hodnota dva objekty popisovač zabezpečení.  
  
```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně! = – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně! = – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `lhs` je menší než `rhs`, jinak **false**.  
  
##  <a name="operator_lt__eq"></a>CSid::operator&lt;=  
 Porovná relativní hodnota dva objekty popisovač zabezpečení.  
  
```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně! = – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně! = – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `lhs` je menší než nebo rovno `rhs`, jinak **false**.  
  
##  <a name="operator_gt"></a>CSid::operator&gt;  
 Porovná relativní hodnota dva objekty popisovač zabezpečení.  
  
```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně! = – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně! = – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `lhs` je větší než `rhs`, jinak **false**.  
  
##  <a name="operator_gt__eq"></a>CSid::operator&gt;=  
 Porovná relativní hodnota dva objekty popisovač zabezpečení.  
  
```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na levé straně! = – operátor.  
  
 `rhs`  
 `SID` (Security identifier) nebo `CSid` které se zobrazí na pravé straně! = – operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `lhs` je větší než nebo rovno `rhs`, jinak **false**.  
  
##  <a name="operator_const_sid__star"></a>CSid::operator const SID *  
 Přetypování `CSid` objekt, který má ukazatel na `SID` struktury (security identifier).  
  
```  
operator const SID *() const throw(...);
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí adresu `SID` struktura.  
  
##  <a name="sid"></a>CSid::Sid  
 Vrátí `SID` struktury (security identifier) jako řetězec.  
  
```
LPCTSTR Sid() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `SID` struktura jako řetězec ve formátu, který je vhodný pro zobrazení, úložiště a přenosu. Ekvivalentní [ConvertSidToStringSid](http://msdn.microsoft.com/library/windows/desktop/aa376399).  
  
##  <a name="sidnameuse"></a>CSid::SidNameUse  
 Vrátí popis stavu `CSid` objektu.  
  
```
SID_NAME_USE SidNameUse() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací hodnotu data člena, který ukládá hodnotu popisující stav `CSid` objektu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SidTypeUser|Označuje uživatele `SID` (security identifier).|  
|SidTypeGroup|Určuje skupinu `SID`.|  
|SidTypeDomain|Určuje doménu `SID`.|  
|SidTypeAlias|Označuje alias `SID`.|  
|SidTypeWellKnownGroup|Označuje `SID` pro známá skupina.|  
|SidTypeDeletedAccount|Označuje `SID` odstraněného účtu.|  
|SidTypeInvalid|Určuje neplatnou `SID`.|  
|SidTypeUnknown|Určuje neznámé `SID` typu.|  
|SidTypeComputer|Označuje `SID` pro počítač.|  
  
### <a name="remarks"></a>Poznámky  
 Volání [CSid::LoadAccount](#loadaccount) aktualizovat `CSid` objekt před voláním `SidNameUse` vrátit stav. `SidNameUse`nezmění stav objektu (pomocí volání do **funkce LookupAccountName** nebo **funkce LookupAccountSid**), ale pouze vrací aktuální stav.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)   
 [Operátory](../../atl/reference/atl-operators.md)
