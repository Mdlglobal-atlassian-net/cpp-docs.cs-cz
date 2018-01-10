---
title: "Třída CRegKey | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dffc650c54c4a50fb4b3b1fe2c22ac82501b8b45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cregkey-class"></a>CRegKey – třída
Tato třída poskytuje metody pro práci s položky systémového registru.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CRegKey
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRegKey::CRegKey](#cregkey)|Konstruktor|  
|[CRegKey:: ~ CRegKey](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRegKey::Attach](#attach)|Voláním této metody lze připojit nastavení HKEY k `CRegKey` objekt nastavením [m_hKey](#m_hkey) člen popisovač `hKey`.|  
|[CRegKey::Close](#close)|Volat tuto metodu za účelem uvolnění [m_hKey](#m_hkey) člen zpracování a nastavte ji na hodnotu NULL.|  
|[CRegKey::Create](#create)|Volat tuto metodu za účelem vytvoření k zadanému klíči, pokud neexistuje jako podklíč `hKeyParent`.|  
|[CRegKey::DeleteSubKey](#deletesubkey)|Voláním této metody lze odebrat z registru se zadaným klíčem.|  
|[CRegKey::DeleteValue](#deletevalue)|Voláním této metody lze odebrat hodnotu pole z [m_hKey](#m_hkey).|  
|[CRegKey::Detach](#detach)|Volat tuto metodu za účelem odpojení [m_hKey](#m_hkey) popisovač člena z `CRegKey` objektu a nastavte `m_hKey` na hodnotu NULL.|  
|[CRegKey::EnumKey](#enumkey)|Voláním této metody lze vytvořit výčet podklíčů klíče registru otevřete.|  
|[CRegKey::Flush](#flush)|Voláním této metody lze zapisovat všechny atributy otevřít klíč registru do registru.|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|Volejte tuto metodu za účelem načtení kopie popisovač zabezpečení, ochraně otevřít klíč registru.|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Tato metoda upozorní volající o změnách atributy nebo obsah otevřít klíč registru.|  
|[CRegKey::Open](#open)|Volání této metody se zadaným klíčem a nastavit [m_hKey](#m_hkey) k popisovači tohoto klíče.|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Volejte tuto metodu za účelem načtení binární data pro název zadanou hodnotu.|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Voláním této metody lze načíst data DWORD s hodnotou pro název zadanou hodnotu.|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Volejte tuto metodu za účelem načtení dat identifikátor GUID pro název zadanou hodnotu.|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Volejte tuto metodu za účelem načtení nahrazován data pro název zadanou hodnotu.|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Volejte tuto metodu za účelem načtení dat Qword – zadaná hodnota názvu.|  
|[CRegKey::QueryStringValue](#querystringvalue)|Volejte tuto metodu za účelem načtení dat řetězce pro název zadanou hodnotu.|  
|[CRegKey::QueryValue](#queryvalue)|Voláním této metody lze načíst data pro zadanou hodnotu pole [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako **ATL_DEPRECATED**.|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Volejte tuto metodu za účelem odeberte zadaný klíč z registru a explicitně odeberte všechny podklíče.|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Volejte tuto metodu a nastavit binární hodnotu klíče registru.|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|Volejte tuto metodu a nastavit hodnotu DWORD klíče registru.|  
|[CRegKey::SetGUIDValue](#setguidvalue)|Volejte tuto metodu a nastavit hodnotu GUID klíče registru.|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|Volejte tuto metodu a nastavit zabezpečení klíče registru.|  
|[CRegKey::SetKeyValue](#setkeyvalue)|Volejte tuto metodu pro ukládání dat v poli zadanou hodnotu zadaného klíče.|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Volejte tuto metodu za účelem nahrazován hodnotu klíče registru.|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|Voláním této metody lze nastavit QWORD hodnotu klíče registru.|  
|[CRegKey::SetStringValue](#setstringvalue)|Volejte tuto metodu a nastavit řetězcovou hodnotu klíče registru.|  
|[CRegKey::SetValue](#setvalue)|Volat tuto metodu pro ukládání dat v poli zadanou hodnotu [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako **ATL_DEPRECATED**.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|Převede `CRegKey` objekt, který má nastavení HKEY.|  
|[CRegKey::operator =](#operator_eq)|Operátor přiřazení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|Obsahuje popisovač klíče registru přidružené `CRegKey` objektu.|  
|[CRegKey::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu|  
  
## <a name="remarks"></a>Poznámky  
 `CRegKey`poskytuje metody pro vytvoření nebo odstranění klíče a hodnoty v registru systému. Registr obsahuje sadu specifické pro instalaci definic pro součásti systému, jako jsou například čísla verzí softwaru, logického fyzického mapování nainstalovaný hardware a objektů COM.  
  
 `CRegKey`poskytuje programovací rozhraní do registru systému pro daný počítač. Například otevřít klíč registru konkrétní, volání `CRegKey::Open`. Chcete-li načíst nebo upravit datové hodnoty, volejte `CRegKey::QueryValue` nebo `CRegKey::SetValue`, v uvedeném pořadí. Zavřete klíč, volání `CRegKey::Close`.  
  
 Při zavření klíč registru data je zápis na pevný disk. Tento proces může trvat několik sekund. Pokud vaše aplikace musí explicitně zápisu dat registru na pevný disk, můžete zavolat [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32 funkce. Ale **RegFlushKey** používá mnoho systémových prostředků a by měla být volána pouze v nezbytně nutných případech.  
  
> [!IMPORTANT]
>  Všechny metody, které umožňují volajícímu zadat umístění registru by mohly číst data, která nemůže být důvěryhodný. Metody, které využívají [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) měli vzít v úvahu, který tuto funkci explicitně nezpracovává řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="attach"></a>CRegKey::Attach  
 Voláním této metody lze připojit nastavení HKEY k `CRegKey` objekt nastavením [m_hKey](#m_hkey) člen popisovač `hKey`.  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač klíče registru.  
  
### <a name="remarks"></a>Poznámky  
 **Připojit** bude assert Pokud `m_hKey` hodnotu Null.  
  
##  <a name="close"></a>CRegKey::Close  
 Volat tuto metodu za účelem uvolnění [m_hKey](#m_hkey) člen zpracování a nastavte ji na hodnotu NULL.  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; v opačném případě vrátí chybovou hodnotu.  
  
##  <a name="create"></a>CRegKey::Create  
 Volat tuto metodu za účelem vytvoření k zadanému klíči, pokud neexistuje jako podklíč `hKeyParent`.  
  
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
 `hKeyParent`  
 Popisovač otevřít klíč.  
  
 `lpszKeyName`  
 Určuje název klíče pro vytvořit nebo otevřít. Tento název musí být podklíčem `hKeyParent`.  
  
 `lpszClass`  
 Určuje třídu klíč, který chcete vytvořit nebo otevřít. Výchozí hodnota je REG_NONE.  
  
 `dwOptions`  
 Možnosti pro klíč. Výchozí hodnota je REG_OPTION_NON_VOLATILE. Seznam možných hodnot a popisy najdete v tématu [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) ve Windows SDK.  
  
 `samDesired`  
 Zabezpečení přístupu pro klíč. Výchozí hodnota je KEY_READ &#124; KEY_WRITE. Seznam možných hodnot a popisy najdete v tématu **RegCreateKeyEx**.  
  
 *lpSecAttr*  
 Ukazatel [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje, zda popisovač klíče může být zděděn podřízený proces. Ve výchozím nastavení je tento parametr hodnotu NULL (tj. popisovač nemůže být zděděno).  
  
 *lpdwDisposition*  
 [out] Pokud není hodnotou NULL, načte REG_CREATED_NEW_KEY (Pokud jste klíč neexistoval a byl vytvořen) nebo REG_OPENED_EXISTING_KEY (Pokud je klíč existoval a byl otevřen).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS a otevře klíč. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 **Vytvoření** nastaví [m_hKey](#m_hkey) člen k popisovači tohoto klíče.  
  
##  <a name="cregkey"></a>CRegKey::CRegKey  
 Konstruktor  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Odkaz na `CRegKey` objektu.  
  
 `hKey`  
 Popisovač pro klíč registru.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří nový `CRegKey` objektu. Objekt můžete vytvořit z existující `CRegKey` objekt, nebo z popisovač pro klíč registru.  
  
##  <a name="dtor"></a>CRegKey:: ~ CRegKey  
 Destruktor.  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Verze destruktor `m_hKey`.  
  
##  <a name="deletesubkey"></a>CRegKey::DeleteSubKey  
 Voláním této metody lze odebrat z registru se zadaným klíčem.  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSubKey`  
 Určuje název klíče, který se odstranit. Tento název musí být podklíčem [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 `DeleteSubKey`Odstranit lze pouze klíč, který obsahuje žádné podklíče. Pokud klíč obsahuje podklíče, zavolejte [RecurseDeleteKey](#recursedeletekey) místo.  
  
##  <a name="deletevalue"></a>CRegKey::DeleteValue  
 Voláním této metody lze odebrat hodnotu pole z [m_hKey](#m_hkey).  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszValue`  
 Určuje hodnotu pole, které chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
##  <a name="detach"></a>CRegKey::Detach  
 Volat tuto metodu za účelem odpojení [m_hKey](#m_hkey) popisovač člena z `CRegKey` objektu a nastavte `m_hKey` na hodnotu NULL.  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nastavení HKEY přidružené `CRegKey` objektu.  
  
##  <a name="enumkey"></a>CRegKey::EnumKey  
 Voláním této metody lze vytvořit výčet podklíčů klíče registru otevřete.  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Podklíčů index. Tento parametr musí být nula první volání a pak se zvýší při následných voláních  
  
 `pszName`  
 Ukazatel na vyrovnávací paměť, která přijímá název podklíče, včetně ukončující znak hodnoty null. Název podklíče zkopírován do vyrovnávací paměti, není úplné klíče hierarchii.  
  
 *pnNameLength*  
 Ukazatel na proměnné, která určuje velikost v TCHARs vyrovnávací paměti určeného `pszName` parametr. Tato velikost by měla obsahovat ukončující znak hodnoty null. Když metoda vrátí, na kterou odkazuje proměnná *pnNameLength* obsahuje počet znaků, které jsou uložené ve vyrovnávací paměti. Vrátí počet nezahrnuje ukončující znak hodnoty null.  
  
 *pftLastWriteTime*  
 Ukazatel na proměnnou, která přijímá čas podklíč výčtové poslední do byla zapsána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit výčet podklíčů, volejte `CRegKey::EnumKey` s indexem 0. Zvýší hodnotu indexu a opakujte, dokud ERROR_NO_MORE_ITEMS vrátí metoda. Další informace najdete v tématu [Funkce RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862) ve Windows SDK.  
  
##  <a name="flush"></a>CRegKey::Flush  
 Voláním této metody lze zapisovat všechny atributy otevřít klíč registru do registru.  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867) ve Windows SDK.  
  
##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity  
 Volejte tuto metodu za účelem načtení kopie popisovač zabezpečení, ochraně otevřít klíč registru.  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) hodnotu, která určuje informace o požadované zabezpečení.  
  
 `psd`  
 Ukazatel na vyrovnávací paměť, která obdrží kopii popisovač požadovaný zabezpečení.  
  
 `pnBytes`  
 Velikost v bajtech vyrovnávací paměti, na kterou odkazuje `psd`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, je vrácenou hodnotu že kód nenulové hodnoty chyby je definována v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313).  
  
##  <a name="m_hkey"></a>CRegKey::m_hKey  
 Obsahuje popisovač klíče registru přidružené `CRegKey` objektu.  
  
```
HKEY m_hKey;
```  
  
##  <a name="m_ptm"></a>CRegKey::m_pTM  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue  
 Tato metoda upozorní volající o změnách atributy nebo obsah otevřít klíč registru.  
  
```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *bWatchSubtree*  
 Určuje příznak, který označuje, zda chcete sestavu změny v zadaný klíč a všechny jeho podklíče nebo pouze v zadaný klíč. Pokud má parametr hodnotu TRUE, metoda sestavy změny v klíč a jeho podklíčů. Pokud má parametr hodnotu FALSE, metoda sestavy změny pouze v klíči.  
  
 *dwNotifyFilter*  
 Určuje, že by měly být uvedeny sadu příznaky, které řídí, jaké změny. Tento parametr může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|Volající upozorněte, pokud je podklíč přidat nebo odstranit.|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|Upozorněte volající změny atributů klíče, jako je například informace popisovače zabezpečení.|  
|REG_NOTIFY_CHANGE_LAST_SET|Upozorněte volající změny na hodnotu klíče. To může zahrnovat přidání nebo odstranění hodnotu nebo změna stávající hodnotu.|  
|REG_NOTIFY_CHANGE_SECURITY|Upozorněte volající změny do popisovače zabezpečení klíče.|  
  
 `hEvent`  
 Popisovač události. Pokud *bAsync* parametr má hodnotu TRUE, vrátí metoda okamžitě a změny jsou uvedeny signalizace této události. Pokud `bAsync` hodnotu FALSE, `hEvent` je ignorována.  
  
 `bAsync`  
 Určuje příznak, který určuje, jak metodu sestavy změny. Pokud má parametr hodnotu TRUE, metoda vrátí okamžitě a sestavy změny podle signalizace zadané události. Pokud tento parametr hodnotu FALSE, metoda nevrátí dokud došlo ke změně. Pokud `hEvent` neurčuje platnou událost `bAsync` parametr nemůže mít hodnotu TRUE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda neupozorní volající, pokud zadaný klíč se odstraní.  
  
 Ukázka programu a další podrobnosti najdete v tématu [funkce RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892).  
  
##  <a name="open"></a>CRegKey::Open  
 Volání této metody se zadaným klíčem a nastavit [m_hKey](#m_hkey) k popisovači tohoto klíče.  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hKeyParent`  
 Popisovač otevřít klíč.  
  
 `lpszKeyName`  
 Určuje název klíče pro vytvořit nebo otevřít. Tento název musí být podklíčem `hKeyParent`.  
  
 `samDesired`  
 Zabezpečení přístupu pro klíč. Výchozí hodnota je KEY_ALL_ACCESS. Seznam možných hodnot a popisy najdete v tématu [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; Chyba nenulovou hodnotu, jinak hodnota definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `lpszKeyName` parametru má hodnotu NULL nebo body na prázdný řetězec, **otevřete** otevře nový popisovač klíče identifikovaný `hKeyParent`, ale nezavře všechny dříve otevřen popisovač.  
  
 Na rozdíl od [CRegKey::Create](#create), **otevřete** nevytvoří se zadaným klíčem, pokud neexistuje.  
  
##  <a name="operator_hkey"></a>CRegKey::operator HKEY  
 Převede `CRegKey` objekt, který má nastavení HKEY.  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>CRegKey::operator =  
 Operátor přiřazení.  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč pro kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na nový klíč.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor umožňuje odpojit `key` z jeho aktuálního objektu a přiřadí ji k `CRegKey` místo toho objekt.  
  
##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue  
 Volejte tuto metodu za účelem načtení binární data pro název zadanou hodnotu.  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `pValue`  
 Ukazatel na vyrovnávací paměť, která přijímá data hodnotu.  
  
 `pnBytes`  
 Ukazatel na proměnné, která určuje velikost v bajtech vyrovnávací paměti, na kterou odkazuje `pValue` parametr. Po návratu metody obsahuje tato proměnná velikost dat zkopírována do vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není typu REG_BINARY, je vrácena ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá **RegQueryValueEx** a potvrdí, že se vrátí správný typ dat. V tématu [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkci používanou touto metodou. nezpracovává explicitně řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue  
 Voláním této metody lze načíst data DWORD s hodnotou pro název zadanou hodnotu.  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `dwValue`  
 Ukazatel na vyrovnávací paměť, která přijímá DWORD.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není typu REG_DWORD, je vrácena ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá **RegQueryValueEx** a potvrdí, že se vrátí správný typ dat. V tématu [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkci používanou touto metodou. nezpracovává explicitně řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue  
 Volejte tuto metodu za účelem načtení dat identifikátor GUID pro název zadanou hodnotu.  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `guidValue`  
 Ukazatel na proměnnou, která přijímá identifikátor GUID.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není platný identifikátor GUID, je vrácena ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá `CRegKey::QueryStringValue` a převede řetězec na identifikátor GUID pomocí [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589).  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat.  
  
##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue  
 Volejte tuto metodu za účelem načtení nahrazován data pro název zadanou hodnotu.  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `pszValue`  
 Ukazatel na vyrovnávací paměť, která přijímá nahrazován data. Multistring je pole řetězce ukončené hodnotou null, ukončila příkazem dva znaky null.  
  
 `pnChars`  
 Velikost v TCHARs vyrovnávací paměti, na kterou odkazuje `pszValue`. Po návratu metody `pnChars` obsahuje velikost v TCHARs z multistring načíst, včetně ukončující znak hodnoty null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není typu REG_MULTI_SZ, je vrácena ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá **RegQueryValueEx** a potvrdí, že se vrátí správný typ dat. V tématu [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkci používanou touto metodou. nezpracovává explicitně řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue  
 Volejte tuto metodu za účelem načtení dat Qword – zadaná hodnota názvu.  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `qwValue`  
 Ukazatel na vyrovnávací paměť, která přijímá QWORD.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není typu REG_QWORD, je vrácena ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá **RegQueryValueEx** a potvrdí, že se vrátí správný typ dat. V tématu [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkci používanou touto metodou. nezpracovává explicitně řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="querystringvalue"></a>CRegKey::QueryStringValue  
 Volejte tuto metodu za účelem načtení dat řetězce pro název zadanou hodnotu.  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz.  
  
 `pszValue`  
 Ukazatel na vyrovnávací paměť, která přijímá data řetězec.  
  
 `pnChars`  
 Velikost v TCHARs vyrovnávací paměti, na kterou odkazuje `pszValue`. Po návratu metody `pnChars` obsahuje velikost v TCHARs řetězce načíst, včetně ukončující znak hodnoty null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí se ERROR_SUCCESS. Pokud metoda nemůže načíst hodnotu, vrátí kód nenulové hodnoty Chyba definované v nezdařila. H. Pokud data odkazuje není typu REG_SZ, je vrácena ERROR_INVALID_DATA. Pokud metoda vrátí hodnotu ERROR_MORE_DATA, `pnChars` rovná nule, není vyrovnávací paměti požadovaná velikost v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá **RegQueryValueEx** a potvrdí, že se vrátí správný typ dat. V tématu [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkci používanou touto metodou. nezpracovává explicitně řetězce, které jsou NULL byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="queryvalue"></a>CRegKey::QueryValue  
 Voláním této metody lze načíst data pro zadanou hodnotu pole [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako **ATL_DEPRECATED**.  
  
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
 `pszValueName`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název hodnotu pro dotaz. Pokud `pszValueName` má hodnotu NULL nebo prázdný řetězec "", metoda načte typ a dat pro klíč je nepojmenovaný nebo výchozí hodnotu, pokud existuje.  
  
 `pdwType`  
 Ukazatel na proměnnou, která přijímá kód označující typ dat uložených v zadaná hodnota. `pdwType` Parametr může mít hodnotu NULL, pokud kód typ není potřeba.  
  
 `pData`  
 Ukazatel na vyrovnávací paměť, která přijímá data hodnotu. Tento parametr může mít hodnotu NULL, pokud není požadovaná data.  
  
 `pnBytes`  
 Ukazatel na proměnné, která určuje velikost v bajtech vyrovnávací paměti, na kterou odkazuje `pData` parametr. Po návratu metody obsahuje tato proměnná velikost dat zkopírována do *pData.*  
  
 `dwValue`  
 Pole hodnoty číselná data.  
  
 `lpszValueName`  
 Určuje hodnotu pole, které chcete zadat dotaz.  
  
 `szValue`  
 Pole hodnoty dat řetězců.  
  
 `pdwCount`  
 Velikost dat řetězce. Její hodnota je zpočátku nastavena na velikost `szValue` vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; Kód nenulové hodnoty chyby, jinak hodnota definovaná v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Dvě původní verze `QueryValue` již nejsou podporovány a jsou označeny jako **ATL_DEPRECATED**. Kompilátor vás upozorní, pokud se používají tyto formuláře.  
  
 Zbývající volání metod RegQueryValueEx.  
  
> [!IMPORTANT]
>  Tato metoda umožňuje volajícímu zadat jakékoli umístění registru, potenciálně čtení dat, který nelze důvěřovat. Navíc RegQueryValueEx funkci používanou touto metodou. nezpracovává řetězce, které jsou explicitně `NULL` byla ukončena. Obě podmínky zkontrolovat pro volací kód.  
  
##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey  
 Volejte tuto metodu za účelem odeberte zadaný klíč z registru a explicitně odeberte všechny podklíče.  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszKey*  
 Určuje název klíče, který se odstranit. Tento název musí být podklíčem [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; Chyba nenulovou hodnotu, jinak hodnota definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Pokud klíč má podklíče, musí volat tuto metodu za účelem odstranění klíče.  
  
##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue  
 Volejte tuto metodu a nastavit binární hodnotu klíče registru.  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `pValue`  
 Ukazatel na vyrovnávací paměť obsahující data, která mají být uloží spolu s názvem zadanou hodnotu.  
  
 `nBytes`  
 Určuje velikost v bajtech informace, na kterou odkazuje `pValue` parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) pro zápis hodnoty registru.  
  
##  <a name="setdwordvalue"></a>CRegKey::SetDWORDValue  
 Volejte tuto metodu a nastavit hodnotu DWORD klíče registru.  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `dwValue`  
 Data DWORD s hodnotou k uložení s názvem zadanou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) pro zápis hodnoty registru.  
  
##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue  
 Volejte tuto metodu a nastavit hodnotu GUID klíče registru.  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `guidValue`  
 Odkaz na identifikátor GUID do se uloží spolu s názvem zadanou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda využívá `CRegKey::SetStringValue` a převede identifikátor GUID na řetězec pomocí [StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893).  
  
##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue  
 Volejte tuto metodu pro ukládání dat v poli zadanou hodnotu zadaného klíče.  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszKeyName`  
 Určuje název klíče, který se vytvořit nebo otevřít. Tento název musí být podklíčem [m_hKey](#m_hkey).  
  
 `lpszValue`  
 Určuje data, která mají být uloženy. Tento parametr musí obsahovat hodnotu NULL.  
  
 `lpszValueName`  
 Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, se přidá.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; Kód nenulové hodnoty chyby, jinak hodnota definovaná v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze vytvořit nebo otevřít `lpszKeyName` klíč a uložit `lpszValue` data v `lpszValueName` pole value.  
  
##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity  
 Volejte tuto metodu a nastavit zabezpečení klíče registru.  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 Určuje složky nastavit popisovač zabezpečení. Hodnota může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|Nastaví seznamu klíče volitelného řízení přístupu (DACL). Klíč musí mít přístup zápis_DAC nebo volající proces musí být vlastníka objektu.|  
|GROUP_SECURITY_INFORMATION|Nastaví klíče primární skupiny identifikátor zabezpečení (SID). Klíč musí mít přístup zápis_vlastníka nebo volající proces musí být vlastníka objektu.|  
|OWNER_SECURITY_INFORMATION|Nastaví SID vlastníka klíče. Klíč musí mít přístup zápis_vlastníka nebo volající proces musí být vlastníka objektu nebo mít oprávnění SE_TAKE_OWNERSHIP_NAME povolena.|  
|SACL_SECURITY_INFORMATION|Nastaví seznam řízení přístupu systému klíče (SACL). Klíč musí mít ACCESS_SYSTEM_SECURITY přístup. Správný způsob, jak získat tento přístup je umožnit SE_SECURITY_NAME [oprávnění](http://msdn.microsoft.com/library/windows/desktop/aa379306) v volajícího aktuální přístupový token, otevřít popisovač pro ACCESS_SYSTEM_SECURITY přístup a pak zakažte oprávnění.|  
  
 `psd`  
 Ukazatel na [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) struktura, která určuje atributy zabezpečení mají nastavit pro zadaný klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví atributy zabezpečení klíče. V tématu [RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314) další podrobnosti.  
  
##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue  
 Volejte tuto metodu za účelem nahrazován hodnotu klíče registru.  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `pszValue`  
 Ukazatel na nahrazován data, která mají být uloží spolu s názvem zadanou hodnotu. Multistring je pole řetězce ukončené hodnotou null, ukončila příkazem dva znaky null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) pro zápis hodnoty registru.  
  
##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue  
 Voláním této metody lze nastavit QWORD hodnotu klíče registru.  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `qwValue`  
 Qword – data k uložení s názvem zadanou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) pro zápis hodnoty registru.  
  
##  <a name="setstringvalue"></a>CRegKey::SetStringValue  
 Volejte tuto metodu a nastavit řetězcovou hodnotu klíče registru.  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není přítomna, metoda ho přidá klíč.  
  
 `pszValue`  
 Ukazatel na řetězec data, která mají být uloží spolu s názvem zadanou hodnotu.  
  
 `dwType`  
 Typ řetězce pro zápis do registru: REG_SZ (výchozí) nebo REG_EXPAND_SZ (pro multistrings).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda úspěšné, je vrácenou hodnotu ERROR_SUCCESS. Pokud metoda selže, návratová hodnota je kód nenulové hodnoty chyby definované v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx) pro zápis hodnoty registru.  
  
##  <a name="setvalue"></a>CRegKey::SetValue  
 Volat tuto metodu pro ukládání dat v poli zadanou hodnotu [m_hKey](#m_hkey). Dřívější verze této metody již nejsou podporovány a jsou označeny jako **ATL_DEPRECATED**.  
  
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
 `pszValueName`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení. Pokud hodnotu s tímto názvem již není součástí klíče, metoda ho přidá klíč. Pokud `pszValueName` má hodnotu NULL nebo prázdný řetězec "", metoda nastaví typ a dat pro klíč je nepojmenovaný nebo výchozí hodnotu.  
  
 `dwType`  
 Určuje kód označující typ dat, na kterou odkazuje `pValue` parametr.  
  
 `pValue`  
 Ukazatel na vyrovnávací paměť obsahující data, která mají být uloží spolu s názvem zadanou hodnotu.  
  
 `nBytes`  
 Určuje velikost v bajtech informace, na kterou odkazuje `pValue` parametr. Pokud jsou data typu REG_SZ, REG_EXPAND_SZ nebo REG_MULTI_SZ, `nBytes` musí obsahovat velikost ukončující znak hodnoty null.  
  
 `hKeyParent`  
 Popisovač otevřít klíč.  
  
 `lpszKeyName`  
 Určuje název klíče pro vytvořit nebo otevřít. Tento název musí být podklíčem `hKeyParent`.  
  
 `lpszValue`  
 Určuje data, která mají být uloženy. Tento parametr musí obsahovat hodnotu NULL.  
  
 `lpszValueName`  
 Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, se přidá.  
  
 `dwValue`  
 Určuje data, která mají být uloženy.  
  
 `bMulti`  
 Pokud je hodnota false, znamená, že řetězec je typu REG_SZ. V případě hodnoty true znamená, že řetězec je multistring typu REG_MULTI_SZ.  
  
 `nValueLen`  
 Pokud `bMulti` má hodnotu true, `nValueLen` je délka *lpszValue* řetězec znaků. Pokud `bMulti` je nastavena hodnota false, hodnota -1 označuje, že metoda automaticky vypočítá délku.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí ERROR_SUCCESS; Kód nenulové hodnoty chyby, jinak hodnota definovaná v nezdařila. H.  
  
### <a name="remarks"></a>Poznámky  
 Dvě původní verze `SetValue` jsou označeny jako **ATL_DEPRECATED** a by měl být dále používán. Kompilátor vás upozorní, pokud se používají tyto formuláře.  
  
 Třetí volání metod [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka DCOM](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
