---
title: CAtlTransactionManager – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 968582feccd8ba9252ca009699eef6eae2c5c3d6
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167822"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager – třída

Třída CAtlTransactionManager poskytuje obálku funkcí KTM (kernel Transaction Manager).

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager destruktor|
|[CAtlTransactionManager](#catltransactionmanager)|Konstruktor CAtlTransactionManager|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Zavřít](#close)|Zavře jeden popisovač transakce.|
|[Potvrzení](#commit)|Požaduje, aby transakce byla potvrzena.|
|[Vytvořit](#create)|Vytvoří popisovač transakce.|
|[CreateFile](#createfile)|Vytvoří nebo otevře soubor, datový proud souboru nebo adresář jako transakční operaci.|
|[DeleteFile](#deletefile)|Odstraní existující soubor jako transakční operaci.|
|[FindFirstFile](#findfirstfile)|Vyhledá v adresáři soubor nebo podadresář jako transakční operaci.|
|[GetFileAttributes](#getfileattributes)|Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.|
|[Chyba funkce GetFileAttributesEx](#getfileattributesex)|Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.|
|[GetHandle –](#gethandle)|Vrátí popisovač transakce.|
|[Fallback](#isfallback)|Určuje, zda jsou povolena náhradní volání.|
|[MoveFile](#movefile)|Přesune existující soubor nebo adresář, včetně jeho podřízených, jako transakční operace.|
|[RegCreateKeyEx](#regcreatekeyex)|Vytvoří zadaný klíč registru a přidruží ho k transakci. Pokud klíč už existuje, funkce ho otevře.|
|[RegDeleteKey](#regdeletekey)|Odstraní podklíč a jeho hodnoty ze zadaného zobrazení registru pro konkrétní platformu jako transakční operace.|
|[Volání RegOpenKeyEx](#regopenkeyex)|Otevře zadaný klíč registru a přidruží ho k transakci.|
|[Návrat](#rollback)|Požaduje vrácení transakce zpět.|
|[SetFileAttributes](#setfileattributes)|Nastaví atributy pro soubor nebo adresář jako transakční operaci.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|TRUE, pokud je podporována záloha; V opačném případě NEPRAVDA.|
|[m_hTransaction](#m_htransaction)|Popisovač transakce.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltransactionmanager. h

## <a name="catltransactionmanager"></a><a name="dtor"></a>~ CAtlTransactionManager

CAtlTransactionManager destruktor

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Poznámky

Při normálním zpracování je transakce automaticky potvrzena a uzavřena. Pokud je destruktor volán během výjimky unwind, transakce je vrácena zpět a zavřena.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Konstruktor CAtlTransactionManager

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parametry

*bFallback*<br/>
Hodnota TRUE označuje záložní podporu. Pokud je funkce transacted neúspěšná, třída automaticky zavolá funkci "non-transactd". Hodnota FALSE neoznačuje žádná záložní volání.

*bAutoCreateTransaction*<br/>
Hodnota TRUE označuje, že je obslužná rutina transakce vytvořena automaticky v konstruktoru. Hodnota FALSE znamená, že není.

### <a name="remarks"></a>Poznámky

## <a name="close"></a><a name="close"></a>Uzavírací

Zavře popisovač transakce.

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato obálka volá `CloseHandle` funkci. Metoda je automaticky volána v destruktoru.

## <a name="commit"></a><a name="commit"></a>Potvrzuj

Požaduje, aby transakce byla potvrzena.

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato obálka volá `CommitTransaction` funkci. Metoda je automaticky volána v destruktoru.

## <a name="create"></a><a name="create"></a>Vytvořeny

Vytvoří popisovač transakce.

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato obálka volá `CreateTransaction` funkci. Ověřit pro

## <a name="createfile"></a><a name="createfile"></a>CreateFile

Vytvoří nebo otevře soubor, datový proud souboru nebo adresář jako transakční operaci.

```cpp
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

*lpFileName*<br/>
Název objektu, který má být vytvořen nebo otevřen.

*dwDesiredAccess*<br/>
Přístup k objektu, který může být shrnut jako čtení, zápis, obojí nebo ani (nula). Nejčastěji používané hodnoty jsou GENERIC_READ, GENERIC_WRITE nebo obojí: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
Režim sdílení objektu, který lze číst, zapisovat, obojí, odstranit, všechny tyto nebo žádné: 0, FILE_SHARE_DELETE FILE_SHARE_READ FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Ukazatel na SECURITY_ATTRIBUTES strukturu, která obsahuje volitelný popisovač zabezpečení a také určuje, zda lze vrácený popisovač dědit pomocí podřízených procesů. Parametr může mít hodnotu NULL.

*dwCreationDisposition*<br/>
Akce, která se má provést u souborů, které existují a neexistují. Tento parametr musí být jedna z následujících hodnot, které nelze kombinovat: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING nebo TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Atributy souboru a příznaky. Tento parametr může obsahovat libovolnou kombinaci dostupných atributů souboru (FILE_ATTRIBUTE_ *). Všechny ostatní atributy souboru přepíšou FILE_ATTRIBUTE_NORMAL. Tento parametr může také obsahovat kombinace příznaků (FILE_FLAG_\*) pro řízení chování ukládání do vyrovnávací paměti, režimy přístupu a další příznaky pro zvláštní účely. Tyto hodnoty jsou kombinovány\* s libovolnými FILE_ATTRIBUTE_ hodnotami.

*hTemplateFile*<br/>
Platný popisovač souboru šablony s přístupem GENERIC_READ práva. Soubor šablony poskytuje atributy souboru a rozšířené atributy pro soubor, který se vytváří. Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač, který lze použít pro přístup k objektu.

### <a name="remarks"></a>Poznámky

Tato obálka volá `CreateFileTransacted` funkci.

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile

Odstraní existující soubor jako transakční operaci.

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Název souboru, který se má odstranit

### <a name="remarks"></a>Poznámky

Tato obálka volá `DeleteFileTransacted` funkci.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

Vyhledá v adresáři soubor nebo podadresář jako transakční operaci.

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Adresář nebo cesta a název souboru, který chcete vyhledat. Tento parametr může obsahovat zástupné znaky, jako je například hvězdička (*) nebo otazník ().

*pNextInfo*<br/>
Ukazatel na strukturu WIN32_FIND_DATA, která přijímá informace o nalezeném souboru nebo podadresáři.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je popisovač hledání používaný při následném volání `FindNextFile` nebo. `FindClose` Pokud dojde k chybě nebo pokud funkce nenajde soubory z hledaného řetězce v parametru *lpFileName* , návratová hodnota je INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Poznámky

Tato obálka volá `FindFirstFileTransacted` funkci.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Název souboru nebo adresáře.

### <a name="remarks"></a>Poznámky

Tato obálka volá `GetFileAttributesTransacted` funkci.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>Chyba funkce GetFileAttributesEx

Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Název souboru nebo adresáře.

*fInfoLevelId*<br/>
Úroveň informací atributu, které mají být načteny.

*lpFileInformation*<br/>
Ukazatel na vyrovnávací paměť, která obdrží informace o atributu. Typ informací o atributu, který je uložen do této vyrovnávací paměti, je určen hodnotou *fInfoLevelId*. Pokud je parametr *FInfoLevelId* GetFileExInfoStandard, pak tento parametr odkazuje na strukturu WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Poznámky

Tato obálka volá `GetFileAttributesTransacted` funkci.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle –

Vrátí popisovač transakce.

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač transakce pro třídu. Vrátí hodnotu NULL, `CAtlTransactionManager` Pokud není připojena k popisovači.

### <a name="remarks"></a>Poznámky

## <a name="isfallback"></a><a name="isfallback"></a>Fallback

Určuje, zda jsou povolena náhradní volání.

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud třída podporuje náhradní volání. V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

TRUE, pokud je podporována záloha; V opačném případě NEPRAVDA.

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>Poznámky

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Popisovač transakce.

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Poznámky

## <a name="movefile"></a><a name="movefile"></a>MoveFile

Přesune existující soubor nebo adresář, včetně jeho podřízených, jako transakční operace.

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parametry

*lpOldFileName*<br/>
Aktuální název existujícího souboru nebo adresáře v místním počítači.

*lpNewFileName*<br/>
Nový název souboru nebo adresáře. Tento název již nesmí existovat. Nový soubor může být na jiném systému souborů nebo jednotce. Nový adresář musí být na stejné jednotce.

### <a name="remarks"></a>Poznámky

Tato obálka volá `MoveFileTransacted` funkci.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Vytvoří zadaný klíč registru a přidruží ho k transakci. Pokud klíč už existuje, funkce ho otevře.

```cpp
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

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název podklíče, který tato funkce otevře nebo vytvoří.

*dwReserved*<br/>
Tento parametr je rezervovaný a musí být nula.

*lpClass*<br/>
Uživatelsky definovaná třída tohoto klíče. Tento parametr může být ignorován. Tento parametr může mít hodnotu NULL.

*dwOptions*<br/>
Tento parametr může být jedna z následujících hodnot: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE nebo REG_OPTION_VOLATILE.

*samDesired*<br/>
Maska, která určuje přístupová práva pro klíč.

*lpSecurityAttributes*<br/>
Ukazatel na strukturu SECURITY_ATTRIBUTES, která určuje, zda vrácený popisovač mohou být děděny podřízenými procesy. Pokud má *lpSecurityAttributes* hodnotu null, nelze popisovač dědit.

*phkResult*<br/>
Ukazatel na proměnnou, která přijímá popisovač pro otevřený nebo vytvořený klíč. Pokud klíč není jedním z předdefinovaných klíčů registru, zavolejte `RegCloseKey` funkci po dokončení používání popisovače.

*lpdwDisposition*<br/>
Ukazatel na proměnnou, která přijímá jednu z následujících hodnot Disposition: REG_CREATED_NEW_KEY nebo REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="remarks"></a>Poznámky

Tato obálka volá `RegCreateKeyTransacted` funkci.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Odstraní podklíč a jeho hodnoty ze zadaného zobrazení registru pro konkrétní platformu jako transakční operace.

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*hKey*|Popisovač pro otevřený klíč registru.|
|*lpSubKey*|Název klíče, který se má odstranit|

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="remarks"></a>Poznámky

Tato obálka volá `RegDeleteKeyTransacted` funkci.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>Volání RegOpenKeyEx

Otevře zadaný klíč registru a přidruží ho k transakci.

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název podklíče registru, který se má otevřít

*ulOptions*<br/>
Tento parametr je rezervovaný a musí být nula.

*samDesired*<br/>
Maska, která určuje přístupová práva pro klíč.

*phkResult*<br/>
Ukazatel na proměnnou, která přijímá popisovač pro otevřený nebo vytvořený klíč. Pokud klíč není jedním z předdefinovaných klíčů registru, zavolejte `RegCloseKey` funkci po dokončení používání popisovače.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se funkce nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WinError. h

### <a name="remarks"></a>Poznámky

Tato obálka volá `RegOpenKeyTransacted` funkci.

## <a name="rollback"></a><a name="rollback"></a>Návrat

Požaduje vrácení transakce zpět.

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato obálka volá `RollbackTransaction` funkci.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

Nastaví atributy pro soubor nebo adresář jako transakční operaci.

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Název souboru nebo adresáře.

*dwAttributes*<br/>
Atributy souboru, které mají být nastaveny pro daný soubor. Další informace najdete v tématu [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Poznámky

Tato obálka volá `SetFileAttributesTransacted` funkci.

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
