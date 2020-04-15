---
title: Třída CAtlTransactionManager
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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321328"
---
# <a name="catltransactionmanager-class"></a>Třída CAtlTransactionManager

Třída CAtlTransactionManager poskytuje obálku funkcí správce transakcí jádra (KTM).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlTransactionManager;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[~CAtlTransactionManager](#dtor)|Destruktor CAtlTransactionManager.|
|[CAtlTransactionManager](#catltransactionmanager)|Konstruktor CAtlTransactionManager.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zavřít](#close)|Zavře jeden popisovač transakce.|
|[Potvrzení](#commit)|Požaduje, aby transakce potvrzena.|
|[Vytvořit](#create)|Vytvoří popisovač transakce.|
|[Vytvořit soubor](#createfile)|Vytvoří nebo otevře soubor, datový proud souborů nebo adresář jako transakční operaci.|
|[Deletefile](#deletefile)|Odstraní existující soubor jako transakční operaci.|
|[Soubor FindFirst](#findfirstfile)|Vyhledá v adresáři soubor nebo podadresář jako transakční operaci.|
|[Atributy getfile](#getfileattributes)|Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.|
|[GetFileAttributesEx](#getfileattributesex)|Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.|
|[GetHandle](#gethandle)|Vrátí popisovač transakce.|
|[IsFallback](#isfallback)|Určuje, zda jsou povolena záložní volání.|
|[Movefile](#movefile)|Přesune existující soubor nebo adresář, včetně jeho podřízených, jako transakční operaci.|
|[RegCreateKeyEx](#regcreatekeyex)|Vytvoří zadaný klíč registru a přidruží jej k transakci. Pokud klíč již existuje, funkce jej otevře.|
|[RegDeleteKey](#regdeletekey)|Odstraní podklíč a jeho hodnoty ze zadaného zobrazení registru specifického pro platformu jako transakční operaci.|
|[RegOpenKeyEx](#regopenkeyex)|Otevře zadaný klíč registru a přidruží jej k transakci.|
|[Vrácení zpět](#rollback)|Požaduje, aby transakce byla vrácena zpět.|
|[Atributy souboru SetFile](#setfileattributes)|Nastaví atributy souboru nebo adresáře jako transakční operaci.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|PRAVDA, pokud je záloha podporována; FALSE jinak.|
|[m_hTransaction](#m_htransaction)|Popisovač transakce.|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltransactionmanager.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>~CAtlTransactionManager

Destruktor CAtlTransactionManager.

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Poznámky

Při normálním zpracování je transakce automaticky potvrzena a uzavřena. Pokud je destruktor volán během unwind výjimky, transakce je vrácena zpět a uzavřena.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Konstruktor CAtlTransactionManager.

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parametry

*bFallback*<br/>
TRUE označuje podporu záložní. Pokud transakční funkce selže, třída automaticky volá funkci "non-transacted". FALSE označuje žádné "záložní" volání.

*bAutoCreateTransaction*<br/>
TRUE označuje, že obslužná rutina transakce je vytvořena automaticky v konstruktoru. FALSE označuje, že tomu tak není.

### <a name="remarks"></a>Poznámky

## <a name="close"></a><a name="close"></a>Zavřete

Zavře popisovač transakce.

```
inline BOOL Close();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tento obálka `CloseHandle` volá funkci. Metoda je automaticky volána v destruktoru.

## <a name="commit"></a><a name="commit"></a>Spáchat

Požaduje, aby transakce potvrzena.

```
inline BOOL Commit();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tento obálka `CommitTransaction` volá funkci. Metoda je automaticky volána v destruktoru.

## <a name="create"></a><a name="create"></a>Vytvořit

Vytvoří popisovač transakce.

```
inline BOOL Create();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tento obálka `CreateTransaction` volá funkci. Zkontrolujte, zda

## <a name="createfile"></a><a name="createfile"></a>Vytvořit soubor

Vytvoří nebo otevře soubor, datový proud souborů nebo adresář jako transakční operaci.

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

*název lpFileName*<br/>
Název objektu, který má být vytvořen nebo otevřen.

*dwDesiredAccess*<br/>
Přístup k objektu, který lze shrnout jako čtení, zápis, obojí nebo ani jeden (nula). Nejčastěji používané hodnoty jsou GENERIC_READ, GENERIC_WRITE nebo obojí: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
Režim sdílení objektu, který lze číst, psát, oba, odstranit všechny tyto nebo žádné: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Ukazatel na SECURITY_ATTRIBUTES strukturu, která obsahuje volitelný popisovač zabezpečení a také určuje, zda vrácený popisovač může být zděděn podřízenými procesy. Parametr může být NULL.

*dwCreationDispozice*<br/>
Akce, která má být u souborů, které existují a neexistují. Tento parametr musí být jednou z následujících hodnot, které nelze kombinovat: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING nebo TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Atributy souboru a příznaky. Tento parametr může zahrnovat libovolnou kombinaci dostupných atributů souboru (FILE_ATTRIBUTE_*). Všechny ostatní atributy souboru přepíší FILE_ATTRIBUTE_NORMAL. Tento parametr může také obsahovat\*kombinace příznaků (FILE_FLAG_) pro řízení chování ukládání do vyrovnávací paměti, režimy přístupu a další příznaky pro speciální účely. Tyto kombinovat s\* všechny FILE_ATTRIBUTE_ hodnoty.

*hTemplateFile*<br/>
Platný popisovač souboru šablony s GENERIC_READ přístupové právo. Soubor šablony dodává atributy souboru a rozšířené atributy pro soubor, který je vytvářen. Tento parametr může být NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač, který lze použít pro přístup k objektu.

### <a name="remarks"></a>Poznámky

Tento obálka `CreateFileTransacted` volá funkci.

## <a name="deletefile"></a><a name="deletefile"></a>Deletefile

Odstraní existující soubor jako transakční operaci.

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*název lpFileName*<br/>
Název souboru, který má být odstraněn.

### <a name="remarks"></a>Poznámky

Tento obálka `DeleteFileTransacted` volá funkci.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>Soubor FindFirst

Vyhledá v adresáři soubor nebo podadresář jako transakční operaci.

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parametry

*název lpFileName*<br/>
Adresář nebo cesta a název souboru, který chcete vyhledat. Tento parametr může obsahovat zástupné znaky, například hvězdičku (*) nebo otazník ().

*pNextInfo*<br/>
Ukazatel na strukturu WIN32_FIND_DATA, která přijímá informace o nalezeném souboru nebo podadresáři.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je popisovač `FindNextFile` `FindClose`hledání použitý v následnévolání nebo . Pokud funkce selže nebo se nezdaří najít soubory z vyhledávacího řetězce v parametru *lpFileName,* vrátí hodnota je INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Poznámky

Tento obálka `FindFirstFileTransacted` volá funkci.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>Atributy getfile

Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*název lpFileName*<br/>
Název souboru nebo adresáře.

### <a name="remarks"></a>Poznámky

Tento obálka `GetFileAttributesTransacted` volá funkci.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Načte atributy systému souborů pro zadaný soubor nebo adresář jako transakční operaci.

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parametry

*název lpFileName*<br/>
Název souboru nebo adresáře.

*fInfoLevelId*<br/>
Úroveň informace o atributu načíst.

*lpFileInformation*<br/>
Ukazatel na vyrovnávací paměť, která obdrží informace o atributu. Typ informace o atributu, který je uložen do této vyrovnávací paměti je určen hodnotou *fInfoLevelId*. Pokud je parametr *fInfoLevelId* GetFileExInfoStandard, pak tento parametr odkazuje na WIN32_FILE_ATTRIBUTE_DATA strukturu.

### <a name="remarks"></a>Poznámky

Tento obálka `GetFileAttributesTransacted` volá funkci.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle

Vrátí popisovač transakce.

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač transakce pro třídu. Vrátí hodnotu `CAtlTransactionManager` NULL, pokud není připojen k popisovač.

### <a name="remarks"></a>Poznámky

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback

Určuje, zda jsou povolena záložní volání.

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, je třída podporuje záložní volání. FALSE jinak.

### <a name="remarks"></a>Poznámky

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

PRAVDA, pokud je záloha podporována; FALSE jinak.

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Poznámky

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Popisovač transakce.

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Poznámky

## <a name="movefile"></a><a name="movefile"></a>Movefile

Přesune existující soubor nebo adresář, včetně jeho podřízených, jako transakční operaci.

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parametry

*lpOldFileName*<br/>
Aktuální název existujícího souboru nebo adresáře v místním počítači.

*lpNewFileName*<br/>
Nový název souboru nebo adresáře. Tento název již nesmí existovat. Nový soubor může být v jiném systému souborů nebo jednotce. Nový adresář musí být na stejné jednotce.

### <a name="remarks"></a>Poznámky

Tento obálka `MoveFileTransacted` volá funkci.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Vytvoří zadaný klíč registru a přidruží jej k transakci. Pokud klíč již existuje, funkce jej otevře.

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

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název podklíče, který tato funkce otevře nebo vytvoří.

*dwVyhrazeno*<br/>
Tento parametr je vyhrazen a musí být nula.

*lpClass*<br/>
Uživatelem definovaná třída tohoto klíče. Tento parametr může být ignorován. Tento parametr může být NULL.

*Dwoptions*<br/>
Tento parametr může být jedna z následujících hodnot: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE nebo REG_OPTION_VOLATILE.

*samDesired*<br/>
Maska, která určuje přístupová práva pro klíč.

*lpSecurityAttributes*<br/>
Ukazatel na strukturu SECURITY_ATTRIBUTES, která určuje, zda vrácený popisovač může být zděděn podřízenými procesy. Pokud *lpSecurityAttributes* je NULL, popisovač nelze zdědit.

*phkVýsledek*<br/>
Ukazatel na proměnnou, která přijímá popisovač otevřeného nebo vytvořeného klíče. Pokud klíč není jedním z předdefinovaných klíčů `RegCloseKey` registru, zavolejte funkci po dokončení použití popisovače.

*lpdwDispozice*<br/>
Ukazatel na proměnnou, která obdrží jednu z následujících dispozičních hodnot: REG_CREATED_NEW_KEY nebo REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="remarks"></a>Poznámky

Tento obálka `RegCreateKeyTransacted` volá funkci.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Odstraní podklíč a jeho hodnoty ze zadaného zobrazení registru specifického pro platformu jako transakční operaci.

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*hKlíč*|Popisovač otevřeného klíče registru.|
|*lpSubKey*|Název klíče, který má být odstraněn.|

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="remarks"></a>Poznámky

Tento obálka `RegDeleteKeyTransacted` volá funkci.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

Otevře zadaný klíč registru a přidruží jej k transakci.

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název podklíče registru, který má být otevřen.

*ulMožnosti*<br/>
Tento parametr je vyhrazen a musí být nula.

*samDesired*<br/>
Maska, která určuje přístupová práva pro klíč.

*phkVýsledek*<br/>
Ukazatel na proměnnou, která přijímá popisovač otevřeného nebo vytvořeného klíče. Pokud klíč není jedním z předdefinovaných klíčů `RegCloseKey` registru, zavolejte funkci po dokončení použití popisovače.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h

### <a name="remarks"></a>Poznámky

Tento obálka `RegOpenKeyTransacted` volá funkci.

## <a name="rollback"></a><a name="rollback"></a>Vrácení zpět

Požaduje, aby transakce byla vrácena zpět.

```
inline BOOL Rollback();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tento obálka `RollbackTransaction` volá funkci.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>Atributy souboru SetFile

Nastaví atributy souboru nebo adresáře jako transakční operaci.

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parametry

*název lpFileName*<br/>
Název souboru nebo adresáře.

*dwAtributy*<br/>
Atributy souboru, které chcete pro soubor nastavit. Další informace naleznete v [tématu SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Poznámky

Tento obálka `SetFileAttributesTransacted` volá funkci.

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
