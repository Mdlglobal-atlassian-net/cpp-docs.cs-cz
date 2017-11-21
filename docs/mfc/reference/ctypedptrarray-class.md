---
title: "CTypedPtrArray – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs: C++
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 975844d2a5dcad3afecd07411d2992abb6c8578b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray – třída
Typově bezpečný "obálky" poskytuje pro objekty třídy `CPtrArray` nebo `CObArray`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Základní třída třídy pole typu ukazatele; musí být třídu pole ( `CObArray` nebo `CPtrArray`).  
  
 `TYPE`  
 Typ elementů uložené v poli základní třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|Přidá nový prvek na konec pole. Zvětšování pole v případě potřeby|  
|[CTypedPtrArray::Append](#append)|Přidá na konec jiné obsah jedno pole. Zvětšování pole v případě potřeby|  
|[CTypedPtrArray::Copy](#copy)|Zkopíruje jiného pole k poli; zvětšování pole v případě potřeby.|  
|[CTypedPtrArray::ElementAt](#elementat)|Vrátí dočasné odkaz na element ukazatele v rámci pole.|  
|[CTypedPtrArray::GetAt](#getat)|Vrátí hodnotu v daném indexu.|  
|[CTypedPtrArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny elementy v jiném poli).|  
|[CTypedPtrArray::SetAt](#setat)|Nastaví hodnotu pro daného indexu; pole není povoleno zvětšovat.|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daného indexu; zvětšování pole v případě potřeby.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CTypedPtrArray::operator]](#operator_at)|Nastaví nebo získá element v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití `CTypedPtrArray` místo `CPtrArray` nebo `CObArray`, kontrola typu zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.  
  
 Kromě toho `CTypedPtrArray` obálku provádí většinu přetypování, která by byla zapotřebí, pokud jste použili `CObArray` nebo `CPtrArray`.  
  
 Protože všechny `CTypedPtrArray` jsou vložené funkce, pomocí této šablony nemá vliv na výrazně velikost a rychlost kódu.  
  
 Další informace o používání `CTypedPtrArray`, najdete v článcích [kolekce](../../mfc/collections.md) a [na základě šablon třídy](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtempl.h  
  
##  <a name="add"></a>CTypedPtrArray::Add  
 Tato funkce člen volá `BASE_CLASS` **:: Přidat**.  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementu, který se má přidat do pole.  
  
 `newElement`  
 Element, který se má přidat do tohoto pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::Add](../../mfc/reference/cobarray-class.md#add).  
  
##  <a name="append"></a>CTypedPtrArray::Append  
 Tato funkce člen volá `BASE_CLASS` **:: připojení**.  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Základní třída třídy pole typu ukazatele; musí být třídu pole ( [CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYP*  
 Typ elementů uložené v poli základní třídy.  
  
 *src*  
 Zdroj prvky, které je připojeno k matici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvního připojení prvku.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::Append](../../mfc/reference/cobarray-class.md#append).  
  
##  <a name="copy"></a>CTypedPtrArray::Copy  
 Tato funkce člen volá `BASE_CLASS` **:: kopie**.  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Základní třída třídy pole typu ukazatele; musí být třídu pole ( [CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYP*  
 Typ elementů uložené v poli základní třídy.  
  
 *src*  
 Zdroj elementy zkopírovány do pole.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).  
  
##  <a name="elementat"></a>CTypedPtrArray::ElementAt  
 Tato vložená funkce volá `BASE_CLASS` **:: ElementAt**.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů uložené v toto pole.  
  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Dočasné odkaz na element v umístění, které `nIndex`. Tento element je typu zadaném pomocí parametr šablony *typu*.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).  
  
##  <a name="getat"></a>CTypedPtrArray::GetAt  
 Tato vložená funkce volá `BASE_CLASS` **:: GetAt**.  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů uložené v poli.  
  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie element v umístění, které `nIndex`. Tento element je typu zadaném pomocí parametr šablony *typu*.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>CTypedPtrArray::InsertAt  
 Tato funkce člen volá `BASE_CLASS` **:: InsertAt**.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYP*  
 Typ elementů uložené v poli základní třídy.  
  
 `newElement`  
 Objekt ukazatel umístit do tohoto pole. A `newElement` hodnoty **NULL** je povolen.  
  
 `nCount`  
 Počet, který tento element musí být vložen (výchozí hodnota je 1).  
  
 `nStartIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené `CObArray::GetUpperBound`.  
  
 `BASE_CLASS`  
 Základní třída třídy pole typu ukazatele; musí být třídu pole ( [CObArray](../../mfc/reference/cobarray-class.md) nebo [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 `pNewArray`  
 Další pole, které obsahuje prvky, který se má přidat do tohoto pole.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).  
  
##  <a name="operator_at"></a>[CTypedPtrArray::operator]  
 Tyto operátory vložené volání `BASE_CLASS` **:: [] – operátor**.  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr šablony určující typ elementů uložené v poli.  
  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="remarks"></a>Poznámky  
 Volá se první operátor pro pole, které nejsou **const**, lze použít v vpravo (hodnota r) nebo doleva (l-value) příkazu přiřazení. Pro druhý, volána **const** pole, lze použít pouze na pravé straně.  
  
 Ladicí verze knihovny vyhodnotí, pokud dolní index (buď na levé nebo pravé straně příkazu přiřazení) je mimo rozsah.  
  
##  <a name="setat"></a>CTypedPtrArray::SetAt  
 Tato funkce člen volá `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYP*  
 Typ elementů uložené v poli základní třídy.  
  
 *PTR*  
 Ukazatel na element, který má být vložen v poli na nIndex. Je povolena hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).  
  
##  <a name="setatgrow"></a>CTypedPtrArray::SetAtGrow  
 Tato funkce člen volá `BASE_CLASS` **:: SetAtGrow**.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0.  
  
 *TYP*  
 Typ elementů uložené v poli základní třídy.  
  
 `newElement`  
 Ukazatel objektu, který má být přidán do tohoto pole. A **NULL** je povolena hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPtrArray – třída](../../mfc/reference/cptrarray-class.md)   
 [CObArray – třída](../../mfc/reference/cobarray-class.md)
