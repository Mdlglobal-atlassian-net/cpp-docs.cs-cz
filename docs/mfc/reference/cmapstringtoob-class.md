---
title: Třída CMapStringToOb | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
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
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52adc7ce08644fb002b2a0a2cd91d20d15d4f24a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb – třída
Třídy kolekce slovník, který je přiřazen jedinečný `CString` objekty ke `CObject` ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMapStringToOb : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](#getcount)|Vrátí počet prvků v této mapě.|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Určuje aktuální počet elementů v zatřiďovací tabulce.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Získá další prvek pro iterace.|  
|[CMapStringToOb::GetSize](#getsize)|Vrátí počet prvků v této mapě.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Vrátí pozici prvního prvku.|  
|[CMapStringToOb::HashKey](#hashkey)|Vypočítá hodnotu hash zadaného klíče.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializuje zatřiďovací tabulku.|  
|[CMapStringToOb::IsEmpty](#isempty)|Testy pro podmínku prázdný mapy (žádné elementy).|  
|[CMapStringToOb::Lookup](#lookup)|Vyhledá neplatný ukazatel na základě klíče neplatný ukazatel. Hodnota ukazatele, není entita, na kterou odkazuje, se používá pro klíče porovnání.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Vrátí odkaz na klíč spojený se zadanou hodnotou klíče.|  
|[CMapStringToOb::RemoveAll](#removeall)|Odebere všechny elementy mapy.|  
|[CMapStringToOb::RemoveKey](#removekey)|Odebere element určeného klíč.|  
|[CMapStringToOb::SetAt](#setat)|Vloží element do mapy; nahradí existující elementu, pokud je nalezen odpovídající klíč.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](#operator_at)|Vloží element do mapy – operátor nahrazování pro `SetAt`.|  
  
## <a name="remarks"></a>Poznámky  
 Po vložení `CString` -  `CObject*` pár (element) do mapy, můžete efektivně načíst nebo odstranit pár pomocí řetězec nebo `CString` hodnotu jako klíč. Můžete také iterovat přes všechny elementy v mapě.  
  
 Proměnné typu **pozice** se používá pro přístup k alternativní položka v všechny varianty mapy. Můžete použít **pozice** "pamatovat" položku a k iteraci v rámci mapy. Může si myslíte, že je tento iterace sekvenční hodnotou klíče; není. Je neurčitém pořadí načtené elementů.  
  
 `CMapStringToOb` zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Každý prvek serializován zase Pokud mapy uložen do archivu, buď pomocí přetížené vložení ( **<<**) operátor nebo pomocí `Serialize` – členská funkce.  
  
 Pokud potřebujete výpis diagnostiky jednotlivých prvků v mapě ( `CString` hodnotu a `CObject` obsah), hloubka kontext výpisu musíte nastavit na 1 nebo vyšší.  
  
 Když `CMapStringToOb` je odstraněn objekt, pokud jeho elementy odstraněna, nebo `CString` objekty a `CObject` ukazatele, se odeberou. Objekty odkazuje `CObject` ukazatele nejsou zničena.  
  
 Odvození třídy map je podobná odvození seznamu. Najdete v článku [kolekce](../../mfc/collections.md) ilustraci odvození třídy speciální seznamu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb  
 Vytvoří prázdnou `CString`- na - `CObject*` mapy.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametry  
 `nBlockSize`  
 Určuje členitost přidělení paměti pro rozšíření mapy.  
  
### <a name="remarks"></a>Poznámky  
 S růstem mapy jednotek se přidělí paměť `nBlockSize` položky.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné **CMapStringToOb:: CMapStringToOb**.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
##  <a name="getcount"></a>  CMapStringToOb::GetCount  
 Určuje, kolik prvky jsou v mapě.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v této mapě.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetCount`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount (const;)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount (const;)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount (const;)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount (const;)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount (const;)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount (const;)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize  
 Určuje aktuální počet elementů v zatřiďovací tabulce.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků v zatřiďovací tabulce.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetHashTableSize`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize (const;)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize (const;)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize (const;)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize (const;)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize (const;)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize (const;)**|  
  
##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc  
 Načte element mapy v *rNextPosition*, pak aktualizuje *rNextPosition* odkazovat na další prvek v mapě.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rNextPosition*  
 Určuje odkaz na **pozice** hodnoty vrácené předchozí **GetNextAssoc** nebo **GetStartPosition** volání.  
  
 *rKey*  
 Určuje vrácená klíč načtený elementu (řetězec).  
  
 *rValue*  
 Určuje vrácená hodnota načtené elementu ( **CObject** ukazatel). Další informace o tomto parametru najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nejvhodnější pro iterace v rámci všechny elementy v mapě. Všimněte si, že pořadí pozice není nutně stejná jako hodnota klíče pořadí.  
  
 Pokud načtené elementem je poslední v mapě, pak nová hodnota *rNextPosition* je nastaven na **NULL**.  
  
 Pro *rValue* parametr, nezapomeňte přetypovat vašeho typu objektu pro **CObject\*&**, což je co vyžaduje kompilátor, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 To neplatí o **GetNextAssoc** pro maps na základě šablon.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné **CMapStringToOb::GetNextAssoc**.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, void\* &**  *rKey* **, WORD &** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, CString &** *rKey* **, void\* &**  *rValue* **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, CString &** *rKey* **, CString &** *rValue* **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *rValue* **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (pozice &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *rValue* **) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>  CMapStringToOb::GetSize  
 Vrátí počet elementů mapy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v mapě.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet elementů v mapě.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetSize`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; (INT_PTR getsize –)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; (INT_PTR getsize –)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; (INT_PTR getsize –)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; (INT_PTR getsize –)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; (INT_PTR getsize –)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; (INT_PTR getsize –)**|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition  
 Spuštění mapy iterace vrácením **pozice** hodnotu, která se dá předat do `GetNextAssoc` volání.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **pozice** hodnotu, která určuje počáteční pozici pro iterace mapování, nebo **NULL** Pokud mapy je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Iterace pořadí není předvídatelný; "první prvek v mapě" má proto žádné zvláštní význam.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::GetStartPosition`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POZICE GetStartPosition (const;)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POZICE GetStartPosition (const;)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POZICE GetStartPosition (const;)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POZICE GetStartPosition (const;)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POZICE GetStartPosition (const;)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POZICE GetStartPosition (const;)**|  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMapStringToOb::GetNextAssoc](#getnextassoc).  
  
##  <a name="hashkey"></a>  CMapStringToOb::HashKey  
 Vypočítá hodnotu hash zadaného klíče.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč, jehož hodnota hash je vypočtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota hash klíče  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::HashKey`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**HashKey – UINT (void\***  `key` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**HashKey – UINT (void\***  `key` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**HashKey – UINT (LPCTSTR** `key` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**HashKey – UINT (LPCTSTR** `key` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**HashKey – UINT (WORD** `key` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**HashKey – UINT (WORD** `key` **) const;**|  
  
##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable  
 Inicializuje zatřiďovací tabulku.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hashSize`  
 Počet položek v zatřiďovací tabulce.  
  
 `bAllocNow`  
 Pokud **TRUE**, přidělí zatřiďovací tabulku při inicializaci; v opačném případě je přidělená v tabulce, v případě potřeby.  
  
### <a name="remarks"></a>Poznámky  
 Pro nejlepší výkon velikost tabulky hash musí být číslo prime. Minimalizovala kolize, by měl mít velikost přibližně 20 procent větší než největší předpokládaného datové sady.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::InitHashTable`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (Celé_číslo** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>  CMapStringToOb::IsEmpty  
 Určuje, zda mapy je prázdný.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že tato mapa neobsahuje žádné elementy. jinak 0.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [RemoveAll](#removeall).  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí další členské funkce, které jsou podobné **CMapStringToOb:: IsEmpty**.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty (const;)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty (const;)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty (const;)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty (const;)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty (const;)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty (const;)**|  
  
##  <a name="lookup"></a>  CMapStringToOb::Lookup  
 Vrátí `CObject` ukazatel na základě `CString` hodnotu.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč řetězec, který identifikuje elementu, který chcete vyhledávat.  
  
 `rValue`  
 Určuje vrácená hodnota z vyhledaných elementu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl nalezen element; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Lookup` používá algoritmus hash se s klíčem, který přesně odpovídá rychle najít elementu mapy ( `CString` hodnotu).  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::LookUp`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Vyhledávání BOOL (void\***  `key` **, void\* &**  `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Vyhledávání BOOL (void\***  `key` **, WORD &** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Vyhledávání BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Vyhledávání BOOL (LPCTSTR** `key` **, CString &** `rValue` **) const;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Vyhledávání BOOL (WORD** `key` **, CObject\* &**  `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Vyhledávání BOOL (WORD** `key` **, void\* &**  `rValue` **) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey  
 Vrátí odkaz na klíč spojený se zadanou hodnotou klíče.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje klíč řetězec, který identifikuje elementu, který chcete vyhledávat.  
  
 `rKey`  
 Odkaz na související klíč.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl klíč nalezen; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí odkazu na klíč nebezpečné použití po přidruženého prvku byla odebrána z mapování, nebo po mapy, byl zničen.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné **CMapStringToOb:: LookupKey**.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Vyhledávací BOOL (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Vyhledávací BOOL (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const;**|  
  
##  <a name="operator_at"></a>  [CMapStringToOb::operator]  
 Vhodnou náhradu za `SetAt` – členská funkce.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na ukazatel `CObject` objektu; nebo **NULL** Pokud mapy je prázdný nebo `key` je mimo rozsah.  
  
### <a name="remarks"></a>Poznámky  
 Proto je lze použít pouze na levé straně příkazu přiřazení (l hodnota). Pokud neexistuje žádný element mapy se zadaným klíčem, je vytvoření nového elementu.  
  
 Ekvivalentní tento operátor není žádná "pravé straně" (r-value), protože je možné, který klíč asi se nenašla v mapě. Použití `Lookup` – členská funkce pro načtení elementu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné **[CMapStringToOb::operator]**.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& [] – operátor (void\***  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & – operátor [] (void\***  `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& [] – operátor (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & – operátor [] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& [] – operátor (word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& [] – operátor (word** `key`  **\);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>  CMapStringToOb::RemoveAll  
 Odebere všechny elementy mapy a zničí `CString` klíče objekty.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 `CObject` Nejsou zničení objektů odkazuje každý klíč. `RemoveAll` Funkce může způsobit nevracení paměti, pokud je není ujistit, že odkazovaná `CObject` objekty budou ztraceny.  
  
 Funkce funguje správně, pokud mapy už je prázdný.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::RemoveAll`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void (RemoveAll);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void (RemoveAll);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void (RemoveAll);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void (RemoveAll);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void (RemoveAll);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void (RemoveAll);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>  CMapStringToOb::RemoveKey  
 Vyhledá položku mapování odpovídající zadaný klíč; poté Pokud je nalezen klíč, odebere položku.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje řetězec, který používá pro vyhledávání map.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla položka nalezena a úspěšně odebral; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To může způsobit nevracení paměti, pokud `CObject` objekt není odstranit jinde.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::RemoveKey`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\***  `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>  CMapStringToOb::SetAt  
 Primární znamená vložit element v mapování.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Určuje řetězec, který je klíč nového elementu.  
  
 `newValue`  
 Určuje, `CObject` ukazatele, který je hodnota nového elementu.  
  
### <a name="remarks"></a>Poznámky  
 Nejprve je klíč vyhledávat. Pokud je nalezen klíč, pak se změní s odpovídající hodnotou; v opačném případě se vytvoří nový klíč hodnota elementu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CMapStringToOb::SetAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void\***  `key` **, void\***  `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void\***  `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void\***  `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject\***  `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void\***  `newValue` **);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr – třída](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord – třída](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr Class](../../mfc/reference/cmapstringtoptr-class.md)   
 [CMapStringToString – třída](../../mfc/reference/cmapstringtostring-class.md)   
 [CMapWordToOb Class](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr – třída](../../mfc/reference/cmapwordtoptr-class.md)
