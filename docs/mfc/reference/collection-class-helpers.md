---
title: Pomocné rutiny třídy kolekce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d00d78acf7ddf8cfa27e117cbcdbbb00c7d6fa6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce
Třídy kolekce `CMap`, `CList`, a `CArray` použít šablonované globální pomocných funkcí pro tyto účely jako porovnávání, kopírování a serializace prvků. Jako součást vaší implementace třídy na základě `CMap`, `CList`, a `CArray`, je nutné přepsat tyto funkce v případě potřeby s verzemi přizpůsobit typ dat uložených na mapě, seznamu nebo pole. Informace o přepsání pomocných funkcí, jako `SerializeElements`, najdete v článku [kolekcí: jak provádět typově bezpečné kolekce](../../mfc/how-to-make-a-type-safe-collection.md). Všimněte si, že **constructelements –** a **destructelements –** jsou zastaralé.  
  
 Knihovny Microsoft Foundation Class poskytuje následující globální funkce v afxtempl.h při přizpůsobení kolekce tříd:  
  
### <a name="collection-class-helpers"></a>Pomocné rutiny třídy kolekce  
  
|||  
|-|-|  
|[Compareelements –](#compareelements)|Určuje, zda elementy jsou stejné.|  
|[Copyelements –](#copyelements)|Zkopíruje elementy z jednoho pole do jiného.|  
|[Dumpelements –](#dumpelements)|Poskytuje výstup diagnostiky orientované datového proudu.|  
|[HashKey.](#hashkey)|Vypočítá klíč algoritmu hash.|  
|[Serializeelements –](#serializeelements)|Ukládá nebo načítá elementy do nebo z archivu.|  
  
##  <a name="compareelements"></a>  Compareelements –  
 Volat přímo nástrojem [CList::Find] (clist class.md #not_found.md #clist__find a nepřímo [cmap__lookup](cmap-class.md#lookup) a [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ první prvek, který se má porovnat.  
  
 `pElement1`  
 Ukazatel na první prvek, který se má porovnat.  
  
 `ARG_TYPE`  
 Typ druhého elementu, který se má porovnat.  
  
 `pElement2`  
 Ukazatel na druhý prvkem, který se má porovnat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt na kterou odkazuje `pElement1` je stejný jako objekt, na kterou odkazuje `pElement2`; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `CMap` Volá použití `CMap` parametry šablony *klíč* a `ARG_KEY`.  
  
 Výchozí implementace vrací výsledek při porovnání  *\*pElement1* a  *\*pElement2*. Funkci přepište tak, aby porovná elementy způsobem, který je vhodný pro vaši aplikaci.  
  
 Relační operátor definuje jazyka C++ ( `==`) pro jednoduché typy ( `char`, `int`, **float**a tak dále), ale nedefinuje operátor porovnání pro třídy a struktury. Pokud chcete použít `CompareElements` nebo k vytvoření instance jednoho typu tříd kolekce, které se používá, musíte definovat relační operátor nebo přetížení `CompareElements` s verzí, která vrátí odpovídající hodnoty.  
  
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
 *TYP*  
 Parametr šablony určující typ elementů, které se mají zkopírovat.  
  
 `pDest`  
 Ukazatel na cílový, které budou elementy zkopírovány.  
  
 `pSrc`  
 Ukazatel na zdroj prvky, které mají být zkopírovány.  
  
 `nCount`  
 Počet prvků, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace používá operátor jednoduchého přiřazení ( **=** ) k provedení operace kopírování. Pokud typ kopírovány nemá přetížené operátor =, pak provede výchozí implementace bitové kopie.  
  
 Informace o implementaci toto a další podpůrné funkce, najdete v článku [kolekcí: jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxtempl.h  
  
##  <a name="dumpelements"></a>  Dumpelements –  
 Poskytuje orientované na datový proud výstup diagnostiky v textové podobě pro elementy kolekce při přepisu.  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parametry  
 `dc`  
 Dump kontext pro vypsání elementy.  
  
 *TYP*  
 Určení typu elementů parametr šablony.  
  
 `pElements`  
 Ukazatel na elementy, které mají být uloženy.  
  
 `nCount`  
 Počet prvků mají být uloženy.  
  
### <a name="remarks"></a>Poznámky  
 **CArray::Dump**, **CList::Dump**, a **CMap::Dump** funkce toto volání, pokud je hloubkou výpisu větší než 0.  
  
 Výchozí implementace neprovede žádnou akci. Pokud elementy kolekce jsou odvozeny od `CObject`, přepsání bude obvykle iteraci v rámci kolekce elementů, volání `Dump` pro každý prvek v vypněte.  
  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxtempl.h  
  
##  <a name="hashkey"></a>  HashKey.  
 Vypočítá hodnotu hash pro zadaný klíč.  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr šablony zadání datový typ používaný pro přístup k klíče mapy.  
  
 `key`  
 Klíč, jehož hodnota hash je vypočtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota hash klíče.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána přímo nástrojem [CMap::RemoveKey](cmap-class.md#removekey) a nepřímo [CMap::Lookup](cmap-class.md#lookup) a [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).
  
 Výchozí implementace vytvoří hodnotu hash přepínáním `key` přímo pomocí čtyř pozic. Funkci přepište tak, aby ho vrátil hodnoty hash vhodné pro vaši aplikaci.  
  
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
  
##  <a name="serializeelements"></a>  Serializeelements –  
 [Carray –](carray-class.md), [CList](clist-class.md), a [CMap](cmap-class.md) volání této funkce určená k serializaci elementy.  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Určení typu elementů parametr šablony.  
  
 `ar`  
 Objekt archivu pro archivaci do nebo z.  
  
 `pElements`  
 Ukazatel na elementy archivován.  
  
 `nCount`  
 Počet elementů archivovaných  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nemá bitové operace čtení nebo zápisu.  
  
 Informace o implementaci toto a další podpůrné funkce, najdete v článku [kolekcí: jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v článku [kolekcí: jak provádět typově bezpečné kolekce](../how-to-make-a-type-safe-collection.md).  
 
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxtempl.h 
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [CMap – třída](cmap-class.md)   
 [CList – třída](clist-class.md)   
 [CArray – třída](carray-class.md)