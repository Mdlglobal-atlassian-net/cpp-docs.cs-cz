---
title: Cregkey – třída
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
ms.openlocfilehash: 1215c66f1f40cfbc96b813d4eb5084f07698bc01
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778296"
---
# <a name="cregkey-class"></a>Cregkey – třída

Tato třída poskytuje metody pro práci s položkami v systémovém registru.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CRegKey::Attach](#attach)|Volejte tuto metodu za účelem připojení HKEY k `CRegKey` objektu tak, že nastavíte [m_hKey](#m_hkey) popisovač člena `hKey`.|
|[CRegKey::Close](#close)|Volejte tuto metodu za účelem uvolnění [m_hKey](#m_hkey) člen zpracování a nastavte ho na hodnotu NULL.|
|[CRegKey::Create](#create)|Volejte tuto metodu za účelem vytvoření se zadaným klíčem, pokud neexistuje jako podklíč `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Voláním této metody lze odebrat z registru se zadaným klíčem.|
|[CRegKey::DeleteValue](#deletevalue)|Voláním této metody lze odebrat pole hodnoty z [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Volejte tuto metodu za účelem odpojení [m_hKey](#m_hkey) popisovač člena z `CRegKey` objektu a nastavte `m_hKey` na hodnotu NULL.|
|[CRegKey::EnumKey](#enumkey)|Voláním této metody lze vytvořit výčet podklíčů klíče otevřít registr.|
|[CRegKey::Flush](#flush)|Volání této metody zapsat všechny atributy otevřít klíč registru do registru.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Voláním této metody lze načíst kopii popisovače zabezpečení, ochrana otevřít klíč registru.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Tato metoda upozorní volající o změnách atributy nebo obsah otevřít klíč registru.|
|[CRegKey::Open](#open)|Volejte tuto metodu za účelem otevření zadaného klíče a nastavte [m_hKey](#m_hkey) ke zpracování tohoto klíče.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Voláním této metody lze načíst binární data pro zadanou hodnotu názvu.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Volejte tuto metodu za účelem získání dat DWORD zadaná hodnota názvu.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Volejte tuto metodu za účelem načtení dat identifikátoru GUID pro zadanou hodnotu názvu.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Volejte tuto metodu za účelem získání nahrazován dat pro zadanou hodnotu názvu.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Volejte tuto metodu za účelem načtení dat QWORD zadanou hodnotu názvu.|
|[CRegKey::QueryStringValue](#querystringvalue)|Volejte tuto metodu za účelem načtení dat řetězce pro název zadanou hodnotu.|
|[CRegKey::QueryValue](#queryvalue)|Voláním této metody lze načíst data pro zadanou hodnotu pole [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Voláním této metody lze odebrat z registru se zadaným klíčem a explicitně odstraňte všechny podklíče.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Voláním této metody lze nastavit binární hodnotu klíče registru.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Voláním této metody nastavte hodnotu DWORD klíče registru.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Voláním této metody lze nastavit hodnotu GUID klíče registru.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Volejte tuto metodu za účelem nastavení zabezpečení klíče registru.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Volejte tuto metodu za účelem ukládání dat v zadané hodnotě pole zadaný klíč.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Voláním této metody lze nastavit nahrazován hodnotu klíče registru.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Voláním této metody lze nastavit hodnota QWORD klíče registru.|
|[CRegKey::SetStringValue](#setstringvalue)|Voláním této metody nastavte hodnotu řetězce klíče registru.|
|[CRegKey::SetValue](#setvalue)|Volejte tuto metodu za účelem ukládání dat v poli zadanou hodnotu [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|Převede `CRegKey` objekt HKEY.|
|[CRegKey::operator =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Obsahuje popisovač klíče registru přidružené `CRegKey` objektu.|
|[CRegKey::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu|

## <a name="remarks"></a>Poznámky

`CRegKey` poskytuje metody pro vytváření a odstraňování klíčů a hodnot v registru systému. Registr obsahuje instalace konkrétní sadu definic pro součásti systému, jako je například čísla verzí softwaru, mapování logické fyzické nainstalovaných hardwaru a modelu COM objekty.

`CRegKey` poskytuje programovací rozhraní do systémového registru pro daný počítač. Například chcete-li otevřít klíč registru konkrétní volání `CRegKey::Open`. Chcete-li načíst nebo upravit datovou hodnotu, zavolejte `CRegKey::QueryValue` nebo `CRegKey::SetValue`v uvedeném pořadí. Klíč uzavřete volání `CRegKey::Close`.

Při zavření klíče registru data je zápis na pevný disk. Tento proces může trvat několik sekund. Pokud vaše aplikace musí explicitně zapisují data registru na pevný disk, můžete volat [funkce RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) funkci Win32. Ale `RegFlushKey` používá mnoho systémových prostředků a by měla být volána pouze v případě, že je nezbytně nutné.

> [!IMPORTANT]
>  Všechny metody, které umožňují volajícímu zadat umístění registru mohly načíst data, která nemůže být důvěryhodný. Metody, které usnadňují používání [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) brát v úvahu, že tato funkce nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="attach"></a>  CRegKey::Attach

Volejte tuto metodu za účelem připojení HKEY k `CRegKey` objektu tak, že nastavíte [m_hKey](#m_hkey) popisovač člena *hKey*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač klíče registru.

### <a name="remarks"></a>Poznámky

`Attach` Pokud vyhodnocena `m_hKey` je jiná než NULL.

##  <a name="close"></a>  CRegKey::Close

Volejte tuto metodu za účelem uvolnění [m_hKey](#m_hkey) člen zpracování a nastavte ho na hodnotu NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě vrátí chybovou hodnotu.

##  <a name="create"></a>  CRegKey::Create

Volejte tuto metodu za účelem vytvoření se zadaným klíčem, pokud neexistuje jako podklíč *hKeyParent*.

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
Popisovač otevřít klíč.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*lpszClass*<br/>
Určuje třídu klíč, který má být vytvořen nebo otevřen. Výchozí hodnota je REG_NONE.

*dwOptions*<br/>
Možnosti pro klíč. Výchozí hodnota je REG_OPTION_NON_VOLATILE. Seznam možných hodnot a popisy najdete v tématu [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) v sadě Windows SDK.

*samDesired*<br/>
Zabezpečený přístup ke klíči. Výchozí hodnota je KEY_READ &#124; KEY_WRITE. Seznam možných hodnot a popisy najdete v tématu `RegCreateKeyEx`.

*lpSecAttr*<br/>
Ukazatel [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která označuje, zda popisovač klíče mohou být zděděny podřízený proces. Ve výchozím nastavení tento parametr hodnotu NULL (tj. nemůže být zděděn popisovač).

*lpdwDisposition*<br/>
[out] Pokud není NULL, načte REG_CREATED_NEW_KEY (Pokud klíč neexistuje a vytvořila) nebo REG_OPENED_EXISTING_KEY (Pokud klíč existuje a byl otevřen).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS a otevře klíč. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

`Create` Nastaví [m_hKey](#m_hkey) člen ke zpracování tohoto klíče.

##  <a name="cregkey"></a>  CRegKey::CRegKey

Konstruktor

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Odkaz na `CRegKey` objektu.

*hKey*<br/>
Popisovač klíče registru.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Vytvoří novou `CRegKey` objektu. Objekt můžete vytvořit ze stávajícího `CRegKey` objektu, nebo z popisovač klíče registru.

##  <a name="dtor"></a>  CRegKey::~CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Poznámky

Verze destruktor `m_hKey`.

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

Voláním této metody lze odebrat z registru se zadaným klíčem.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszSubKey*<br/>
Určuje název klíče odstranit. Tento název musí být podklíč [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

`DeleteSubKey` můžete odstranit pouze klíč, který nemá žádné podklíče. Pokud klíč má podklíčích, zavolejte [RecurseDeleteKey](#recursedeletekey) místo.

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

Voláním této metody lze odebrat pole hodnoty z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*<br/>
Určuje hodnotu pole odebrat.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

##  <a name="detach"></a>  CRegKey::Detach

Volejte tuto metodu za účelem odpojení [m_hKey](#m_hkey) popisovač člena z `CRegKey` objektu a nastavte `m_hKey` na hodnotu NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nastavení HKEY přidružené `CRegKey` objektu.

##  <a name="enumkey"></a>  CRegKey::EnumKey

Voláním této metody lze vytvořit výčet podklíčů klíče otevřít registr.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Podklíč indexu. Tento parametr musí být nula první volání a poté zvýšen pro pozdější volání

*pszName*<br/>
Ukazatel do vyrovnávací paměti, která přijímá název podklíče, včetně ukončujícího znaku null. Pouze název podklíče zkopírován do vyrovnávací paměti, ne celý klíč hierarchie.

*pnNameLength*<br/>
Ukazatel na proměnnou, která určuje velikost v TCHARs vyrovnávací paměti určené *pszName* parametru. Tato velikost by měla obsahovat ukončujícího znaku null. Když metoda vrátí, proměnné, na které odkazuje *pnNameLength* obsahuje počet znaků, které jsou uloženy ve vyrovnávací paměti. Vrátí počet nezahrnuje ukončující znak null.

*pftLastWriteTime*<br/>
Ukazovat na proměnnou, která přijímá čas Výčtový podklíč posledního zápisu do.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit výčet podklíčů, zavolejte `CRegKey::EnumKey` s indexem 0. Zvýší hodnotu indexu a opakujte, dokud ERROR_NO_MORE_ITEMS vrátí metoda hodnotu. Další informace najdete v tématu [Funkce RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) v sadě Windows SDK.

##  <a name="flush"></a>  CRegKey::Flush

Volání této metody zapsat všechny atributy otevřít klíč registru do registru.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) v sadě Windows SDK.

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

Voláním této metody lze načíst kopii popisovače zabezpečení, ochrana otevřít klíč registru.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) hodnotu, která určuje požadované informace zabezpečení.

*psd*<br/>
Ukazatel do vyrovnávací paměti, která obdrží kopii popisovače požadované zabezpečení.

*pnBytes*<br/>
Velikost v bajtech, vyrovnávací paměti, na které odkazuje *psd*.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód je definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Obsahuje popisovač klíče registru přidružené `CRegKey` objektu.

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

Ukazatel `CAtlTransactionManager` objektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

Tato metoda upozorní volající o změnách atributy nebo obsah otevřít klíč registru.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bWatchSubtree*<br/>
Určuje příznak, který označuje, jestli se oznámit změny v se zadaným klíčem a všem příslušným podklíčům nebo jenom se zadaným klíčem. Pokud tento parametr má hodnotu TRUE, metoda sestavy změny do klíče a jeho podklíčů. Pokud má parametr hodnotu FALSE, metoda hlásí změn pouze v klíči.

*dwNotifyFilter*<br/>
Určuje, že by se měly hlásit sada příznaků, které řídí, jaké změny. Tento parametr může být kombinací následujícího:

|Value|Význam|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Oznámit volajícího podklíč je přidána nebo odstraněna.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Oznámit volajícímu změny atributů klíče, jako jsou informace popisovač zabezpečení.|
|REG_NOTIFY_CHANGE_LAST_SET|Oznámit volajícímu změn na hodnotu klíče. To může zahrnovat přidávání nebo odstraňování hodnotu nebo změnit stávající hodnotu.|
|REG_NOTIFY_CHANGE_SECURITY|Oznámit volajícímu změn do popisovače zabezpečení klíče.|

*hEvent*<br/>
Zpracování události. Pokud *bAsync* parametr má hodnotu TRUE, vrátí metoda okamžitě a změny jsou hlášeny sadou signalizace události. Pokud *bAsync* má hodnotu FALSE, *hEvent* se ignoruje.

*bAsync*<br/>
Určuje příznak, který určuje, jak metoda hlásí změny. Pokud tento parametr má hodnotu TRUE, metoda vrátí hodnotu okamžitě a hlásí změny podle signalizace zadané události. Pokud tento parametr hodnotu FALSE, metoda nevrátí dokud došlo ke změně. Pokud *hEvent* neurčuje platnou událost *bAsync* parametr nemůže mít hodnotu TRUE.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato metoda není oznámit volajícímu, pokud zadaný klíč se odstraní.

Ukázka programu a další podrobnosti najdete v tématu [funkce RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>  CRegKey::Open

Volejte tuto metodu za účelem otevření zadaného klíče a nastavte [m_hKey](#m_hkey) ke zpracování tohoto klíče.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*<br/>
Popisovač otevřít klíč.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*samDesired*<br/>
Zabezpečený přístup ke klíči. Výchozí hodnota je KEY_ALL_ACCESS. Seznam možných hodnot a popisy najdete v tématu [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulovou chybovou hodnotu podle nezdařila. H.

### <a name="remarks"></a>Poznámky

Pokud *lpszKeyName* parametr má hodnotu NULL nebo body na prázdný řetězec, `Open` otevře nový popisovač klíče identifikovaný *hKeyParent*, ale nezavře všechny dřív otevřených popisovač.

Na rozdíl od [CRegKey::Create](#create), `Open` nevytvoří se zadaným klíčem, pokud neexistuje.

##  <a name="operator_hkey"></a>  CRegKey::operator HKEY

Převede `CRegKey` objekt HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>  CRegKey::operator =

Operátor přiřazení.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč zkopírujte.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nový klíč.

### <a name="remarks"></a>Poznámky

Tento operátor odpojí *klíč* z jeho aktuálního objektu a přiřadí ji k `CRegKey` namísto toho objekt.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Voláním této metody lze načíst binární data pro zadanou hodnotu názvu.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*pValue*<br/>
Ukazatel do vyrovnávací paměti, která přijímá hodnotu data.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost v bajtech, vyrovnávací paměti, na které odkazují *pValue* parametru. Po návratu metody obsahuje tato proměnná velikost data kopírovaná do vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není typu REG_BINARY, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda používá `RegQueryValueEx` a potvrdí, že se vrátí správný typ data. Zobrazit [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) další podrobnosti.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Také [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkce používané touto metodou nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

Volejte tuto metodu za účelem získání dat DWORD zadaná hodnota názvu.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*dwValue*<br/>
Ukazatel do vyrovnávací paměti, která přijímá DWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není typu REG_DWORD, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda používá `RegQueryValueEx` a potvrdí, že se vrátí správný typ data. Zobrazit [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) další podrobnosti.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Také [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkce používané touto metodou nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Volejte tuto metodu za účelem načtení dat identifikátoru GUID pro zadanou hodnotu názvu.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*guidValue*<br/>
Ukazovat na proměnnou, která přijímá identifikátor GUID.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není platný identifikátor GUID, je vrácena ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda používá `CRegKey::QueryStringValue` a převede řetězec na identifikátor GUID pomocí [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Volejte tuto metodu za účelem získání nahrazován dat pro zadanou hodnotu názvu.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*pszValue*<br/>
Ukazatel do vyrovnávací paměti, která přijímá nahrazován data. Řetězci FixedLength multistring je pole zakončené znakem null řetězců, ukončeny dva znaky s hodnotou null.

*pnChars*<br/>
Velikost v TCHARs vyrovnávací paměti, na které odkazuje *pszValue*. Po návratu metody *pnChars* obsahuje velikost v TCHARs nástroje řetězci FixedLength multistring načíst, včetně ukončujícího znaku null.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není typu REG_MULTI_SZ, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda používá `RegQueryValueEx` a potvrdí, že se vrátí správný typ data. Zobrazit [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) další podrobnosti.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Také [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkce používané touto metodou nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Volejte tuto metodu za účelem načtení dat QWORD zadanou hodnotu názvu.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*qwValue*<br/>
Ukazatel do vyrovnávací paměti, která přijímá QWORD.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není typu REG_QWORD, vrátí se ERROR_INVALID_DATA.

### <a name="remarks"></a>Poznámky

Tato metoda používá `RegQueryValueEx` a potvrdí, že se vrátí správný typ data. Zobrazit [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) další podrobnosti.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Také [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkce používané touto metodou nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

Volejte tuto metodu za účelem načtení dat řetězce pro název zadanou hodnotu.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu.

*pszValue*<br/>
Ukazatel do vyrovnávací paměti, která přijímá data řetězce.

*pnChars*<br/>
Velikost v TCHARs vyrovnávací paměti, na které odkazuje *pszValue*. Po návratu metody *pnChars* obsahuje velikost v TCHARs řetězce načíst, včetně ukončujícího znaku null.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí se ERROR_SUCCESS. Jestliže metoda selže načtení hodnoty, vrátí nenulový chybový kód definovaný v nezdařila. H. Pokud data odkazovaná není typu REG_SZ, vrátí se ERROR_INVALID_DATA. Pokud metoda vrátí hodnotu ERROR_MORE_DATA, *pnChars* rovná nule, nikoli velikost požadované vyrovnávací paměti v bajtech.

### <a name="remarks"></a>Poznámky

Tato metoda používá `RegQueryValueEx` a potvrdí, že se vrátí správný typ data. Zobrazit [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) další podrobnosti.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Také [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkce používané touto metodou nezpracovává explicitně řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Voláním této metody lze načíst data pro zadanou hodnotu pole [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

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
Ukazatel na řetězec zakončený hodnotou null obsahující název hodnoty dotazu. Pokud *pszValueName* má hodnotu NULL nebo prázdný řetězec "", metoda načte typ a data klíče uživatele nepojmenované nebo výchozí hodnotu, pokud existuje.

*pdwType*<br/>
Ukazovat na proměnnou, která přijímá kódem, který označuje typ dat uložených v zadané hodnotě. *PdwType* parametr může mít hodnotu NULL, pokud typ kódu se nevyžaduje.

*pData*<br/>
Ukazatel do vyrovnávací paměti, která přijímá hodnotu data. Tento parametr může mít hodnotu NULL, pokud data se nevyžaduje.

*pnBytes*<br/>
Ukazatel na proměnnou, která určuje velikost v bajtech, vyrovnávací paměti, na které odkazují *pData* parametru. Po návratu metody obsahuje tato proměnná velikost data kopírovaná do *pData.*

*dwValue*<br/>
Pole hodnoty číselná data.

*lpszValueName*<br/>
Určuje pole hodnoty tak, aby se dalo dotazovat.

*szValue*<br/>
Pole hodnoty dat řetězce.

*pdwCount*<br/>
Velikost dat řetězců. Jeho hodnota nastavená na velikost zpočátku *szValue* vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Dvě původní verze `QueryValue` již nejsou podporovány a jsou označeny jako ATL_DEPRECATED. Kompilátor vydá upozornění, pokud se používají tyto formuláře.

Zbývající volání metod modulu RegQueryValueEx.

> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, která nemůže být důvěryhodný. Navíc funkci modulu RegQueryValueEx používané touto metodou explicitně nezpracovává řetězců, které jsou NULL byl ukončen. Obě podmínky by měl sloužit k volajícímu kódu.

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

Voláním této metody lze odebrat z registru se zadaným klíčem a explicitně odstraňte všechny podklíče.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey*<br/>
Určuje název klíče odstranit. Tento název musí být podklíč [m_hKey](#m_hkey).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulovou chybovou hodnotu podle nezdařila. H.

### <a name="remarks"></a>Poznámky

Pokud klíč má podklíčích, musí volat tuto metodu za účelem odstranění klíče.

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

Voláním této metody lze nastavit binární hodnotu klíče registru.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pValue*<br/>
Ukazatel do vyrovnávací paměti, obsahující data uloží v rámci zadaný název hodnoty.

*nBytes*<br/>
Určuje velikost v bajtech, informace, na které odkazují *pValue* parametru.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pro zápis hodnoty do registru.

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

Voláním této metody nastavte hodnotu DWORD klíče registru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*dwValue*<br/>
DWORD data, která mají být uloženy se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pro zápis hodnoty do registru.

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

Voláním této metody lze nastavit hodnotu GUID klíče registru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*guidValue*<br/>
Odkaz na identifikátor GUID k uložení se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá `CRegKey::SetStringValue` a převede identifikátor GUID do řetězce pomocí [StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

Volejte tuto metodu za účelem ukládání dat v zadané hodnotě pole zadaný klíč.

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
Určuje data, která mají být uloženy. Tento parametr musí mít hodnotu NULL.

*lpszValueName*<br/>
Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, je přidána.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem vytvoření nebo otevření *lpszKeyName* klíč a uložit *lpszValue* data v *lpszValueName* pole hodnoty.

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

Volejte tuto metodu za účelem nastavení zabezpečení klíče registru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Určuje součásti nastavit popisovač zabezpečení. Hodnota může být kombinací následujícího:

|Value|Význam|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Nastaví seznam klíče volitelný řízení přístupu (DACL). Klíč musí mít přístup WRITE_DAC nebo volající proces musí být vlastníkem daného objektu.|
|GROUP_SECURITY_INFORMATION|Nastaví identifikátor klíče primární skupinu zabezpečení (SID). Klíč musí mít přístup zápis_vlastníka nebo volající proces musí být vlastníkem daného objektu.|
|OWNER_SECURITY_INFORMATION|Nastaví SID vlastníka klíče. Klíč musí mít přístup zápis_vlastníka, nebo musí být vlastníka objektu nebo mít povolené oprávnění SE_TAKE_OWNERSHIP_NAME volající proces.|
|SACL_SECURITY_INFORMATION|Nastaví seznam klíče systému řízení přístupu (SACL). Klíč musí mít ACCESS_SYSTEM_SECURITY přístup. Správný způsob, jak získat tento přístup je povolit SE_SECURITY_NAME [oprávnění](/windows/desktop/secauthz/privileges) v přístupovém tokenu aktuální volajícího otevřít popisovač pro ACCESS_SYSTEM_SECURITY přístup a potom zakažte oprávnění.|

*psd*<br/>
Ukazatel [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) struktura, která určuje atributy zabezpečení k nastavení pro zadaný klíč.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Nastaví atributy zabezpečení klíč. Zobrazit [RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) další podrobnosti.

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

Voláním této metody lze nastavit nahrazován hodnotu klíče registru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pszValue*<br/>
Ukazatel na nahrazován data uloží v rámci zadaný název hodnoty. Řetězci FixedLength multistring je pole zakončené znakem null řetězců, ukončeny dva znaky s hodnotou null.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pro zápis hodnoty do registru.

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

Voláním této metody lze nastavit hodnota QWORD klíče registru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*qwValue*<br/>
QWORD data, která mají být uloženy se zadaným názvem hodnoty.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pro zápis hodnoty do registru.

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

Voláním této metody nastavte hodnotu řetězce klíče registru.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není přítomna, metoda ji přidá do klíče.

*pszValue*<br/>
Ukazatel na řetězec data uloží v rámci zadaný název hodnoty.

*dwType*<br/>
Typ řetězce pro zápis do registru: REG_SZ (výchozí) nebo REG_EXPAND_SZ (pro vícenásobné řetězce).

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je ERROR_SUCCESS. Jestliže metoda selže, vrácená hodnota je nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Tato metoda používá [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pro zápis hodnoty do registru.

##  <a name="setvalue"></a>  CRegKey::SetValue

Volejte tuto metodu za účelem ukládání dat v poli zadanou hodnotu [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako ATL_DEPRECATED.

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
Ukazatel na řetězec obsahující název hodnoty nastavení. Pokud hodnota s tímto názvem již není k dispozici v klíči, metoda ji přidá do klíče. Pokud *pszValueName* má hodnotu NULL nebo prázdný řetězec "", nastaví typ metody a datové klíče uživatele nepojmenované nebo výchozí hodnotu.

*dwType*<br/>
Určuje kód označující typ dat, na které odkazují *pValue* parametru.

*pValue*<br/>
Ukazatel do vyrovnávací paměti, obsahující data uloží v rámci zadaný název hodnoty.

*nBytes*<br/>
Určuje velikost v bajtech, informace, na které odkazují *pValue* parametru. Pokud jsou data typu REG_SZ, REG_EXPAND_SZ nebo REG_MULTI_SZ, *nBytes* musí obsahovat velikost ukončujícího znaku null.

*hKeyParent*<br/>
Popisovač otevřít klíč.

*lpszKeyName*<br/>
Určuje název klíče, který má být vytvořen nebo otevřen. Tento název musí být podklíč *hKeyParent*.

*lpszValue*<br/>
Určuje data, která mají být uloženy. Tento parametr musí mít hodnotu NULL.

*lpszValueName*<br/>
Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, je přidána.

*dwValue*<br/>
Určuje data, která mají být uloženy.

*bMulti*<br/>
Pokud má hodnotu false, označuje, že řetězec má typ REG_SZ. Hodnota true určuje to, že je řetězci FixedLength multistring typu REG_MULTI_SZ.

*nValueLen*<br/>
Pokud *bMulti* má hodnotu true, *nValueLen* je délka *lpszValue* řetězec znaků. Pokud *bMulti* má hodnotu false, hodnota -1 znamená, že metoda automaticky vypočítá délku.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí ERROR_SUCCESS; v opačném případě nenulový chybový kód definovaný v nezdařila. H.

### <a name="remarks"></a>Poznámky

Dvě původní verze `SetValue` jsou označeny jako ATL_DEPRECATED a by měl být už nebude používat. Kompilátor vydá upozornění, pokud se používají tyto formuláře.

Třetí volání metody [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa).

## <a name="see-also"></a>Viz také:

[Ukázkový model DCOM](../../overview/visual-cpp-samples.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
