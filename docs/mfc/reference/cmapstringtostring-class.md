---
title: Třída CMapStringToString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
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
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToString [MFC], CPair
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
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43c9fdc667f5bd40b6c683f6e48753a084266847
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037645"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString – třída
Podporuje mapy `CString` objekty s klíči `CString` objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CMapStringToString` jsou podobné funkce člena třídy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Z důvodu této podobnosti, můžete použít `CMapStringToOb` referenční dokumentace pro konkrétní funkce člen. Po zobrazení `CObject` ukazatel jako návratová hodnota nebo "výstupní" funkce parametr nahrazení ukazatele na **char**. Po zobrazení `CObject` ukazatel jako "vstupní" funkce parametr, nahraďte ukazatel na **char**.  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 například překládá do  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>Veřejné struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|Vnořené struktury obsahující hodnotou klíče a hodnoty objekt přidružený řetězce.|  
  
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
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Získá ukazatel na první `CString` v mapě.|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Získá ukazatel na další `CString` pro iterace.|  
|[CMapStringToString::PLookup](#plookup)|Vrátí ukazatel na `CString` jejíž hodnota odpovídá zadané hodnotě.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Odebere všechny elementy mapy.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Odebere element určeného klíč.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Vloží element do mapy; nahradí existující elementu, pokud je nalezen odpovídající klíč.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Vloží element do mapy – operátor nahrazování pro `SetAt`.|  
  
## <a name="remarks"></a>Poznámky  
 `CMapStringToString` zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Každý prvek serializován zase Pokud mapy uložen do archivu, buď pomocí přetížené vložení ( **<<**) operátor nebo pomocí `Serialize` – členská funkce.  
  
 Pokud potřebujete výpis individuální `CString` -  `CString` elementy, je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Když `CMapStringToString` je odstraněn objekt, pokud jeho elementy odstraněna, nebo `CString` objekty jsou odebrány podle potřeby.  
  
 Další informace o `CMapStringToString`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
##  <a name="cpair"></a>  CMapStringToString::CPair  
 Obsahuje hodnotu klíče a hodnoty objekt přidružený řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Toto je vnořené struktury v rámci třídy [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).  
  
 Struktura se skládá ze dvou polích:  
  
- **klíč** se skutečnou hodnotou typ klíče.  
  
- **Hodnota** hodnota přidruženého objektu.  
  
 Se používá k ukládání vrácené hodnoty z [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), a [CMapStringToString::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Příklad  
  Příklad použití, podívejte se na příklad pro [CMapStringToString::PLookup](#plookup).  
  
##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc  
 Vrátí první položku objekt map.  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na první položku v mapě; v tématu [CMapStringToString::CPair](#cpair). Pokud mapy je prázdná, je hodnota `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se vrátit ukazatel prvním elementem v objektu mapy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc  
 Načte elementu mapy, na kterou odkazuje *pAssocRec*.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pAssoc*  
 Odkazuje na položku mapování vrácený předchozím [PGetNextAssoc](#pgetnextassoc) nebo [PGetFirstAssoc](#pgetfirstassoc) volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku v mapě; v tématu [CMapStringToString::CPair](#cpair). Pokud se element nachází posledních v mapě, je hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu k iteraci v rámci všechny elementy v mapě. Načíst první prvek pomocí volání `PGetFirstAssoc` a pak iteraci v rámci mapy při následných voláních k `PGetNextAssoc`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>  CMapStringToString::PLookup  
 Vyhledá hodnotu namapované na k danému klíči.  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 *Klíč*  
 Ukazatel na klíč pro element, který má být vyhledán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel se zadaným klíčem.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem vyhledání elementu mapy s klíčem, který přesně odpovídá danému klíči.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



