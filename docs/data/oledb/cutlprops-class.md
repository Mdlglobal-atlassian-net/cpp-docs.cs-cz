---
title: CUtlProps – třída
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- CUtlProps
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 5accc7e5901e8082f5483bca5439462a3c4ffd24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525759"
---
# <a name="cutlprops-class"></a>CUtlProps – třída

Implementuje vlastnosti pro celou řadu vlastností rozhraní technologie OLE DB (například `IDBProperties`, `IDBProperties`, a `IRowsetInfo`).

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída, která obsahuje `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Getpropvalue –](#getpropvalue)|Získá vlastnost ze sady vlastností.|
|[IsValidValue –](#isvalidvalue)|Slouží k ověření hodnotu před nastavením vlastnosti.|
|[OnInterfaceRequested](#oninterfacerequested)|Zpracovává požadavky pro volitelné rozhraní, když příjemce volá metodu pro vytvoření rozhraní objektu.|
|[OnPropertyChanged –](#onpropertychanged)|Volá se po nastavení vlastnosti pro zpracování zřetězené vlastnosti.|
|[Setpropvalue –](#setpropvalue)|Nastaví vlastnost v sadu vlastností.|

## <a name="remarks"></a>Poznámky

Většina této třídy je podrobnost implementace.

`CUtlProps` obsahuje dva členy pro nastavení vlastnosti interně: [getpropvalue –](../../data/oledb/cutlprops-getpropvalue.md) a [setpropvalue –](../../data/oledb/cutlprops-setpropvalue.md).

Další informace o makra použít v mapování sady vlastností, naleznete v tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) a [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="getpropvalue"></a> CUtlProps::GetPropValue

Získá vlastnost ze sady vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
[in] Identifikátor GUID sada vlastností.

*dwPropId*<br/>
[in] Vlastnost index.

*pvValue*<br/>
[out] Ukazatel na hodnotu typu variant, která obsahuje novou hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

`Failure` na selhání a S_OK v případě úspěšného ověření.

## <a name="isvalidvalue"></a> CUtlProps::IsValidValue

Slouží k ověření hodnotu před nastavením vlastnosti.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Index pole vlastností nastavenou; nula, pokud existuje pouze jedna vlastnost sady.

*pDBProp*<br/>
ID vlastnosti a nová hodnota v [DBPROP](/previous-versions/windows/desktop/ms717970) struktury.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT. Výchozí návratová hodnota je S_OK.

### <a name="remarks"></a>Poznámky

Pokud máte jakékoli rutiny ověřování, které chcete spustit na hodnotu, která se chystáte použít k nastavení vlastnosti, by měly přepsat tuto funkci. Například může ověřovat DBPROP_AUTH_PASSWORD proti heslo tabulky, abyste zjistili platnou hodnotu.

## <a name="oninterfacerequested"></a> CUtlProps::OnInterfaceRequested

Zpracovává požadavky pro volitelné rozhraní, když příjemce volá metodu v jednom objektu vytváření rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parametry

*riid*<br/>
[in] Identifikátor IID pro požadované rozhraní. Další podrobnosti naleznete v popisu *riid* parametr `ICommand::Execute` v *OLE DB referenční informace pro programátory* (v *sadu MDAC SDK*).

### <a name="remarks"></a>Poznámky

`OnInterfaceRequested` zpracovává požadavky příjemce pro volitelné rozhraní, když příjemce volá metodu v jednom objektu vytváření rozhraní (například `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`, nebo `ICommand`). Nastaví vlastnost odpovídající OLE DB pro požadované rozhraní. Například, pokud uživatel požaduje `IID_IRowsetLocate`, `OnInterfaceRequested` nastaví `DBPROP_IRowsetLocate` rozhraní. To udržuje správný stav při vytváření sady řádků.

Tato metoda je volána, když příjemce volá `IOpenRowset::OpenRowset` nebo `ICommand::Execute`.

Pokud příjemce otevře objekt a vyžádá volitelné rozhraní, poskytovateli třeba nastavit vlastnosti přidružené k rozhraní k VARIANT_TRUE. Pokud chcete povolit zpracování specifické pro vlastnost `OnInterfaceRequested` je volána před provedením poskytovatele `Execute` metoda je volána. Ve výchozím nastavení `OnInterfaceRequested` zpracovává následujících rozhraní:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Pokud chcete zpracovávat další rozhraní, přepište tuto funkci ve třídě zdroje, relace, příkazu nebo sady řádků dat pro funkci procesu. Přepsání by měl projít rozhraní normální nastavení nebo získání vlastnosti k zajištění, že nastavení vlastností také nastaví všechny zřetězené vlastnosti (viz [OnPropertyChanged –](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="onpropertychanged"></a> CUtlProps::OnPropertyChanged

Volá se po nastavení vlastnosti pro zpracování zřetězené vlastnosti.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Index pole vlastností nastavenou; nula, pokud existuje pouze jedna vlastnost sady.

*pDBProp*<br/>
ID vlastnosti a nová hodnota v [DBPROP](/previous-versions/windows/desktop/ms717970) struktury.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT. Výchozí návratová hodnota je S_OK.

### <a name="remarks"></a>Poznámky

Pokud chcete zpracovat zřetězené vlastnosti, jako je například záložek nebo aktualizace, jejichž hodnoty jsou závislé na hodnotě jiné vlastnosti, by měly přepsat tuto funkci.

### <a name="example"></a>Příklad

V této funkci uživatel získá ID vlastnosti z `DBPROP*` parametru. Nyní je možné porovnat ID pro vlastnosti řetězce. Když je vlastnost nalezena, `SetProperties` je volána s vlastností, které se nastaví ve spojení s jiné vlastnosti. V takovém případě pokud se z nich dostane `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, nebo `DBPROP_ORDEREDBOOKMARKS` , jeden můžete nastavit `DBPROP_BOOKMARKS` vlastnost.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a> CUtlProps::SetPropValue

Nastaví vlastnost v sadu vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
[in] Identifikátor GUID sada vlastností.

*dwPropId*<br/>
[in] Vlastnost index.

*pvValue*<br/>
[in] Ukazatel na hodnotu typu variant, která obsahuje novou hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

`Failure` na selhání a S_OK v případě úspěšného ověření.

## <a name="see-also"></a>Viz také

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)