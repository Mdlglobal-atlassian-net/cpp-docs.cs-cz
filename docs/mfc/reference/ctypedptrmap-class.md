---
title: CTypedPtrMap – třída
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
ms.openlocfilehash: 41416c8223ac94364e8f83028ea93189e9f3f60c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373259"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap – třída

Poskytuje typově bezpečné "obálky" pro objekty `CMapPtrToPtr`tříd `CMapPtrToWord` `CMapWordToPtr`mapy `CMapStringToPtr`ukazatele , , a .

## <a name="syntax"></a>Syntaxe

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Základní třída mapové třídy zadaný ukazatel; musí být třída mapy `CMapPtrToPtr` `CMapPtrToWord`ukazatele `CMapWordToPtr`( `CMapStringToPtr`, , , nebo ).

*Klíč*<br/>
Třída objektu použitá jako klíč k mapě.

*Hodnotu*<br/>
Třída objektu uloženého v mapě.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|
|[CTypedPtrMap::Vyhledávání](#lookup)|Vrátí `KEY` na základě `VALUE`.|
|[CTypedPtrMap::Odebrat klíč](#removekey)|Odebere prvek určený klíčem.|
|[CTypedPtrMap::SetAt](#setat)|Vloží prvek do mapy; nahradí existující prvek, pokud je nalezen odpovídající klíč.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CTypedPtrMap::operátor \[\]](#operator_at)|Vloží prvek do mapy.|

## <a name="remarks"></a>Poznámky

Při použití `CTypedPtrMap`, c++ nástroj pro kontrolu typů pomáhá eliminovat chyby způsobené neodpovídající typy ukazatelů.

Vzhledem `CTypedPtrMap` k tomu, že všechny funkce jsou vřadit, použití této šablony nemá významný vliv na velikost nebo rychlost kódu.

Další informace o `CTypedPtrMap`použití naleznete v článcích Kolekce a [Třídy](../../mfc/collections.md) [založené na šablonách](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc

Načte prvek mapy `rNextPosition`na `rNextPosition` , pak aktualizuje odkazovat na další prvek v mapě.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rPozice*<br/>
Určuje odkaz na hodnotu POSITION vrácenou předchozím `GetNextAssoc` voláním `BASE_CLASS` **nebo ::GetStartPosition.**

*Klíč*<br/>
Parametr šablony určující typ klíčů mapy.

*rKlíč*<br/>
Určuje vrácený klíč načteného prvku.

*Hodnotu*<br/>
Parametr šablony určující typ hodnot mapy.

*rValue*<br/>
Určuje vrácenou hodnotu načteného prvku.

### <a name="remarks"></a>Poznámky

Tato funkce je nejužitečnější pro iterace přes všechny prvky v mapě. Všimněte si, že pořadí pozic není nutně stejné jako pořadí hodnot klíče.

Pokud načtený prvek je poslední v mapě, pak `rNextPosition` je nová hodnota nastavena na HODNOTU NULL.

Tato inline `BASE_CLASS`funkce volá **::GetNextAssoc**.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::Vyhledávání

`Lookup`používá algoritmus hash rychle najít prvek mapy s klíčem, který přesně odpovídá.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Parametr šablony určující základní třídu třídy této mapy.

*key*<br/>
Klíč prvku, který má být vyhlédnut.

*Hodnotu*<br/>
Parametr šablony určující typ hodnot uložených v této mapě.

*rValue*<br/>
Určuje vrácenou hodnotu načteného prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl prvek nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

Tato inline `BASE_CLASS`funkce volá **::Vyhledávání**.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::operátor [ ]

Tento operátor lze použít pouze na levé straně příkazu přiřazení (hodnota l).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parametry

*Hodnotu*<br/>
Parametr šablony určující typ hodnot uložených v této mapě.

*BASE_CLASS*<br/>
Parametr šablony určující základní třídu třídy této mapy.

*key*<br/>
Klíč prvku, který má být vyhledán nebo vytvořen v mapě.

### <a name="remarks"></a>Poznámky

Pokud neexistuje žádný prvek mapy se zadaným klíčem, je vytvořen nový prvek. Neexistuje žádná "pravá strana" (hodnota r) ekvivalentní tomuto operátoru, protože existuje možnost, že klíč nemusí být nalezen v mapě. Pro `Lookup` načítání prvků použijte členská funkci.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap::Odebrat klíč

Tato členská `BASE_CLASS`funkce volá **::RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Parametr šablony určující typ klíčů mapy.

*key*<br/>
Klíč pro prvek, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla položka nalezena a úspěšně odebrána; jinak 0.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

Tato členská `BASE_CLASS`funkce volá **::SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Parametr šablony určující typ klíčů mapy.

*key*<br/>
Určuje hodnotu klíče newValue.

*Newvalue*<br/>
Určuje ukazatel objektu, který je hodnotou nového prvku.

### <a name="remarks"></a>Poznámky

Podrobnější poznámky naleznete v tématu [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Viz také

[Odběr vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Třída CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr – třída](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr – třída](../../mfc/reference/cmapstringtoptr-class.md)
