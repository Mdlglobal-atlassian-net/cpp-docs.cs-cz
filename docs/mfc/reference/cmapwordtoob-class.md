---
title: "Třída CMapWordToOb | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
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
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7166fd1b0ce0f8e9152c617979d0ec80bfb2b57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmapwordtoob-class"></a>CMapWordToOb – třída
Podporuje mapy `CObject` ukazatele s klíči 16bitové slova.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMapWordToOb : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CMapWordToOb` jsou podobné funkce člena třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti, můžete použít `CMapStringToOb` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CString` nebo **const** ukazatel na `char` jako parametr funkce nebo vrací hodnotu, nahraďte **WORD**.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 například překládá do  
  
 `BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`  
  
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
 `CMapWordToOb`zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Každý prvek serializován zase Pokud mapy uložen do archivu, buď pomocí přetížené vložení (  **<<** ) operátor nebo pomocí `Serialize` – členská funkce.  
  
 Pokud potřebujete výpis individuální **WORD** -  `CObject` elementy, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Když `CMapWordToOb` je odstraněn objekt, pokud jeho elementy odstraněna, nebo `CObject` ukazatele, se odeberou. Objekty odkazuje `CObject` ukazatele nejsou zničena.  
  
 Další informace o `CMapWordToOb`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapWordToOb`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



