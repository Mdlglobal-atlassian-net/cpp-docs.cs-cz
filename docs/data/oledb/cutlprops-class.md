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
ms.openlocfilehash: 3498ec1250d9443007acb3b12ec25983a71587d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211104"
---
# <a name="cutlprops-class"></a>CUtlProps – třída

Implementuje vlastnosti pro celou řadu OLE DBch vlastností rozhraní (například `IDBProperties`, `IDBProperties`a `IRowsetInfo`).

## <a name="syntax"></a>Syntaxe

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída obsahující `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetPropValue](#getpropvalue)|Načte vlastnost ze sady vlastností.|
|[IsValidValue](#isvalidvalue)|Slouží k ověření hodnoty před nastavením vlastnosti.|
|[OnInterfaceRequested](#oninterfacerequested)|Zpracovává požadavky na volitelné rozhraní, když příjemce volá metodu na rozhraní pro vytvoření objektu.|
|[V-PropertyChanged](#onpropertychanged)|Volá se po nastavení vlastnosti pro zpracování zřetězených vlastností.|
|[SetPropValue](#setpropvalue)|Nastaví vlastnost v sadě vlastností.|

## <a name="remarks"></a>Poznámky

Většina této třídy je podrobností implementace.

`CUtlProps` obsahuje dva členy pro interní nastavení vlastností: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) a [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Další informace o makrech použitých v mapě sady vlastností naleznete v tématu [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) a [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a>CUtlProps:: GetPropValue

Načte vlastnost ze sady vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
pro Identifikátor GUID pro PropSet.

*dwPropId*<br/>
pro Index vlastnosti.

*pvValue*<br/>
mimo Ukazatel na variantu, která obsahuje novou hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

`Failure` při selhání a v případě úspěchu S_OK.

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a>CUtlProps:: IsValidValue

Slouží k ověření hodnoty před nastavením vlastnosti.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Index do pole sady vlastností; nula, pokud je k dispozici pouze jedna sada vlastností.

*pDBProp*<br/>
ID vlastnosti a nová hodnota ve struktuře [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Výchozí návratová hodnota je S_OK.

### <a name="remarks"></a>Poznámky

Pokud máte nějaké rutiny ověřování, které chcete spustit na hodnotě, kterou se chystáte použít k nastavení vlastnosti, měli byste tuto funkci přepsat. Můžete například ověřit DBPROP_AUTH_PASSWORD proti tabulce hesel, abyste určili platnou hodnotu.

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a>CUtlProps:: OnInterfaceRequested

Zpracovává požadavky na volitelné rozhraní, když příjemce volá metodu na jednom z rozhraní pro vytvoření objektu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parametry

*riid*<br/>
pro IID pro požadované rozhraní. Další podrobnosti najdete v popisu parametru *riid* `ICommand::Execute` v referenční příručce pro *OLE DB programátora* (v sadě *MDAC SDK*).

### <a name="remarks"></a>Poznámky

`OnInterfaceRequested` zpracovává požadavky spotřebitelů na volitelné rozhraní, když příjemce volá metodu na jednom z rozhraní pro vytváření objektů (například `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`nebo `ICommand`). Nastaví odpovídající vlastnost OLE DB pro požadované rozhraní. Například pokud spotřebitel požaduje `IID_IRowsetLocate`, `OnInterfaceRequested` nastaví rozhraní `DBPROP_IRowsetLocate`. Tím se zachová správný stav při vytváření sady řádků.

Tato metoda je volána, když příjemce volá `IOpenRowset::OpenRowset` nebo `ICommand::Execute`.

Pokud příjemce otevře objekt a požádá o volitelné rozhraní, poskytovatel by měl nastavit vlastnost přidruženou k tomuto rozhraní na VARIANT_TRUE. Aby bylo možné použít zpracování specifické pro vlastnosti, `OnInterfaceRequested` je volána před voláním metody `Execute` poskytovatele. Ve výchozím nastavení `OnInterfaceRequested` zpracovává následující rozhraní:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Pokud chcete zpracovat jiná rozhraní, přepište tuto funkci ve zdroji dat, relaci, příkazu nebo třídě sady řádků pro zpracování funkcí. Vaše přepsání by mělo projít běžnými rozhraními vlastností set/get, aby bylo zajištěno, že vlastnosti nastavení také nastaví všechny zřetězené vlastnosti [(viz](../../data/oledb/cutlprops-onpropertychanged.md)přepsané).

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a>CUtlProps::-PropertyChanged

Volá se po nastavení vlastnosti pro zpracování zřetězených vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Index do pole sady vlastností; nula, pokud je k dispozici pouze jedna sada vlastností.

*pDBProp*<br/>
ID vlastnosti a nová hodnota ve struktuře [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Výchozí návratová hodnota je S_OK.

### <a name="remarks"></a>Poznámky

Pokud chcete zpracovat zřetězené vlastnosti, jako jsou například záložky nebo aktualizace, jejichž hodnoty jsou závislé na hodnotě jiné vlastnosti, měli byste tuto funkci přepsat.

### <a name="example"></a>Příklad

V této funkci uživatel získá ID vlastnosti z parametru `DBPROP*`. Nyní je možné porovnat ID s vlastností a řetězit. Když je vlastnost nalezena, `SetProperties` je volána s vlastností, která bude nyní nastavena ve spojení s jinou vlastností. V takovém případě, pokud jeden získá vlastnost `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`nebo `DBPROP_ORDEREDBOOKMARKS`, může jedna nastavit vlastnost `DBPROP_BOOKMARKS`.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a>CUtlProps:: SetPropValue

Nastaví vlastnost v sadě vlastností.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
pro Identifikátor GUID pro PropSet.

*dwPropId*<br/>
pro Index vlastnosti.

*pvValue*<br/>
pro Ukazatel na variantu, která obsahuje novou hodnotu vlastnosti.

### <a name="return-value"></a>Návratová hodnota

`Failure` při selhání a v případě úspěchu S_OK.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
