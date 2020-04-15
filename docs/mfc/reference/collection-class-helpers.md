---
title: Pomocné rutiny třídy kolekce
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374818"
---
# <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce

Třídy `CMap`kolekce `CList`, `CArray` a používat šablony globální pomocné funkce pro takové účely, jako je porovnání, kopírování a serializace prvků. Jako součást implementace tříd založených `CMap` `CList`na `CArray`, , a , je nutné přepsat tyto funkce podle potřeby s verzemi přizpůsobenými typu dat uložených v mapě, seznamu nebo poli. Informace o přepsání pomocných `SerializeElements`funkcí, jako jsou například kolekce: [Jak vytvořit kolekci bezpečného pro daný typ](../../mfc/how-to-make-a-type-safe-collection.md). Všimněte `ConstructElements` `DestructElements` si, že a byly zastaralé.

Knihovna tříd Microsoft Foundation poskytuje následující globální funkce v afxtempl.h, které vám pomohou přizpůsobit třídy kolekce:

### <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce

|||
|-|-|
|[Porovnat prvky](#compareelements)|Označuje, zda prvky jsou stejné.|
|[CopyElements](#copyelements)|Kopíruje prvky z jednoho pole do druhého.|
|[DumpElements](#dumpelements)|Poskytuje diagnostický výstup orientovaný na datový proud.|
|[HashKey](#hashkey)|Vypočítá klíč hash.|
|[Serializovat prvky](#serializeelements)|Ukládá nebo načítá prvky do nebo z archivu.|

## <a name="compareelements"></a><a name="compareelements"></a>Porovnat prvky

Voláno přímo [CList::Find](clist-class.md#not_found.md#clist__find a nepřímo [cmap__lookup](cmap-class.md#lookup) a [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Typ prvníprvek, který má být porovnán.

*pElement1*<br/>
Ukazatel na první prvek, který má být porovnán.

*ARG_TYPE*<br/>
Typ druhého prvku, který má být porovnán.

*pElement2*<br/>
Ukazatel na druhý prvek, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt, na který je zaměřen *pElement1,* roven objektu, na který je zaměřen a na který je uvedeno *pElement2*; jinak 0.

### <a name="remarks"></a>Poznámky

Volání `CMap` používají `CMap` parametry šablony *KEY* a *ARG_KEY*.

Výchozí implementace vrátí výsledek porovnání * \*pElement1* a * \*pElement2*. Přepsat tuto funkci tak, aby porovnává prvky způsobem, který je vhodný pro vaši aplikaci.

Jazyk C++ definuje operátor porovnání `==`( ) pro jednoduché typy (**char**, **int**, **float**a tak dále), ale nedefinuje operátor porovnání pro třídy a struktury. Pokud chcete použít `CompareElements` nebo vytvořit instanci jedné z tříd kolekce, která ji používá, `CompareElements` musíte buď definovat operátor porovnání nebo přetížení s verzí, která vrací příslušné hodnoty.

### <a name="requirements"></a>Požadavky

   **Záhlaví:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

Tato funkce je volána přímo [carray::append](carray-class.md#append) a [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků, které mají být kopírovány.

*pDest*<br/>
Ukazatel na cíl, kde budou prvky zkopírovány.

*pSrc*<br/>
Ukazatel na zdroj prvků, které mají být zkopírovány.

*nCount*<br/>
Počet prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Výchozí implementace používá k provedení **=** operace kopírování operátor jednoduché přiřazení ( ). Pokud kopírovaný typ nemá přetížený operator=, pak výchozí implementace provede bitovou kopii.

Informace o implementaci této a dalších pomocných funkcí naleznete v článku [Kolekce: Jak vytvořit kolekci bezpečného pro daný typ](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements

Poskytuje datový proud orientovaný diagnostický výstup v textové podobě pro prvky kolekce při přepsání.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Výpis kontextu pro dumpingové prvky.

*TYP*<br/>
Parametr šablony určující typ prvků.

*pPrvky*<br/>
Ukazatel na prvky, které mají být dumpingové.

*nCount*<br/>
Počet prvků, které mají být dumpingové.

### <a name="remarks"></a>Poznámky

, `CArray::Dump` `CList::Dump`a `CMap::Dump` funkce volání, pokud je hloubka výpisu je větší než 0.

Výchozí implementace neprovede žádné provádění. Pokud jsou odvozeny prvky `CObject`vaší kolekce z , přepsání obvykle iterát `Dump` prostřednictvím kolekce prvků, volání pro každý prvek v pořadí.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey

Vypočítá hodnotu hash pro daný klíč.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parametry

*ARG_KEY*<br/>
Parametr šablony určující datový typ používaný pro přístup ke klíčům mapy.

*key*<br/>
Klíč, jehož hodnota hash má být vypočtena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash klíče.

### <a name="remarks"></a>Poznámky

Tato funkce je volána přímo [CMap::RemoveKey](cmap-class.md#removekey) a nepřímo [CMap::Lookup](cmap-class.md#lookup) a [CMap::Operator &#91;&#93;](cmap-class.md#operator_at).

Výchozí implementace vytvoří hodnotu hash posunutím *klíče* doprava o čtyři pozice. Přepsat tuto funkci tak, aby vrátí hodnoty hash vhodné pro vaši aplikaci.

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

  **Záhlaví** afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>Serializovat prvky

[CArray](carray-class.md), [CList](clist-class.md)a [CMap](cmap-class.md) volají tuto funkci k serializaci prvků.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parametry

*TYP*<br/>
Parametr šablony určující typ prvků.

*ar*<br/>
Objekt archivace, ze který chcete archivovat, nebo z nich.

*pPrvky*<br/>
Ukazatel na prvky, které jsou archivovány.

*nCount*<br/>
Počet archivovaných prvků

### <a name="remarks"></a>Poznámky

Výchozí implementace provádí bitové čtení nebo zápis.

Informace o implementaci této a dalších pomocných funkcí naleznete v článku [Kolekce: Jak vytvořit kolekci bezpečného pro daný typ](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Příklad

Viz příklad v článku [Kolekce: Jak vytvořit typově bezpečnou kolekci](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxtempl.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[Třída CMap](cmap-class.md)<br/>
[CList – třída](clist-class.md)<br/>
[Třída CArray](carray-class.md)
