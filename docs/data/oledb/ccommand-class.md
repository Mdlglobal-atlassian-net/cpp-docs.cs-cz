---
title: CCommand – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 74cabc19dd21be78771fba177758131d13c8794d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338360"
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
 *TAccessor*  
 Typ třídy přístupového objektu (například `CDynamicParameterAccessor`, `CDynamicStringAccessor`, nebo `CEnumeratorAccessor`), že chcete, aby příkaz použil. Výchozí hodnota je `CNoAccessor`, která určuje, že třída nepodporují parametry nebo výstupní sloupce.  
  
 *TRowset*  
 Typ třídy sady řádků (například `CArrayRowset` nebo `CNoRowset`), že chcete, aby příkaz použil. Výchozí hodnota je `CRowset`.  
  
 *TMultiple*  
 Chcete-li použít technologie OLE DB příkaz, který může vrátit více výsledků, zadejte [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Jinak použijte [cnomultipleresults –](../../data/oledb/cnomultipleresults-class.md). Podrobnosti najdete v tématu [hodnotu IMultipleResults](https://msdn.microsoft.com/library/ms721289.aspx).  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zavřít](#close)|Zavře aktuální příkaz.|  
|[GetNextResult](#getnextresult)|Načte další výsledek při použití více výsledků sad.|  
|[Otevřít](#open)|Spustí a volitelně vazba příkazu.|  
  
### <a name="inherited-methods"></a>Zděděné metody  
  
|||  
|-|-|  
|[Vytvoření](#create)|Vytvoří nový příkaz pro zadaná relace a pak nastaví text příkazu.|  
|[CreateCommand](#createcommand)|Vytvoří nový příkaz.|  
|[GetParameterInfo](#getparameterinfo)|Získá seznam parametrů příkazu, jejich názvy a jejich typy.|  
|[Příprava](#prepare)|Ověří a optimalizuje aktuální příkaz.|  
|[ReleaseCommand](#releasecommand)|Uvolní parametr přistupujícím objektu v případě potřeby a uvolní příkazu.|  
|[SetParameterInfo](#setparameterinfo)|Určuje nativní typ každý parametr příkazu.|  
|[Unprepare –](#unprepare)|Zahodí aktuální plán provádění příkazu.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto třídu používejte, když budete chtít provádět operace, která na základě parametru nebo spuštění příkazu. Pokud potřebujete pouze otevřít jednoduché sady řádků, použijte [CTable](../../data/oledb/ctable-class.md) místo.  
  
 Přístupový objekt třídy, kterou používáte určuje metodu vazby parametrů a data.  
  
 Všimněte si, že nemůžete použít, uložené procedury pomocí zprostředkovatele OLE DB Provider pro Jet protože tento zprostředkovatel nepodporuje uložené procedury (v řetězcích dotazů jsou povoleny pouze konstanty).  

## <a name="close"></a> CCommand::Close
Uvolní přistupujícího objektu sady řádků, asociovaný s příkazem.  
  
### <a name="syntax"></a>Syntaxe

```cpp
void Close();  
```  
  
### <a name="remarks"></a>Poznámky  
 Příkaz používá sadu řádků, přístupový objekt set výsledek a (volitelně) parametr přístupového objektu (na rozdíl od tabulek, které nepodporuje parametry a není nutné přístupový objekt parametr).  
  
 Při spouštění příkazu byste měli volat i `Close` a [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) po příkazu.  
  
 Pokud chcete spustit tak stejný příkaz opakovaně, by měla uvolnit každý přístupový objekt set výsledek voláním `Close` před voláním `Execute`. Na konci série, by měla uvolnit parametr přístupového objektu voláním `ReleaseCommand`. Další z typických možností je volání uložené procedury, která má výstupní parametry. Mnoho poskytovatelů (např. zprostředkovatel OLE DB pro SQL Server) hodnoty výstupních parametrů nebude dostupný dokud ho neukončíte přístupový objekt set výsledek. Volání `Close` zavřete vrácené sady řádků a přístupový objekt set výsledek, ale ne parametr přístupového objektu, takže budete moct načíst hodnoty výstupních parametrů.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete volat `Close` a `ReleaseCommand` při spuštění stejného příkazu opakovaně.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="getnextresult"></a> CCommand::GetNextResult
Načte další výsledek, nastavte, pokud je k dispozici.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected, 
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pulRowsAffected*  
 [/ out] Ukazatel na paměti, kde se vrátí počet řádků, které jsou ovlivněny příkazu.  
  
 *bBind*  
 [in] Určuje, zda vytvořit vazbu příkazu automaticky po spouštěna. Výchozí hodnota je **true**, což způsobí, že příkaz, který má být automaticky vázán. Nastavení *bBind* k **false** brání automatické vazby příkazu tak, aby mohl vytvořit vazbu ručně. (Ruční vazba je zajímavé především uživatelům OLAP).  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je sada výsledků dotazu byla dříve získána, tato funkce uvolní předchozí sady výsledků a odpojuje sloupce. Pokud *bBind* je **true**, naváže nové sloupce.  
  
 Tuto funkci byste měli volat pouze v případě, že jste zadali víc výsledků nastavením `CCommand` parametr šablony *TMultiple*=`CMultipleResults`. 

## <a name="open"></a> CCommand::Open
Spustí a volitelně vazba příkazu.  
  
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
 *Relace*  
 [in] Relace, ve kterém chcete provést příkaz.  
  
 *wszCommand*  
 [in] Příkaz k provedení, předán jako řetězec znaků Unicode. Může mít hodnotu NULL, při použití `CAccessor`, v takovém případě bude příkaz načíst z hodnotu předanou [DEFINE_COMMAND](../../data/oledb/define-command.md) – makro. Zobrazit [ICommand::Execute](https://msdn.microsoft.com/library/ms718095.aspx) v *OLE DB referenční informace pro programátory* podrobnosti.  
  
 *szCommand*  
 [in] Stejné jako *wszCommand* s tím rozdílem, že tento parametr má příkaz řetězec ANSI. Čtvrtý formu této metody může nabývat hodnoty NULL. Viz "Poznámky" dále v tomto tématu podrobnosti.  
  
 *pPropSet*  
 [in] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](https://msdn.microsoft.com/library/ms713696.aspx) v *referenční informace pro OLE DB programátory* ve Windows SDK.  
  
 *pRowsAffected*  
 [/ out] Ukazatel na paměti, kde se vrátí počet řádků, které jsou ovlivněny příkazu. Pokud  *\*pRowsAffected* má hodnotu NULL, je vrácen žádný počet řádků. V opačném případě `Open` nastaví  *\*pRowsAffected* podle následujících podmínek:  
  
|If|Pak...|  
|--------|----------|  
|`cParamSets` Prvek `pParams` je větší než 1|*\*pRowsAffected* představuje celkový počet všech sad parametrů, zadaný v provádění ovlivněných řádků.|  
|Počet ovlivněných řádků není k dispozici|*\*pRowsAffected* je nastavena na hodnotu -1.|  
|Tento příkaz neprovede aktualizaci, odstranění nebo vložení řádků|*\*pRowsAffected* není definován.|  
  
 *guidCommand*  
 [in] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má být použit při analýze text příkazu. Zobrazit [ICommandText::GetCommandText](https://msdn.microsoft.com/library/ms709825.aspx) a [ICommandText::SetCommandText](https://msdn.microsoft.com/library/ms709757.aspx) v *OLE DB referenční informace pro programátory* podrobnosti.  
  
 *bBind*  
 [in] Určuje, zda vytvořit vazbu příkazu automaticky po spouštěna. Výchozí hodnota je **true**, což způsobí, že příkaz, který má být automaticky vázán. Nastavení *bBind* k **false** brání automatické vazby příkazu tak, aby mohl vytvořit vazbu ručně. (Ruční vazba je zajímavé především uživatelům OLAP).  
  
 *ulPropSets*  
 [in] Počet [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury předané *pPropSet* argument.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 První tři formy `Open` provést relaci, vytvoření příkazu a spusťte příkaz vazby parametrů podle potřeby.  
  
 První formulář `Open` přebírá řetězec příkazu kódování Unicode a nemá žádnou výchozí hodnotu.  
  
 Tedy o druhou podobu `Open` použije příkaz řetězec ANSI a žádná výchozí hodnota (k dispozici kvůli zpětné kompatibilitě se stávajícími aplikacemi ANSI).  
  
 Třetí forma `Open` umožňuje příkaz řetězec, který má být hodnota NULL, z důvodu typ **int** s výchozí hodnotou Null. Je určen pro volání `Open(session, NULL);` nebo `Open(session);` vzhledem k tomu, že je hodnota NULL typu **int**. Tato verze vyžaduje a kontrolní výrazy, které **int** parametr mít hodnotu NULL.  
  
 Čtvrtý tvar `Open` Pokud již jste vytvořili příkaz a chcete provést jeden [připravit](../../data/oledb/ccommand-prepare.md) a více provedení.  
  
> [!NOTE]
>  `Open` volání `Execute`, která pak volá `GetNextResult`. 

## <a name="create"></a> CCommand::Create
Volání [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) vytvoření příkazu pro zadané relaci, pak zavolá [ICommandText::SetCommandText](https://msdn.microsoft.com/library/ms709825.aspx) zadat text příkazu.  
  
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
 *Relace*  
 [in] Relace, na kterém chcete vytvořit příkaz.  
  
 *wszCommand*  
 [in] Ukazatel text v kódu Unicode řetězce příkazu.  
  
 *szCommand*  
 [in] Ukazatel na ANSI text příkazu řetězce.  
  
 *guidCommand*  
 [in] Identifikátor GUID, který určuje syntaxi a obecná pravidla pro zprostředkovatele, který má být použit při analýze text příkazu. Popis dialekty, naleznete v tématu [ICommandText::GetCommandText](https://msdn.microsoft.com/library/ms709825.aspx) v *OLE DB referenční informace pro programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 První formulář `Create` příkaz řetězce Unicode. Tedy o druhou podobu `Create` přebírá řetězec ANSI příkazu (k dispozici kvůli zpětné kompatibilitě se stávajícími aplikacemi ANSI).

## <a name="createcommand"></a> CCommand::CreateCommand
Vytvoří nový příkaz.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 *Relace*  
 [in] A `CSession` objekt, který se má přidružit nový příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří příkaz pomocí objektu zadaná relace.  

## <a name="getparameterinfo"></a> CCommand::GetParameterInfo
Získá seznam parametrů příkazu, jejich názvy a jejich typy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [ICommandWithParameters::GetParameterInfo](https://msdn.microsoft.com/library/ms714917.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.   

## <a name="prepare"></a> CCommand::Prepare
Ověří a optimalizuje aktuální příkaz.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *cExpectedRuns*  
 [in] Počet pokusů, které očekáváte, že spustíte příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zabalí metodu OLE DB [ICommandPrepare::Prepare](https://msdn.microsoft.com/library/ms718370.aspx).  

## <a name="releasecommand"></a> CCommand::ReleaseCommand
Uvolní parametr přístupového objektu a následně uvolní příkazu samého.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
```  
  
### <a name="remarks"></a>Poznámky  
 `ReleaseCommand` používá se společně s `Close`. Zobrazit [Zavřít](../../data/oledb/ccommand-close.md) podrobnosti o použití. 

## <a name="setparameterinfo"></a> CCommand::SetParameterInfo
Určuje nativní typ každý parametr příkazu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [ICommandWithParameters::SetParameterInfo](https://msdn.microsoft.com/library/ms725393.aspx) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="unprepare"></a> CCommand::Unprepare
Zahodí aktuální plán provádění příkazu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::Unprepare() throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zabalí metodu OLE DB [ICommandPrepare::Unprepare](https://msdn.microsoft.com/library/ms719635.aspx). 
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)