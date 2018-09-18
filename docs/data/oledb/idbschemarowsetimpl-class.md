---
title: IDBSchemaRowsetImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d998654b92e2e75836bb9dad9e3d7fc17bfa0bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103103"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl – třída

Poskytuje implementaci pro sad řádků schématu.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
### <a name="parameters"></a>Parametry  

*SessionClass*<br/>
Třída, podle kterého `IDBSchemaRowsetImpl` dědí. Tato třída bude obvykle třídu relace uživatele. 

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CheckRestrictions](#checkrestrictions)|Ověří platnost omezení proti sada řádků schématu.|  
|[CreateSchemaRowset](#createschemarowset)|Implementuje funkci objektu Tvůrce modelu COM pro objekt zadaný parametrem šablony.|  
|[SetRestrictions](#setrestrictions)|Určuje, která omezení podpory pro sadu řádků schématu konkrétní.|  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetRowset –](#getrowset)|Vrací sadu řádků schématu.|  
|[GetSchemas –](#getschemas)|Vrátí seznam sad řádků schématu přístupné [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|  
  
## <a name="remarks"></a>Poznámky  

Tato třída implementuje [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) rozhraní a funkce přepsaly creator [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).  
  
OLE DB pomocí sad řádků schématu vrátí data o datech ve zprostředkovateli. Taková data se často nazývá "metadata." Ve výchozím nastavení, musí vždycky podporovat zprostředkovatele `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, a `DBSCHEMA_PROVIDER_TYPES`, jak je popsáno v [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory*. Sady řádků schématu jsou určené v objektu map schématu. Informace o položkách mapování schématu najdete v tématu [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).  
  
OLE DB Provider průvodce, v Průvodci objektu ATL automaticky generuje kód pro sad řádků schématu ve vašem projektu. (Ve výchozím nastavení podporuje Průvodce sady řádků schématu povinné už jsme zmínili.) Při vytváření nového konzumenta s použitím Průvodce objektem ATL, používá Průvodce na správná data svázat zprostředkovatele sady řádků schématu. Pokud vaše sady řádků schématu k poskytování správných metadat neimplementují, průvodce se nebudou vázat správná data.  
  
Informace o tom, jak Podpora sad řádků schématu ve zprostředkovateli najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
Další informace o sad řádků schématu najdete v tématu [sad řádků schématu](/previous-versions/windows/desktop/ms712921\(v=vs.85\)) v *OLE DB referenční informace pro programátory*.  

## <a name="checkrestrictions"></a> IDBSchemaRowsetImpl::CheckRestrictions

Ověří platnost omezení proti sada řádků schématu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>Parametry  

*rguidSchema*<br/>
[in] Odkaz na identifikátor GUID sady řádků požadované schéma (například `DBSCHEMA_TABLES`).  
  
*cRestrictions –*<br/>
[in] Počet omezení, které příjemce předaný pro sadu řádků schématu.  
  
*rgRestrictions*<br/>
[in] Pole s délkou *cRestrictions* omezení hodnot, která se má nastavit. Další informace najdete v popisu *rgRestrictions* parametr [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
### <a name="remarks"></a>Poznámky  

Použití `CheckRestrictions` ke kontrole platnosti omezení pro sadu řádků schématu. Zkontroluje omezení pro `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, a `DBSCHEMA_PROVIDER_TYPES` sad řádků schématu. Pojmenujte ji k určení, zda uživatele volání `IDBSchemaRowset::GetRowset` je správná. Pokud chcete zajistit podporu sad řádků schématu než ty, které uvedené výše, měli byste vytvořit vlastní funkce k provedení této úlohy.  
  
`CheckRestrictions` Určuje, pokud je příjemce volání [GetRowset –](../../data/oledb/idbschemarowsetimpl-getrowset.md) správné omezení a typ správný omezení (například VT_BSTR řetězce), které zprostředkovatel podporuje. Také určuje, pokud jsou podporovány správný počet omezení. Ve výchozím nastavení `CheckRestrictions` bude žádat poskytovatele, až [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) volání, která omezení podporuje v dané sadě řádků. Poté porovná omezení od uživatele s ohledem podporována zprostředkovatelem a buď úspěšná nebo neúspěšná.  
  
Další informace o sad řádků schématu najdete v tématu [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory* v sadě Windows SDK.  

## <a name="createschemarowset"></a> IDBSchemaRowsetImpl::CreateSchemaRowset

Implementuje funkci objektu Tvůrce modelu COM pro objekt zadaný parametrem šablony.  
  
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
[in] Vnější [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro agregaci, jinak hodnota NULL.  
  
*cRestrictions –*<br/>
[in] Počet omezení použitých na sady řádků schématu.  
  
*rgRestrictions*<br/>
[in] Pole `cRestrictions` **VARIANT**s použít v sadě řádků.  
  
*riid*<br/>
[in] Rozhraní pro [QueryInterface](../../atl/queryinterface.md) pro výstupu `IUnknown`.  
  
*cPropertySets*<br/>
[in] Nastaví počet vlastnost nastavit.  
  
*rgPropertySets*<br/>
[in] Pole [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury, které určují vlastnosti nastavena.  
  
*ppRowset*<br/>
[out] Odchozích dat `IUnknown` požadoval *riid*. To `IUnknown` je rozhraní objektu sady řádků schématu.  
  
*pSchemaRowset*<br/>
[out] Ukazatel na instanci třídy sady řádků schématu. Obvykle tento parametr se nepoužívá, ale můžete použít, pokud je nutné provést další práce na sadu řádků schématu před přidělovat k objektu modelu COM. Životnost *pSchemaRowset* je svázaná s *ppRowset*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Tato funkce implementuje obecný tvůrce pro všechny druhy sad řádků schématu. Uživateli obvykle nevolá této funkce. Je volána implementace mapování schématu. 

## <a name="setrestrictions"></a> IDBSchemaRowsetImpl::SetRestrictions

Určuje, která omezení podpory pro sadu řádků schématu konkrétní.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void SetRestrictions(ULONG cRestrictions,  
   GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>Parametry  

*cRestrictions –*<br/>
[in] Počet omezení *rgRestrictions* pole a počet identifikátory GUID *rguidSchema* pole.  
  
*rguidSchema*<br/>
[in] Pole identifikátorů GUID sady řádků schématu, pro které chcete načíst omezení. Každý prvek pole obsahuje identifikátor GUID sady řádků jedno schéma (například `DBSCHEMA_TABLES`).  
  
*rgRestrictions*<br/>
[in] Pole s délkou *cRestrictions* omezení hodnot, která se má nastavit. Každý prvek odpovídá omezení pro sadu řádků schématu identifikované identifikátorem GUID. Pokud sada řádků schématu není podporována zprostředkovatelem, prvku nastavená na hodnotu nula. V opačném případě **ULONG** hodnota obsahuje bitová maska, která představuje omezení podporované na tomto sada řádků schématu. Další informace, na kterém omezení odpovídají konkrétní schématu sady řádků, najdete v tabulce sada řádků schématu GUID v [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory* v Windows SADA SDK.  
  
### <a name="remarks"></a>Poznámky  

`IDBSchemaRowset` Objektu volání `SetRestrictions` k určení, která omezení podpory pro sadu řádků schématu konkrétní (je volán [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) prostřednictvím upcasted ukazatele). Omezení povolit uživatelům načítat pouze odpovídající řádky (například vyhledat všechny sloupce v tabulce "MyTable"). Omezení jsou volitelné a v případě, ve které nejsou podporovány (výchozí), vždy vrátí se všechna data.  
  
Nastaví výchozí implementace této metody *rgRestrictions* pole prvků na hodnotu 0. Přepište výchozí nastavení ve své třídě relace pro nastavení omezení pro jiné než výchozí.  
  
Informace o implementaci Podpora sad řádků schématu najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
Příklad poskytovatele, který podporuje sad řádků schématu, najdete v článku [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) vzorku.  
  
Další informace o sad řádků schématu najdete v tématu [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory* v sadě Windows SDK. 
  
## <a name="getrowset"></a> IDBSchemaRowsetImpl::GetRowset

Vrací sadu řádků schématu.  
  
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
[in] Vnější `IUnknown` při agregovat; jinak hodnota NULL.  
  
*rguidSchema*<br/>
[in] Odkaz na identifikátor GUID sady řádků požadované schéma (například `DBSCHEMA_TABLES`).  
  
*cRestrictions –*<br/>
[in] Počet omezení použít v sadě řádků.  
  
*rgRestrictions*<br/>
[in] Pole `cRestrictions` **VARIANT**, které představují omezení.  
  
*riid*<br/>
[in] Identifikátor IID k vyžádání sady řádků schématu nově vytvořený.  
  
*cPropertySets*<br/>
[in] Nastaví počet vlastnost nastavit.  
  
*rgPropertySets*<br/>
[/ out] Pole [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) struktury nastavit pro sadu řádků schématu nově vytvořený.  
  
*ppRowset*<br/>
[out] Ukazatel na požadované rozhraní pro nově vytvořené schéma řádků.  
  
### <a name="remarks"></a>Poznámky  

Tato metoda vyžaduje, aby uživatel měl schéma mapování ve třídě relace. Pomocí informací o mapování schématu, `GetRowset` vytvoří objekt dané sadě řádků, pokud *rguidSchema* rovná parametru na jednu z položek mapování identifikátory GUID. Zobrazit [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) popis položku mapování.  
  
Zobrazit [IDBSchemaRowset::GetRowset](/previous-versions/windows/desktop/ms722634\(v=vs.85\)) ve Windows SDK.  

## <a name="getschemas"></a> IDBSchemaRowsetImpl::GetSchemas

Vrátí seznam sad řádků schématu přístupné [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest);  
```  
  
#### <a name="parameters"></a>Parametry  

*pcSchemas*<br/>
[out] Ukazatel **ULONG** , který je vyplněna počet schémat.  
  
*prgSchemas*<br/>
[out] Ukazatel na pole identifikátorů GUID, který je vyplněný s ukazatelem na pole Sada řádků schématu identifikátory GUID.  
  
*prgRest*<br/>
[out] Ukazatel na pole **ULONG**, které má být vyplněna pole omezení.  
  
### <a name="remarks"></a>Poznámky  

Tato metoda vrací pole všech řádků schématu podporovanou zprostředkovatelem. Zobrazit [IDBSchemaRowset::GetSchemas](/previous-versions/windows/desktop/ms719605\(v=vs.85\)) ve Windows SDK.  
  
Implementaci této funkce vyžaduje, aby uživatel mít schéma mapování ve třídě relace. Pomocí informací o schématu mapování, pak odpovědí s polem identifikátory GUID pro schémata v objektu map. Reprezentuje schémata podporována zprostředkovatelem.  

## <a name="see-also"></a>Viz také  

[Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)