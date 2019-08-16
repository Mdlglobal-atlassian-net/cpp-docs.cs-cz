---
title: IDBSchemaRowsetImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: 3c34f84254fc57b6cd5f8b4763faac313a01636b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501396"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl – třída

Poskytuje implementaci pro sady řádků schématu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Parametry

*SessionClass*<br/>
Třída, která `IDBSchemaRowsetImpl` je zděděna. Obvykle tato třída bude třídou relace uživatele.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CheckRestrictions](#checkrestrictions)|Kontroluje platnost omezení proti sadě řádků schématu.|
|[CreateSchemaRowset](#createschemarowset)|Implementuje funkci tvůrce objektu modelu COM pro objekt určený parametrem šablony.|
|[SetRestrictions](#setrestrictions)|Určuje, která omezení podporuje konkrétní sada řádků schématu.|

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[GetRowset](#getrowset)|Vrátí sadu řádků schématu.|
|[GetSchemas](#getschemas)|Vrátí seznam sad řádků schématu přístupných pomocí [IDBSchemaRowsetImpl:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|

## <a name="remarks"></a>Poznámky

Tato třída implementuje rozhraní [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) a funkci založena Creator [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).

OLE DB používá sady řádků schématu k vrácení dat o datech ve zprostředkovateli. Tato data se často nazývají "metadata". Ve výchozím nastavení musí `DBSCHEMA_TABLES`poskytovatel vždy podporovat, `DBSCHEMA_COLUMNS`a `DBSCHEMA_PROVIDER_TYPES`, jak je popsáno v části [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenci OLE DB programátora*. Sady řádků schématu jsou označeny v mapě schématu. Informace o položkách map schématu naleznete v tématu [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).

Průvodce poskytovatelem OLE DB v průvodci objekty ATL automaticky generuje kód pro sady řádků schématu v projektu. (Ve výchozím nastavení Průvodce podporuje výše uvedené povinná sada řádků schématu.) Při vytváření příjemce pomocí Průvodce objekty ATL používá Průvodce sady řádků schématu ke svázání správných dat s poskytovatelem. Pokud neimplementujete sady řádků schématu k poskytnutí správných metadat, průvodce nebude navazovat správná data.

Informace o tom, jak podporovat sady řádků schématu ve zprostředkovateli, naleznete v tématu [podpůrné sady řádků schématu](../../data/oledb/supporting-schema-rowsets.md).

Další informace o sadách řádků schématu naleznete v tématu [sady řádků schématu](/previous-versions/windows/desktop/ms712921(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="checkrestrictions"></a> IDBSchemaRowsetImpl::CheckRestrictions

Kontroluje platnost omezení proti sadě řádků schématu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Parametry

*rguidSchema*<br/>
pro Odkaz na požadovaný identifikátor GUID sady řádků schématu (například `DBSCHEMA_TABLES`).

*cRestrictions –*<br/>
pro Počet omezení, která příjemce předal pro sadu řádků schématu.

*rgRestrictions*<br/>
pro Pole délky *CRestrictions –* hodnot omezení, které mají být nastaveny. Další informace najdete v popisu parametru *rgRestrictions* v [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

### <a name="remarks"></a>Poznámky

Slouží `CheckRestrictions` ke kontrole platnosti omezení proti sadě řádků schématu. Kontroluje omezení pro `DBSCHEMA_TABLES`sady řádků `DBSCHEMA_COLUMNS`schématu, `DBSCHEMA_PROVIDER_TYPES` a. Zavolejte ho k určení, jestli `IDBSchemaRowset::GetRowset` je volání uživatele správné. Pokud chcete podporovat jiné sady řádků schématu než ty, které jsou uvedeny výše, měli byste vytvořit vlastní funkci pro provedení této úlohy.

`CheckRestrictions`Určuje, zda příjemce volá [sadu GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) se správným omezením a správným typem omezení (například VT_BSTR pro řetězec), který podporuje zprostředkovatel. Také určuje, zda je podporován správný počet omezení. Ve výchozím nastavení `CheckRestrictions` vyzve poskytovatele, prostřednictvím volání [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) , která omezení podporuje v dané sadě řádků. Pak porovná omezení od příjemce s tím, jak jsou podporována poskytovatelem, a buď uspěje, nebo selže.

Další informace o sadách řádků schématu naleznete v tématu [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

## <a name="createschemarowset"></a> IDBSchemaRowsetImpl::CreateSchemaRowset

Implementuje funkci tvůrce objektu modelu COM pro objekt určený parametrem šablony.

### <a name="syntax"></a>Syntaxe

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Vnější rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) při agregaci, jinak null.

*cRestrictions –*<br/>
pro Počet omezení použitých pro sadu řádků schématu.

*rgRestrictions*<br/>
pro Pole `cRestrictions` **variant**s, které má být použito pro sadu řádků.

*riid*<br/>
pro Rozhraní pro [QueryInterface](../../atl/queryinterface.md) pro výstup `IUnknown`.

*cPropertySets*<br/>
pro Počet sad vlastností, které mají být nastaveny.

*rgPropertySets*<br/>
pro Pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury, které určují vlastnosti, které jsou nastaveny.

*ppRowset*<br/>
mimo Odchozí `IUnknown` požadavek od *riid*. Toto `IUnknown` je rozhraní objektu sady řádků schématu.

*pSchemaRowset*<br/>
mimo Ukazatel na instanci třídy sady řádků schématu. Tento parametr obvykle není použit, ale lze jej použít, pokud je nutné provést více práce na sadě řádků schématu před tím, než je předáte objektu COM. Životnost *pSchemaRowset* je vázána *ppRowset*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce implementuje obecného autora pro všechny typy sad řádků schématu. Obvykle uživatel nevolá tuto funkci. Je volána implementací mapy schématu.

## <a name="setrestrictions"></a> IDBSchemaRowsetImpl::SetRestrictions

Určuje, která omezení podporuje konkrétní sada řádků schématu.

### <a name="syntax"></a>Syntaxe

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Parametry

*cRestrictions –*<br/>
pro Počet omezení v poli *rgRestrictions* a počet identifikátorů GUID v poli *rguidSchema* .

*rguidSchema*<br/>
pro Pole identifikátorů GUID sady řádků schématu, pro které mají být načtena omezení. Každý prvek pole obsahuje identifikátor GUID jedné sady řádků schématu (například `DBSCHEMA_TABLES`).

*rgRestrictions*<br/>
pro Pole délky *CRestrictions –* hodnot omezení, které mají být nastaveny. Každý prvek odpovídá omezením pro sadu řádků schématu identifikovanou identifikátorem GUID. Pokud není sada řádků schématu podporována poskytovatelem, je prvek nastaven na hodnotu nula. V opačném případě hodnota **ulong** obsahuje bitovou masku, která představuje omezení podporovaná na dané sadě řádků schématu. Další informace o tom, která omezení odpovídají konkrétní sadě řádků schématu, naleznete v tabulce identifikátorů GUID sady řádků schématu v sadě [řádků](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *odkazu OLE DB programátor* v Windows SDK.

### <a name="remarks"></a>Poznámky

Objekt volá `SetRestrictions` k určení, která omezení podporuje konkrétní sada řádků schématu (je volána pomocí GetSchemas přes přetypováníný ukazatel). [](../../data/oledb/idbschemarowsetimpl-getschemas.md) `IDBSchemaRowset` Omezení umožňují spotřebitelům načíst pouze vyhovující řádky (například najít všechny sloupce v tabulce "MyTable"). Omezení jsou volitelná a v případě, že nejsou podporovány žádné (výchozí), jsou všechna data vždy vrácena.

Výchozí implementace této metody nastaví prvky pole *rgRestrictions* na hodnotu 0. Přepsáním výchozí hodnoty ve třídě Session nastavte jiná omezení než výchozí.

Informace o implementaci podpory sady řádků schématu naleznete v tématu [podpůrné sady řádků schématu](../../data/oledb/supporting-schema-rowsets.md).

Příklad zprostředkovatele, který podporuje sady řádků schématu, naleznete v ukázce [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

Další informace o sadách řádků schématu naleznete v tématu [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

## <a name="getrowset"></a> IDBSchemaRowsetImpl::GetRowset

Vrátí sadu řádků schématu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
pro Vnější `IUnknown` při agregaci; jinak null.

*rguidSchema*<br/>
pro Odkaz na požadovaný identifikátor GUID sady řádků schématu (například `DBSCHEMA_TABLES`).

*cRestrictions –*<br/>
pro Počet omezení, která mají být použita pro sadu řádků.

*rgRestrictions*<br/>
pro Pole `cRestrictions` **variant**s, které představuje omezení.

*riid*<br/>
pro Identifikátor IID pro požadavek na nově vytvořenou sadu řádků schématu.

*cPropertySets*<br/>
pro Počet sad vlastností, které mají být nastaveny.

*rgPropertySets*<br/>
[in/out] Pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury, které se mají nastavit na nově vytvořené sadě řádků schématu.

*ppRowset*<br/>
mimo Ukazatel na požadované rozhraní na nově vytvořené sadě řádků schématu.

### <a name="remarks"></a>Poznámky

Tato metoda vyžaduje, aby měl uživatel ve třídě Session mapu schématu. Pomocí informací o mapě schématu vytvoří `GetRowset` daný objekt sady řádků, pokud je parametr *rguidSchema* roven jednomu z identifikátorů GUID položek mapování. Popis položky mapování naleznete v tématu [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) .

Viz [IDBSchemaRowset:: GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) v Windows SDK.

## <a name="getschemas"></a> IDBSchemaRowsetImpl::GetSchemas

Vrátí seznam sad řádků schématu přístupných pomocí [IDBSchemaRowsetImpl:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Parametry

*pcSchemas*<br/>
mimo Ukazatel na **ulong** , který je vyplněn počtem schémat.

*prgSchemas*<br/>
mimo Ukazatel na pole identifikátorů GUID, které jsou vyplněny ukazatelem na pole identifikátorů GUID sady řádků schématu.

*prgRest*<br/>
mimo Ukazatel na pole **ulong**s, které má být vyplněno polem omezení.

### <a name="remarks"></a>Poznámky

Tato metoda vrací pole všech sad řádků schématu podporovaných zprostředkovatelem. Viz [IDBSchemaRowset::](/previous-versions/windows/desktop/ms719605(v=vs.85)) GetSchemas v Windows SDK.

Implementace této funkce vyžaduje, aby uživatel měl mapu schématu ve třídě Session. Pomocí informací o mapě schématu pak odpoví pole identifikátorů GUID pro schémata na mapě. To představuje schémata podporovaná zprostředkovatelem.

## <a name="see-also"></a>Viz také:

[Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)