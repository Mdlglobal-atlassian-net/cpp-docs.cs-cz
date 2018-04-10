---
title: Třída CMap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd7c1b23e3c586bf89a86e17d85ee5b5050fbf37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmap-class"></a>CMap – třída
Třída kolekce slovník, který mapuje klíče jedinečné hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>Parametry  
 `KEY`  
 Třída objektu použitého jako klíč k mapy.  
  
 `ARG` *_* `KEY`  
 Datový typ používaný pro `KEY` argumenty; obvykle odkaz na `KEY`.  
  
 `VALUE`  
 Třída objektu uložené v mapě.  
  
 `ARG` *_* `VALUE`  
 Datový typ používaný pro `VALUE` argumenty; obvykle odkaz na `VALUE`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-structures"></a>Veřejné struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[CMap::CPair](#cpair)|Vnořené struktury obsahující hodnotou klíče a hodnoty přidruženého objektu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMap::CMap](#cmap)|Sestaví kolekci, který mapuje klíče hodnoty.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMap::GetCount](#getcount)|Vrátí počet prvků v této mapě.|  
|[CMap::GetHashTableSize](#gethashtablesize)|Vrátí počet prvků v zatřiďovací tabulce.|  
|[CMap::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|  
|[CMap::GetSize](#getsize)|Vrátí počet prvků v této mapě.|  
|[CMap::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|  
|[CMap::InitHashTable](#inithashtable)|Inicializuje zatřiďovací tabulku a určuje jeho velikost.|  
|[CMap::IsEmpty](#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|  
|[CMap::Lookup](#lookup)|Vyhledá hodnotu namapované na k danému klíči.|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Vrací ukazatel na první prvek.|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|Získá ukazatel na další prvek pro iterace.|  
|[CMap::PLookup](#plookup)|Vrací ukazatel na klíč, jehož hodnota odpovídá zadané hodnotě.|  
|[CMap::RemoveAll](#removeall)|Odebere všechny elementy mapy.|  
|[CMap::RemoveKey](#removekey)|Odebere element určeného klíč.|  
|[CMap::SetAt](#setat)|Vloží element do mapy; nahradí existující elementu, pokud je nalezen odpovídající klíč.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CMap::operator]](#operator_at)|Vloží element do mapy – operátor nahrazování pro `SetAt`.|  
  
## <a name="remarks"></a>Poznámky  
 Po vložení pár klíč hodnota (element) do mapy, můžete efektivně načíst nebo odstranit pár pomocí klíče k přístupu. Můžete také iterovat přes všechny elementy v mapě.  
  
 Proměnné typu **pozice** se používá pro alternativní přístup k položky. Můžete použít **pozice** "pamatovat" položku a k iteraci v rámci mapy. Může si myslíte, že je tento iterace sekvenční hodnotou klíče; není. Je neurčitém pořadí načtené elementů.  
  
 Určité funkce člena třídy volání globální pomocné funkce, které je nutné upravit pro většiny použití `CMap` třídy. V tématu [pomocné rutiny třídy kolekce](../../mfc/reference/collection-class-helpers.md) v oddílu makra a globální prvky `MFC Reference`.  
  
 `CMap`přepsání [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pro podporu serializace a vypsání jejích elementů. Pokud je uložen mapu k archivu pomocí `Serialize`, každý element mapy zase serializován. Výchozí implementaci `SerializeElements` pomocné funkce nemá bitové operace zápisu. Pro informace o serializaci položek kolekce ukazatel odvozené od `CObject` nebo najdete v části Další uživatelem definované typy [postupy: Příprava typově bezpečné kolekce](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Pokud potřebujete výpis diagnostiky jednotlivých prvků v mapě (klíče a hodnoty), je nutné nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Když `CMap` je odstraněn objekt, nebo při jeho prvky jsou odebrány, jsou odebrány klíče a hodnoty.  
  
 Odvození třídy map je podobná odvození seznamu. Najdete v článku [kolekce](../../mfc/collections.md) ilustraci odvození třídy speciální seznamu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtempl.h  
  
##  <a name="cmap"></a>CMap::CMap  
 Vytvoří prázdný mapy.  
  
```  
CMap(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Určuje členitost přidělení paměti pro rozšíření mapy.  
  
### <a name="remarks"></a>Poznámky  
 S růstem mapy jednotek se přidělí paměť `nBlockSize` položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>CMap::CPair  
 Obsahuje hodnotu klíče a hodnoty přidruženého objektu.  
  
### <a name="remarks"></a>Poznámky  
 Toto je vnořené struktury v rámci třídy [CMap](../../mfc/reference/cmap-class.md).  
  
 Struktura se skládá ze dvou polích:  
  
- **klíč** se skutečnou hodnotou typ klíče.  
  
- **Hodnota** hodnota přidruženého objektu.  
  
 Se používá k ukládání vrácené hodnoty z [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), a [CMap::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Příklad  
 Příklad použití, podívejte se na příklad pro [CMap::PLookup](#plookup).  
  
##  <a name="getcount"></a>CMap::GetCount  
 Získá počet elementů v mapě.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::Lookup](#lookup).  
  
##  <a name="gethashtablesize"></a>CMap::GetHashTableSize  
 Určuje počet elementů v zatřiďovací tabulce pro mapu.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v zatřiďovací tabulce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>CMap::GetNextAssoc  
 Načte element mapy v `rNextPosition`, pak aktualizuje `rNextPosition` odkazovat na další prvek v mapě.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rNextPosition`  
 Určuje odkaz na **pozice** hodnoty vrácené předchozí `GetNextAssoc` nebo `GetStartPosition` volání.  
  
 *KEY*  
 Určení typu klíče mapy pro parametr šablony.  
  
 `rKey`  
 Určuje vrácená klíč načtený elementu.  
  
 *HODNOTA*  
 Parametr šablony určující typ hodnoty na mapě.  
  
 `rValue`  
 Určuje vrácená hodnota načtené elementu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nejvhodnější pro iterace v rámci všechny elementy v mapě. Všimněte si, že pořadí pozice není nutně stejná jako hodnota klíče pořadí.  
  
 Pokud načtené elementem je poslední v mapě, pak nová hodnota `rNextPosition` je nastaven na **NULL**.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::SetAt](#setat).  
  
##  <a name="getsize"></a>CMap::GetSize  
 Vrátí počet elementů mapy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v mapě.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet elementů v mapě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>CMap::GetStartPosition  
 Spuštění mapy iterace vrácením **pozice** hodnotu, která se dá předat do `GetNextAssoc` volání.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která určuje počáteční pozici pro iterace mapování, nebo **NULL** Pokud mapy je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Iterace pořadí není předvídatelný; "první prvek v mapě" má proto žádné zvláštní význam.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::SetAt](#setat).  
  
##  <a name="inithashtable"></a>CMap::InitHashTable  
 Inicializuje zatřiďovací tabulku.  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>Parametry  
 `hashSize`  
 Počet položek v zatřiďovací tabulce.  
  
 `bAllocNow`  
 Pokud **TRUE**, přidělí zatřiďovací tabulku při inicializaci; v opačném případě je přidělená v tabulce, v případě potřeby.  
  
### <a name="remarks"></a>Poznámky  
 Pro nejlepší výkon velikost tabulky hash musí být číslo prime. Minimalizovala kolize, by měl mít velikost přibližně 20 procent větší než největší předpokládaného datové sady.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::Lookup](#lookup).  
  
##  <a name="isempty"></a>CMap::IsEmpty  
 Určuje, zda mapy je prázdný.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že tato mapa neobsahuje žádné elementy. jinak 0.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::RemoveAll](#removeall).  
  
##  <a name="lookup"></a>CMap::Lookup  
 Vyhledá hodnotu namapované na k danému klíči.  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr šablony určující typ `key` hodnotu.  
  
 `key`  
 Určuje klíč, který identifikuje elementu, který chcete vyhledávat.  
  
 *HODNOTA*  
 Určuje typ hodnota, která má být prohledávat.  
  
 `rValue`  
 Získá hodnotu vyhledaných.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl nalezen element; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Lookup`používá algoritmus hash a rychle tak najít elementu mapy s klíčem, který přesně odpovídá danému klíči.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>[CMap::operator]  
 Vhodnou náhradu za `SetAt` – členská funkce.  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>Parametry  
 *HODNOTA*  
 Parametr šablony určující typ hodnoty mapy.  
  
 `ARG_KEY`  
 Parametr šablony zadejte hodnotu klíče.  
  
 `key`  
 Klíč používaný k načtení hodnoty z mapování.  
  
### <a name="remarks"></a>Poznámky  
 Proto je lze použít pouze na levé straně příkazu přiřazení (l hodnota). Pokud neexistuje žádný element mapy se zadaným klíčem, je vytvoření nového elementu.  
  
 Ekvivalentní tento operátor není žádná "pravé straně" (r-value), protože je možné, který klíč asi se nenašla v mapě. Použití `Lookup` – členská funkce pro načtení elementu.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::Lookup](#lookup).  
  
##  <a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc  
 Vrátí první položku objekt map.  
  
```  
const CPair* PGetFirstAssoc() const; 
CPair* PGetFirstAssoc();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na první položku v mapě; v tématu [CMap::CPair](#cpair). Pokud mapy neobsahuje žádné položky, hodnota je **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se vrátit ukazatel prvním elementem v objektu mapy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMap::PGetNextAssoc  
 Načte elementu mapy, na kterou odkazuje `pAssocRec`.  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;  
  
CPair *PGetNextAssoc(const CPair* pAssocRet);
```  
  
### <a name="parameters"></a>Parametry  
 *pAssocRet*  
 Odkazuje na položku mapování vrácený předchozím [PGetNextAssoc](#pgetnextassoc) nebo [CMap::PGetFirstAssoc](#pgetfirstassoc) volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další položku v mapě; v tématu [CMap::CPair](#cpair). Pokud se element nachází posledních v mapě, je hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu k iteraci v rámci všechny elementy v mapě. Načíst první prvek pomocí volání `PGetFirstAssoc` a pak iteraci v rámci mapy při následných voláních k `PGetNextAssoc`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>CMap::PLookup  
 Vyhledá hodnotu namapované na k danému klíči.  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč elementu má být vyhledán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na strukturu klíče; v tématu [CMap::CPair](#cpair). Pokud není nalezena žádná shoda, `CMap::PLookup` vrátí `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem vyhledání elementu mapy s klíčem, který přesně odpovídá danému klíči.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>CMap::RemoveAll  
 Odebere všechny hodnoty z této mapě voláním globální pomocné funkce **destructelements –**.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce funguje správně, pokud mapy už je prázdný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]  
  
##  <a name="removekey"></a>CMap::RemoveKey  
 Vyhledá položku mapování odpovídající zadaný klíč; poté Pokud je nalezen klíč, odebere položku.  
  
```  
BOOL RemoveKey(ARG_KEY key);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Určení typu klíče parametr šablony.  
  
 `key`  
 Klíč elementu k odebrání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla položka nalezena a úspěšně odebral; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 **Destructelements –** pomocné funkce slouží k odebrání položky.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>CMap::SetAt  
 Primární znamená vložit element v mapování.  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr šablony určující typ `key` parametr.  
  
 `key`  
 Určuje klíč nového elementu.  
  
 `ARG_VALUE`  
 Parametr šablony určující typ `newValue` parametr.  
  
 `newValue`  
 Určuje hodnotu nového elementu.  
  
### <a name="remarks"></a>Poznámky  
 Nejprve je klíč vyhledávat. Pokud je nalezen klíč, pak se změní s odpovídající hodnotou; v opačném případě se vytvoří nový pár klíč hodnota.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)  
