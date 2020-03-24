---
title: CCommand – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 5da843405cfec4d1d571a3140f132513d8b068ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212079"
---
# <a name="ccommand-class"></a>CCommand – třída

Poskytuje metody pro nastavení a spuštění příkazu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Typ přístupové třídy (například `CDynamicParameterAccessor`, `CDynamicStringAccessor`nebo `CEnumeratorAccessor`), kterou má příkaz použít. Výchozí hodnota je `CNoAccessor`, která určuje, že Třída nepodporuje parametry nebo výstupní sloupce.

*TRowset*<br/>
Typ třídy sady řádků (například `CArrayRowset` nebo `CNoRowset`), kterou má příkaz použít. Výchozí formát je `CRowset`.

*TMultiple*<br/>
Chcete-li použít příkaz OLE DB, který může vracet více výsledků, zadejte [CMultipleResults –](../../data/oledb/cmultipleresults-class.md). V opačném případě použijte [CNoMultipleResults –](../../data/oledb/cnomultipleresults-class.md). Podrobnosti najdete v tématu [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Uzavírací](#close)|Zavře aktuální příkaz.|
|[GetNextResult](#getnextresult)|Načte další výsledek při použití více sad výsledků dotazu.|
|[Otevírají](#open)|Provede a případně vytvoří vazby k příkazu.|

### <a name="inherited-methods"></a>Zděděné metody

|||
|-|-|
|[Vytvoření](#create)|Vytvoří nový příkaz pro zadanou relaci a pak nastaví text příkazu.|
|[CreateCommand](#createcommand)|Vytvoří nový příkaz.|
|[GetParameterInfo](#getparameterinfo)|Načte seznam parametrů příkazu, jejich názvy a jejich typy.|
|[Systém](#prepare)|Ověří a optimalizuje aktuální příkaz.|
|[ReleaseCommand](#releasecommand)|V případě potřeby uvolní přistupující objekt parametru a pak uvolní příkaz.|
|[SetParameterInfo](#setparameterinfo)|Určuje nativní typ každého parametru příkazu.|
|[Odpřipravit](#unprepare)|Zahodí aktuální plán spuštění příkazu.|

## <a name="remarks"></a>Poznámky

Tuto třídu použijte v případě, že potřebujete provést operaci založenou na parametrech nebo provést příkaz. Pokud stačí pouze otevřít jednoduchou sadu řádků, použijte místo toho hodnotu [CTable](../../data/oledb/ctable-class.md) .

Přístupová třída, kterou používáte, určuje metodu vazby parametrů a dat.

Všimněte si, že nemůžete použít uložené procedury u poskytovatele OLE DB pro stroj Jet, protože tento zprostředkovatel nepodporuje uložené procedury (v řetězcích dotazů jsou povoleny pouze konstanty).

## <a name="ccommandclose"></a><a name="close"></a>CCommand:: Close

Uvolní sadu řádků přistupující k příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Příkaz používá sadu řádků, přístupový objekt sady výsledků a (volitelně) přístup k parametru (na rozdíl od tabulek, které nepodporují parametry a nepotřebují přistupující objekt parametru).

Při spuštění příkazu byste měli volat `Close` i [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) po příkazu.

Při opakovaném spuštění stejného příkazu byste měli vydávat každý přístupový objekt sady výsledků voláním `Close` před voláním `Execute`. Na konci série byste měli uvolnit přístup k parametru voláním `ReleaseCommand`. Dalším běžným scénářem je volání uložené procedury, která má výstupní parametry. U mnoha poskytovatelů (například poskytovatele OLE DB pro SQL Server) nebudou hodnoty výstupních parametrů dostupné, dokud nezavřete přístupový objekt sady výsledků. Zavolejte `Close`, aby se zavřela vrácená sada řádků a přístupového objektu sady výsledků, ale nikoli přístup k parametru, což vám umožní načíst výstupní hodnoty parametrů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak lze volat `Close` a `ReleaseCommand` při opakovaném spuštění stejného příkazu.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand:: GetNextResult

Načte další sadu výsledků, pokud je k dispozici.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parametry

*pulRowsAffected*<br/>
[in/out] Ukazatel na paměť, kde je vrácen počet řádků ovlivněných příkazem.

*bBind*<br/>
pro Určuje, zda se má při spuštění vytvořit vazba příkazu automaticky. Výchozí hodnota je **true**, což způsobí, že se příkaz automaticky sváže. Nastavením *bBind* na **false** zabráníte automatické vazbě příkazu, abyste se mohli svázat ručně. (Ruční vazba je zvláště důležitá pro uživatele OLAP.)

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud byla sada výsledků dříve načtena, tato funkce uvolní předchozí sadu výsledků dotazu a odpojí sloupce. Pokud *bBind* má bBind **hodnotu true**, sváže nové sloupce.

Tuto funkci byste měli zavolat pouze v případě, že jste zadali více výsledků nastavením parametru šablony `CCommand` *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand:: Open

Provede a případně vytvoří vazby k příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
pro Relace, ve které se má příkaz Spustit.

*wszCommand*<br/>
pro Příkaz, který se má provést, se předává jako řetězec Unicode. Může mít hodnotu NULL při použití `CAccessor`, v takovém případě se příkaz načte z hodnoty předané do makra [DEFINE_COMMAND](../../data/oledb/define-command.md) . Podrobnosti najdete v tématu [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) v *Referenční příručce programátora OLE DB* .

*szCommand*<br/>
pro Stejné jako *wszCommand* s tím rozdílem, že tento parametr přebírá řetězec příkazu ANSI. Čtvrtá forma této metody může mít hodnotu NULL. Podrobnosti najdete v části "poznámky" dále v tomto tématu.

*pPropSet*<br/>
pro Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

*pRowsAffected*<br/>
[in/out] Ukazatel na paměť, kde je vrácen počet řádků ovlivněných příkazem. Pokud *\*pRowsAffected* má hodnotu null, není vrácen žádný počet řádků. V opačném případě `Open` nastaví *\*pRowsAffected* podle následujících podmínek:

|Pokud uživatel|Potom si|
|--------|----------|
|`cParamSets` prvek `pParams` je větší než 1.|*\*pRowsAffected* představuje celkový počet řádků ovlivněných všemi sadami parametrů určenými při provádění.|
|Počet ovlivněných řádků není k dispozici.|*\*pRowsAffected* je nastavená na hodnotu-1.|
|Příkaz neaktualizuje, neodstraní ani nevloží řádky.|*\*pRowsAffected* není definován.|

*guidCommand*<br/>
pro Identifikátor GUID, který určuje syntaxi a obecná pravidla pro poskytovatele, který se má použít při analýze textu příkazu. Podrobnosti naleznete v tématu [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) a [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) v *Referenční příručce programátora OLE DB* .

*bBind*<br/>
pro Určuje, zda se má při spuštění vytvořit vazba příkazu automaticky. Výchozí hodnota je **true**, což způsobí, že se příkaz automaticky sváže. Nastavením *bBind* na **false** zabráníte automatické vazbě příkazu, abyste se mohli svázat ručně. (Ruční vazba je zvláště důležitá pro uživatele OLAP.)

*ulPropSets*<br/>
pro Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur předaných v argumentu *pPropSet* .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

První tři formy `Open` pobírají relaci, vytvoří příkaz a spustí příkaz, podle potřeby vytvoří vazbu libovolných parametrů.

První forma `Open` přebírá řetězec příkazu Unicode a nemá žádnou výchozí hodnotu.

Druhá forma `Open` přebírá řetězec příkazu ANSI a nemá žádnou výchozí hodnotu (poskytuje zpětnou kompatibilitu s existujícími aplikacemi standardu ANSI).

Třetí forma `Open` umožňuje, aby byl řetězec příkazu NULL, protože typ **int** má výchozí hodnotu null. Je k dispozici pro volání `Open(session, NULL);` nebo `Open(session);`, protože hodnota NULL je typu **int**. Tato verze vyžaduje a vyhodnotí, že parametr **int** má hodnotu null.

Pokud jste již vytvořili příkaz a chcete provést jeden připravený a více [spuštění, použijte](../../data/oledb/ccommand-prepare.md) čtvrtou formu `Open`.

> [!NOTE]
>  `Open` volá `Execute`, která zase volá `GetNextResult`.

## <a name="ccommandcreate"></a><a name="create"></a>CCommand:: Create

Zavolá metodu [CCommand:: CreateCommand](../../data/oledb/ccommand-createcommand.md) k vytvoření příkazu pro zadanou relaci a pak zavolá metodu [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) , která určuje text příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
pro Relace, na které se má příkaz vytvořit.

*wszCommand*<br/>
pro Ukazatel na text v kódu Unicode řetězce příkazu.

*szCommand*<br/>
pro Ukazatel na text ANSI řetězce příkazu.

*guidCommand*<br/>
pro Identifikátor GUID, který určuje syntaxi a obecná pravidla pro poskytovatele, který se má použít při analýze textu příkazu. Popis dialektů naleznete v tématu [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) v *referenci OLE DB programátora*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

První forma `Create` přebírá řetězec příkazu Unicode. Druhá forma `Create` přebírá řetězec příkazu ANSI (poskytnutý kvůli zpětné kompatibilitě se stávajícími aplikacemi standardu ANSI).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand:: CreateCommand

Vytvoří nový příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
pro Objekt `CSession`, který se má přidružit k novému příkazu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří příkaz pomocí zadaného objektu Session.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand:: GetParameterInfo

Načte seznam parametrů příkazu, jejich názvy a jejich typy.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parametry

Viz [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::P ravit

Ověří a optimalizuje aktuální příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parametry

*cExpectedRuns*<br/>
pro Počet, kolikrát jste očekávali provedení příkazu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda zalomí metodu OLE DB [ICommandPrepare::P ravit](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand:: ReleaseCommand

Uvolní přistupující objekt parametru a pak uvolní samotný příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Poznámky

`ReleaseCommand` se používá ve spojení s `Close`. Podrobnosti o využití najdete v tématu [zavření](../../data/oledb/ccommand-close.md) .

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand:: SetParameterInfo

Určuje nativní typ každého parametru příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parametry

Viz [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand:: Unprepare

Zahodí aktuální plán spuštění příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda zabalí metodu OLE DB [ICommandPrepare:: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
