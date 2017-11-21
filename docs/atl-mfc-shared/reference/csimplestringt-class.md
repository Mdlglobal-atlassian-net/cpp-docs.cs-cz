---
title: "Třída CSimpleStringT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
dev_langs: C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27f163b76d037ca91330890c7d38c37c182b6b1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csimplestringt-class"></a>CSimpleStringT – třída
Tato třída reprezentuje `CSimpleStringT` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>Parametry  
 `BaseType`  
 Tyto typy znaků třídy string. Může být jedna z následujících akcí:  
  
- `char`(pro znakových řetězců v kódu ANSI).  
  
- `wchar_t`(pro znakových řetězců v kódu Unicode).  
  
- **Tchar –** (pro ANSI a Unicode řetězce znaků).  

## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|Ukazatel na konstantní řetězec.|  
|[CSimpleStringT::PXSTR](#pxstr)|Ukazatel na řetězec.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|Vytvoří `CSimpleStringT` objekty různými způsoby.|  
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destruktor.|  

  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|Připojí `CSimpleStringT` objekt, který má na existující `CSimpleStringT` objektu.|  
|[CSimpleStringT::AppendChar](#appendchar)|Přidá znak na stávající `CSimpleStringT` objektu.|  
|[CSimpleStringT::CopyChars](#copychars)|Zkopíruje znaky jiným řetězcem.|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Zkopíruje znaky na jiný řetězec, ve které se překrývají vyrovnávací paměti.|  
|[CSimpleStringT::Empty](#empty)|Vynutí řetězec tak, aby mít nulovou délku.|  
|[CSimpleStringT::FreeExtra](#freeextra)|Uvolní všechny další paměti dříve přidělené objekt řetězce.|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|Načte přidělené délka `CSimpleStringT` objektu.|  
|[CSimpleStringT::GetAt](#getat)|Vrátí znak na dané pozici.|  
|[CSimpleStringT::GetBuffer](#getbuffer)|Vrací ukazatel na znaky v `CSimpleStringT`.|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Vrací ukazatel na znaky v `CSimpleStringT`, zkracování na určenou délku.|  
|[CSimpleStringT::GetLength](#getlength)|Vrátí počet znaků `CSimpleStringT` objektu.|  
|[CSimpleStringT::GetManager](#getmanager)|Načte správce paměti `CSimpleStringT` objektu.|  
|[CSimpleStringT::GetString](#getstring)|Načte řetězec znaků|  
|[CSimpleStringT::IsEmpty](#isempty)|Testy zda `CSimpleStringT` objekt neobsahuje žádné znaky.|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|Zakáže počítání odkazů a chrání je řetězec ve vyrovnávací paměti.|  
|[CSimpleStringT::Preallocate](#preallocate)|Přiděluje určitou velikostí paměti pro vyrovnávací paměť znak.|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Uvolní řízení vyrovnávací paměti vrácené `GetBuffer`.|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Uvolní řízení vyrovnávací paměti vrácené `GetBuffer`.|  
|[CSimpleStringT::SetAt](#setat)|Nastaví znak na dané pozici.|  
|[CSimpleStringT::SetManager](#setmanager)|Nastaví správce paměti `CSimpleStringT` objektu.|  
|[CSimpleStringT::SetString](#setstring)|Nastaví řetězec `CSimpleStringT` objektu.|  
|[CSimpleStringT::StringLength](#stringlength)|Vrátí počet znaků v zadaném řetězci.|  
|[CSimpleStringT::Truncate](#truncate)|Zkrátí řetězec, který má zadané délky.|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Umožňuje počítání odkazů a uvolní řetězec ve vyrovnávací paměti.|  

### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Přímý přístup k znaky, které jsou uložené v `CSimpleStringT` objekt jako řetězec stylu jazyka C.|  
|[CSimpleStringT::operator\[\]](#operator_at)|Vrátí znak na dané pozici – operátor nahrazování pro `GetAt`.|  
|[CSimpleStringT::operator +=](#operator_add_eq)|Zřetězí nového řetězce na konec existující řetězec.|  
|[CSimpleStringT::operator =](#operator_eq)|Přiřadí novou hodnotu k `CSimpleStringT` objektu.|  
  
### <a name="remarks"></a>Poznámky  
 `CSimpleStringT`je základní třída pro různé třídy řetězec podporované Visual C++. Správa paměti objektu řetězce a zacházení s vyrovnávací pamětí základní poskytuje minimální podporu. Pokročilejší řetězcových objektů, najdete v části [CStringT třída](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpstr.h  


## <a name="append"></a>CSimpleStringT::Append
Připojí `CSimpleStringT` objekt, který má na existující `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parametry  
 `strSrc`  
 `CSimpleStringT` Objekt, který má být připojen.  
  
 `pszSrc`  
 Ukazatel na řetězec obsahující znaky, které mají být připojena.  
  
 `nLength`  
 Počet znaků pro připojení.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze připojit existující `CSimpleStringT` objektu na jiný `CSimpleStringT` objektu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::Append`.  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="appendchar"></a>CSimpleStringT::AppendChar
Přidá znak na stávající `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>Parametry  
 *ch*  
 Znak, který má být připojen  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce pro připojení je zadaný znak na konec existující `CSimpleStringT` objektu.  
  
##  <a name="copychars"></a>CSimpleStringT::CopyChars  
 Zkopíruje znak nebo znaků, který má `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>Parametry  
 `pchDest`  
 Ukazatel na řetězec znaků.  
  
 `pchSrc`  
 Ukazatel na řetězec obsahující znaky, které se mají zkopírovat.  
  
 `nChars`  
 Počet `pchSrc` znaky, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze kopírovat znaky z `pchSrc` k `pchDest` řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::CopyChars`.  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped
Zkopíruje znak nebo znaků, který má `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>Parametry  
 `pchDest`  
 Ukazatel na řetězec znaků.  
  
 `pchSrc`  
 Ukazatel na řetězec obsahující znaky, které se mají zkopírovat.  
  
 `nChars`  
 Počet `pchSrc` znaky, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze kopírovat znaky z `pchSrc` k `pchDest` řetězec. Na rozdíl od `CopyChars`, `CopyCharsOverlapped` poskytuje bezpečné metodu pro kopírování z vyrovnávací paměti znaků, které může být překryté.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CSimpleStringT::CopyChars](#copychars), nebo zdrojový kód pro `CSimpleStringT::SetString` (umístěný ve atlsimpstr.h).  
  
##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT  
 Vytvoří `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>Parametry  
 `strSrc`  
 Existující `CSimpleStringT` objekt, který se má zkopírovat do této `CSimpleStringT` objektu.  
  
 `pchSrc`  
 Ukazatel na pole znaků délky `nLength`, není null byla ukončena.  
  
 `pszSrc`  
 Řetězce ukončené hodnotou null zkopírovat do této `CSimpleStringT` objektu.  
  
 `nLength`  
 Počet znaků v `pch`.  
  
 `pStringMgr`  
 Ukazatel na správce paměti `CSimpleStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CSimpleStringT`, najdete v části [Správa paměti a CStringT](../memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit nový `CSimpleStringT` objektu. Protože konstruktorů zkopírovat do nového úložiště přidělené vstupních dat, může způsobit paměti výjimky.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::CSimpleStringT` pomocí knihovny ATL `typedef` `CSimpleString`. `CSimpleString`je běžně používané specializace šablony třídy `CSimpleStringT`.  
  
```cpp  
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"   
```

  
##  <a name="empty"></a>CSimpleStringT::Empty
To umožňuje `CSimpleStringT` objektu prázdný řetězec a uvolní paměť podle potřeby.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [řetězce: Vyčištění výjimka CString](../cstring-exception-cleanup.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::Empty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="freeextra"></a>CSimpleStringT::FreeExtra
Uvolní všechny paměť navíc dříve přidělena řetězec, ale už nepotřebují.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>Poznámky  
 To by snížení režie paměti spotřebovávají objekt řetězce. Metoda přidělí vyrovnávací paměť na přesný délku vrácený [GetLength](#getlength).  
  
### <a name="example"></a>Příklad  
```cpp  
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its 
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra 
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```
  
### <a name="remarks"></a>Poznámky  
 Výstup z tohoto příkladu je následující:  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength  
Načte přidělené délka `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků, které jsou přidělené pro tento objekt.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu můžete určit počet znaků, které jsou přidělené pro tento `CSimpleStringT` objektu. V tématu [FreeExtra](#freeextra) příklad volání této funkce.  
  
##  <a name="getat"></a>CSimpleStringT::GetAt  
Vrátí jeden znak od `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Index počítaný od nuly znaku v `CSimpleStringT` objektu. `iChar` Parametr musí být větší než nebo rovna 0 a menší než hodnoty vrácené [GetLength](#getlength). V opačném `GetAt` vygeneruje výjimku.  
  
### <a name="return-value"></a>Návratová hodnota  
 `XCHAR` Obsahující znak na zadané pozici v řetězci.  
  
### <a name="remarks"></a>Poznámky  
 Volání této metody vrátit jeden znak určeného `iChar`. Přetížené dolní index (`[]`) operátor je vhodné aliasu pro `GetAt`. Null ukončení je adresovatelný bez generování výjimku pomocí `GetAt`. Však není zjištěné službou `GetLength`, a hodnota vrácená je 0.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `CSimpleStringT::GetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="getbuffer"></a>CSimpleStringT::GetBuffer  
Vrací ukazatel na interní znak vyrovnávací paměti pro `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>Parametry  
 `nMinBufferLength`  
 Minimální počet znaků, které mohou být uloženy znak vyrovnávací paměti. Tato hodnota nezahrnuje místo pro zakončením hodnotu null.  
  
 Pokud `nMinBufferLength` je větší než délka aktuální vyrovnávací paměti, `GetBuffer` zničí aktuální vyrovnávací paměti, nahradí vyrovnávací paměti požadovaná velikost a počet odkazů objekt se obnoví na nulu. Pokud jste dříve volána [LockBuffer](#lockbuffer) na této vyrovnávací paměti, přijdete o uzamčení vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 `PXSTR` Ukazatel do vyrovnávací paměti (ukončené hodnotou null) znak objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této metody vrátit vyrovnávací paměti obsah `CSimpleStringT` objektu. Vrácený `PXSTR` není konstantní a proto umožňuje Přímá úprava `CSimpleStringT` obsah.  
  
 Pokud používáte ukazatel vrácený `GetBuffer` Změna obsahu řetězce, musí volat [ReleaseBuffer](#releasebuffer) před všemi ostatními použitím `CSimpleStringT` metody člen.  
  
 Adresu vrácený `GetBuffer` nemusí být platná po zavolání `ReleaseBuffer` protože další `CSimpleStringT` operace může způsobit `CSimpleStringT` vyrovnávací paměť k znovu přidělit. Vyrovnávací paměť není znovu přidělit, pokud nezměníte délka `CSimpleStringT`.  
  
 Vyrovnávací paměť je automaticky při vydání `CSimpleStringT` objekt zničena.  
  
 Pokud jste udržování přehledu o délka řetězce sami, nesmí se připojí ukončující znak hodnoty null. Však musíte zadat délku řetězce konečné při vydání vyrovnávací paměti s `ReleaseBuffer`. Pokud přidáte ukončující znak hodnoty null, by měla předávat -1 (výchozí) po zadanou dobu. `ReleaseBuffer`potom Určuje velikost vyrovnávací paměti.  
  
 Pokud je nedostatek paměti pro uspokojení `GetBuffer` požádat, tato metoda vyvolá CMemoryException *.  
  
### <a name="example"></a>Příklad  
```cpp  
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();   
```
  
##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength  
Vrací ukazatel na interní znak vyrovnávací paměti pro `CSimpleStringT` objekt, zkrátit nebo ročně zvýší jeho délka v případě potřeby tak, aby přesně odpovídaly délka zadaná v `nLength`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>Parametry  
 `nLength`  
 Přesný velikost `CSimpleStringT` znak vyrovnávací paměti ve znacích.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `PXSTR` ukazatel do vyrovnávací paměti (ukončené hodnotou null) znak objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem načtení zadané délky vnitřní vyrovnávací paměť `CSimpleStringT` objektu. Vrácený `PXSTR` ukazatel není `const` a proto umožňuje Přímá úprava `CSimpleStringT` obsah.  
  
 Pokud používáte ukazatel vrácený [GetBufferSetLength](#getbuffersetlength) Změna obsahu řetězce, volání `ReleaseBuffer` aktualizuje interní stav `CsimpleStringT` před všemi ostatními použitím `CSimpleStringT` metody.  
  
 Adresu vrácený `GetBufferSetLength` nemusí být platná po zavolání `ReleaseBuffer` protože další `CSimpleStringT` operace může způsobit `CSimpleStringT` vyrovnávací paměť k znovu přidělit. Vyrovnávací paměť není přiřazeny, pokud nezměníte délka `CSimpleStringT`.  
  
 Vyrovnávací paměť je automaticky při vydání `CSimpleStringT` objekt zničena.  
  
 Pokud jste udržování přehledu o délka řetězce sami, není nepřidáte ukončující znak hodnoty null. Je nutné zadat délku v posledním řetězci uvedené, při vydání vyrovnávací paměti pomocí `ReleaseBuffer`. Pokud připojení ukončující znak hodnoty null při volání `ReleaseBuffer`, předat hodnotu -1 (výchozí) pro délku na `ReleaseBuffer`, a `ReleaseBuffer` provede `strlen` na určit jeho délka vyrovnávací paměti.  
  
 Další informace o počítání odkazů najdete v následujících článcích:  
  
- [Správa životnosti objektu prostřednictvím počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms687260) ve Windows SDK. 
  
- [Implementace počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms693431) ve Windows SDK.
  
- [Pravidla pro správu počty odkazů](http://msdn.microsoft.com/library/windows/desktop/ms692481) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::GetBufferSetLength`.  
  
```cpp  
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer() 
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```
  
##  <a name="getlength"></a>CSimpleStringT::GetLength  
Vrátí počet znaků `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků v řetězci.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu, která vrátí počet znaků v objektu. Počet nezahrnuje zakončením hodnotu null.  
  
 Pro vícebajtových znakových sad (MBCS), `GetLength` počty jednotlivých 8bitové znak; to znamená, realizace a záznam bajtů v jedné vícebajtových znaků, se počítají jako dva bajty. V tématu [FreeExtra](#freeextra) příklad volání této funkce.  
  
##  <a name="getmanager"></a>CSimpleStringT::GetManager  
Načte správce paměti `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na správce paměti pro `CSimpleStringT` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem načtení paměť manager používané `CSimpleStringT` objektu. Další informace o Správci paměti a řetězcových objektů najdete v tématu [Správa paměti a CStringT](../memory-management-with-cstringt.md).  
  
##  <a name="getstring"></a>CSimpleStringT::GetString
Načte řetězcem znaků.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec znaků ukončený hodnotou null.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem načtení související s řetězcem znaků `CSimpleStringT` objektu.  
  
> [!NOTE]
>  Vrácený `PCXSTR` ukazatel `const` a nepovoluje přímou úpravu `CSimpleStringT` obsah.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::GetString`.  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="isempty"></a>CSimpleStringT::IsEmpty  
Testy `CSimpleStringT` objekt pro prázdný podmínku.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud `CSimpleStringT` objekt má délku 0; v opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu lze zjistit, pokud objekt obsahuje prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::IsEmpty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer  
Zakáže počítání odkazů a chrání je řetězec ve vyrovnávací paměti.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CSimpleStringT` objekt nebo řetězce ukončené hodnotou null.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem uzamčení vyrovnávací paměti z `CSimpleStringT` objektu. Při volání `LockBuffer`, vytvoření kopie řetězce, s -1 pro počet odkazů. Pokud hodnotu počtu odkazů -1, považuje za "uzamčeném" stav řetězec ve vyrovnávací paměti. Řetězec je v uzamčeném stavu, chráněn dvěma způsoby:  
  
-   Žádný jiný řetězec, můžete získat odkaz na data v uzamčeném řetězci, i když tento řetězec je přiřazena uzamčeném řetězec.  
  
-   Uzamčení řetězec nikdy odkazuje jiný řetězec, i v případě, že jiný řetězec, se zkopíruje na uzamčeném řetězec.  
  
 Blokováním řetězec ve vyrovnávací paměti, je zajistit, že výhradní podržení řetězec ve vyrovnávací paměti zůstanou beze změn.  
  
 Po dokončení s `LockBuffer`, volání [UnlockBuffer](#unlockbuffer) resetovat počet odkazů na 1.  
  
> [!NOTE]
>  Když zavoláte [getbuffer –](#getbuffer) na uzamčeném vyrovnávací paměť a nastavte `GetBuffer` parametr `nMinBufferLength` na hodnotu větší než délka vyrovnávací paměti pro aktuální, dojde ke ztrátě uzamčení vyrovnávací paměti. Volání do `GetBuffer` zničí aktuální vyrovnávací paměti, nahradí vyrovnávací paměti požadovaná velikost a počet odkazů se obnoví na nulu.  
  
 Další informace o počítání odkazů najdete v následujících článcích:  
  
- [Správa životnosti objektu prostřednictvím počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms687260) ve Windows SDK  
  
- [Implementace počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms693431) ve Windows SDK  
  
- [Pravidla pro správu počty odkazů](http://msdn.microsoft.com/library/windows/desktop/ms692481) ve Windows SDK  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::LockBuffer`.  
  
```cpp  
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```
  
##  <a name="operator_at"></a>CSimpleStringT::operator\[\]  
Volání této funkce pro přístup k jednoho znaku pole znaků.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Index nule znaku v řetězci.  
  
### <a name="remarks"></a>Poznámky  
 Přetížené dolní index (`[]`) operátor vrátí jeden znak určeného index založený na nule v `iChar`. Tento operátor. je vhodné nenahrazuje [GetAt](#getat) – členská funkce.  
  
> [!NOTE]
>  Můžete použít dolní index (`[]`) operátor má být získána hodnota znaku v `CSimpleStringT`, ale nemůžete ji použít ke změně hodnoty znaku v `CSimpleStringT`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití **[CSimpleStringT::operator]**.  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="operator_at"></a>CSimpleStringT::operator\[\]
Volání této funkce pro přístup k jednoho znaku pole znaků.  
  
### <a name="syntax"></a>Syntaxe  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>Parametry  
 `iChar`  
 Index nule znaku v řetězci.  
  
### <a name="remarks"></a>Poznámky  
 Přetížené dolní index (`[]`) operátor vrátí jeden znak určeného index založený na nule v `iChar`. Tento operátor. je vhodné nenahrazuje [GetAt](#getat) – členská funkce.  
  
> [!NOTE]
>  Můžete použít dolní index (`[]`) operátor má být získána hodnota znaku v `CSimpleStringT`, ale nemůžete ji použít ke změně hodnoty znaku v `CSimpleStringT`.  
  
  
##  <a name="operator_add_eq"></a>CSimpleStringT::operator +=  
Spojí nové řetězec nebo znak na konec existující řetězec.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT& operator +=(PCXSTR pszSrc); 
CSimpleStringT& operator +=(const CSimpleStringT& strSrc); 
template<int t_nSize>  
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc); 
CSimpleStringT& operator +=(char ch); 
CSimpleStringT& operator +=(unsigned char ch); 
CSimpleStringT& operator +=(wchar_t ch);
```  
#### <a name="parameters"></a>Parametry  
 `pszSrc`  
 Ukazatel na řetězce ukončené hodnotou null.  
  
 `strSrc`  
 Ukazatele na existující `CSimpleStringT` objektu.  
  
 *ch*  
 Znak, který má být připojen.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přijímá jiné `CSimpleStringT` objekt nebo znak. Všimněte si, že paměť výjimky může dojít při každém použití tento operátor řetězení vzhledem k tomu, že nové úložiště může být přidělené znaky, které jsou přidány do tohoto `CSimpleStringT` objektu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití **CSimpleStringT::operator +=**.  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="operator_eq"></a>CSimpleStringT::operator =  
Přiřadí novou hodnotu k `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>Parametry  
 `pszSrc`  
 Ukazatel na řetězce ukončené hodnotou null.  
  
 `strSrc`  
 Ukazatele na existující `CSimpleStringT` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud cílový řetězec (levé straně) je již dostatečně velký pro uložení nová data, se provádí žádné nové přidělení paměti. Všimněte si, že paměť výjimky může dojít při každém použití operátor přiřazení, protože nové úložiště je často přidělené k uchování výsledná `CSimpleStringT` objektu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití **CSimpleStringT::operator =**.  
  
```cpp  
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;      
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```
  
##  <a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR  

 Přímý přístup k znaky, které jsou uložené v `CSimpleStringT` objekt jako řetězec stylu jazyka C.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>Návratová hodnota  
 Znak ukazatel na data řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Žádné znaky jsou zkopírovány; Vrátí se pouze ukazatel. Dávejte pozor, se tento operátor. Pokud změníte `CString` objektu po získání ukazatele znak, může způsobit opakované přidělení paměti, která by způsobila neplatnost ukazatele.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití **CSimpleStringT::operator PCXSTR**.  
  
```cpp  
// If the prototype of a function is known to the compiler, 
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype, 
// you must invoke the cast operator explicitly. For example, 
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and 
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will 
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;   
``` 
  
##  <a name="pcxstr"></a>CSimpleStringT::PCXSTR
Ukazatel na konstantní řetězec.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="preallocate"></a>CSimpleStringT::Preallocate  
Přiděluje určitou velikostí pro bajtů `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>Parametry  
 `nLength`  
 Přesný velikost `CSimpleStringT` znak vyrovnávací paměti ve znacích.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze přidělit velikost vyrovnávací paměti specifické pro `CSimpleStringT` objektu.  
  
 `CSimpleStringT`generuje `STATUS_NO_MEMORY` výjimka, pokud nelze přidělit místo pro vyrovnávací paměť znak. Ve výchozím nastavení, přidělení paměti provádí funkce rozhraní API WIN32 `HeapAlloc` nebo `HeapReAlloc`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::Preallocate`.  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="pxstr"></a>CSimpleStringT::PXSTR  
Ukazatel na řetězec.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer  
Uvolní řízení vyrovnávací paměti přidělené [getbuffer –](#getbuffer).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Nové délka řetězce v znaky, není počítání zakončením hodnotu null. Pokud má řetězec hodnotu null byla ukončena,-1 výchozí hodnota se nastaví `CSimpleStringT` velikost na aktuální délku řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze přidělit jinému uživateli nebo uvolněte vyrovnávací paměť objekt řetězce. Pokud víte, že řetězec ve vyrovnávací paměti je null byla ukončena, můžete vynechat `nNewLength` argument. Pokud řetězec vašeho není null byla ukončena, použijte `nNewLength` zadat jeho délka. Adresu vrácený [getbuffer –](#getbuffer) je neplatný po zavolání `ReleaseBuffer` nebo jakékoliv `CSimpleStringT` operaci.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::ReleaseBuffer`.  
  
```cpp  
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

  // use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```
  
##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Uvolní řízení vyrovnávací paměti přidělené [getbuffer –](#getbuffer).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Délka řetězce vydán  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je funkčně podobná [ReleaseBuffer](#releasebuffer) s tím rozdílem, že musí být předán platný délku objekt řetězce.  
  
##  <a name="setat"></a>CSimpleStringT::SetAt  
Nastaví jeden znak od `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Index počítaný od nuly znaku v `CSimpleStringT` objektu. `iChar` Parametr musí být větší než nebo rovna 0 a menší než hodnoty vrácené [GetLength](#getlength).  
  
 *ch*  
 Nový znak.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu přepsat znaku na `iChar`. Tato metoda nebude zvětšit řetězec, pokud `iChar` přesahuje hranice existující řetězec.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::SetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="setmanager"></a>CSimpleStringT::SetManager  
Určuje správce paměti `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>Parametry  
 `pStringMgr`  
 Ukazatel na nový správce paměti.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze zadat novou paměť manager používané `CSimpleStringT` objektu. Další informace o Správci paměti a řetězcových objektů najdete v tématu [Správa paměti a CStringT](../memory-management-with-cstringt.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::SetManager`.  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="setstring"></a>CSimpleStringT::SetString  
Nastaví řetězec `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parametry  
 `pszSrc`  
 Ukazatel na řetězce ukončené hodnotou null.  
  
 `nLength`  
 Počet znaků v `pszSrc`.  
  
### <a name="remarks"></a>Poznámky  
 Zkopírujte řetězec do `CSimpleStringT` objektu. `SetString`přepíše starší řetězec data ve vyrovnávací paměti.  
  
 Obě verze `SetString` zkontrolujte, zda `pszSrc` je ukazatel s hodnotou null a pokud se jedná, výjimku **E_INVALIDARG** chyby.  
  
 Jeden parametr verze `SetString` očekává `pszSrc` tak, aby odkazoval na řetězec ukončené hodnotou null.  
  
 Parametr dvě verze `SetString` také očekává `pszSrc` řetězec ukončené hodnotou null. Používá `nLength` jako délka řetězce Pokud nejprve zjistí zakončením hodnotu null.  
  
 Parametr dvě verze `SetString` také zkontroluje, zda `pszSrc` odkazuje na umístění v aktuální vyrovnávací paměti v `CSimpleStringT`. V tomto případě speciální `SetString` používá funkci kopírování paměti, která nepřepisuje data řetězec jako kopíruje data řetězec zpět do jeho vyrovnávací paměti.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::SetString`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```
  
##  <a name="stringlength"></a>CSimpleStringT::StringLength  
Vrátí počet znaků v zadaném řetězci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```  
#### <a name="parameters"></a>Parametry  
 `psz`  
 Ukazatel na řetězce ukončené hodnotou null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků v `psz`; není počítání zakončením hodnotu null.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze načíst počet znaků v řetězci, na kterou odkazuje `psz`.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::StringLength`.  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="truncate"></a>CSimpleStringT::Truncate
Zkrátí řetězec, který má nové délky.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Nové délka řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem zkrácení obsah na nové délku řetězce.  
  
> [!NOTE]
>  To nemá vliv přidělené délka vyrovnávací paměti. Pokud chcete snížit nebo zvyšte aktuální vyrovnávací paměti, přečtěte si téma [FreeExtra](#freeextra) a [Preallocate](#preallocate).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `CSimpleStringT::Truncate`.  
  
```cpp  
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
``` 
  
##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer
 Odemkne vyrovnávací paměti s `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem resetování počet odkazů řetězec na hodnotu 1.  
  
 `CSimpleStringT` Automaticky volání destruktoru `UnlockBuffer` zajistit, že vyrovnávací paměť není při volání destruktoru uzamčena. Příklad této metody naleznete v části [LockBuffer](#lockbuffer).  
  
##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT
Zničí `CSimpleStringT` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu zrušení `CSimpleStringT` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)