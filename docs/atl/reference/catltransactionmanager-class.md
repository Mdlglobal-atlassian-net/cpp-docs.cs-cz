---
title: "Třída CAtlTransactionManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0def8aa809cd1ccc115ccc2a09b1ae752316098f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager – třída
Třída CAtlTransactionManager poskytuje obálku pro funkce správce KTM (Kernel Transaction).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager destruktor.|  
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zavřete](#close)|Zavře jeden popisovač transakce.|  
|[Potvrzení](#commit)|Počet požadavků, transakce se potvrdí.|  
|[Vytvoření](#create)|Vytvoří popisovač transakce.|  
|[CreateFile](#createfile)|Vytvoří nebo otevře soubor, datový proud souboru nebo adresáři jako zpracovaných operaci.|  
|[DeleteFile](#deletefile)|Odstraní existující soubor jako zpracovaných operaci.|  
|[FindFirstFile](#findfirstfile)|Vyhledá adresář pro soubor nebo podadresáři jako zpracovaných operaci.|  
|[GetFileAttributes](#getfileattributes)|Načte atributy systému souborů pro určený soubor nebo adresář jako zpracovaných operaci.|  
|[GetFileAttributesEx](#getfileattributesex)|Načte atributy systému souborů pro určený soubor nebo adresář jako zpracovaných operaci.|  
|[Gethandle –](#gethandle)|Vrátí popisovač transakce.|  
|[IsFallback](#isfallback)|Určuje, zda je povoleno záložní volání.|  
|[MoveFile](#movefile)|Přesune existující soubor nebo adresář, včetně jeho podřízených položek, jako zpracovaných operaci.|  
|[RegCreateKeyEx](#regcreatekeyex)|Vytvoří zadaný klíč registru a přidruží ji transakce. Pokud klíč již existuje, funkce ho otevře.|  
|[RegDeleteKey](#regdeletekey)|Odstraní podklíč a jeho hodnoty z registru zadané zobrazení specifických pro platformy jako zpracovaných operaci.|  
|[RegOpenKeyEx](#regopenkeyex)|Otevře určený klíč registrů a přidruží ji transakce.|  
|[Vrácení zpět](#rollback)|Požadavky, které transakce vrácena zpět.|  
|[SetFileAttributes](#setfileattributes)|Nastaví atributy souboru nebo adresáři jako zpracovaných operaci.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|`TRUE`Pokud je podporovaná záložní; `FALSE` jinak.|  
|[m_hTransaction](#m_htransaction)|Popisovač transakce.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltransactionmanager.h  
  
##  <a name="dtor"></a>~ CAtlTransactionManager  
 CAtlTransactionManager destruktor.  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Poznámky  
 V normálním zpracování transakce je automaticky potvrzené a uzavřen. Pokud je destruktor je volána v průběhu unwind výjimky, transakce je vrácena zpět a zavřít.  
  
##  <a name="catltransactionmanager"></a>CAtlTransactionManager  
 CAtlTransactionManager konstruktor.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bFallback`  
 `TRUE`Určuje záložní podpory. Pokud zpracovaných funkce selže, třída automaticky volá funkci "beztransakční". `FALSE`označuje žádná "záložní" volání.  
  
 `bAutoCreateTransaction`  
 `TRUE`Určuje, zda obslužná rutina transakce se vytvoří automaticky v konstruktoru. `FALSE`Označuje, že není.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="close"></a>Zavřete  
 Zavře popisovač transakce.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `CloseHandle` funkce. V destruktoru se automaticky zavolá tato metoda.  
  
##  <a name="commit"></a>Potvrzení  
 Počet požadavků, transakce se potvrdí.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `CommitTransaction` funkce. V destruktoru se automaticky zavolá tato metoda.  
  
##  <a name="create"></a>Vytvoření  
 Vytvoří popisovač transakce.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `CreateTransaction` funkce. Zkontrolujte ho pro  
  
##  <a name="createfile"></a>CreateFile  
 Vytvoří nebo otevře soubor, datový proud souboru nebo adresáři jako zpracovaných operaci.  
  
```
inline HANDLE CreateFile(
  LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Název objektu vytvořit nebo otevřít.  
  
 `dwDesiredAccess`  
 Přístup k objektu, který může být shrnuto jako číst, zapisovat, oba, nebo žádný z nich (nula). Nejčastěji používané hodnoty jsou všeobecné_čtení a všeobecné_zápis: všeobecné_čtení &#124; VŠEOBECNÉ_ZÁPIS.  
  
 `dwShareMode`  
 Režim sdílení objektu, který může být číst, zapisovat, obě, odstranit, všechny z nich nebo žádné: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 `lpSecurityAttributes`  
 Ukazatel na strukturu SECURITY_ATTRIBUTES, která obsahuje popisovač volitelné zabezpečení a také určuje, zda může být vrácená popisovač zděděn podřízené procesy. Tento parametr může být `NULL`.  
  
 `dwCreationDisposition`  
 Akci, kterou chcete provést se soubory, které existují a neexistují. Tento parametr musí mít jednu z následujících hodnot, které nelze kombinovat: CREATE_ALWAYS CREATE_NEW, OPEN_ALWAYS OPEN_EXISTING nebo TRUNCATE_EXISTING.  
  
 `dwFlagsAndAttributes`  
 Atributy souboru a značky. Tento parametr může obsahovat libovolnou kombinaci atributů k dispozici soubor (FILE_ATTRIBUTE_ *). Všechny ostatní atributy souboru přepsat FILE_ATTRIBUTE_NORMAL. Tento parametr může také obsahovat kombinace příznaky (FILE_FLAG_\*) pro řízení chování ukládání do vyrovnávací paměti, přístup k režimy a nastavení další příznaky speciální. Tyto se kombinují s žádné FILE_ATTRIBUTE_\* hodnoty.  
  
 `hTemplateFile`  
 Platný popisovač do souboru šablony s právo všeobecné_čtení k přístupu. Soubor šablony poskytuje atributy souboru a rozšířených atributů pro soubor, který je právě vytvářena. Tento parametr může být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač, který slouží pro přístup k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `CreateFileTransacted` funkce.  
  
##  <a name="deletefile"></a>DeleteFile  
 Odstraní existující soubor jako zpracovaných operaci.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Název souboru k odstranění.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `DeleteFileTransacted` funkce.  
  
##  <a name="findfirstfile"></a>FindFirstFile  
 Vyhledá adresář pro soubor nebo podadresáři jako zpracovaných operaci.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Adresář nebo cesta a název souboru pro vyhledávání. Tento parametr může obsahovat zástupné znaky, jako je znak hvězdičky (*) nebo znaky otazníku ().  
  
 `pNextInfo`  
 Ukazatel na strukturu WIN32_FIND_DATA, která přijímá informace týkající se nachází soubor nebo podadresáři.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce úspěšné, je vrácenou hodnotu vyhledávání popisovač použít v následných volání `FindNextFile` nebo `FindClose`. Pokud funkce selže nebo nepodaří najít soubory z řetězec pro hledání v `lpFileName` INVALID_HANDLE_VALUE je parametr, návratovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `FindFirstFileTransacted` funkce.  
  
##  <a name="getfileattributes"></a>GetFileAttributes  
 Načte atributy systému souborů pro určený soubor nebo adresář jako zpracovaných operaci.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Název souboru nebo adresáře.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `GetFileAttributesTransacted` funkce.  
  
##  <a name="getfileattributesex"></a>GetFileAttributesEx  
 Načte atributy systému souborů pro určený soubor nebo adresář jako zpracovaných operaci.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Název souboru nebo adresáře.  
  
 `fInfoLevelId`  
 Úroveň informace o atributu pro načtení.  
  
 `lpFileInformation`  
 Ukazatel na vyrovnávací paměť, která přijímá informace o atributu. Informace o atributu, který je uložen do vyrovnávací paměti pro tento typ je dáno hodnotu `fInfoLevelId`. Pokud `fInfoLevelId` parametr je GetFileExInfoStandard pak tento parametr odkazuje na WIN32_FILE_ATTRIBUTE_DATA struktura.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `GetFileAttributesTransacted` funkce.  
  
##  <a name="gethandle"></a>Gethandle –  
 Vrátí popisovač transakce.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač transakce pro třídu. Vrátí `NULL` Pokud `CAtlTransactionManager` není připojen k popisovač.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isfallback"></a>IsFallback  
 Určuje, zda je povoleno záložní volání.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` je třída podporuje záložní volání. `FALSE`jinak.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bfallback"></a>m_bFallback  
 `TRUE`Pokud je podporovaná záložní; `FALSE` jinak.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_htransaction"></a>m_hTransaction  
 Popisovač transakce.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movefile"></a>MoveFile  
 Přesune existující soubor nebo adresář, včetně jeho podřízených položek, jako zpracovaných operaci.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpOldFileName`  
 Aktuální název existující soubor nebo adresář na místním počítači.  
  
 `lpNewFileName`  
 Nový název pro tento soubor nebo adresář. Tento název nesmí již existuje. Nový soubor může být v jiném souboru systému nebo na jednotce. Nový adresář musí být na stejné jednotce.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `MoveFileTransacted` funkce.  
  
##  <a name="regcreatekeyex"></a>RegCreateKeyEx  
 Vytvoří zadaný klíč registru a přidruží ji transakce. Pokud klíč již existuje, funkce ho otevře.  
  
```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název podklíče, který tuto funkci otevře nebo vytvoří.  
  
 `dwReserved`  
 Tento parametr je vyhrazen a musí být nula.  
  
 `lpClass`  
 Uživatelsky definované třídy tohoto klíče. Tento parametr může být ignorován. Tento parametr může mít hodnotu NULL.  
  
 `dwOptions`  
 Tento parametr může být jedna z následujících hodnot: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE nebo REG_OPTION_VOLATILE.  
  
 `samDesired`  
 Maska, která určuje přístupová práva pro klíč.  
  
 `lpSecurityAttributes`  
 Ukazatel na strukturu SECURITY_ATTRIBUTES, která určuje, zda může být vrácená popisovač zděděn podřízené procesy. Pokud `lpSecurityAttributes` je `NULL`, nemůže být zděděna popisovač.  
  
 `phkResult`  
 Ukazatel na proměnnou, která přijímá popisovač pro otevřenou nebo vytvořený klíč. Pokud klíč není jedním z klíče registru předdefinované, zavolejte `RegCloseKey` funkční i po dokončení použitím popisovače.  
  
 `lpdwDisposition`  
 Ukazatel na proměnné, která přijme některý z následujících hodnot dispozice: REG_CREATED_NEW_KEY nebo REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `RegCreateKeyTransacted` funkce.  
  
##  <a name="regdeletekey"></a>RegDeleteKey  
 Odstraní podklíč a jeho hodnoty z registru zadané zobrazení specifických pro platformy jako zpracovaných operaci.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`hKey`|Popisovač otevřít klíč registru.|  
|`lpSubKey`|Název klíče, který se odstranit.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `RegDeleteKeyTransacted` funkce.  
  
##  <a name="regopenkeyex"></a>RegOpenKeyEx  
 Otevře určený klíč registrů a přidruží ji transakce.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název podklíče registru otevřít.  
  
 `ulOptions`  
 Tento parametr je vyhrazen a musí být nula.  
  
 `samDesired`  
 Maska, která určuje přístupová práva pro klíč.  
  
 `phkResult`  
 Ukazatel na proměnnou, která přijímá popisovač pro otevřenou nebo vytvořený klíč. Pokud klíč není jedním z klíče registru předdefinované, zavolejte `RegCloseKey` funkční i po dokončení použitím popisovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce návratovou hodnotu je definovaný v Winerror.h kód nenulové hodnoty chyby  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `RegOpenKeyTransacted` funkce.  
  
##  <a name="rollback"></a>Vrácení zpět  
 Požadavky, které transakce vrácena zpět.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `RollbackTransaction` funkce.  
  
##  <a name="setfileattributes"></a>SetFileAttributes  
 Nastaví atributy souboru nebo adresáři jako zpracovaných operaci.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Název souboru nebo adresáře.  
  
 `dwAttributes`  
 Atributy souboru pro soubor. Další informace najdete v tématu [SetFileAttributesTransacted](http://go.microsoft.com/fwlink/p/?linkid=158699).  
  
### <a name="remarks"></a>Poznámky  
 Volá tuto obálku `SetFileAttributesTransacted` funkce.  
  
## <a name="see-also"></a>Viz také  
 [Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
