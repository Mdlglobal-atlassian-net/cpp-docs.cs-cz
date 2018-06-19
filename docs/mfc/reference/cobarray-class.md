---
title: Třída CObArray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3995734918f50ed01fe6df7fb034c3ea37b630cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377911"
---
# <a name="cobarray-class"></a>CObArray – třída
Podporuje pole `CObject` ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CObArray : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::CObArray](#cobarray)|Vytvoří prázdné pole `CObject` ukazatele.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::Add](#add)|Přidá prvek na konec pole; zvětšování pole v případě potřeby.|  
|[CObArray::Append](#append)|Připojí další pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::Copy](#copy)|Zkopíruje jiného pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::ElementAt](#elementat)|Vrátí dočasné odkaz na element ukazatele v rámci pole.|  
|[CObArray::FreeExtra](#freeextra)|Uvolní všechny nevyužitou paměť nad aktuální horní mez.|  
|[CObArray::GetAt](#getat)|Vrátí hodnotu v daném indexu.|  
|[CObArray::GetCount](#getcount)|Získá počet elementů v toto pole.|  
|[CObArray::GetData](#getdata)|Umožňuje přístup k prvkům v poli. Může být **NULL**.|  
|[CObArray::GetSize](#getsize)|Získá počet elementů v toto pole.|  
|[CObArray::GetUpperBound](#getupperbound)|Vrátí největší platný index.|  
|[CObArray::InsertAt](#insertat)|Vloží zadaný index elementu (nebo všechny elementy v jiném poli).|  
|[CObArray::IsEmpty](#isempty)|Určuje, zda pole prázdné.|  
|[CObArray::RemoveAll](#removeall)|Odebere všechny elementy z tohoto pole.|  
|[CObArray::RemoveAt](#removeat)|Odebere element na konkrétním indexu.|  
|[CObArray::SetAt](#setat)|Nastaví hodnotu pro daného indexu; pole není povoleno zvětšovat.|  
|[CObArray::SetAtGrow](#setatgrow)|Nastaví hodnotu pro daného indexu; zvětšování pole v případě potřeby.|  
|[CObArray::SetSize](#setsize)|Nastaví počet prvků mají být obsažena v toto pole.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CObArray::operator]](#operator_at)|Nastaví nebo získá element v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato pole objektů jsou podobná C pole, ale můžete dynamicky zmenšit a růst podle potřeby.  
  
 Indexy pole vždy spustit na pozici 0. Můžete se rozhodnout, zda pro opravu horní mez nebo povolit pole pro rozbalit, pokud přidáte elementy za aktuální vazby. Se přidělí paměť souvisle horní mez, i když některé prvky jsou null.  
  
 V části Win32, velikost `CObArray` objektu je omezena pouze na dostupné paměti.  
  
 Stejně jako u pole C, čas přístupu `CObArray` indexované element konstantní a je nezávislý na velikost pole.  
  
 `CObArray` zahrnuje `IMPLEMENT_SERIAL` makro pro podporu serializace a vypsání jejích elementů. Pokud pole `CObject` ukazatele je uložen do archivu s operátorem přetížené vložení nebo s `Serialize` členské funkce se každý `CObject` element je, pak serializovat společně s jeho index pole.  
  
 Pokud potřebujete výpis individuální `CObject` prvků v poli, je nutné nastavit hloubka `CDumpContext` objekt, který má 1 nebo vyšší.  
  
 Když `CObArray` je odstraněn objekt, nebo pokud jeho elementy odeberou se jenom `CObject` ukazatele jsou odebrány, nikoliv objekty odkazují.  
  
> [!NOTE]
>  Před použitím pole, použijte `SetSize` k zahájení jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 Pole odvození třídy je podobná odvození seznamu. Podrobnosti o odvození třídy speciální seznamu, najdete v článku [kolekce](../../mfc/collections.md).  
  
> [!NOTE]
>  Je nutné použít `IMPLEMENT_SERIAL` makro k implementaci vaší odvozené třídy, pokud chcete serializovat pole.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
##  <a name="add"></a>  CObArray::Add  
 Přidá nový prvek na konec pole, pole narůstají o 1.  
  
```  
INT_PTR Add(CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `newElement`  
 `CObject` Ukazatele, který se má přidat do tohoto pole.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index přidaný prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [SetSize](#setsize) je použito `nGrowBy` mohou být přiděleny hodnotu větší než 1, pak paměť navíc. Horní mez však bude zvýšit pouze 1.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Add`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Přidat INT_PTR (BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Přidat INT_PTR (DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Přidat INT_PTR (void\***  `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Přidat INT_PTR (LPCTSTR** `newElement` **); throw (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Přidat INT_PTR (Celé_číslo** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Přidat INT_PTR (WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `Add example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $442A 21`  
  
 `[1] = a CAge at $4468 40`  
  
##  <a name="append"></a>  CObArray::Append  
 Volání této funkce člena pro přidání do konce daného pole obsah z jiného pole.  
  
```  
INT_PTR Append(const CObArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Zdroj elementů připojí k poli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvního připojení prvku.  
  
### <a name="remarks"></a>Poznámky  
 Pole musí být stejného typu.  
  
 V případě potřeby **připojení** může přidělit paměť navíc, aby dokázala pojmout elementy k poli.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Append`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Připojit INT_PTR (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Připojit INT_PTR (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Připojit INT_PTR (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Připojit INT_PTR (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Připojit INT_PTR (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Připojit INT_PTR (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]  
  
##  <a name="copy"></a>  CObArray::Copy  
 Volání této funkce člena přepsat prvky dané pole s prvky jiného pole stejného typu.  
  
```  
void Copy(const CObArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Zdroj elementy zkopírovány do pole.  
  
### <a name="remarks"></a>Poznámky  
 **Kopírování** není uvolnit paměť, nicméně v případě potřeby **kopie** může přidělit paměť navíc, aby dokázala pojmout elementů zkopírovaných do pole.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::Copy`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void kopírování (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void kopírování (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void kopírování (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void kopírování (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void kopírování (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void kopírování (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]  
  
##  <a name="cobarray"></a>  CObArray::CObArray  
 Vytvoří prázdnou `CObject` ukazatel pole.  
  
```  
CObArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Pole zvětšování jeden element najednou.  
  
 V následující tabulce jsou uvedeny další konstruktory, které jsou podobné `CObArray::CObArray`.  
  
|Třída|Konstruktor|  
|-----------|-----------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray ();**|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]  
  
##  <a name="elementat"></a>  CObArray::ElementAt  
 Vrátí dočasné odkaz na element ukazatele v rámci pole.  
  
```  
CObject*& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `GetUpperBound`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CObject` ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Slouží k implementaci přiřazení levé straně operátor pro pole. Všimněte si, že se jedná o pokročilé funkce, který se má použít pouze k implementaci operátory speciální pole.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::ElementAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE & ElementAt (INT_PTR** `nIndex` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & ElementAt (INT_PTR** `nIndex` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & ElementAt (INT_PTR** `nIndex` **);**|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CObArray::GetSize](#getsize).  
  
##  <a name="freeextra"></a>  CObArray::FreeExtra  
 Uvolní všechny paměť navíc, který byl přidělen při se zvětšil pole.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nemá žádný vliv na velikost nebo horní mez pole.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::FreeExtra`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void (FreeExtra);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void (FreeExtra);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void (FreeExtra);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void (FreeExtra);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void (FreeExtra);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void (FreeExtra);**|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CObArray::GetData](#getdata).  
  
##  <a name="getat"></a>  CObArray::GetAt  
 Vrátí pole element v zadaném indexu.  
  
```  
CObject* GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `GetUpperBound`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `CObject` Ukazatel element aktuálně v tohoto indexu.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Předávání zápornou hodnotu nebo hodnotu větší než hodnoty vrácené `GetUpperBound` způsobí selhání kontrolního výrazu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**GetAt BAJTŮ (INT_PTR** `nIndex` **) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]  
  
##  <a name="getcount"></a>  CObArray::GetCount  
 Vrátí počet prvků pole.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v poli.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení počet prvků v poli. Protože indexy jsou od nuly, velikost je větší než největší index 1.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetCount`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount (const;)**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount (const;)**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount (const;)**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount (const;)**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount (const;)**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount (const;)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]  
  
##  <a name="getdata"></a>  CObArray::GetData  
 Pomocí této funkce člen můžete získat přímý přístup k prvků v poli.  
  
```  
const CObject** GetData() const;  
  
CObject** GetData();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pole `CObject` ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou k dispozici žádné elementy `GetData` vrátí hodnotu null.  
  
 Při přímý přístup k elementům pole vám může pomoci pracovat rychleji, buďte opatrní při volání metody `GetData`; případné chyby přímo provedete ovlivnit prvků pole.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetData`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const BAJTŮ\* () GetData const; BYTE\* GetData ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const DWORD\* GetData const (); DWORD\* GetData ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const void\* \* (GetData) const; void\* \* GetData ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const CString\* () GetData const; CString\* GetData ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const Celé_číslo\* () GetData const; UINT\* GetData ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const WORD\* () GetData const; WORD\* GetData ();**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]  
  
##  <a name="getsize"></a>  CObArray::GetSize  
 Vrátí velikost pole.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že indexy jsou od nuly, velikost je větší než největší index 1.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetSize`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; (INT_PTR getsize –)**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; (INT_PTR getsize –)**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; (INT_PTR getsize –)**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; (INT_PTR getsize –)**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; (INT_PTR getsize –)**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; (INT_PTR getsize –)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>  CObArray::GetUpperBound  
 Vrátí aktuální horní mez toto pole.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index (založený na nule) horní mez.  
  
### <a name="remarks"></a>Poznámky  
 Protože indexy pole jsou od nuly, tato funkce vrátí hodnotu 1 menší než `GetSize`.  
  
 Podmínka **(GetUpperBound)** = -1 označuje, že pole neobsahuje žádné elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::GetUpperBound`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; (INT_PTR GetUpperBound)**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]  
  
##  <a name="insertat"></a>  CObArray::InsertAt  
 Vloží zadaný index elementu (nebo všechny elementy v jiném poli).  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    CObject* newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CObArray* pNewArray);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené `GetUpperBound`.  
  
 `newElement`  
 `CObject` Ukazatel umístit do tohoto pole. A `newElement` hodnoty **NULL** je povolen.  
  
 `nCount`  
 Počet, který tento element musí být vložen (výchozí hodnota je 1).  
  
 `nStartIndex`  
 Celé číslo index, který může být větší než hodnoty vrácené `GetUpperBound`.  
  
 `pNewArray`  
 Další pole, které obsahuje prvky, který se má přidat do tohoto pole.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti `InsertAt` Vloží jednu elementu (nebo více kopií elementu) na zadaný index v poli. V procesu posune (podle zvyšování index) existující element v indexu a posune až všechny elementy nad ním.  
  
 Druhá verze vloží všechny elementy z jiné `CObArray` kolekce, začínající `nStartIndex` pozici.  
  
 `SetAt` Funkce, naproti tomu nahrazuje jeden element zadané pole a není posunutí žádné elementy.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::InsertAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, BAJTŮ** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CByteArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CDWordArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void\***  `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CPtrArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CUIntArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CWordArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `InsertAt example: A CObArray with 3 elements`  
  
 `[0] = a CAge at $45C8 21`  
  
 `[1] = a CAge at $4646 30`  
  
 `[2] = a CAge at $4606 40`  
  
##  <a name="isempty"></a>  CObArray::IsEmpty  
 Určuje, zda pole prázdné.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je pole prázdné; jinak 0.  
  
##  <a name="operator_at"></a>  [CObArray::operator]  
 Tyto dolního indexu jsou vhodnou náhradu za `SetAt` a `GetAt` funkce.  
  
```  
CObject*& operator[](int_ptr nindex);  
CObject* operator[](int_ptr nindex) const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Volá se první operátor pro pole, které nejsou **const**, mohou být použity na právo (hodnota r) nebo doleva (l-value) příkazu přiřazení. Druhá s názvem volat pro **const** pole, mohou být použity pouze na pravé straně.  
  
 Ladicí verze knihovny vyhodnotí, pokud dolní index (buď na levé nebo pravé straně příkazu přiřazení) je mimo rozsah.  
  
 V následující tabulce jsou uvedeny dalšími operátory, které jsou podobné **[CObArray::operator]**.  
  
|Třída|Operátor|  
|-----------|--------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**[] BAJTŮ & – operátor (int_ptr** `nindex`  **\);**<br /><br /> **BYTE [] – operátor (int_ptr** `nindex`  **\) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**[] Typu DWORD & – operátor (int_ptr** `nindex`  **\);**<br /><br /> **[] – Operátor typu DWORD (int_ptr** `nindex`  **\) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& [] – operátor (int_ptr** `nindex`  **\);**<br /><br /> **void\* [] – operátor (int_ptr** `nindex`  **\) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & – operátor [] (int_ptr** `nindex`  **\);**<br /><br /> **[] – Operátor CString (int_ptr** `nindex`  **\) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & – operátor [] (int_ptr** `nindex`  **\);**<br /><br /> **[] – Operátor UINT (int_ptr** `nindex`  **\) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & – operátor [] (int_ptr** `nindex`  **\);**<br /><br /> **WORD [] – operátor (int_ptr** `nindex`  **\) const;**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]  
  
##  <a name="removeall"></a>  CObArray::RemoveAll  
 Odebere všechny odkazy pro toto pole, ale neodstraní ve skutečnosti `CObject` objekty.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud toto pole je již prázdný, funkce stále funguje.  
  
 `RemoveAll` Funkce uvolní všechny paměti používané pro úložiště ukazatele.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::RemoveAll`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void (RemoveAll);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void (RemoveAll);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void (RemoveAll);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void (RemoveAll);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void (RemoveAll);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void (RemoveAll);**|  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]  
  
##  <a name="removeat"></a>  CObArray::RemoveAt  
 Odebere jeden či více elementů počínaje zadaným indexem v matici.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `GetUpperBound`.  
  
 `nCount`  
 Počet elementů k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 V procesu Posune dolů všechny elementy výše odebrané elementy. Se snižuje horní svázané pole, ale není volné paměti.  
  
 Pokud se pokusíte odebrat další prvky, než jsou obsaženy v poli výše odebrání bodu, pak vyhodnotí ladicí verze knihovny.  
  
 `RemoveAt` Funkce odebere `CObject` ukazatel z pole, ale nedojde k odstranění samotného objektu.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::RemoveAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1);**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `RemoveAt example: A CObArray with 1 elements`  
  
 `[0] = a CAge at $4606 40`  
  
##  <a name="setat"></a>  CObArray::SetAt  
 Nastaví element pole u zadaného indexu.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0 a menší než nebo rovna hodnotě vrácené `GetUpperBound`.  
  
 `newElement`  
 Ukazatel objekt, který má být vložen do tohoto pole. A **NULL** je povolena hodnota.  
  
### <a name="remarks"></a>Poznámky  
 `SetAt` nezpůsobí pole pro růst. Použití `SetAtGrow` Pokud chcete, aby pole automaticky zvětšovat.  
  
 Je nutné zajistit, že hodnota indexu představuje platnou pozici v poli. Pokud je mimo rozsah, pak vyhodnotí ladicí verze knihovny.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetAt`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **, BAJTŮ** `newElement` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, DWORD** `newElement` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void\***  `newElement` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, UINT** `newElement` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, WORD** `newElement` **);**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `SetAt example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $47E0 30`  
  
 `[1] = a CAge at $47A0 40`  
  
##  <a name="setatgrow"></a>  CObArray::SetAtGrow  
 Nastaví element pole u zadaného indexu.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Celé číslo index, který je větší než nebo rovna 0.  
  
 `newElement`  
 Ukazatel objektu, který má být přidán do tohoto pole. A **NULL** je povolena hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Pole zvětšování automaticky v případě potřeby (horní mez se upraví pro umístění nového elementu).  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetAtGrow`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, BAJTŮ** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void\***  `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Příklad  
  V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny příklady kolekce.  
  
 [!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]  
  
 Výsledky z tohoto programu jsou následující:  
  
 `SetAtGrow example: A CObArray with 4 elements`  
  
 `[0] = a CAge at $47C0 21`  
  
 `[1] = a CAge at $4800 40`  
  
 `[2] = NULL`  
  
 `[3] = a CAge at $4840 65`  
  
##  <a name="setsize"></a>  CObArray::SetSize  
 Určuje velikost prázdný nebo stávajícímu poli; v případě potřeby přidělí paměť.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewSize`  
 Novou velikost pole (počet elementů). Musí být větší než nebo rovna 0.  
  
 `nGrowBy`  
 Minimální počet element sloty přidělit, pokud je nutné zvýšit velikost.  
  
### <a name="remarks"></a>Poznámky  
 Pokud novou velikost je menší než původní velikost, se zkrátí pole a vydání všechny nepoužívané paměti. Efektivitu, volání `SetSize` k nastavení velikosti pole před jeho použitím. Tím se zabrání potřeba znovu přidělte a zkopírujte pole pokaždé, když je položka přidána.  
  
 `nGrowBy` Parametr ovlivňuje přidělení interní paměť, když se pole zvětšuje. Jeho použití nikdy ovlivňuje velikost pole, podle `GetSize` a `GetUpperBound`.  
  
 Pokud se zvětšil velikost pole, přiděleny všechny nově **CObject \***  ukazatele jsou nastaveny na hodnotu NULL.  
  
 Následující tabulka uvádí další členské funkce, které jsou podobné `CObArray::SetSize`.  
  
|Třída|Členská funkce|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CObArray::GetData](#getdata).  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CStringArray – třída](../../mfc/reference/cstringarray-class.md)   
 [CPtrArray – třída](../../mfc/reference/cptrarray-class.md)   
 [CByteArray – třída](../../mfc/reference/cbytearray-class.md)   
 [CWordArray – třída](../../mfc/reference/cwordarray-class.md)   
 [CDWordArray – třída](../../mfc/reference/cdwordarray-class.md)
