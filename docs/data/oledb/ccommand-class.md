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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368620"
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

*TPřipis*<br/>
Typ třídy přistupujícího `CDynamicStringAccessor`zařízení `CEnumeratorAccessor`(například `CDynamicParameterAccessor`, , nebo), kterou má příkaz použít. Výchozí hodnota `CNoAccessor`je , která určuje, že třída nepodporuje parametry nebo výstupní sloupce.

*Sada tslád*<br/>
Typ třídy sady řádků `CArrayRowset` (například nebo), `CNoRowset`kterou má příkaz použít. Výchozí formát je `CRowset`.

*TVíce*<br/>
Chcete-li použít příkaz OLE DB, který může vrátit více výsledků, zadejte [CMultipleResults](../../data/oledb/cmultipleresults-class.md). V opačném případě použijte [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Podrobnosti naleznete v [tématu IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zavřít](#close)|Zavře aktuální příkaz.|
|[GetNextVýsledek](#getnextresult)|Načte další výsledek při použití více sad výsledků.|
|[Otevřít](#open)|Provede a volitelně sváže příkaz.|

### <a name="inherited-methods"></a>Zděděné metody

|||
|-|-|
|[Vytvořit](#create)|Vytvoří nový příkaz pro zadanou relaci a nastaví text příkazu.|
|[Příkaz CreateCommand](#createcommand)|Vytvoří nový příkaz.|
|[GetParameterInfo](#getparameterinfo)|Získá seznam parametrů příkazu, jejich názvy a jejich typy.|
|[Příprava](#prepare)|Ověří a optimalizuje aktuální příkaz.|
|[ReleaseCommand](#releasecommand)|V případě potřeby uvolní přistupující objekt parametru a poté vydá příkaz.|
|[SetParameterInfo](#setparameterinfo)|Určuje nativní typ každého parametru příkazu.|
|[Zrušit přípravu](#unprepare)|Zahodí aktuální plán spuštění příkazu.|

## <a name="remarks"></a>Poznámky

Tuto třídu použijte, pokud potřebujete provést operaci založenou na parametrech nebo provést příkaz. Pokud potřebujete pouze otevřít jednoduchou sadu řádků, použijte místo toho [CTable.](../../data/oledb/ctable-class.md)

Třída přistupujícího objektu, kterou používáte, určuje metodu parametrů vazby a dat.

Všimněte si, že nelze použít uložené procedury s zprostředkovatelem OLE DB pro Jet, protože tento zprostředkovatel nepodporuje uložené procedury (v řetězcích dotazu jsou povoleny pouze konstanty).

## <a name="ccommandclose"></a><a name="close"></a>CCommand::Zavřít

Uvolní přistupovací sadu řádků přidruženou k příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Příkaz používá sadu řádků, přistupující objekt sady výsledků a (volitelně) přistupující objekt parametru (na rozdíl od tabulek, které nepodporují parametry a nepotřebují přistupující objekt parametru).

Při spuštění příkazu, měli `Close` byste volat oba a [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) za příkaz.

Pokud chcete spustit stejný příkaz opakovaně, měli byste uvolnit každý `Close` přistupující sekatel sady výsledků voláním před voláním `Execute`. Na konci řady byste měli uvolnit přistupující `ReleaseCommand`objekt parametru voláním . Dalším běžným scénářem je volání uložené procedury, která má výstupní parametry. U mnoha zprostředkovatelů (například zprostředkovatele OLE DB pro SQL Server) nebudou hodnoty výstupních parametrů přístupné, dokud nezavřete přistupující ho objektu sady výsledků. Volání `Close` zavřete vrácenou sadu řádků a přístupový objekt sady výsledků, ale nikoli přistupující objekt parametru, což umožňuje načíst hodnoty výstupních parametrů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Close` `ReleaseCommand` můžete volat a při opakovaném spuštění stejného příkazu.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand::GetNextResult

Načte další sadu výsledků, pokud je k dispozici.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parametry

*pulRowsAffected*<br/>
[dovnitř/ven] Ukazatel na paměť, kde je vrácen počet řádků ovlivněných příkazem.

*bVazba*<br/>
[v] Určuje, zda má být příkaz po provedení automaticky svázán. Výchozí hodnota je **true**, která způsobí, že příkaz bude automaticky vázán. Nastavení *bBind* na **false** zabraňuje automatické vazbě příkazu, takže můžete vázat ručně. (Ruční vazba je zvláště zajímavá pro uživatele OLAP.)

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Pokud byla sada výsledků dříve načtena, tato funkce uvolní předchozí sadu výsledků a odpojí sloupce. Pokud *bBind* je **true**, váže nové sloupce.

Tuto funkci byste měli volat pouze v případě, že jste zadali více výsledků nastavením `CCommand` parametru šablony *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand::Otevřít

Provede a volitelně sváže příkaz.

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

*Relace*<br/>
[v] Relace, ve kterém chcete spustit příkaz.

*příkaz wsz*<br/>
[v] Příkaz, který má být proveden, předán jako řetězec Unicode. Může být null `CAccessor`při použití , v takovém případě bude příkaz načten z hodnoty předané [DEFINE_COMMAND](../../data/oledb/define-command.md) makro. Podrobnosti naleznete v [tématu ICommand::Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) in the *OLE DB Programmer's Reference.*

*szCommand*<br/>
[v] Stejné jako *wszCommand* s tím rozdílem, že tento parametr trvá ansi příkazový řetězec. Čtvrtá forma této metody může mít hodnotu NULL. Podrobnosti naleznete dále v části Poznámky v tomto tématu.

*pPropSet*<br/>
[v] Ukazatel na pole [dbpropset](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [Sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci programátora OLE DB* v sadě Windows SDK.

*ovlivněné pRows*<br/>
[dovnitř/ven] Ukazatel na paměť, kde je vrácen počet řádků ovlivněných příkazem. Pokud * \*pRowsAffected* je NULL, je vrácena žádná počet řádků. V `Open` opačném případě nastaví * \*pRowsAffected* podle následujících podmínek:

|Pokud uživatel|Pak...|
|--------|----------|
|Prvek `cParamSets` `pParams` je větší než 1|pRowsAffected představuje celkový počet řádků ovlivněných všemi sadami parametrů zadanými v provádění. * \**|
|Počet ovlivněných řádků není k dispozici.|pRowsAffected je nastavena na -1. * \**|
|Příkaz neaktualizuje, neodstraní ani nevkládá řádky|pRowsAffected není definován. * \**|

*příkaz guidCommand*<br/>
[v] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má být používán při analýzě textu příkazu. Podrobnosti naleznete v tématech [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) a [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) v *referenci programátora OLE DB.*

*bVazba*<br/>
[v] Určuje, zda má být příkaz po provedení automaticky svázán. Výchozí hodnota je **true**, která způsobí, že příkaz bude automaticky vázán. Nastavení *bBind* na **false** zabraňuje automatické vazbě příkazu, takže můžete vázat ručně. (Ruční vazba je zvláště zajímavá pro uživatele OLAP.)

*ulPropSady*<br/>
[v] Počet [dbpropset](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury předány v *pPropSet* argument.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

První tři formy `Open` trvat relace, vytvořit příkaz a spustit příkaz, vazba všechny parametry podle potřeby.

První forma `Open` má řetězec příkazu Unicode a nemá žádnou výchozí hodnotu.

Druhá forma `Open` má příkazový řetězec ANSI a žádná výchozí hodnota (za předpokladu, že zpětná kompatibilita s existujícími aplikacemi ANSI).

Třetí forma `Open` umožňuje příkazový řetězec být NULL, z důvodu typu **int** s výchozí hodnotou NULL. Je k dispozici `Open(session, NULL);` pro `Open(session);` volání nebo protože NULL je typu **int**. Tato verze vyžaduje a tvrdí, že parametr **int** má hodnotu NULL.

Použijte čtvrtý formulář, `Open` pokud jste již vytvořili příkaz a chcete provést jeden [Připravit](../../data/oledb/ccommand-prepare.md) a více spuštění.

> [!NOTE]
> `Open`hovory `Execute`, které `GetNextResult`zase volá .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand::Vytvořit

Volá [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) k vytvoření příkazu pro zadanou relaci, pak zavolá [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) a určí text příkazu.

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

*Relace*<br/>
[v] Relace, na které chcete vytvořit příkaz.

*příkaz wsz*<br/>
[v] Ukazatel na text Unicode příkazového řetězce.

*szCommand*<br/>
[v] Ukazatel na text ANSI příkazového řetězce.

*příkaz guidCommand*<br/>
[v] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má být používán při analýzě textu příkazu. Popis dialektů naleznete v [tématu ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) v *referenční příručce programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

První forma `Create` trvá unicode příkazový řetězec. Druhá forma `Create` má příkazový řetězec ANSI (za předpokladu, že zpětná kompatibilita s existujícími aplikacemi ANSI).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand::Příkaz CreateCommand

Vytvoří nový příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parametry

*Relace*<br/>
[v] Objekt, `CSession` který má být přidružen k novému příkazu.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří příkaz pomocí zadaného objektu relace.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand::GetParameterInfo

Získá seznam parametrů příkazu, jejich názvy a jejich typy.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parametry

Viz [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) v *odkazu programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::Prepare

Ověří a optimalizuje aktuální příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parametry

*cExpectedRuns*<br/>
[v] Počet, kolikrát očekáváte spuštění příkazu.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda zabalí metodu OLE DB [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand::ReleaseCommand

Uvolní přistupující objekt parametru a potom uvolní samotný příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Poznámky

`ReleaseCommand`se používá ve `Close`spojení s . Podrobnosti o použití najdete v tématu [Zavřít.](../../data/oledb/ccommand-close.md)

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand::SetParameterInfo

Určuje nativní typ každého parametru příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parametry

Viz [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) v *odkazu programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand::Nepřipravit

Zahodí aktuální plán spuštění příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda zabalí metodu OLE DB [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Viz také

[Šablony spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Odkaz na šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
