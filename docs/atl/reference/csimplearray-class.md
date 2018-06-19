---
title: Třída CSimpleArray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187dee79cd09e366fb56d9cd0e71395589476a69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364261"
---
# <a name="csimplearray-class"></a>CSimpleArray – třída
Tato třída poskytuje metody pro správu jednoduchých polí.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ dat pro uložení v poli.  
  
 `TEqual`  
 Objekt znak, který slouží k definování test rovnosti pro elementy typu `T`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|V konstruktoru pro jednoduché pole.|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|Destruktor pro jednoduché pole.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|Přidá nového elementu k poli.|  
|[CSimpleArray::Find](#find)|Vyhledá element v poli.|  
|[CSimpleArray::GetData](#getdata)|Vrací ukazatel na data uložená v poli.|  
|[CSimpleArray::GetSize](#getsize)|Vrátí počet prvků, které jsou uložené v poli.|  
|[CSimpleArray::Remove](#remove)|Odebere pole daného elementu.|  
|[CSimpleArray::RemoveAll](#removeall)|Odebere všechny elementy z pole.|  
|[CSimpleArray::RemoveAt](#removeat)|Odebere zadaný element z pole.|  
|[CSimpleArray::SetAtIndex](#setatindex)|Nastaví zadaný element v poli.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|Načte z pole elementu.|  
|[CSimpleArray::operator =](#operator_eq)|Operátor přiřazení.|  

  
## <a name="remarks"></a>Poznámky  
 `CSimpleArray` poskytuje metody pro vytváření a správu jednoduché pole daného typu `T`.  
  
 Parametr `TEqual` poskytuje způsob definování rovnosti funkce pro dva elementy typu `T`. Vytvořením třídy podobné [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), je možné změnit chování test rovnosti pro jakékoli dané pole. Například při plánování práce s pole ukazatele, může být užitečné k definování rovnosti jako v závislosti na hodnoty, které odkazují ukazatele. Výchozí implementace využívá **operator=()**.  
  
 Obě `CSimpleArray` a [CSimpleMap](../../atl/reference/csimplemap-class.md) jsou navrženy pro malý počet elementů. [CAtlArray](../../atl/reference/catlarray-class.md) a [CAtlMap](../../atl/reference/catlmap-class.md) by měl být použit při pole obsahuje velký počet elementů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="add"></a>  CSimpleArray::Add  
 Přidá nového elementu k poli.  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Elementu, který chcete přidat do pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud element úspěšně přidán do pole, FALSE jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray  
 V konstruktoru pro objekt array.  
  
```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```     
  
### <a name="parameters"></a>Parametry  
 *src*  
 Existující objekt `CSimpleArray`.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje datových členů, vytvoření nové prázdné `CSimpleArray` objekt nebo kopii existující `CSimpleArray` objektu.  
  
##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray  
 Destruktor.  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="find"></a>  CSimpleArray::Find  
 Vyhledá element v poli.  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Element, který chcete vyhledat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index nalezen element nebo -1, pokud element nebyl nalezen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="getdata"></a>  CSimpleArray::GetData  
 Vrací ukazatel na data uložená v poli.  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na data v poli.  
  
##  <a name="getsize"></a>  CSimpleArray::GetSize  
 Vrátí počet prvků, které jsou uložené v poli.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků, které jsou uložené v poli.  
  
##  <a name="operator_at"></a>  CSimpleArray::operator \[\]  
 Načte z pole elementu.  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí element pole odkazuje `nIndex`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="operator_eq"></a>  CSimpleArray::operator =  
 Operátor přiřazení.  
  
```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Pole pro kopírování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na aktualizaci `CSimpleArray` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Zkopíruje všechny elementy z `CSimpleArray` objekt odkazovaný *src* do aktuální objekt pole nahrazení všechna existující data.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="remove"></a>  CSimpleArray::Remove  
 Odebere pole daného elementu.  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Elementu, který chcete odebrat z pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud element je nalezen a odebrána, FALSE, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je odebrán element, zbývající prvků v poli se označuje jako k vyplnění prázdná místo.  
  
##  <a name="removeall"></a>  CSimpleArray::RemoveAll  
 Odebere všechny elementy z pole.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny elementy, které jsou aktuálně uloženy v poli.  
  
##  <a name="removeat"></a>  CSimpleArray::RemoveAt  
 Odebere zadaný element z pole.  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indexu odkazující na elementu, který chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud element byla odebrána, FALSE, pokud index je neplatný.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je odebrán element, zbývající prvků v poli se označuje jako k vyplnění prázdná místo.  
  
##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex  
 Nastavte Zadaný prvek v poli.  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index elementu, který chcete změnit.  
  
 *t*  
 Hodnota pro přiřazení daného elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE Pokud úspěšné, FALSE, pokud nebyla platná index.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
