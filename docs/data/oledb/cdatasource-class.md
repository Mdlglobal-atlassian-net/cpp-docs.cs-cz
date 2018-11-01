---
title: CDataSource – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: f52b5b4313f8c9703a578f7d0d3ed672555f647e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646108"
---
# <a name="cdatasource-class"></a>CDataSource – třída

Objekt zdroje dat OLE DB, což představuje prostřednictvím poskytovatele připojení ke zdroji dat odpovídá.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataSource
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zavřít](#close)|Ukončí připojení.|
|[Getinitializationstring –](#getinitializationstring)|Načte inicializační řetězec zdroje dat, která je aktuálně otevřená.|
|[GetProperties](#getproperties)|Získá hodnoty vlastností pro připojených zdrojů dat aktuálně nastavená.|
|[Metoda GetProperty](#getproperty)|Získá hodnotu jedné vlastnosti pro připojených zdrojů dat aktuálně nastavená.|
|[Otevřít](#open)|Vytvoří připojení ke zprostředkovateli (zdroj dat), buď pomocí `CLSID`, `ProgID`, nebo `CEnumerator` moniker poskytnutá volajícím.|
|[OpenFromFileName](#openfromfilename)|Otevře se zdroji dat ze souboru určeném názvem souboru zadaný uživatelem.|
|[OpenFromInitializationString –](#openfrominitializationstring)|Otevře se zdroji dat určené inicializačního řetězce.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Umožňuje uživateli vybrat dříve vytvořeného datového souboru odkaz k otevření odpovídající zdroj dat.|
|[Openwithservicecomponents –](#openwithservicecomponents)|Otevře objekt zdroje dat pomocí dialogového okna dat propojení.|

## <a name="remarks"></a>Poznámky

Jednu nebo více relací databázi lze vytvořit pro jedno připojení. Tyto relace jsou reprezentovány `CSession`. Je nutné volat [CDataSource::Open](../../data/oledb/cdatasource-open.md) k otevření připojení před vytvořením relace s `CSession::Open`.

Příklad použití `CDataSource`, najdete v článku [CatDB](../../visual-cpp-samples.md) vzorku.

## <a name="close"></a> CDataSource::Close

Ukončí připojení uvolněním `m_spInit` ukazatele.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a> CDataSource::GetInitializationString

Načte inicializačního řetězce zdroje dat, který je momentálně otevřený.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString, 
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Parametry

*pInitializationString*<br/>
[out] Ukazatel na řetězec inicializace.

*bIncludePassword*<br/>
[in] **true** Pokud řetězec obsahuje heslo; v opačném případě **false**.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný řetězec inicializace je možné později znovu toto připojení ke zdroji dat.

## <a name="getproperties"></a> CDataSource::GetProperties

Vrátí informace o vlastnosti požadované pro objekt zdroje dat připojených.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperties(ULONG ulPropIDSets, 
   constDBPROPIDSET* pPropIDSet, 
   ULONG* pulPropertySets, 
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Parametry

Zobrazit [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344) v *referenční informace pro OLE DB programátory* ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

K získání jedné vlastnosti, použijte [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="getproperty"></a> CDataSource::GetProperty

Vrátí hodnotu zadané vlastnosti pro objekt připojené datové zdroje.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperty(const GUID& guid, 
   DBPROPID propid, 
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Parametry

*identifikátor GUID*<br/>
[in] Identifikátor GUID identifikující vlastnost, pro které se má vrátit vlastnost nastavit.

*číslo PropId*<br/>
[in] Vlastnost ID pro vlastnost vrátit.

*pVariant*<br/>
[out] Ukazatel na varianty kde `GetProperty` vrátí hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Chcete-li získat více vlastností, použijte [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="open"></a> CDataSource::Open

Otevře připojení ke zdroji dat pomocí `CLSID`, `ProgID`, nebo `CEnumerator` moniker nebo se zobrazí výzva s dialogovým oknem Lokátor.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID, 
   DBPROPSET* pPropSet = NULL, 
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID, 
   LPCTSTR pName,LPCTSTR pUserName = NULL, 
   LPCTSTR pPassword = NULL, 
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
[in] `CLSID` Data zprostředkovatele.

*pPropSet*<br/>
[in] Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](/previous-versions/windows/desktop/ms713696) v *referenční informace pro OLE DB programátory* ve Windows SDK.

*nPropertySets*<br/>
[in] Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury předané *pPropSet* argument.

*pName*<br/>
[in] Název databáze pro připojení.

*pUserName*<br/>
[in] Jméno uživatele.

*pPassword*<br/>
[in] Heslo uživatele.

*nInitMode*<br/>
[in] Režim inicializaci databáze. Zobrazit [inicializační vlastnosti](/previous-versions/windows/desktop/ms723127)v *OLE DB referenční informace pro programátory* v sadě Windows SDK pro seznam režimů platné inicializace. Pokud *nInitMode* je nula, žádná inicializace režimu je součástí sady vlastností, které se používá k otevření připojení.

*szProgID*<br/>
[in] Identifikátor programu.

*Enumerátor*<br/>
[in] A [CEnumerator](../../data/oledb/cenumerator-class.md) objekt použitý k získání monikeru pro otevření připojení, pokud volající neurčuje `CLSID`.

*hWnd*<br/>
[in] Popisovač okna, který má být nadřazená dialogového okna. Pomocí funkce přetížení, která používá *hWnd* parametr se automaticky vyvolá součásti služby; podrobnosti najdete v části poznámky.

*dwPromptOptions*<br/>
[in] Určuje styl Lokátor dialogové okno k zobrazení. Možné hodnoty najdete v článku Msdasc.h.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Přetížení metody, která používá *hWnd* parametr otevře objekt zdroje dat pomocí služby komponent v oledb32.dll; Tato knihovna DLL obsahuje implementaci součásti služby funkcí, jako je třeba sdílení prostředků ve fondech, automaticky Zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB programátora odkaz na [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

Přetížení metody, které nepoužívají *hWnd* parametr otevřít objekt zdroje dat bez použití v oledb32.dll součásti služby. A [CDataSource](../../data/oledb/cdatasource-class.md) objekt otevřené se tyto funkce přetížení se nebudete moct využívat některé funkce součásti služby.

### <a name="example"></a>Příklad

Následující kód ukazuje, jak otevřít zdroj dat Jet 4.0 s šablonami technologie OLE DB. Je považovat za zdroj dat Jet zdroji dat OLE DB. Nicméně volání `Open` potřebuje dvě sady vlastností: jednu pro DBPROPSET_DBINIT a druhou pro DBPROPSET_JETOLEDB_DBINIT, tak, že nastavíte DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

Otevře se zdroji dat ze souboru určeném názvem souboru zadaný uživatelem.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Parametry

*szFileName*<br/>
[in] Název souboru, obvykle připojení ke zdroji dat (. Soubor UDL).

Další informace o souborech odkaz data (soubory UDL) najdete v tématu [Data přehled rozhraní API odkazu](/previous-versions/windows/desktop/ms718102) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda se otevře objekt zdroje dat pomocí služby komponent v oledb32.dll; Tato knihovna DLL obsahuje implementaci funkce součásti služby, jako je sdílení prostředků ve fondech, automatické zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB programátora odkaz na [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openfrominitializationstring"></a> CDataSource::OpenFromInitializationString

Otevře se zdroji dat určené uživatelem zadané inicializačního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString, 
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Parametry

*szInitializationString*<br/>
[in] Inicializační řetězec.

*fPromptForInfo*<br/>
[in] Pokud tento argument je nastavená na **true**, pak `OpenFromInitializationString` nastaví vlastnost DBPROP_INIT_PROMPT DBPROMPT_COMPLETEREQUIRED, která určuje, že se uživateli výzva, pouze pokud je zapotřebí více informací. To je užitečné v situacích, ve kterých inicializačního řetězce určuje databázi, která vyžaduje heslo, ale řetězec neobsahuje heslo. Uživatel bude vyzván k heslo (nebo všechny chybějící informace) při pokusu o připojení k databázi.

Výchozí hodnota je **false**, která určuje, zda uživatel nikdy výzvami (sady DBPROP_INIT_PROMPT k DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda se otevře objekt zdroje dat pomocí služby komponent v oledb32.dll; Tato knihovna DLL obsahuje implementaci funkce součásti služby, jako je sdílení prostředků ve fondech, automatické zařazení transakce a tak dále.

## <a name="openwithpromptfilename"></a> CDataSource::OpenWithPromptFileName

Tato metoda se zobrazí výzva se dialogové okno a potom otevře zdroj dat s využitím souboru zadaný uživatelem.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ), 
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE, 
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač okna, který má být nadřazená dialogového okna.

*dwPromptOptions*<br/>
[in] Určuje styl Lokátor dialogové okno k zobrazení. Možné hodnoty najdete v článku Msdasc.h.

*szInitialDirectory*<br/>
[in] Počáteční adresář, který má zobrazit v dialogovém okně Lokátor.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda se otevře objekt zdroje dat pomocí služby komponent v oledb32.dll; Tato knihovna DLL obsahuje implementaci funkce součásti služby, jako je sdílení prostředků ve fondech, automatické zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB programátora odkaz na [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openwithservicecomponents"></a> CDataSource::OpenWithServiceComponents

Otevře objekt zdroje dat pomocí služby komponent v oledb32.dll.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
[in] `CLSID` Data zprostředkovatele.

*szProgID*<br/>
[in] ID programu zprostředkovatele dat

*pPropset*<br/>
[in] Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](/previous-versions/windows/desktop/ms713696) v *referenční informace pro OLE DB programátory* ve Windows SDK. Pokud je inicializovat objekt zdroje dat, vlastnosti musí patřit do skupiny vlastností zdroje dat. Pokud stejná vlastnost je zadán více než jednou v *pPropset*, jehož hodnota se používá se specifickým pro zprostředkovatele. Pokud *ulPropSets* je nula, tento parametr je ignorován.

*ulPropSets*<br/>
[in] Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury předané *pPropSet* argument. Pokud to je nula, poskytovatel ignoruje *pPropset*.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda se otevře objekt zdroje dat pomocí služby komponent v oledb32.dll; Tato knihovna DLL obsahuje implementaci funkce součásti služby, jako je sdílení prostředků ve fondech, automatické zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB programátora odkaz na [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)