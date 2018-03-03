---
title: "Třída CMapPtrToWord | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 634f22ae50247a8d4f3a0d3e19e6e6bdef7041d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord – třída
Podporuje mapy slova 16 bitů s klíči neplatné ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMapPtrToWord : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CMapPtrToWord` jsou podobné funkce člena třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti, můžete použít `CMapStringToOb` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako parametr funkce nebo vrací hodnotu, nahraďte **WORD**. Po zobrazení `CString` nebo **const** ukazatel na `char` jako parametr funkce nebo vrací hodnotu, nahraďte ukazatel na `void`.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 například překládá do  
  
 `BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Vrátí počet prvků v této mapě.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Určuje aktuální počet elementů v zatřiďovací tabulce.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Získá další prvek pro iterace.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Vrátí počet prvků v této mapě.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Vrátí pozici prvního prvku.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Vypočítá hodnotu hash zadaného klíče.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializuje zatřiďovací tabulku.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Vyhledá neplatný ukazatel na základě klíče neplatný ukazatel. Hodnota ukazatele, není entita, na kterou odkazuje, se používá pro klíče porovnání.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Vrátí odkaz na klíč spojený se zadanou hodnotou klíče.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny elementy mapy.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere element určeného klíč.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží element do mapy; nahradí existující elementu, pokud je nalezen odpovídající klíč.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží element do mapy – operátor nahrazování pro `SetAt`.|  
  
## <a name="remarks"></a>Poznámky  
 `CMapWordToPtr`zahrnuje `IMPLEMENT_DYNAMIC` makro pro podporu přístupu běhového typu a k vypsání `CDumpContext` objektu. Pokud potřebujete výpis prvků jednotlivých mapy, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Mapy ukazatel slovo nesmí být serializován.  
  
 Když `CMapPtrToWord` je odstraněn objekt, nebo při jeho prvky jsou odebrány, jsou odebrány následující ukazatele a slova. Entity, které odkazuje klíčové ukazatele neodeberou.  
  
 Další informace o `CMapPtrToWord`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapPtrToWord`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



