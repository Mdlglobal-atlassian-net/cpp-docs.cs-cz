---
title: "Třída CTokenPrivileges | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
dev_langs: C++
helpviewer_keywords: CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b6a7d1c76b9ddb0aa555e8856f26da99611f553
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges – třída
Tato třída je obálka pro **TOKEN_PRIVILEGES** struktury.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CTokenPrivileges
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Konstruktor|  
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenPrivileges::Add](#add)|Přidá jeden nebo více oprávnění k `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::Delete](#delete)|Odstraní oprávnění z `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::DeleteAll](#deleteall)|Odstraní všechna oprávnění z `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetCount](#getcount)|Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Načte zobrazované názvy pro oprávnění, které jsou součástí `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetLength](#getlength)|Vrátí velikost vyrovnávací paměti v bajtech požadované pro uchovávání **TOKEN_PRIVILEGES** struktura reprezentována `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Načte místně jedinečné identifikátory (LUID) a atribut příznaky z `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Načte názvy oprávnění a atribut příznaky z `CTokenPrivileges` objektu.|  
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Vrátí ukazatel **TOKEN_PRIVILEGES** struktury.|  
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Načte atribut spojený s názvem dané oprávnění.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Vrhá hodnotu na ukazatel **TOKEN_PRIVILEGES** struktury.|  
|[CTokenPrivileges::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 [Přístupový token](http://msdn.microsoft.com/library/windows/desktop/aa374909) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen všem uživatelům přihlášení systému Windows NT nebo Windows 2000.  
  
 Přístupový token se používá k popisu různých udělena všem uživatelům oprávnění zabezpečení. Oprávnění se skládá z 64bitové číslo názvem místně jedinečný identifikátor ( [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)) a řetězce popisovače.  
  
 `CTokenPrivileges` Třída je obálka pro [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury a obsahuje další oprávnění nebo 0. Oprávnění lze přidat, odstraní nebo předmětem dotazu pomocí metody zadané třídy.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="add"></a>CTokenPrivileges::Add  
 Přidá jeden nebo více oprávnění k `CTokenPrivileges` objektu tokenu přístupu.  
  
```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);  
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje název tohoto oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H.  
  
 `bEnable`  
 V případě hodnoty true je oprávnění povoleno. Když má hodnotu false, jsou oprávnění zakázána.  
  
 `rPrivileges`  
 Odkaz na [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury. Oprávnění a atributy zkopírovány z tuto strukturu a přidat do `CTokenPrivileges` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 První formulář tato metoda vrátí hodnotu PRAVDA, pokud je oprávnění úspěšně přidán, false jinak.  
  
##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges  
 Konstruktor  
  
```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );  
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CTokenPrivileges` Objekt, který chcete přiřadit nový objekt.  
  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktura přiřadit nové `CTokenPrivileges` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CTokenPrivileges` Můžete volitelně vytvořit objekt pomocí **TOKEN_PRIVILEGES** struktura nebo dříve definovaném `CTokenPrivileges` objektu.  
  
##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges  
 Destruktor.  
  
```
virtual ~CTokenPrivileges() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru uvolní všechny přidělené prostředky.  
  
##  <a name="delete"></a>CTokenPrivileges::Delete  
 Odstraní oprávnění z `CTokenPrivileges` objektu tokenu přístupu.  
  
```
bool Delete(LPCTSTR pszPrivilege) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje název tohoto oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H. Například může tento parametr zadejte konstanta SE_SECURITY_NAME nebo jeho odpovídající řetězec "SeSecurityPrivilege."  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud oprávnění byla úspěšně odstraněna, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je užitečná jako nástroj pro vytváření tokenů s omezeným přístupem v systému Windows 2000.  
  
##  <a name="deleteall"></a>CTokenPrivileges::DeleteAll  
 Odstraní všechna oprávnění z `CTokenPrivileges` objektu tokenu přístupu.  
  
```
void DeleteAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstraní všechna oprávnění, které jsou součástí `CTokenPrivileges` objektu tokenu přístupu.  
  
##  <a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames  
 Načte zobrazované názvy pro oprávnění, které jsou součástí `CTokenPrivileges` objektu tokenu přístupu.  
  
```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisplayNames`  
 Ukazatel na pole `CString` objekty. **Záznamů CNAME** je definován jako definice typu: **CTokenPrivileges::CAtlArray\<CString >**.  
  
### <a name="remarks"></a>Poznámky  
 Parametr `pDisplayNames` ukazatel na pole `CString` objekty, které obdrží zobrazované názvy odpovídající oprávnění, které jsou součástí `CTokenPrivileges` objektu. Tato metoda načte zobrazované názvy pouze pro zadaný v části oprávnění definovaná WINNT oprávnění. H.  
  
 Tato metoda načte zobrazitelné název: například, pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, zobrazitelné název je "Vynutit vypnutí ze vzdáleného systému." Chcete-li získat název systému, použijte [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).  
  
##  <a name="getcount"></a>CTokenPrivileges::GetCount  
 Vrátí počet položek oprávnění v `CTokenPrivileges` objektu.  
  
```
UINT GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet oprávnění, které jsou součástí `CTokenPrivileges` objektu.  
  
##  <a name="getlength"></a>CTokenPrivileges::GetLength  
 Vrátí délku `CTokenPrivileges` objektu.  
  
```
UINT GetLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet bajtů požadovaných k uložení **TOKEN_PRIVILEGES** struktura reprezentována `CTokenPrivileges` objektu, včetně všech položek oprávnění obsahuje.  
  
##  <a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes  
 Načte místně jedinečné identifikátory (LUID) a atribut příznaky z `CTokenPrivileges` objektu.  
  
```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pPrivileges`  
 Ukazatele na pole [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) objekty. **CLUIDArray** definice typu je definován jako **CAtlArray\<LUID > CLUIDArray**.  
  
 `pAttributes`  
 Ukazatel na pole objektů typu DWORD. Pokud tento parametr vynechán nebo má hodnotu NULL, nejsou načíst atributy. **CAttributes** definice typu je definován jako **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výčet všech oprávnění, které jsou součástí `CTokenPrivileges` přístup k objektu tokenu a umístění jednotlivých LUID a (volitelně) příznaky atribut do pole objektů.  
  
##  <a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes  
 Načte příznaky názvu a podle atributu z `CTokenPrivileges` objektu.  
  
```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pNames*  
 Ukazatele na pole `CString` objekty. **Záznamů CNAME** definice typu je definován jako **CAtlArray \<CString > záznamů CNAME**.  
  
 `pAttributes`  
 Ukazatel na pole objektů typu DWORD. Pokud tento parametr vynechán nebo má hodnotu NULL, nejsou načíst atributy. **CAttributes** definice typu je definován jako **CAtlArray \<DWORD > CAttributes**.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výčet všech oprávnění, které jsou součástí `CTokenPrivileges` objekt, umístění název a (volitelně) příznaky atribut do pole objektů.  
  
 Tato metoda načte název atributu, nikoli název zobrazitelné: například, pokud je název atributu SE_REMOTE_SHUTDOWN_NAME, název systému je "Oprávnění SeRemoteShutdownPrivilege." Chcete-li získat zobrazitelný název, použijte metodu [CTokenPrivileges::GetDisplayNames](#getdisplaynames).  
  
##  <a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES  
 Vrátí ukazatel **TOKEN_PRIVILEGES** struktury.  
  
```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury.  
  
##  <a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege  
 Načte atribut spojený s názvem dané oprávnění.  
  
```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje název tohoto oprávnění, jak jsou definovány v WINNT. Soubor hlaviček H. Například může tento parametr zadejte konstanta SE_SECURITY_NAME nebo jeho odpovídající řetězec "SeSecurityPrivilege."  
  
 `pdwAttributes`  
 Ukazatel na proměnnou, která přijímá atributy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je atribut úspěšně načteny, false jinak.  
  
##  <a name="operator_eq"></a>CTokenPrivileges::operator =  
 Operátor přiřazení.  
  
```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);  
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktura přiřadit `CTokenPrivileges` objektu.  
  
 `rhs`  
 `CTokenPrivileges` Objekt, který chcete přiřadit k objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CTokenPrivileges` objektu.  
  
##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES *  
 Vrhá hodnotu na ukazatel **TOKEN_PRIVILEGES** struktury.  
  
```  
operator const TOKEN_PRIVILEGES *() const throw(...);
```  
  
### <a name="remarks"></a>Poznámky  
 Vrhá hodnotu na ukazatel [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630) struktury.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [TOKEN_PRIVILEGES](http://msdn.microsoft.com/library/windows/desktop/aa379630)   
 [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261)   
 [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
