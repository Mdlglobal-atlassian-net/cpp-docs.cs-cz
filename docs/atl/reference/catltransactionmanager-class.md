---
title: Catltransactionmanager – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3776f95db1a1e6fad8f885e23bb0dc8836a31ff
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681655"
---
# <a name="catltransactionmanager-class"></a>Catltransactionmanager – třída
Catltransactionmanager – třída poskytuje obálku pro funkce transakcí správce KTM (Kernel).  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ Catltransactionmanager –](#dtor)|Catltransactionmanager – destruktor|  
|[Catltransactionmanager –](#catltransactionmanager)|Catltransactionmanager – konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Zavřít](#close)|Zavře jeden popisovač transakce.|  
|[Potvrzení změn](#commit)|Požadavky, že transakce se potvrzeny.|  
|[Vytvoření](#create)|Vytvoří popisovač transakce.|  
|[CreateFile](#createfile)|Vytvoří a otevře soubor, datový proud souboru nebo adresáři jako Počet zrušených zpracovaných operací.|  
|[DeleteFile](#deletefile)|Odstraní existující soubor jako Počet zrušených zpracovaných operací.|  
|[FindFirstFile](#findfirstfile)|Vyhledá v adresáři souboru nebo podadresáře rámci transakčním režimu operace.|  
|[GetFileAttributes](#getfileattributes)|Získá atributy systému souborů pro určený soubor nebo adresář jako Počet zrušených zpracovaných operací.|  
|[GetFileAttributesEx](#getfileattributesex)|Získá atributy systému souborů pro určený soubor nebo adresář jako Počet zrušených zpracovaných operací.|  
|[Gethandle –](#gethandle)|Vrátí popisovač transakcí.|  
|[IsFallback](#isfallback)|Určuje, zda je povoleno použití náhradní lokality volá.|  
|[MoveFile](#movefile)|Přesune existující soubor nebo adresář, včetně jejích potomků, rámci transakčním režimu operace.|  
|[RegCreateKeyEx](#regcreatekeyex)|Vytvoří zadaného klíče registru a přidruží ji k transakci. Pokud klíč již existuje, funkce otevře.|  
|[RegDeleteKey](#regdeletekey)|Odstraní podklíče a jeho hodnot z registru zadané zobrazení specifické pro platformu rámci transakčním režimu operace.|  
|[Volání RegOpenKeyEx](#regopenkeyex)|Otevře zadaný klíč registru a přidruží ji k transakci.|  
|[Vrácení zpět](#rollback)|Požadavky, které transakce vrácena zpět.|  
|[SetFileAttributes](#setfileattributes)|Nastaví atributy pro soubor nebo adresář jako Počet zrušených zpracovaných operací.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|Hodnota TRUE, pokud se podporuje na náhradní řešení; FALSE v opačném případě.|  
|[m_hTransaction](#m_htransaction)|Popisovač transakce.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltransactionmanager.h  
  
##  <a name="dtor"></a>  ~ Catltransactionmanager –  
 Catltransactionmanager – destruktor  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Poznámky  
 V běžném zpracování transakce je automaticky potvrzené a zavřít. Pokud během unwind výjimek je volán destruktor, transakce je vrácena zpět a zavřít.  
  
##  <a name="catltransactionmanager"></a>  Catltransactionmanager –  
 Catltransactionmanager – konstruktor.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bFallback*  
 Hodnota TRUE označuje podporu použití náhradní lokality. Pokud počet zrušených zpracovaných funkce selže, třída automaticky volá funkci "beztransakční". Hodnota FALSE označuje žádný "základní" volání.  
  
 *bAutoCreateTransaction*  
 Hodnota TRUE označuje, že obslužná rutina transakce se vytvoří automaticky v konstruktoru. Hodnota FALSE označuje, že není.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="close"></a>  Zavřít  
 Uzavře popisovač transakce.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě úspěchu; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `CloseHandle` funkce. V destruktoru je automaticky volána metoda.  
  
##  <a name="commit"></a>  Potvrzení změn  
 Požadavky, že transakce se potvrzeny.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě úspěchu; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `CommitTransaction` funkce. V destruktoru je automaticky volána metoda.  
  
##  <a name="create"></a>  Vytvoření  
 Vytvoří popisovač transakce.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě úspěchu; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `CreateTransaction` funkce. Zkontrolujte ho pro  
  
##  <a name="createfile"></a>  CreateFile  
 Vytvoří a otevře soubor, datový proud souboru nebo adresáři jako Počet zrušených zpracovaných operací.  
  
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
 *lpFileName*  
 Název objektu má být vytvořen nebo otevřen.  
  
 *dwDesiredAccess*  
 Přístup k objektu, který lze shrnout jako čtení, zápis, obou nebo ani jedna (nula). Nejčastěji používanými hodnotami jsou všeobecné_čtení či GENERIC_WRITE: všeobecné_čtení &#124; ke GENERIC_WRITE.  
  
 *dwShareMode*  
 Režim sdílení objektu, který může být čtení, zápisu a obě, odstranění, všechny z nich, nebo žádný: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 *lpSecurityAttributes*  
 Ukazatel na strukturu SECURITY_ATTRIBUTES, která obsahuje popisovač volitelné zabezpečení a také určuje, zda lze Vrácený popisovač Zdědit podřízenými procesy. Tento parametr může mít hodnotu NULL.  
  
 *dwCreationDisposition*  
 Akce na souborech, které existují a neexistují. Tento parametr musí být jedna z následujících hodnot, které nelze kombinovat: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING nebo TRUNCATE_EXISTING.  
  
 *dwFlagsAndAttributes*  
 Atributy souboru a příznaky. Tento parametr může obsahovat libovolnou kombinaci atributů k dispozici souboru (FILE_ATTRIBUTE_ *). Všechny ostatní atributy souboru přepsat FILE_ATTRIBUTE_NORMAL. Tento parametr může obsahovat také kombinace příznaků (FILE_FLAG_\*) pro řízení chování ukládání do vyrovnávací paměti, přístup k režimech a další příznaky zvláštní účely. Tyto se kombinují s jakékoli FILE_ATTRIBUTE_\* hodnoty.  
  
 *hTemplateFile*  
 Platný popisovač do souboru šablony s všeobecné_čtení přístupové právo. Soubor šablony, který poskytuje atributy souboru a rozšířených atributů souboru, který se vytváří. Tento parametr může mít hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač, který slouží pro přístup k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `CreateFileTransacted` funkce.  
  
##  <a name="deletefile"></a>  DeleteFile  
 Odstraní existující soubor jako Počet zrušených zpracovaných operací.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Název souboru, který má být odstraněna.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `DeleteFileTransacted` funkce.  
  
##  <a name="findfirstfile"></a>  FindFirstFile  
 Vyhledá v adresáři souboru nebo podadresáře rámci transakčním režimu operace.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Adresář nebo cesta a název souboru, který chcete vyhledat. Tento parametr může obsahovat zástupné znaky, jako je hvězdička (*) nebo (otazník).  
  
 *pNextInfo*  
 Ukazatel na strukturu WIN32_FIND_DATA, která přijímá informace týkající se nenašel soubor nebo podadresáře.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce uspěje, vrácená hodnota je použít v následných volání hledání popisovač `FindNextFile` nebo `FindClose`. Pokud funkce selže nebo se nezdaří pro nalezení souborů z hledaného řetězce v *lpFileName* INVALID_HANDLE_VALUE je parametr, návratová hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `FindFirstFileTransacted` funkce.  
  
##  <a name="getfileattributes"></a>  GetFileAttributes  
 Získá atributy systému souborů pro určený soubor nebo adresář jako Počet zrušených zpracovaných operací.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Název souboru nebo adresáře.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `GetFileAttributesTransacted` funkce.  
  
##  <a name="getfileattributesex"></a>  GetFileAttributesEx  
 Získá atributy systému souborů pro určený soubor nebo adresář jako Počet zrušených zpracovaných operací.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Název souboru nebo adresáře.  
  
 *fInfoLevelId*  
 Úroveň atribut informace se mají načíst.  
  
 *lpFileInformation*  
 Ukazatel do vyrovnávací paměti, která bude přijímat informace o atributu. Typ atributu informací, které jsou uloženy do této vyrovnávací paměti je určen hodnotou *fInfoLevelId*. Pokud *fInfoLevelId* parametr je GetFileExInfoStandard pak tento parametr odkazuje na strukturu WIN32_FILE_ATTRIBUTE_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `GetFileAttributesTransacted` funkce.  
  
##  <a name="gethandle"></a>  Gethandle –  
 Vrátí popisovač transakcí.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač transakce pro třídu. Vrátí hodnotu NULL, pokud `CAtlTransactionManager` není připojen k popisovač.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isfallback"></a>  IsFallback  
 Určuje, zda je povoleno použití náhradní lokality volá.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, je použití náhradní lokality volá podporuje třídy. FALSE v opačném případě.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bfallback"></a>  m_bFallback  
 Hodnota TRUE, pokud se podporuje na náhradní řešení; FALSE v opačném případě.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_htransaction"></a>  m_hTransaction  
 Popisovač transakce.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="movefile"></a>  MoveFile  
 Přesune existující soubor nebo adresář, včetně jejích potomků, rámci transakčním režimu operace.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpOldFileName*  
 Aktuální název existující soubor nebo adresář v místním počítači.  
  
 *lpNewFileName*  
 Nový název pro soubor nebo adresář. Tento název nesmí existovat. Nový soubor může být na jiný systém souborů nebo disku. Nový adresář musí být na stejné jednotce.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `MoveFileTransacted` funkce.  
  
##  <a name="regcreatekeyex"></a>  RegCreateKeyEx  
 Vytvoří zadaného klíče registru a přidruží ji k transakci. Pokud klíč již existuje, funkce otevře.  
  
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
 *podstrom hKey*  
 Popisovač otevřít klíč registru.  
  
 *lpSubKey*  
 Název, který tato funkce se otevře, nebo vytvoří podklíč.  
  
 *dwReserved*  
 Tento parametr je vyhrazen a musí být nula.  
  
 *lpClass*  
 Uživatelsky definované třídy tohoto klíče. Tento parametr může být ignorován. Tento parametr může mít hodnotu NULL.  
  
 *dwOptions*  
 Tento parametr může být jedna z následujících hodnot: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE nebo REG_OPTION_VOLATILE.  
  
 *samDesired*  
 Maska, která určuje přístupová práva pro klíč.  
  
 *lpSecurityAttributes*  
 Ukazatel na strukturu SECURITY_ATTRIBUTES, která určuje, zda lze Vrácený popisovač Zdědit podřízenými procesy. Pokud *lpSecurityAttributes* má hodnotu NULL, nelze dědit popisovač.  
  
 *phkResult*  
 Ukazovat na proměnnou, která přijímá popisovač klíče otevřená nebo je vytvořený. Pokud klíč není jeden z klíčů registru předdefinované, zavolejte `RegCloseKey` funkční i po dokončení pomocí popisovač.  
  
 *lpdwDisposition*  
 Ukazatel na proměnnou, která přijme některý z následujících hodnot dispozice: REG_CREATED_NEW_KEY nebo REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `RegCreateKeyTransacted` funkce.  
  
##  <a name="regdeletekey"></a>  RegDeleteKey  
 Odstraní podklíče a jeho hodnot z registru zadané zobrazení specifické pro platformu rámci transakčním režimu operace.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*podstrom hKey*|Popisovač otevřít klíč registru.|  
|*lpSubKey*|Název klíče, která se má odstranit.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `RegDeleteKeyTransacted` funkce.  
  
##  <a name="regopenkeyex"></a>  Volání RegOpenKeyEx  
 Otevře zadaný klíč registru a přidruží ji k transakci.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parametry  
 *podstrom hKey*  
 Popisovač otevřít klíč registru.  
  
 *lpSubKey*  
 Název podklíče registru otevřít.  
  
 *ulOptions*  
 Tento parametr je vyhrazen a musí být nula.  
  
 *samDesired*  
 Maska, která určuje přístupová práva pro klíč.  
  
 *phkResult*  
 Ukazovat na proměnnou, která přijímá popisovač klíče otevřená nebo je vytvořený. Pokud klíč není jeden z klíčů registru předdefinované, zavolejte `RegCloseKey` funkční i po dokončení pomocí popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `RegOpenKeyTransacted` funkce.  
  
##  <a name="rollback"></a>  Vrácení zpět  
 Požadavky, které transakce vrácena zpět.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě úspěchu; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `RollbackTransaction` funkce.  
  
##  <a name="setfileattributes"></a>  SetFileAttributes  
 Nastaví atributy pro soubor nebo adresář jako Počet zrušených zpracovaných operací.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Název souboru nebo adresáře.  
  
 *dwAttributes*  
 Atributy souboru, který se mají nastavit pro soubor. Další informace najdete v tématu [SetFileAttributesTransacted](/windows/desktop/api/winbase/nf-winbase-setfileattributestransacteda).  
  
### <a name="remarks"></a>Poznámky  
 Tato Obálka volání `SetFileAttributesTransacted` funkce.  
  
## <a name="see-also"></a>Viz také  
 [Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
