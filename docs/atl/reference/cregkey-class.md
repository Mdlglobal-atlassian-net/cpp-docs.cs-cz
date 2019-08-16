---
title: CRegKey – třída
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: 3faf446f74577034a3d0676b90ebe7027ef6da06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496539"
---
# <a name="cregkey-class"></a>CRegKey – třída

Tato třída poskytuje metody pro manipulaci s položkami v systémovém registru.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRegKey
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Konstruktor|
|[CRegKey::~CRegKey](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRegKey::Attach](#attach)|Voláním této metody připojte k `CRegKey` objektu objekt HKEY nastavením popisovače členů [m_hKey](#m_hkey) na `hKey`hodnotu.|
|[CRegKey:: Close](#close)|Voláním této metody uvolníte členský popisovač [m_hKey](#m_hkey) a nastavíte jej na hodnotu null.|
|[CRegKey::Create](#create)|Voláním této metody vytvoříte zadaný klíč, pokud neexistuje jako podklíč `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Voláním této metody odeberete zadaný klíč z registru.|
|[CRegKey::DeleteValue](#deletevalue)|Voláním této metody odeberete pole hodnoty z [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Voláním této metody odpojíte [m_hKey](#m_hkey) členský popisovač od `CRegKey` objektu a nastavíte `m_hKey` hodnotu null.|
|[CRegKey:: EnumKey](#enumkey)|Voláním této metody můžete vytvořit výčet podklíčů pro otevřený klíč registru.|
|[CRegKey:: flush](#flush)|Voláním této metody zapíšete všechny atributy otevřeného klíče registru do registru.|
|[CRegKey:: GetKeySecurity](#getkeysecurity)|Voláním této metody načtěte kopii popisovače zabezpečení, který chrání otevřený klíč registru.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Tato metoda upozorní volajícího na změny atributů nebo obsahu otevřeného klíče registru.|
|[CRegKey::Open](#open)|Voláním této metody otevřete zadaný klíč a nastavte [m_hKey](#m_hkey) na popisovač tohoto klíče.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Voláním této metody načtete binární data pro zadaný název hodnoty.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Voláním této metody načtete data DWORD pro zadaný název hodnoty.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Voláním této metody načtete data GUID pro zadaný název hodnoty.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Voláním této metody načtete data s více řetězci pro zadaný název hodnoty.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Voláním této metody načtete data QWORD pro zadaný název hodnoty.|
|[CRegKey::QueryStringValue](#querystringvalue)|Voláním této metody načtete data řetězce pro zadaný název hodnoty.|
|[CRegKey::QueryValue](#queryvalue)|Voláním této metody načtete data pro zadané pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Voláním této metody odeberete zadaný klíč z registru a explicitně odeberete všechny podklíče.|
|[CRegKey:: SetBinaryValue](#setbinaryvalue)|Voláním této metody nastavíte binární hodnotu klíče registru.|
|[CRegKey:: SetDWORDValue](#setdwordvalue)|Voláním této metody nastavíte hodnotu DWORD klíče registru.|
|[CRegKey:: SetGUIDValue](#setguidvalue)|Voláním této metody nastavíte hodnotu identifikátoru GUID klíče registru.|
|[CRegKey:: SetKeySecurity](#setkeysecurity)|Voláním této metody nastavíte zabezpečení klíče registru.|
|[CRegKey:: SetKeyValue](#setkeyvalue)|Voláním této metody uložíte data do zadaného pole hodnoty zadaného klíče.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Voláním této metody nastavíte hodnotu pro více řetězců klíče registru.|
|[CRegKey:: SetQWORDValue](#setqwordvalue)|Voláním této metody nastavíte hodnotu QWORD klíče registru.|
|[CRegKey::SetStringValue](#setstringvalue)|Voláním této metody nastavíte hodnotu řetězce klíče registru.|
|[CRegKey:: SetValue](#setvalue)|Voláním této metody uložíte data do zadaného pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|`CRegKey` Převede objekt na HKEY.|
|[CRegKey:: operator =](#operator_eq)|Operátor přiřazení|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Obsahuje popisovač klíče registru přidruženého `CRegKey` k objektu.|
|[CRegKey::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objekt|

## <a name="remarks"></a>Poznámky

`CRegKey`poskytuje metody pro vytváření a odstraňování klíčů a hodnot v registru systému. Registr obsahuje sadu definicí pro součásti systému specifické pro instalaci, například čísla verzí softwaru, mapování nainstalovanáho hardwaru a objekty COM.

`CRegKey`poskytuje programovací rozhraní k systémovému registru pro daný počítač. Chcete-li například otevřít konkrétní klíč registru, zavolejte `CRegKey::Open`. Chcete-li načíst nebo upravit datovou hodnotu `CRegKey::QueryValue` , `CRegKey::SetValue`zavolejte nebo v uvedeném pořadí. Chcete-li zavřít klíč, `CRegKey::Close`zavolejte.

Když klíč zavřete, data registru se zapisují (vyprázdní) na pevný disk. Tento proces může trvat několik sekund. Pokud vaše aplikace musí explicitně zapisovat data registru na pevný disk, můžete zavolat funkci [funkce RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32. Nástroj ale `RegFlushKey` používá mnoho systémových prostředků a měl by se volat jenom v případě, že je nezbytný.

> [!IMPORTANT]
>  Jakékoli metody, které umožňují volajícímu určit umístění v registru, mohou číst data, která nelze důvěřovat. Metody, které používají [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) , by měly vzít v úvahu, že tato funkce explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="attach"></a>CRegKey:: Attach

Voláním této metody připojte k `CRegKey` objektu objekt HKEY nastavením popisovače členské [m_hKey](#m_hkey) na hodnotu *HKEY*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač klíče registru.

### <a name="remarks"></a>Poznámky

`Attach`vyhodnotí `m_hKey` , pokud je hodnota jiná než null.

##  <a name="close"></a>CRegKey:: Close

Voláním této metody uvolníte členský popisovač [m_hKey](#m_hkey) a nastavíte jej na hodnotu null.

```
LONG Close() throw();
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě vrátí chybovou hodnotu.

##  <a name="create"></a>CRegKey:: Create

Voláním této metody vytvoříte zadaný klíč, pokud neexistuje jako podklíč pro *hKeyParent*.

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*<br/>
Popisovač otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíčem *hKeyParent*.

*lpszClass*<br/>
Určuje třídu klíče, který má být vytvořen nebo otevřen. Výchozí hodnota je REG_NONE.

*dwOptions*<br/>
Možnosti pro klíč Výchozí hodnota je REG_OPTION_NON_VOLATILE. Seznam možných hodnot a popisů naleznete v tématu [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) v Windows SDK.

*samDesired*<br/>
Přístup k zabezpečení klíče Výchozí hodnota je KEY_READ &#124; KEY_WRITE. Seznam možných hodnot a popisů naleznete v tématu `RegCreateKeyEx`.

*lpSecAttr*<br/>
Ukazatel na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která označuje, zda může být popisovač klíče zděděn podřízeným procesem. Ve výchozím nastavení má tento parametr hodnotu NULL (což znamená, že popisovač Nelze zdědit).

*lpdwDisposition*<br/>
mimo Pokud hodnota není NULL, načte buď REG_CREATED_NEW_KEY (Pokud klíč neexistoval a byl vytvořen), nebo REG_OPENED_EXISTING_KEY (Pokud klíč existoval a byl otevřen).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS a otevře klíč. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

`Create`Nastaví člena [m_hKey](#m_hkey) na popisovač tohoto klíče.

##  <a name="cregkey"></a>CRegKey:: CRegKey

Konstruktor

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Odkaz na `CRegKey` objekt.

*hKey*<br/>
Popisovač klíče registru.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Vytvoří nový `CRegKey` objekt. Objekt lze vytvořit z existujícího `CRegKey` objektu nebo z popisovače na klíč registru.

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Poznámky

Verze `m_hKey`destruktoru.

##  <a name="deletesubkey"></a>CRegKey::D eleteSubKey

Voláním této metody odeberete zadaný klíč z registru.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszSubKey*<br/>
Určuje název klíče, který se má odstranit. Tento název musí být podklíčem [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

`DeleteSubKey`klíč, který nemá žádné podklíče, lze odstranit pouze. Pokud má klíč podklíče, zavolejte místo toho [RecurseDeleteKey](#recursedeletekey) .

##  <a name="deletevalue"></a>CRegKey::D eleteValue

Voláním této metody odeberete pole hodnoty z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*<br/>
Určuje pole hodnoty, které se má odebrat.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

##  <a name="detach"></a>CRegKey::D etach

Voláním této metody odpojíte [m_hKey](#m_hkey) členský popisovač od `CRegKey` objektu a nastavíte `m_hKey` hodnotu null.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

HKEY přidružený `CRegKey` k objektu

##  <a name="enumkey"></a>CRegKey:: EnumKey

Voláním této metody můžete vytvořit výčet podklíčů pro otevřený klíč registru.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index podklíče. Tento parametr by měl být pro první volání nulový a následně zvýšen pro následná volání.

*pszName*<br/>
Ukazatel na vyrovnávací paměť, která přijímá název podklíče, včetně ukončujícího znaku null. Do vyrovnávací paměti se zkopíruje pouze název podklíče, nikoli úplná hierarchie klíčů.

*pnNameLength*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti určené parametrem *pszName* v TCHARs. Tato velikost by měla zahrnovat ukončující znak null. Když se metoda vrátí, proměnná, na kterou odkazuje *pnNameLength* , obsahuje počet znaků uložených ve vyrovnávací paměti. Vrácený počet nezahrnuje ukončující znak null.

*pftLastWriteTime*<br/>
Ukazatel na proměnnou, která přijímá čas posledního zápisu podklíče do výčtu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit výčet podklíčů, zavolejte `CRegKey::EnumKey` s indexem nula. Zvyšte hodnotu indexu a opakujte akci, dokud metoda nevrátí ERROR_NO_MORE_ITEMS. Další informace najdete v tématu [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) v Windows SDK.

##  <a name="flush"></a>CRegKey:: flush

Voláním této metody zapíšete všechny atributy otevřeného klíče registru do registru.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) v Windows SDK.

##  <a name="getkeysecurity"></a>CRegKey:: GetKeySecurity

Voláním této metody načtěte kopii popisovače zabezpečení, který chrání otevřený klíč registru.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Hodnota [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) , která označuje požadované informace o zabezpečení.

*psd*<br/>
Ukazatel na vyrovnávací paměť, která obdrží kopii požadovaného popisovače zabezpečení.

*pnBytes*<br/>
Velikost vyrovnávací paměti v bajtech, na kterou ukazuje *PSD*.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby je definován v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Obsahuje popisovač klíče registru přidruženého `CRegKey` k objektu.

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="notifychangekeyvalue"></a>CRegKey:: NotifyChangeKeyValue

Tato metoda upozorní volajícího na změny atributů nebo obsahu otevřeného klíče registru.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bWatchSubtree*<br/>
Určuje příznak, který označuje, zda se mají hlásit změny v zadaném klíči a všech jeho podklíčích, nebo pouze v zadaném klíči. Pokud má tento parametr hodnotu TRUE, metoda nahlásí změny v klíči a jejích podklíčích. Pokud má parametr hodnotu FALSE, metoda hlásí změny pouze v klíči.

*dwNotifyFilter*<br/>
Určuje sadu příznaků, které řídí, které změny mají být hlášeny. Tento parametr může být kombinací následujících hodnot:

|Value|Význam|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Upozorní volajícího, že se přidal nebo odstranil nějaký podklíč.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Upozorněte volající změny atributů klíče, jako je například informace popisovače zabezpečení.|
|REG_NOTIFY_CHANGE_LAST_SET|Upozorněte volající změny hodnoty klíče. To může zahrnovat přidání nebo odstranění hodnoty nebo změna existující hodnoty.|
|REG_NOTIFY_CHANGE_SECURITY|Upozorněte volající změny v popisovači zabezpečení klíče.|

*hEvent*<br/>
Zpracování události. Pokud má parametr *bAsync* hodnotu true, metoda se okamžitě vrátí a změny se oznamují signalizací této události. Pokud má *bAsync* hodnotu false, *hEvent* se ignoruje.

*bAsync*<br/>
Určuje příznak, který označuje, jak metoda hlásí změny. Pokud je tento parametr TRUE, metoda vrátí okamžitě a ohlásí změny tím, že signalizuje určenou událost. Pokud je tento parametr FALSE, metoda nevrátí, dokud nedošlo ke změně. Pokud *hEvent* neurčuje platnou událost, parametr *bAsync* nemůže mít hodnotu true.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato metoda neupozorní volajícího, pokud je zadaný klíč odstraněný.

Další podrobnosti a ukázkový program najdete v tématu [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>CRegKey:: Open

Voláním této metody otevřete zadaný klíč a nastavte [m_hKey](#m_hkey) na popisovač tohoto klíče.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*<br/>
Popisovač otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíčem *hKeyParent*.

*samDesired*<br/>
Přístup k zabezpečení klíče Výchozí hodnota je KEY_ALL_ACCESS. Seznam možných hodnot a popisů naleznete v tématu [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě je v WINERROR definována nenulová hodnota chyby. Y.

### <a name="remarks"></a>Poznámky

Pokud má parametr *lpszKeyName* hodnotu null nebo odkazuje na prázdný řetězec, `Open` otevře se nový popisovač klíče identifikovaného *hKeyParent*, ale nezavře žádný dříve otevřený popisovač.

Na rozdíl od [CRegKey:: Create](#create)nebude zadaný klíč vytvořen, `Open` Pokud neexistuje.

##  <a name="operator_hkey"></a>CRegKey:: operator HKEY

`CRegKey` Převede objekt na HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: operator =

Operátor přiřazení

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč ke zkopírování.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nový klíč.

### <a name="remarks"></a>Poznámky

Tento operátor odpojí *klíč* od aktuálního objektu a místo toho jej `CRegKey` přiřadí objektu.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Voláním této metody načtete binární data pro zadaný název hodnoty.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*pValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data hodnoty.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti v bajtech, na kterou ukazuje parametr *pValue* . Když metoda vrátí, tato proměnná obsahuje velikost kopírovaných dat do vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud odkazovaná data nejsou typu REG_BINARY, vrátí ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v tématu [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

Voláním této metody načtete data DWORD pro zadaný název hodnoty.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*dwValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá hodnotu DWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud se na odkazovaná data nejedná o typ REG_DWORD, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v tématu [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Voláním této metody načtete data GUID pro zadaný název hodnoty.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*guidValue*<br/>
Ukazatel na proměnnou, která přijímá identifikátor GUID.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud se odkazovaná data nejedná o platný identifikátor GUID, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `CRegKey::QueryStringValue` a převádí řetězec na identifikátor GUID pomocí [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Voláním této metody načtete data s více řetězci pro zadaný název hodnoty.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*pszValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data s více řetězci. Více řetězců je pole řetězců ukončených hodnotou null, ukončené dvěma znaky null.

*pnChars*<br/>
Velikost vyrovnávací paměti v TCHARs, na kterou ukazuje *pszValue*. Když se metoda vrátí, *pnChars* obsahuje velikost v TCHARs načteného řetězce, včetně ukončujícího znaku null.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud se na odkazovaná data nejedná o typ REG_MULTI_SZ, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v tématu [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Voláním této metody načtete data QWORD pro zadaný název hodnoty.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*qwValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá hodnotu QWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud se odkazuje na data typu REG_QWORD, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v tématu [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

Voláním této metody načtete data řetězce pro zadaný název hodnoty.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování.

*pszValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá řetězcová data.

*pnChars*<br/>
Velikost vyrovnávací paměti v TCHARs, na kterou ukazuje *pszValue*. Když metoda vrátí, *pnChars* obsahuje velikost, která je v TCHARs načteného řetězce, včetně ukončujícího znaku null.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nedokáže načíst hodnotu, vrátí nenulový kód chyby definovaný v WINERROR. Y. Pokud odkazovaná data nejsou typu REG_SZ, vrátí se ERROR_INVALID_DATA. Pokud metoda vrátí ERROR_MORE_DATA, *pnChars* se rovná nule, nikoli požadovaná velikost vyrovnávací paměti v bajtech.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v tématu [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce [volání RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou null. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Voláním této metody načtete data pro zadané pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty k dotazování. Pokud má *pszValueName* hodnotu null nebo prázdný řetězec, "", metoda načte typ a data pro nepojmenované nebo výchozí hodnotu klíče, pokud existuje.

*pdwType*<br/>
Ukazatel na proměnnou, která přijímá kód označující typ dat uložených v zadané hodnotě. Parametr *pdwType* může mít hodnotu null, pokud není požadován kód typu.

*pData*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data hodnoty. Tento parametr může mít hodnotu NULL, pokud nejsou požadovaná data.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti v bajtech, na kterou ukazuje parametr *PDATA* . Když metoda vrátí, tato proměnná obsahuje velikost kopírovaných dat do *PDATA.*

*dwValue*<br/>
Číselná data pole hodnoty.

*lpszValueName*<br/>
Určuje pole hodnoty, které se má dotazovat.

*szValue*<br/>
Řetězcová data pole hodnoty.

*pdwCount*<br/>
Velikost řetězcových dat. Jeho hodnota je zpočátku nastavená na velikost *szValue* vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tyto dvě původní verze `QueryValue` nástroje již nejsou podporovány a jsou označeny jako ATL_DEPRECATED. Kompilátor vydá upozornění, pokud jsou použity tyto formuláře.

Zbývající metoda volá volání RegQueryValueEx.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu určit libovolné umístění v registru a potenciálně číst data, která nelze důvěřovat. Také funkce volání RegQueryValueEx používaná touto metodou explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být zkontrolovány volajícím kódem.

##  <a name="recursedeletekey"></a>CRegKey:: RecurseDeleteKey

Voláním této metody odeberete zadaný klíč z registru a explicitně odeberete všechny podklíče.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey*<br/>
Určuje název klíče, který se má odstranit. Tento název musí být podklíčem [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě je v WINERROR definována nenulová hodnota chyby. Y.

### <a name="remarks"></a>Poznámky

Pokud má klíč podklíče, je nutné zavolat tuto metodu, abyste klíč odstranili.

##  <a name="setbinaryvalue"></a>CRegKey:: SetBinaryValue

Voláním této metody nastavíte binární hodnotu klíče registru.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pValue*<br/>
Ukazatel na vyrovnávací paměť obsahující data, která mají být uložena se zadaným názvem hodnoty.

*nBytes*<br/>
Určuje velikost informací, na které odkazuje parametr *pValue* , v bajtech.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

##  <a name="setdwordvalue"></a>CRegKey:: SetDWORDValue

Voláním této metody nastavíte hodnotu DWORD klíče registru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*dwValue*<br/>
Data typu DWORD, která mají být uložena se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

##  <a name="setguidvalue"></a>CRegKey:: SetGUIDValue

Voláním této metody nastavíte hodnotu identifikátoru GUID klíče registru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*guidValue*<br/>
Odkaz na identifikátor GUID, který se má uložit se zadaným názvem hodnoty

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `CRegKey::SetStringValue` a převádí identifikátor GUID na řetězec pomocí [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>CRegKey:: SetKeyValue

Voláním této metody uložíte data do zadaného pole hodnoty zadaného klíče.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíčem [m_hKey](#m_hkey).

*lpszValue*<br/>
Určuje data, která mají být uložena. Tento parametr nesmí mít hodnotu NULL.

*lpszValueName*<br/>
Určuje pole hodnoty, které se má nastavit. Pokud pole hodnota s tímto názvem ještě v klíči neexistuje, přidá se.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Voláním této metody vytvoříte nebo otevřete klíč *lpszKeyName* a uložíte data *lpszValue* do pole hodnota *lpszValueName* .

##  <a name="setkeysecurity"></a>CRegKey:: SetKeySecurity

Voláním této metody nastavíte zabezpečení klíče registru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Určuje součásti popisovače zabezpečení, které se mají nastavit. Hodnota může být kombinací následujících hodnot:

|Value|Význam|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Nastaví volitelný seznam řízení přístupu (DACL) klíče. Klíč musí mít přístup WRITE_DAC nebo volající proces musí být vlastníkem objektu.|
|GROUP_SECURITY_INFORMATION|Nastaví identifikátor zabezpečení primární skupiny (SID) klíče. Klíč musí mít přístup WRITE_OWNER nebo volající proces musí být vlastníkem objektu.|
|OWNER_SECURITY_INFORMATION|Nastaví identifikátor SID vlastníka klíče. Klíč musí mít přístup WRITE_OWNER nebo volající proces musí být vlastníkem objektu nebo musí mít povolené oprávnění SE_TAKE_OWNERSHIP_NAME.|
|SACL_SECURITY_INFORMATION|Nastaví seznam řízení přístupu (SACL) systému klíče. Klíč musí mít přístup ACCESS_SYSTEM_SECURITY. Správným způsobem, jak tento přístup získat, je povolit [oprávnění](/windows/win32/secauthz/privileges) SE_SECURITY_NAME v aktuálním přístupovém tokenu volajícího, otevřít popisovač pro ACCESS_SYSTEM_SECURITY přístup a pak toto oprávnění zakázat.|

*psd*<br/>
Ukazatel na strukturu [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) , která určuje atributy zabezpečení, které se mají nastavit pro zadaný klíč.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Nastaví atributy zabezpečení klíče. Další podrobnosti najdete v tématu [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) .

##  <a name="setmultistringvalue"></a>CRegKey:: SetMultiStringValue

Voláním této metody nastavíte hodnotu pro více řetězců klíče registru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pszValue*<br/>
Ukazatel na data s více řetězci, který se má uložit se zadaným názvem hodnoty. Více řetězců je pole řetězců ukončených hodnotou null, ukončené dvěma znaky null.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

##  <a name="setqwordvalue"></a>CRegKey:: SetQWORDValue

Voláním této metody nastavíte hodnotu QWORD klíče registru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*qwValue*<br/>
Data QWORD se budou ukládat se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

##  <a name="setstringvalue"></a>CRegKey:: SetStringValue

Voláním této metody nastavíte hodnotu řetězce klíče registru.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pszValue*<br/>
Ukazatel na data řetězce, která se mají uložit se zadaným názvem hodnoty.

*dwType*<br/>
Typ řetězce pro zápis do registru: buď REG_SZ (výchozí) nebo REG_EXPAND_SZ (pro více řetězců).

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud se metoda nezdařila, vrácená hodnota je nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

##  <a name="setvalue"></a>CRegKey:: SetValue

Voláním této metody uložíte data do zadaného pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, kterou chcete nastavit. Pokud hodnota s tímto názvem není v klíči již přítomna, metoda ji přidá do klíče. Pokud má *pszValueName* hodnotu null nebo prázdný řetězec, "", metoda nastaví typ a data pro nepojmenované nebo výchozí hodnoty klíče.

*dwType*<br/>
Určuje kód, který označuje typ dat, na které odkazuje parametr *pValue* .

*pValue*<br/>
Ukazatel na vyrovnávací paměť obsahující data, která mají být uložena se zadaným názvem hodnoty.

*nBytes*<br/>
Určuje velikost informací, na které odkazuje parametr *pValue* , v bajtech. Pokud jsou data typu REG_SZ, REG_EXPAND_SZ nebo REG_MULTI_SZ, *nBytes* musí zahrnovat velikost ukončujícího znaku null.

*hKeyParent*<br/>
Popisovač otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíčem *hKeyParent*.

*lpszValue*<br/>
Určuje data, která mají být uložena. Tento parametr nesmí mít hodnotu NULL.

*lpszValueName*<br/>
Určuje pole hodnoty, které se má nastavit. Pokud pole hodnota s tímto názvem ještě v klíči neexistuje, přidá se.

*dwValue*<br/>
Určuje data, která mají být uložena.

*bMulti*<br/>
Pokud je hodnota false, označuje, že řetězec je typu REG_SZ. Pokud je nastaveno na true, označuje, že řetězec je s více řetězci typu REG_MULTI_SZ.

*nValueLen*<br/>
Pokud má *bMulti* hodnotu true, *nValueLen* je délka řetězce *lpszValue* ve znacích. Pokud je *bMulti* false, hodnota-1 označuje, že metoda bude automaticky počítat délku.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný v WINERROR. Y.

### <a name="remarks"></a>Poznámky

Dvě původní verze `SetValue` nástroje jsou označeny jako ATL_DEPRECATED a neměly by se již používat. Kompilátor vydá upozornění, pokud jsou použity tyto formuláře.

Třetí metoda volá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Viz také:

[Ukázka modelu DCOM](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
