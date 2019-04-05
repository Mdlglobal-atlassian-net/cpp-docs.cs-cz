---
title: CTypedPtrMap Class
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: bc164125f867cf3e2f27b74e69b826cbed31ff1d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781793"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap Class

Poskytuje typově zabezpečenou "obálku" pro objekty tříd ukazatel mapy `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, a `CMapStringToPtr`.

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída typované ukazatele mapování třídy; musí být třída map ukazatel ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, nebo `CMapStringToPtr`).

*KEY*<br/>
Třída objektu se používá jako klíč do mapy.

*HODNOTA*<br/>
Třída objekt uložený v objektu map.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CTypedPtrMap::Lookup](#lookup)|Vrátí `KEY` na základě `VALUE`.|
|[CTypedPtrMap::RemoveKey](#removekey)|Odebere element určený klíč.|
|[CTypedPtrMap::SetAt](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CTypedPtrMap::operator \[ \]](#operator_at)|Vloží prvek do objektu map.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrMap`, kontroly typů zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.

Protože všechny `CTypedPtrMap` jsou vložené funkce, použijte tato šablona nemá vliv na výrazně velikost nebo rychlost kódu.

Další informace o používání `CTypedPtrMap`, najdete v článcích [kolekce](../../mfc/collections.md) a [založené na šablonách třídy](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

Načte prvek mapy v `rNextPosition`, pak aktualizuje `rNextPosition` odkazovat na další prvek v objektu map.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rposition.*<br/>
Určuje referenci na POZICI hodnotu vrácenou předchozím `GetNextAssoc` nebo `BASE_CLASS` **:: GetStartPosition** volání.

*KEY*<br/>
Parametr šablony určující typ klíče na mapě.

*rKey*<br/>
Určuje vrácené klíč načtený elementu.

*HODNOTA*<br/>
Parametr šablony určující typ hodnoty na mapě.

*r-hodnoty*<br/>
Určuje, vrácená hodnota elementu načtený.

### <a name="remarks"></a>Poznámky

Tato funkce je zvláště užitečná pro procházení všech prvků v objektu map. Všimněte si, že sekvence pozice není nutně stejné jako pořadí klíč-hodnota.

Pokud je načtený element poslední v objektu map, pak nová hodnota `rNextPosition` nastaven na hodnotu NULL.

Tato vložená funkce zavolá `BASE_CLASS` **:: GetNextAssoc**.

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` používá algoritmus hash a rychle najít prvek mapy s klíčem, který přesně odpovídá.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Parametr šablony určující základní třídy tuto mapu třídy.

*klíč*<br/>
Klíč elementu, který chcete vyhledávat.

*HODNOTA*<br/>
Parametr šablony určující typ hodnot uložených na této mapě.

*r-hodnoty*<br/>
Určuje, vrácená hodnota elementu načtený.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud element nebyl nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

Tato vložená funkce zavolá `BASE_CLASS` **:: vyhledávání**.

##  <a name="operator_at"></a>  CTypedPtrMap::operator [ ]

Tento operátor lze použít pouze na levé straně příkazu přiřazení (l hodnota).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parametry

*HODNOTA*<br/>
Parametr šablony určující typ hodnot uložených na této mapě.

*BASE_CLASS*<br/>
Parametr šablony určující základní třídy tuto mapu třídy.

*klíč*<br/>
Klíč elementu, který chcete vyhledávat nebo vytvořili v objektu map.

### <a name="remarks"></a>Poznámky

Pokud neexistuje žádné mapování element se zadaným klíčem, se vytvoří nový prvek. Ekvivalentní pro tento operátor není žádný "pravému" (r), protože je možné, že klíče nemusí být nalezen v objektu map. Použití `Lookup` členskou funkci pro prvek načítání.

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

Tato členská funkce volá `BASE_CLASS` **:: RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parametry

*KEY*<br/>
Parametr šablony určující typ klíče na mapě.

*klíč*<br/>
Klíč elementu, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl nalezen a úspěšně odebral; položka jinak 0.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

##  <a name="setat"></a>  CTypedPtrMap::SetAt

Tato členská funkce volá `BASE_CLASS` **:: SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parametry

*KEY*<br/>
Parametr šablony určující typ klíče na mapě.

*klíč*<br/>
Určuje hodnotu klíče newValue.

*newValue*<br/>
Určuje objekt ukazatel, který je hodnota nového elementu.

### <a name="remarks"></a>Poznámky

Podrobné poznámky, naleznete v tématu [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC shromažďování](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr Class](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord Class](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr Class](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)
