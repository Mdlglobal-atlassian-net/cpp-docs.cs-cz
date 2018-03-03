---
title: "CTypedPtrMap – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9056fc73e2718b2a21936c39e630f4d4fddf1eed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap – třída
Poskytuje bezpečnost typů "obálky" pro objekty třídy map ukazatel `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, a `CMapStringToPtr`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Základní třída třídy map typu ukazatele; musí být třída mapy ukazatele ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, nebo `CMapStringToPtr`).  
  
 `KEY`  
 Třída objektu použitého jako klíč k mapy.  
  
 `VALUE`  
 Třída objektu uložené v mapě.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|  
|[CTypedPtrMap::Lookup](#lookup)|Vrátí `KEY` na základě `VALUE`.|  
|[CTypedPtrMap::RemoveKey](#removekey)|Odebere element určeného klíč.|  
|[CTypedPtrMap::SetAt](#setat)|Vloží element do mapy; nahradí existující elementu, pokud je nalezen odpovídající klíč.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CTypedPtrMap::operator]](#operator_at)|Element vloží do mapy.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití `CTypedPtrMap`, kontrola typu zařízení C++ pomáhá eliminovat chyby způsobené typy neodpovídající ukazatelů.  
  
 Protože všechny `CTypedPtrMap` jsou vložené funkce, pomocí této šablony nemá vliv na výrazně velikost a rychlost kódu.  
  
 Další informace o používání `CTypedPtrMap`, najdete v článcích [kolekce](../../mfc/collections.md) a [na základě šablon třídy](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 Načte element mapy v `rNextPosition`, pak aktualizuje `rNextPosition` odkazovat na další prvek v mapě.  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rPosition`  
 Určuje odkaz na **pozice** hodnoty vrácené předchozí `GetNextAssoc` nebo `BASE_CLASS` **:: GetStartPosition** volání.  
  
 *KEY*  
 Určení typu klíče mapy pro parametr šablony.  
  
 `rKey`  
 Určuje vrácená klíč načtený elementu.  
  
 *HODNOTA*  
 Parametr šablony určení typu hodnoty na mapě.  
  
 `rValue`  
 Určuje vrácená hodnota načtené elementu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nejvhodnější pro iterace v rámci všechny elementy v mapě. Všimněte si, že pořadí pozice není nutně stejná jako hodnota klíče pořadí.  
  
 Pokud načtené elementem je poslední v mapě, pak nová hodnota `rNextPosition` je nastaven na **NULL**.  
  
 Tato vložená funkce volá `BASE_CLASS` **:: GetNextAssoc**.  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`používá algoritmus hash se s klíčem, který přesně odpovídá rychle najít elementu mapy.  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `BASE_CLASS`  
 Parametr šablony zadání toto mapování třídy základní třídy.  
  
 `key`  
 Klíč elementu, který chcete vyhledávat.  
  
 *HODNOTA*  
 Parametr šablony určující typy hodnot uložených v této mapě.  
  
 `rValue`  
 Určuje vrácená hodnota načtené elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl nalezen element; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato vložená funkce volá `BASE_CLASS` **:: vyhledávání**.  
  
##  <a name="operator_at"></a>[CTypedPtrMap::operator]  
 Tento operátor. můžete použít pouze na levé straně příkazu přiřazení (l hodnota).  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>Parametry  
 *HODNOTA*  
 Parametr šablony určující typy hodnot uložených v této mapě.  
  
 `BASE_CLASS`  
 Parametr šablony zadání toto mapování třídy základní třídy.  
  
 `key`  
 Klíč elementu, který chcete vyhledávat nebo vytvořené v mapě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud neexistuje žádný element mapy se zadaným klíčem, je vytvoření nového elementu. Ekvivalentní tento operátor není žádná "pravé straně" (r-value), protože je možné, který klíč asi se nenašla v mapě. Použití `Lookup` – členská funkce pro načtení elementu.  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 Tato funkce člen volá `BASE_CLASS` **:: RemoveKey**.  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>Parametry  
 *KEY*  
 Určení typu klíče mapy pro parametr šablony.  
  
 `key`  
 Klíč elementu k odebrání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla položka nalezena a úspěšně odebral; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 Tato funkce člen volá `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>Parametry  
 *KEY*  
 Určení typu klíče mapy pro parametr šablony.  
  
 `key`  
 Určuje hodnotu klíče newValue.  
  
 `newValue`  
 Určuje ukazatele objektu, který je hodnota nového elementu.  
  
### <a name="remarks"></a>Poznámky  
 Podrobné poznámky, najdete v části [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr – třída](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord – třída](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr – třída](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr – třída](../../mfc/reference/cmapstringtoptr-class.md)
