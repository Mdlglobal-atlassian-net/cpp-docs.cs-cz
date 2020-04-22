---
title: Třída CregKey
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
ms.openlocfilehash: d3bdb2e7c3ab0ef56ef7f6fba5d43f1ba0bb7fc6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746518"
---
# <a name="cregkey-class"></a>Třída CregKey

Tato třída poskytuje metody pro manipulaci s položkami v systémovém registru.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRegKey
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Konstruktor|
|[CRegKey::~CRegKey](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CregKey::Připojit](#attach)|Volání této metody připojit HKEY `CRegKey` k objektu nastavením `hKey` [popisovače m_hKey](#m_hkey) člen .|
|[CRegKey::Zavřít](#close)|Volání této metody uvolnit [popisovač člena m_hKey](#m_hkey) a nastavte jej na hodnotu NULL.|
|[CRegKey::Vytvořit](#create)|Volání této metody k vytvoření zadaného klíče, pokud neexistuje `hKeyParent`jako podklíč .|
|[CRegKey::DeleteSubKey](#deletesubkey)|Volání této metody odebrat zadaný klíč z registru.|
|[CRegKey::DeleteValue](#deletevalue)|Volání této metody odebrat pole hodnoty z [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Volání této metody odpojit popisovač [m_hKey](#m_hkey) `m_hKey` člena z objektu a nastavte na hodnotu `CRegKey` NULL.|
|[CRegKey::EnumKey](#enumkey)|Volání této metody výčet podklíče otevřeného klíče registru.|
|[CRegKey::Vyprázdnění](#flush)|Volání této metody zapsat všechny atributy otevřeného klíče registru do registru.|
|[CregKey::GetKeySecurity](#getkeysecurity)|Volání této metody načíst kopii popisovače zabezpečení chrání císl.|
|[CregKey::NotifyChangeKey](#notifychangekeyvalue)|Tato metoda upozorní volajícího na změny atributů nebo obsahu otevřeného klíče registru.|
|[CRegKey::Otevřít](#open)|Volání této metody otevřít zadaný klíč a nastavit [m_hKey](#m_hkey) na popisovač tohoto klíče.|
|[CregKey::Hodnota binárního dotazu](#querybinaryvalue)|Volání této metody načíst binární data pro zadaný název hodnoty.|
|[CregKey::QueryDWORDValue](#querydwordvalue)|Volání této metody načíst data DWORD pro zadaný název hodnoty.|
|[Cregkey::QueryGUIDValue](#queryguidvalue)|Volání této metody načíst data GUID pro zadaný název hodnoty.|
|[CregKey::QueryMultiStringValue](#querymultistringvalue)|Volání této metody načíst víceřetězcová data pro zadaný název hodnoty.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Volání této metody načíst data QWORD pro zadaný název hodnoty.|
|[CregKey::Hodnota řetězce dotazu](#querystringvalue)|Volání této metody načíst data řetězce pro zadaný název hodnoty.|
|[CRegKey::Hodnota dotazu](#queryvalue)|Volání této metody k načtení dat pro zadané pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Volání této metody odebrat zadaný klíč z registru a explicitně odebrat všechny podklíče.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Volání této metody nastavit binární hodnotu klíče registru.|
|[CregKey::SetDWORDValue](#setdwordvalue)|Volání této metody nastavit hodnotu DWORD klíče registru.|
|[Cregkey::SetGUIDValue](#setguidvalue)|Volánítéto metody nastavit hodnotu GUID klíče registru.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Volání této metody nastavit zabezpečení klíče registru.|
|[CregKey::SetKeyValue](#setkeyvalue)|Volání této metody k uložení dat v poli zadané hodnoty zadaného klíče.|
|[CregKey::SetMultiStringValue](#setmultistringvalue)|Volání této metody nastavit hodnotu více řetězců klíče registru.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Volání této metody nastavit hodnotu QWORD klíče registru.|
|[CRegKey::SetStringValue](#setstringvalue)|Volání této metody nastavit hodnotu řetězce klíče registru.|
|[CRegKey::SetValue](#setvalue)|Volání této metody k uložení dat v poli zadané hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CRegKey::operátor HKEY](#operator_hkey)|Převede `CRegKey` objekt na HKEY.|
|[CRegKey::operátor =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Obsahuje popisovač klíče registru přidruženého k objektu. `CRegKey`|
|[CRegKey::m_pTM](#m_ptm)|Ukazatel `CAtlTransactionManager` na objekt|

## <a name="remarks"></a>Poznámky

`CRegKey`Poskytuje metody pro vytváření a odstranění klíčů a hodnot v systémovém registru. Registr obsahuje sadu definic pro systémové součásti specifické pro instalaci, jako jsou čísla verzí softwaru, logická a fyzická mapování nainstalovaného hardwaru a objekty modelu COM.

`CRegKey`poskytuje programovací rozhraní do systémového registru pro daný počítač. Chcete-li například otevřít určitý `CRegKey::Open`klíč registru, volejte . Chcete-li načíst nebo `CRegKey::QueryValue` upravit `CRegKey::SetValue`hodnotu dat, volejte nebo , resp. Chcete-li zavřít `CRegKey::Close`klíč, volejte .

Když zavřete klíč, jeho data registru jsou zapsány (vyprázdněny) na pevný disk. Tento proces může trvat několik sekund. Pokud aplikace musí explicitně zapisovat data registru na pevný disk, můžete volat funkci [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32. Však `RegFlushKey` používá mnoho systémových prostředků a by měla být volána pouze v případě, že je to nezbytně nutné.

> [!IMPORTANT]
> Všechny metody, které umožňují volajícímu určit umístění registru mají potenciál číst data, která nelze důvěřovat. Metody, které používají [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) by měl y vzít v úvahu, že tato funkce není explicitně zpracovávat řetězce, které jsou null ukončena. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CregKey::Připojit

Volání této metody připojit HKEY `CRegKey` k objektu nastavením [popisovače m_hKey](#m_hkey) člena *hKey*.

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač klíče registru.

### <a name="remarks"></a>Poznámky

`Attach`bude uplatňovat, pokud `m_hKey` není null.

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey::Zavřít

Volání této metody uvolnit [popisovač člena m_hKey](#m_hkey) a nastavte jej na hodnotu NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě vrátí chybovou hodnotu.

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey::Vytvořit

Volání této metody k vytvoření zadaného klíče, pokud neexistuje jako podklíč *hKeyParent*.

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

*hParent*<br/>
Rukojeť otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*lpszClass*<br/>
Určuje třídu klíče, který má být vytvořen nebo otevřen. Výchozí hodnota je REG_NONE.

*Dwoptions*<br/>
Možnosti pro klíč. Výchozí hodnota je REG_OPTION_NON_VOLATILE. Seznam možných hodnot a popisů naleznete v tématu [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) v sadě Windows SDK.

*samDesired*<br/>
Přístup k zabezpečení klíče. Výchozí hodnota je KEY_READ KEY_WRITE &#124;. Seznam možných hodnot a popisů `RegCreateKeyEx`naleznete v tématu .

*lpSecAttr*<br/>
Ukazatel na [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) struktury, která označuje, zda popisovač klíče může být zděděn podřízeným procesem. Ve výchozím nastavení je tento parametr null (což znamená, že popisovač nelze zdědit).

*lpdwDispozice*<br/>
[out] Pokud není null, načte buď REG_CREATED_NEW_KEY (pokud klíč neexistoval a byl vytvořen) nebo REG_OPENED_EXISTING_KEY (pokud klíč existoval a byl otevřen).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS a otevře klíč. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

`Create`nastaví [člen m_hKey](#m_hkey) na popisovač tohoto klíče.

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey::CRegKey

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

*hKlíč*<br/>
Popisovač klíče registru.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Vytvoří nový `CRegKey` objekt. Objekt lze vytvořit z `CRegKey` existujícího objektu nebo z popisovače do klíče registru.

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey::~CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní `m_hKey`.

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

Volání této metody odebrat zadaný klíč z registru.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszSubKey*<br/>
Určuje název klíče, který chcete odstranit. Tento název musí být podklíč [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

`DeleteSubKey`může odstranit pouze klíč, který nemá žádné podklíče. Pokud klíč má podklíče, volání [RecurseDeleteKey](#recursedeletekey) místo.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::DeleteValue

Volání této metody odebrat pole hodnoty z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*<br/>
Určuje pole hodnoty, které chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::Detach

Volání této metody odpojit popisovač [m_hKey](#m_hkey) `m_hKey` člena z objektu a nastavte na hodnotu `CRegKey` NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

HKEY přidružené k `CRegKey` objektu.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CRegKey::EnumKey

Volání této metody výčet podklíče otevřeného klíče registru.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Index podklíče. Tento parametr by měl být nula pro první volání a potom se zvětší pro následné volání

*pszName*<br/>
Ukazatel na vyrovnávací paměť, která obdrží název podklíče, včetně ukončujícího znaku null. Pouze název podklíče je zkopírován do vyrovnávací paměti, nikoli do úplné hierarchie klíčů.

*pnNameLength*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti určené parametrem *pszName* v TCHAR. Tato velikost by měla obsahovat ukončující znak null. Když metoda vrátí, proměnná na kterou se vztahuje *pnNameLength* obsahuje počet znaků uložených ve vyrovnávací paměti. Vrácený počet nezahrnuje ukončující znak null.

*pftLastWriteTime*<br/>
Ukazatel na proměnnou, která obdrží čas, kdy byl naposledy zapsán podklíč výčtu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit výčet podklíčů, volání `CRegKey::EnumKey` s indexem nula. Zvýšení hodnoty indexu a opakujte, dokud metoda nevrátí ERROR_NO_MORE_ITEMS. Další informace naleznete v tématu [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) v sadě Windows SDK.

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::Vyprázdnění

Volání této metody zapsat všechny atributy otevřeného klíče registru do registru.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) v sadě Windows SDK.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CregKey::GetKeySecurity

Volání této metody načíst kopii popisovače zabezpečení chrání císl.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Hodnota [SECURITY_INFORMATION,](/windows/win32/SecAuthZ/security-information) která označuje požadované informace o zabezpečení.

*Psd*<br/>
Ukazatel na vyrovnávací paměť, která obdrží kopii požadovaného popisovače zabezpečení.

*pnBytes*<br/>
Velikost vyrovnávací paměti v bajtech, na kterou poukazuje *psd*.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby je definován v WINERROR. H.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey::m_hKey

Obsahuje popisovač klíče registru přidruženého k objektu. `CRegKey`

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CregKey::NotifyChangeKey

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
Určuje příznak, který označuje, zda má být vzadaném klíči a všech jeho podklíčích nebo pouze v zadaném klíči nahlásit změny. Pokud je tento parametr TRUE, metoda hlásí změny v klíči a jeho podklíčích. Pokud je parametr NEPRAVDA, metoda hlásí změny pouze v klíči.

*dwNotifyFilter*<br/>
Určuje sadu příznaků, které řídí, které změny by měly být hlášeny. Tento parametr může být kombinací následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Upozornit volajícího, pokud je podklíč přidán nebo odstraněn.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Upozorněte volajícího na změny atributů klíče, jako jsou například informace o popisovači zabezpečení.|
|REG_NOTIFY_CHANGE_LAST_SET|Upozorněte volajícího na změny hodnoty klíče. To může zahrnovat přidání nebo odstranění hodnoty nebo změnu existující hodnoty.|
|REG_NOTIFY_CHANGE_SECURITY|Upozorněte volajícího na změny popisovače zabezpečení klíče.|

*hUdálost*<br/>
Zpracování události. Pokud je parametr *bAsync* TRUE, metoda se okamžitě vrátí a změny jsou hlášeny signalizací této události. Pokud *je bAsync* FALSE, *hEvent* je ignorován.

*bAsync*<br/>
Určuje příznak, který označuje, jak se metoda hlásí. Pokud je tento parametr TRUE, metoda se okamžitě vrátí a hlásí změny signalizací zadané události. Pokud je tento parametr FALSE, metoda se nevrátí, dokud dojde ke změně. Pokud *funkce hEvent* neurčuje platnou událost, parametr *bAsync* nemůže být TRUE.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato metoda neupozorní volajícího, pokud je odstraněn zadaný klíč.

Další podrobnosti a ukázkový program naleznete v tématu [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::Otevřít

Volání této metody otevřít zadaný klíč a nastavit [m_hKey](#m_hkey) na popisovač tohoto klíče.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hParent*<br/>
Rukojeť otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*samDesired*<br/>
Přístup k zabezpečení klíče. Výchozí hodnota je KEY_ALL_ACCESS. Seznam možných hodnot a popisů naleznete v tématu [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulová chybová hodnota definovaná ve winerror. H.

### <a name="remarks"></a>Poznámky

Pokud je parametr *lpszKeyName* null nebo odkazuje `Open` na prázdný řetězec, otevře nový popisovač klíče identifikovaného *hKeyParent*, ale nezavře žádné dříve otevřené popisovač.

Na rozdíl od [CRegKey::Create](#create)nevytvoří `Open` zadaný klíč, pokud neexistuje.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::operátor HKEY

Převede `CRegKey` objekt na HKEY.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::operátor =

Operátor přiřazení.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč ke kopírování.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nový klíč.

### <a name="remarks"></a>Poznámky

Tento operátor odpojí *klíč* od aktuálního objektu `CRegKey` a místo toho jej přiřadí k objektu.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CregKey::Hodnota binárního dotazu

Volání této metody načíst binární data pro zadaný název hodnoty.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*pHodnota*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data hodnoty.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti v bajtech, na kterou odkazuje parametr *pValue.* Když metoda vrátí, tato proměnná obsahuje velikost dat zkopírovaných do vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou typu REG_BINARY, je vrácena ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v [tématu RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CregKey::QueryDWORDValue

Volání této metody načíst data DWORD pro zadaný název hodnoty.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*dwValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá DWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou typu REG_DWORD, je vrácena ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v [tématu RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>Cregkey::QueryGUIDValue

Volání této metody načíst data GUID pro zadaný název hodnoty.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*guidValue*<br/>
Ukazatel na proměnnou, která přijímá identifikátor GUID.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou platným identifikátorem GUID, je vrácen a vrácen a vrácen a ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `CRegKey::QueryStringValue` a převádí řetězec na identifikátor GUID pomocí [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CregKey::QueryMultiStringValue

Volání této metody načíst víceřetězcová data pro zadaný název hodnoty.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*pszValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data s více řetězci. Víceřetězcový řetězec je pole řetězců ukončených hodnotou null, ukončené dvěma prázdnými znaky.

*pnChars*<br/>
Velikost vyrovnávací paměti v TCHAR, na kterou poukazuje *pszValue*. Když metoda *vrátí, pnChars* obsahuje velikost, v TCHARs, víceřetězcové načtené, včetně ukončující znak null.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou typu REG_MULTI_SZ, je vrácena ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v [tématu RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

Volání této metody načíst data QWORD pro zadaný název hodnoty.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*qwValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá QWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou typu REG_QWORD, je vrácena ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v [tématu RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CregKey::Hodnota řetězce dotazu

Volání této metody načíst data řetězce pro zadaný název hodnoty.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu.

*pszValue*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data řetězce.

*pnChars*<br/>
Velikost vyrovnávací paměti v TCHAR, na kterou poukazuje *pszValue*. Když metoda *vrátí, pnChars* obsahuje velikost, v TCHARs, načíst řetězec, včetně ukončující znak null.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, je vrácena ERROR_SUCCESS. Pokud se metodě nepodaří přečíst hodnotu, vrátí nenulový kód chyby definovaný ve winerror. H. Pokud odkazovaná data nejsou typu REG_SZ, je vrácena ERROR_INVALID_DATA. Pokud metoda vrátí ERROR_MORE_DATA, *pnChars* se rovná nule, není požadovaná velikost vyrovnávací paměti v bajtů.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `RegQueryValueEx` a potvrzuje, že je vrácen správný typ dat. Další podrobnosti najdete v [tématu RegQueryValueEx.](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::Hodnota dotazu

Volání této metody k načtení dat pro zadané pole hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

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
Ukazatel na řetězec s ukončeným hodnotou null obsahující název hodnoty dotazu. Pokud *pszValueName* je NULL nebo prázdný řetězec, "", metoda načte typ a data pro nepojmenované klíče nebo výchozí hodnotu, pokud existuje.

*pdwType*<br/>
Ukazatel na proměnnou, která obdrží kód označující typ dat uložených v zadané hodnotě. Parametr *pdwType* může být null, pokud kód typu není vyžadován.

*Pdata*<br/>
Ukazatel na vyrovnávací paměť, která přijímá data hodnoty. Tento parametr může být NULL, pokud data nejsou vyžadována.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost vyrovnávací paměti v bajtech, na kterou odkazuje parametr *pData.* Když metoda vrátí, tato proměnná obsahuje velikost dat zkopírovaných do *pData.*

*dwValue*<br/>
Číselná data pole hodnoty.

*lpszValueName*<br/>
Určuje pole hodnoty, které má být dotazováno.

*szHodnota*<br/>
Řetězcová data pole hodnoty.

*pdwCount*<br/>
Velikost dat řetězce. Jeho hodnota je zpočátku nastavena na velikost vyrovnávací paměti *szValue.*

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Dvě původní verze `QueryValue` programu již nejsou podporovány a jsou označeny jako ATL_DEPRECATED. Kompilátor vydá upozornění, pokud jsou tyto formuláře použity.

Zbývající metoda volá RegQueryValueEx.

> [!IMPORTANT]
> Tato metoda umožňuje volajícímu zadat libovolné umístění registru, potenciálně čtení dat, která nelze důvěřovat. Funkce RegQueryValueEx použitá touto metodou také explicitně nezpracovává řetězce, které jsou ukončeny hodnotou NULL. Obě podmínky by měly být kontrolovány pomocí volajícího kódu.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

Volání této metody odebrat zadaný klíč z registru a explicitně odebrat všechny podklíče.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey*<br/>
Určuje název klíče, který chcete odstranit. Tento název musí být podklíč [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulová chybová hodnota definovaná ve winerror. H.

### <a name="remarks"></a>Poznámky

Pokud klíč má podklíče, musíte volat tuto metodu k odstranění klíče.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

Volání této metody nastavit binární hodnotu klíče registru.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*pHodnota*<br/>
Ukazatel na vyrovnávací paměť obsahující data, která mají být uložena s názvem zadané hodnoty.

*nBajtu bajtů*<br/>
Určuje velikost informací, na které se v bajtech ukazuje parametr *pValue.*

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CregKey::SetDWORDValue

Volání této metody nastavit hodnotu DWORD klíče registru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*dwValue*<br/>
Data DWORD, která mají být uložena s názvem zadané hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>Cregkey::SetGUIDValue

Volánítéto metody nastavit hodnotu GUID klíče registru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*guidValue*<br/>
Odkaz na identifikátor GUID, který má být uložen se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda využívá `CRegKey::SetStringValue` a převádí identifikátor GUID na řetězec pomocí [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CregKey::SetKeyValue

Volání této metody k uložení dat v poli zadané hodnoty zadaného klíče.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč [m_hKey](#m_hkey).

*lpszValue*<br/>
Určuje data, která mají být uložena. Tento parametr musí být non-NULL.

*lpszValueName*<br/>
Určuje pole hodnoty, které má být nastaveno. Pokud pole hodnoty s tímto názvem v klíči ještě neexistuje, bude přidáno.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Volánítéto metody k vytvoření nebo otevření *klávesy lpszKeyName* a uložení dat *lpszValue* do pole hodnoty *lpszValueName.*

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::SetKeySecurity

Volání této metody nastavit zabezpečení klíče registru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Určuje součásti popisovače zabezpečení, které chcete nastavit. Hodnota může být kombinací následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Nastaví volitelný seznam řízení přístupu (DACL) klíče. Klíč musí mít WRITE_DAC přístup, nebo volající proces musí být vlastníkem objektu.|
|GROUP_SECURITY_INFORMATION|Nastaví identifikátor zabezpečení primární skupiny klíče (SID). Klíč musí mít přístup WRITE_OWNER nebo volající proces musí být vlastníkem objektu.|
|OWNER_SECURITY_INFORMATION|Nastaví sid vlastníka klíče. Klíč musí mít WRITE_OWNER přístup nebo volající proces musí být vlastníkem objektu nebo musí mít povoleno oprávnění SE_TAKE_OWNERSHIP_NAME.|
|SACL_SECURITY_INFORMATION|Nastaví seznam řízení přístupu k systému (SACL). Klíč musí mít ACCESS_SYSTEM_SECURITY přístup. Správný způsob, jak získat tento přístup je povolit [SE_SECURITY_NAME oprávnění](/windows/win32/secauthz/privileges) v volajícím aktuální přístupový token, otevřete popisovač pro přístup ACCESS_SYSTEM_SECURITY a potom zakázat oprávnění.|

*Psd*<br/>
Ukazatel na [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) strukturu, která určuje atributy zabezpečení, které mají být nastaveny pro zadaný klíč.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Nastaví atributy zabezpečení klíče. Další podrobnosti naleznete v tématu [RegSetKeySecurity.](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity)

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CregKey::SetMultiStringValue

Volání této metody nastavit hodnotu více řetězců klíče registru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*pszValue*<br/>
Ukazatel na víceřetězcová data, která mají být uložena s názvem zadané hodnoty. Víceřetězcový řetězec je pole řetězců ukončených hodnotou null, ukončené dvěma prázdnými znaky.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::SetQWORDValue

Volání této metody nastavit hodnotu QWORD klíče registru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*qwValue*<br/>
QWORD data, která mají být uložena s názvem zadané hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::SetStringValue

Volání této metody nastavit hodnotu řetězce klíče registru.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není k dispozici, metoda ji přidá ke klíči.

*pszValue*<br/>
Ukazatel na data řetězce, která mají být uložena s názvem zadané hodnoty.

*dwTyp*<br/>
Typ řetězce pro zápis do registru: buď REG_SZ (výchozí) nebo REG_EXPAND_SZ (pro víceřetězcové).

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud se metoda nezdaří, vrácená hodnota je nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) k zápisu hodnoty do registru.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::SetValue

Volání této metody k uložení dat v poli zadané hodnoty [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

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
Ukazatel na řetězec obsahující název hodnoty, která má být nastavena. Pokud hodnota s tímto názvem již není v klíči k dispozici, metoda ji přidá ke klíči. Pokud *pszValueName* je NULL nebo prázdný řetězec, "", metoda nastaví typ a data pro nepojmenované klíče nebo výchozí hodnotu.

*dwTyp*<br/>
Určuje kód označující typ dat, na která se parametr *pValue* ukazuje.

*pHodnota*<br/>
Ukazatel na vyrovnávací paměť obsahující data, která mají být uložena s názvem zadané hodnoty.

*nBajtu bajtů*<br/>
Určuje velikost informací, na které se v bajtech ukazuje parametr *pValue.* Pokud data jsou typu REG_SZ, REG_EXPAND_SZ nebo REG_MULTI_SZ, *nBajty* musí obsahovat velikost ukončujícího znaku null.

*hParent*<br/>
Rukojeť otevřeného klíče.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*lpszValue*<br/>
Určuje data, která mají být uložena. Tento parametr musí být non-NULL.

*lpszValueName*<br/>
Určuje pole hodnoty, které má být nastaveno. Pokud pole hodnoty s tímto názvem v klíči ještě neexistuje, bude přidáno.

*dwValue*<br/>
Určuje data, která mají být uložena.

*bMulti*<br/>
Pokud false, označuje řetězec je typu REG_SZ. Pokud true, označuje řetězec je víceřetězcový typ REG_MULTI_SZ.

*nHodnotaLen*<br/>
Pokud *bMulti* je true, *nValueLen* je délka *lpszValue* řetězec ve znacích. Pokud *bMulti* je false, hodnota -1 označuje, že metoda vypočítá délku automaticky.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový kód chyby definovaný ve winerror. H.

### <a name="remarks"></a>Poznámky

Dvě původní verze `SetValue` programu jsou označeny jako ATL_DEPRECATED a neměly by být používány. Kompilátor vydá upozornění, pokud jsou tyto formuláře použity.

Třetí metoda volá [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Viz také

[Ukázka DCOM](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
