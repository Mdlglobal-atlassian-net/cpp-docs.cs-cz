---
title: Pomocné rutiny třídy kolekce
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 3992e6c0cf25925e01858016e4bac93d5552fe8b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266143"
---
# <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce

Třídy kolekcí `CMap`, `CList`, a `CArray` použít bez vizuálního vzhledu globální pomocných funkcí pro tyto účely porovnání, kopírování a serializaci elementů. Jako součást vaší implementace tříd na základě `CMap`, `CList`, a `CArray`, je nutné přepsat těchto funkcí podle potřeby s verzemi přizpůsobená pro typ dat uložených v mapě, seznamu nebo pole. Informace o přepsání pomocných funkcí, jako `SerializeElements`, najdete v článku [kolekce: Jak provádět typově bezpečné kolekce](../../mfc/how-to-make-a-type-safe-collection.md). Všimněte si, že `ConstructElements` a `DestructElements` jsou zastaralé.

Knihovny Microsoft Foundation Class poskytuje následující globální funkce afxtempl.h při přizpůsobení tříd kolekce:

### <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce

|||
|-|-|
|[Compareelements –](#compareelements)|Určuje, zda prvky jsou stejné.|
|[Copyelements –](#copyelements)|Zkopíruje prvky z jednoho pole do jiného.|
|[Dumpelements –](#dumpelements)|Poskytuje diagnostický výstup orientovaný na stream.|
|[HashKey](#hashkey)|Vypočítá hodnotu hash klíče.|
|[Serializeelements –](#serializeelements)|Ukládá nebo načítá prvky do nebo z archivu.|

##  <a name="compareelements"></a>  Compareelements –

Přímo za názvem [CList::Find] (CList – class.md #not_found.md #clist__find a nepřímo [cmap__lookup](cmap-class.md#lookup) a [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ první prvek, který se má porovnat.

*pElement1*<br/>
Ukazatel na první prvek, který se má porovnat.

*ARG_TYPE*<br/>
Typ druhý prvek, který se má porovnat.

*pElement2*<br/>
Ukazatel na druhý prvek, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt, který odkazuje *pElement1* je stejný jako objekt, na které odkazuje *pElement2*; jinak 0.

### <a name="remarks"></a>Poznámky

`CMap` Volá použití `CMap` parametry šablony *klíč* a *ARG_KEY*.

Výchozí implementace vrací výsledek porovnání  *\*pElement1* a  *\*pElement2*. Potlačí tuto funkci tak, aby porovná prvky způsobem, který je vhodný pro vaši aplikaci.

Jazyk C++ definuje operátor porovnání ( `==`) pro jednoduché typy (**char**, **int**, **float**, a tak dále), ale není definován pro operátor porovnání třídy a struktury. Pokud chcete použít `CompareElements` nebo vytvořit instanci jedné ze tříd kolekce, které se používá, musíte definovat operátor porovnání nebo přetížení `CompareElements` s verzí, který vrací odpovídající hodnoty.

### <a name="requirements"></a>Požadavky

   **Záhlaví:** afxtempl.h

##  <a name="copyelements"></a>  Copyelements –

Tato funkce je volána přímo nástrojem [CArray::Append](carray-class.md#append) a [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků, které mají být zkopírovány.

*pDest*<br/>
Ukazatel do cíle, které budou elementy zkopírovány.

*pSrc*<br/>
Ukazatel na zdroj prvky, které mají být zkopírovány.

*nCount*<br/>
Počet prvků, které se mají zkopírovat.

### <a name="remarks"></a>Poznámky

Výchozí implementace používá operátor jednoduchého přiřazení ( **=** ) k provedení této operace kopírování. Pokud typ jsou kopírovány nemá přetíženého operátoru =, pak výchozí implementace provádí logické bitové kopie.

Informace o implementaci této a dalších funkcích pomocné rutiny, najdete v článku [kolekce: Jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxtempl.h

##  <a name="dumpelements"></a>  Dumpelements –

Diagnostický výstup orientovaný na stream v textové podobě zajišťující prvky kolekce při přepisu.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
Vypsat kontext pro výpis elementy.

*TYP*<br/>
Parametr šablony určující typ prvků.

*pElements*<br/>
Ukazatel na prvky, které mají být uloženy.

*nCount*<br/>
Počet prvků, které mají být uloženy.

### <a name="remarks"></a>Poznámky

`CArray::Dump`, `CList::Dump`, A `CMap::Dump` funkce to volat, pokud hloubka výpis paměti je větší než 0.

Výchozí implementace nemá žádný účinek. Pokud prvky vaší kolekce jsou odvozeny z `CObject`, přepsání bude obvykle iteraci v rámci kolekce elementů, volání `Dump` pro každý prvek v důsledku.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxtempl.h

##  <a name="hashkey"></a>  HashKey.

Vypočítá hodnotu hash pro zadaný klíč.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující typ dat používá pro přístup k mapování klíčů.

*key*<br/>
Klíč, jehož hodnota hash je vypočítán.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash klíče.

### <a name="remarks"></a>Poznámky

Tato funkce je volána přímo nástrojem [CMap::RemoveKey](cmap-class.md#removekey) a nepřímo [CMap::Lookup](cmap-class.md#lookup) a [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).

Výchozí implementace vytvoří hodnotu hash přepínáním *klíč* přímo pomocí čtyř pozic. Potlačí tuto funkci tak, aby vracel hodnot hash pro vaši aplikaci vhodné.

### <a name="example"></a>Příklad

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Požadavky

  **Hlavička** afxtempl.h

##  <a name="serializeelements"></a>  Serializeelements –

[Carray –](carray-class.md), [CList –](clist-class.md), a [CMap](cmap-class.md) voláním této funkce k serializaci elementů.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků.

*ar*<br/>
Objekt archiv k archivaci nebo odchozí.

*pElements*<br/>
Ukazatel na elementy archivovaných.

*nCount*<br/>
Počet prvků archivovaných

### <a name="remarks"></a>Poznámky

Výchozí implementace neodpovídá bitové operace čtení nebo zápisu.

Informace o implementaci této a dalších funkcích pomocné rutiny, najdete v článku [kolekce: Jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Příklad

Podívejte se na příklad v tomto článku [kolekce: Jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxtempl.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CMap – třída](cmap-class.md)<br/>
[CList – třída](clist-class.md)<br/>
[CArray – třída](carray-class.md)
