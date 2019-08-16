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
ms.openlocfilehash: 3cb522d1f6ed256f8e042bc2f978e8bc5100888c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501405"
---
# <a name="cdatasource-class"></a>CDataSource – třída

Odpovídá objektu zdroje dat OLE DB, který představuje připojení prostřednictvím poskytovatele ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataSource
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zavřít](#close)|Ukončí připojení.|
|[GetInitializationString](#getinitializationstring)|Načte inicializační řetězec aktuálně otevřeného zdroje dat.|
|[GetProperties](#getproperties)|Získá hodnoty vlastností, které jsou aktuálně nastaveny pro připojený zdroj dat.|
|[GetProperty](#getproperty)|Získá hodnotu jedné vlastnosti aktuálně nastavenou pro připojený zdroj dat.|
|[Otevřít](#open)|Vytvoří připojení ke zprostředkovateli (zdroji dat) pomocí `CLSID` `CEnumerator` názvu, `ProgID`nebo monikeru poskytnutého volajícím.|
|[OpenFromFileName](#openfromfilename)|Otevře zdroj dat ze souboru zadaného uživatelem zadaným názvem souboru.|
|[OpenFromInitializationString](#openfrominitializationstring)|Otevře zdroj dat určený inicializačním řetězcem.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Umožňuje uživateli vybrat dříve vytvořený soubor odkazu na data a otevřít tak odpovídající zdroj dat.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Otevře objekt zdroje dat pomocí dialogového okna datový odkaz.|

## <a name="remarks"></a>Poznámky

Jednu nebo více relací databáze lze vytvořit pro jedno připojení. Tyto relace jsou reprezentovány nástrojem `CSession`. Chcete-li otevřít připojení před vytvořením relace pomocí `CSession::Open`, je nutné zavolat [CDataSource:: Open](../../data/oledb/cdatasource-open.md) .

Příklad použití `CDataSource`naleznete v ukázce [CatDB](../../overview/visual-cpp-samples.md) .

## <a name="close"></a>CDataSource:: Close

Ukončí připojení uvolněním `m_spInit` ukazatele.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a>CDataSource:: GetInitializationString

Načte inicializační řetězec aktuálně otevřeného zdroje dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Parametry

*pInitializationString*<br/>
mimo Ukazatel na inicializační řetězec.

*bIncludePassword*<br/>
pro **true** , pokud řetězec obsahuje heslo; v opačném případě **false**.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný inicializační řetězec lze použít pro pozdější opětovné otevření tohoto připojení ke zdroji dat.

## <a name="getproperties"></a>CDataSource:: GetProperties

Vrátí informace o vlastnosti požadované pro objekt připojeného zdroje dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Chcete-li získat jedinou vlastnost, použijte [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="getproperty"></a>CDataSource:: GetProperty

Vrátí hodnotu zadané vlastnosti pro objekt připojeného zdroje dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Parametry

*guid*<br/>
pro Identifikátor GUID identifikující sadu vlastností, pro kterou má být vrácena vlastnost.

*propid*<br/>
pro ID vlastnosti, která se má vrátit

*pVariant*<br/>
mimo Ukazatel na variantu, kde `GetProperty` vrací hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

K získání více vlastností použijte [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="open"></a>CDataSource:: Open

Otevře připojení ke zdroji dat pomocí `CLSID`monikeru, `ProgID`nebo `CEnumerator` nebo vyzve uživatele k zadání lokátoru.

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

*CLSID*<br/>
pro `CLSID` Poskytovatele dat.

*pPropSet*<br/>
pro Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

*nPropertySets*<br/>
pro Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur předaných v argumentu *pPropSet* .

*pName*<br/>
pro Název databáze, ke které se chcete připojit.

*pUserName*<br/>
pro Jméno uživatele.

*pPassword*<br/>
pro Heslo uživatele.

*nInitMode*<br/>
pro Režim inicializace databáze. Seznam [](/previous-versions/windows/desktop/ms723127(v=vs.85))platných režimů inicializace naleznete v tématu věnovaném inicializačním vlastnostem v *referenci OLE DB programátora* v Windows SDK. Pokud je *nInitMode* nula, není v sadě vlastností použité k otevření připojení žádný režim inicializace.

*szProgID*<br/>
pro Identifikátor programu

*čítače*<br/>
pro Objekt [CEnumerator –](../../data/oledb/cenumerator-class.md) , který slouží k získání monikeru pro otevření připojení v případě, že volající neurčí `CLSID`.

*hWnd*<br/>
pro Zajistěte, aby se okno táhlo jako nadřazené dialogové okno. Použití přetížení funkce, které používá parametr *HWND* , automaticky vyvolá součásti služby; Podrobnosti najdete v části poznámky.

*dwPromptOptions*<br/>
pro Určuje styl dialogového okna lokátor, který se má zobrazit. Možné hodnoty naleznete v tématu Msdasc. h.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Přetížení metody, které používá parametr *HWND* , otevře objekt zdroje dat s součástmi služby v Oledb32. dll; Tato knihovna DLL obsahuje implementaci funkcí součástí služby, jako je sdružování prostředků, automatické zařazení transakce atd. Další informace najdete v referenčních informacích k OLE DB v [příručce OLE DB programátor](/previous-versions/windows/desktop/ms713643(v=vs.85)).

Přetížení metod, které nepoužívají parametr *HWND* , otevřou objekt zdroje dat bez použití součástí služby v Oledb32. dll. Objekt [CDataSource](../../data/oledb/cdatasource-class.md) otevřený pomocí těchto přetížení funkcí nebude moci využívat žádnou z funkcí součástí služby.

### <a name="example"></a>Příklad

Následující kód ukazuje, jak otevřít zdroj dat Jet 4,0 pomocí šablon OLE DB. Zdroj dat Jet považujete za zdroj dat OLE DB. Nicméně vaše volání `Open` potřebuje dvě sady vlastností: jeden pro DBPROPSET_DBINIT a druhý pro DBPROPSET_JETOLEDB_DBINIT, takže můžete nastavit DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

Otevře zdroj dat ze souboru zadaného uživatelem zadaným názvem souboru.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Parametry

*szFileName*<br/>
pro Název souboru, obvykle připojení ke zdroji dat (. UDL).

Další informace o souborech datových propojení (soubory. UDL) najdete v tématu [Přehled rozhraní Data Link API](/previous-versions/windows/desktop/ms718102(v=vs.85)) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda otevře objekt zdroje dat pomocí součástí služby v Oledb32. dll; Tato knihovna DLL obsahuje implementaci funkcí součástí služby, jako je sdružování prostředků, automatické zařazení transakce atd. Další informace najdete v referenčních informacích k OLE DB v [příručce OLE DB programátor](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="openfrominitializationstring"></a>CDataSource:: OpenFromInitializationString

Otevře zdroj dat určený inicializačním řetězcem zadaným uživatelem.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Parametry

*szInitializationString*<br/>
pro Inicializační řetězec.

*fPromptForInfo*<br/>
pro Pokud je tento argument nastaven na **hodnotu true**, `OpenFromInitializationString` pak nastaví vlastnost DBPROP_INIT_PROMPT na DBPROMPT_COMPLETEREQUIRED, což určuje, že se uživateli zobrazí výzva pouze v případě, že je třeba zadat další informace. To je užitečné v situacích, kdy inicializační řetězec Určuje databázi, která vyžaduje heslo, ale řetězec neobsahuje heslo. Při pokusu o připojení k databázi se uživateli zobrazí výzva k zadání hesla (nebo jakékoli jiné chybějící informace).

Výchozí hodnota je **false**(NEPRAVDA), která určuje, že se uživateli nikdy nebude zobrazovat výzva (nastaví DBPROP_INIT_PROMPT na DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda otevře objekt zdroje dat pomocí součástí služby v Oledb32. dll; Tato knihovna DLL obsahuje implementaci funkcí součástí služby, jako je sdružování prostředků, automatické zařazení transakce atd.

## <a name="openwithpromptfilename"></a>CDataSource:: OpenWithPromptFileName

Tato metoda vyzve uživatele k zadání dialogového okna a pak otevře zdroj dat pomocí souboru zadaného uživatelem.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Zajistěte, aby se okno táhlo jako nadřazené dialogové okno.

*dwPromptOptions*<br/>
pro Určuje styl dialogového okna lokátor, který se má zobrazit. Možné hodnoty naleznete v tématu Msdasc. h.

*szInitialDirectory*<br/>
pro Počáteční adresář, který se má zobrazit v dialogovém okně lokátor.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda otevře objekt zdroje dat pomocí součástí služby v Oledb32. dll; Tato knihovna DLL obsahuje implementaci funkcí součástí služby, jako je sdružování prostředků, automatické zařazení transakce atd. Další informace najdete v referenčních informacích k OLE DB v [příručce OLE DB programátor](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="openwithservicecomponents"></a>CDataSource:: OpenWithServiceComponents

Otevře objekt zdroje dat pomocí součástí služby v Oledb32. dll.

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

*CLSID*<br/>
pro `CLSID` Od poskytovatele dat.

*szProgID*<br/>
pro ID programu poskytovatele dat.

*pPropset*<br/>
pro Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK. Pokud je objekt zdroje dat inicializován, vlastnosti musí patřit do skupiny vlastností zdroje dat. Pokud je stejná vlastnost zadána více než jednou v *pPropset*, pak se tato hodnota používá pro konkrétního zprostředkovatele. Pokud je *ulPropSets* nula, tento parametr se ignoruje.

*ulPropSets*<br/>
pro Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur předaných v argumentu *pPropSet* . Pokud je tato hodnota nulová, zprostředkovatel ignoruje *pPropset*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda otevře objekt zdroje dat pomocí součástí služby v Oledb32. dll; Tato knihovna DLL obsahuje implementaci funkcí součástí služby, jako je sdružování prostředků, automatické zařazení transakce atd. Další informace najdete v referenčních informacích k OLE DB v [příručce OLE DB programátor](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="see-also"></a>Viz také:

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)