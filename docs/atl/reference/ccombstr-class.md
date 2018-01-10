---
title: "CComBSTR – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
dev_langs: C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 604e3b9841ab628343a48e72612d2e50e85913f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccombstr-class"></a>CComBSTR – třída
Tato třída je obálka pro `BSTR`s.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComBSTR
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComBSTR::CComBSTR](#ccombstr)|Konstruktor|  
|[CComBSTR:: ~ CComBSTR](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComBSTR::Append](#append)|Přidá řetězec do `m_str`.|  
|[CComBSTR::AppendBSTR](#appendbstr)|Připojí `BSTR` k `m_str`.|  
|[CComBSTR::AppendBytes](#appendbytes)|Připojí zadaný počet bajtů, které mají `m_str`.|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Vytvoří `BSTR` z první znak každého prvku safearray a připojí jej k `CComBSTR` objektu.|  
|[CComBSTR::AssignBSTR](#assignbstr)|Přiřadí `BSTR` k `m_str`.|  
|[CComBSTR::Attach](#attach)|Připojí `BSTR` k `CComBSTR` objektu.|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|Vytvoří nule jednorozměrné safearray, kde každý element pole je znak z `CComBSTR` objektu.|  
|[CComBSTR::ByteLength](#bytelength)|Vrátí délku `m_str` v bajtech.|  
|[CComBSTR::Copy](#copy)|Vrátí kopii `m_str`.|  
|[CComBSTR::CopyTo](#copyto)|Vrátí kopii `m_str` prostřednictvím **[out]** parametr|  
|[CComBSTR::Detach](#detach)|Umožňuje odpojit `m_str` z `CComBSTR` objektu.|  
|[CComBSTR::Empty](#empty)|Uvolní `m_str`.|  
|[CComBSTR::Length](#length)|Vrátí délku `m_str`.|  
|[CComBSTR::LoadString](#loadstring)|Načte prostředek typu řetězec.|  
|[CComBSTR::ReadFromStream](#readfromstream)|Načítání `BSTR` objekt z datového proudu.|  
|[CComBSTR::ToLower](#tolower)|Převede řetězec na malá písmena.|  
|[CComBSTR::ToUpper](#toupper)|Převede řetězec na velká písmena.|  
|[CComBSTR::WriteToStream](#writetostream)|Uloží `m_str` do datového proudu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|Přetypování `CComBSTR` do objektu `BSTR`.|  
|[CComBSTR::operator!](#operator_not)|Vrátí `true` nebo `false`, v závislosti na tom, zda `m_str`je `NULL`.|  
|[CComBSTR::operator! =](#operator_neq)|Porovná `CComBSTR` řetězcem.|  
|[CComBSTR::operator &](#operator_amp)|Vrátí adresu `m_str`.|  
|[CComBSTR::operator +=](#operator_add_eq)|Připojí `CComBSTR` k objektu.|  
|[CComBSTR::operator <](#operator_lt)|Porovná `CComBSTR` řetězcem.|  
|[CComBSTR::operator =](#operator_eq)|Přiřadí hodnota `m_str`.|  
|[CComBSTR::operator ==](#operator_eq_eq)|Porovná `CComBSTR` řetězcem.|  
|[CComBSTR::operator >](#operator_gt)|Porovná `CComBSTR` řetězcem.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComBSTR::m_str](#m_str)|Obsahuje `BSTR` přidružené `CComBSTR` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComBSTR` Třída je obálka pro `BSTR`s, které jsou s předponou délku řetězce. Délka se ukládají jako celé číslo v umístění paměti předcházející data v řetězci.  
  
 A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) je ukončené hodnotou null po poslední počítá znak, ale můžou taky obsahovat znaky null vložených v rámci řetězce. Délka řetězce je určen podle počtu znaků, ne první znak hodnoty null.  
  
> [!NOTE]
>  `CComBSTR` Třída poskytuje počet členů (konstruktory, přiřazení operátory a operátory porovnání), které přijímají řetězce ANSI nebo Unicode jako argumenty. ANSI verzích tyto funkce jsou míň efektivní než jejich protějšky znakové sady Unicode, protože dočasné řetězců v kódu Unicode jsou často vytvořili interně. Pro efektivitu použijte Unicode verze, kde je to možné.  
  
> [!NOTE]
>  Z důvodu chování vylepšené vyhledávání implementované v sadě Visual Studio .NET, code, jako `bstr = L"String2" + bstr;`, které může být zkompilovány v předchozích verzích by měla být implementována místo jako `bstr = CStringW(L"String2") + bstr`.  
  
 Seznam upozornění při použití `CComBSTR`, najdete v části [programování pomocí třídy CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="append"></a>CComBSTR::Append  
 Připojí buď `lpsz` nebo `BSTR` členem `bstrSrc` k [m_str](#m_str).  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [v] A `CComBSTR` objekt, který chcete připojit.  
  
 *ch*  
 [v] Znak pro připojení.  
  
 `lpsz`  
 [v] Řetězec znaků ukončený nula připojit. Můžete předat řetězec znaků Unicode prostřednictvím **LPCOLESTR** přetížení nebo řetězec ANSI prostřednictvím `LPCSTR` verze.  
  
 `nLen`  
 [v] Počet znaků od `lpsz` připojit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec ANSI převede na kódování Unicode než se připojí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="appendbstr"></a>CComBSTR::AppendBSTR  
 Připojí zadaný `BSTR` k [m_str](#m_str).  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] A `BSTR` připojit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
### <a name="remarks"></a>Poznámky  
 K této metodě řetězci obyčejnou široká charakterová nepředávejte. Kompilátor nelze zachytit chybu a spustit, když dojde k chybám.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="appendbytes"></a>CComBSTR::AppendBytes  
 Připojí zadaný počet bajtů, které mají [m_str](#m_str) bez převodu.  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 [v] Ukazatel na pole bajtů pro připojení.  
  
 `p`  
 [v] Počet bajtů, které mají připojit.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 Uvolní všechny existující řetězec uchovávat v `CComBSTR` objekt a potom vytvoří `BSTR` z první znak každého prvku safearray a připojí jej k `CComBSTR` objektu.  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [v] Safearray obsahující prvky používané k vytvoření řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
##  <a name="assignbstr"></a>CComBSTR::AssignBSTR  
 Přiřadí `BSTR` k [m_str](#m_str).  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [v] A `BSTR` přiřadit aktuální `CComBSTR` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
##  <a name="attach"></a>CComBSTR::Attach  
 Připojí `BSTR` k `CComBSTR` objekt nastavením [m_str](#m_str) člena *src*.  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 [v] `BSTR` Připojit k objektu.  
  
### <a name="remarks"></a>Poznámky  
 K této metodě řetězci obyčejnou široká charakterová nepředávejte. Kompilátor nelze zachytit chybu a spustit, když dojde k chybám.  
  
> [!NOTE]
>  Tato metoda bude assert, pokud `m_str` jinou hodnotu než **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 Vytvoří nule jednorozměrné safearray, kde každý element pole je znak z `CComBSTR` objektu.  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 [out] Ukazatel na safearray používané pro udržení výsledky této funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch, nebo jakékoli standardní `HRESULT` hodnota chyby.  
  
##  <a name="bytelength"></a>CComBSTR::ByteLength  
 Vrátí počet bajtů v `m_str`, s výjimkou ukončující znak hodnoty null.  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka [m_str](#m_str) člen v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí hodnotu 0, pokud `m_str` je **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="ccombstr"></a>CComBSTR::CComBSTR  
 Konstruktor Výchozí konstruktor sady [m_str](#m_str) člena **NULL**.  
  
```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);  
CComBSTR(REFGUID  guid);  
CComBSTR(int nSize);  
CComBSTR(int nSize, LPCOLESTR sz);  
CComBSTR(int nSize, LPCSTR sz);  
CComBSTR(LPCOLESTR pSrc);  
CComBSTR(LPCSTR pSrc);  
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parametry  
 `nSize`  
 [v] Počet znaků pro kopírování z `sz` nebo počáteční velikost ve znacích `CComBSTR`.  
  
 `sz`  
 [v] Řetězec pro kopírování. Určuje kódování Unicode verze **LPCOLESTR**; Určuje verzi ANSI `LPCSTR`.  
  
 `pSrc`  
 [v] Řetězec pro kopírování. Určuje kódování Unicode verze **LPCOLESTR**; Určuje verzi ANSI `LPCSTR`.  
  
 *src*  
 [v] A `CComBSTR` objektu.  
  
 `guid`  
 [v] Odkaz na **GUID** struktura.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví konstruktor kopie `m_str` na kopii `BSTR` členem *src*. **REFGUID** konstruktor převede **GUID** na řetězec pomocí **StringFromGUID2** a výsledek je uložen.  
  
 Druhá sada konstruktory `m_str` na kopii zadaného řetězce. Pokud předáte hodnotu `nSize`, jenom `nSize` znaků se zkopírují, za nímž následuje ukončující znak hodnoty null.  
  
 `CComBSTR`podporuje přesun sémantiku. Můžete použít konstruktor move (konstruktor, který přebírá deklarátor odkazu ( `&&`) Chcete-li vytvořit nový objekt, který používá stejné základní data jako starý objekt můžete předat jako argument, bez nutnosti kopírování objektu.  
  
 Řetězec, na kterou odkazuje uvolní destruktoru `m_str`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 Destruktor.  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>Poznámky  
 Řetězec, na kterou odkazuje uvolní destruktoru `m_str`.  
  
##  <a name="copy"></a>CComBSTR::Copy  
 Přiděluje a vrátí kopii `m_str`.  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopii [m_str](#m_str) člen. Pokud `m_str` je **NULL**, vrátí **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="copyto"></a>CComBSTR::CopyTo  
 Přiděluje a vrátí kopii [m_str](#m_str) prostřednictvím parametru.  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pbstr*  
 [out] Adresa `BSTR` k vrácení řetězec přidělené touto metodou.  
  
 `pvarDest`  
 [out] Adresa **VARIANT** k vrácení řetězec přidělené touto metodou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu, která udává úspěch nebo neúspěch kopie.  
  
### <a name="remarks"></a>Poznámky  
 Po volání této metody **VARIANT** na kterou odkazuje `pvarDest` bude typu `VT_BSTR`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="detach"></a>CComBSTR::Detach  
 Umožňuje odpojit [m_str](#m_str) z `CComBSTR` objekt a nastaví `m_str` k **NULL**.  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `BSTR` Přidružené `CComBSTR` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="empty"></a>CComBSTR::Empty  
 Uvolní [m_str](#m_str) člen.  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="length"></a>CComBSTR::Length  
 Vrátí počet znaků v `m_str`, s výjimkou ukončující znak hodnoty null.  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka [m_str](#m_str) člen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="loadstring"></a>CComBSTR::LoadString  
 Načte řetězec prostředku zadaného parametrem `nID` a ukládá je v tomto objektu.  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>Parametry  
 V tématu [LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud úspěšně načíst; jinak hodnota je řetězec, vrátí **false**.  
  
### <a name="remarks"></a>Poznámky  
 První funkce načte prostředek z modulu identifikovaný můžete prostřednictvím `hInst` parametr. Funkce second načte prostředek z modulu prostředků přidružené [CComModule](../../atl/reference/ccommodule-class.md)-odvozené objekt použitý v tomto projektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="m_str"></a>CComBSTR::m_str  
 Obsahuje `BSTR` přidružené `CComBSTR` objektu.  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="operator_bstr"></a>CComBSTR::operator BSTR  
 Přetypování `CComBSTR` do objektu `BSTR`.  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Umožňuje předat `CComBSTR` objekty, které se funkce, které mají **[v] BSTR** parametry.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CComBSTR::m_str](#m_str).  
  
##  <a name="operator_not"></a>CComBSTR::operator!  
 Kontroluje, zda `BSTR` řetězec hodnotu NULL.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud [m_str](#m_str) člen **NULL**, jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor pouze zkontroluje hodnotu NULL, není pro prázdný řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="operator_neq"></a>CComBSTR::operator! =  
 Vrátí logickou opak [operátor ==](#operator_eq_eq).  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [v] A `CComBSTR` objektu.  
  
 `pszSrc`  
 [v] Řetězce ukončené nula.  
  
 `nNull`  
 [v] Musí být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud položka porovnávané není rovno `CComBSTR` objektu; jinak vrátí **false**.  
  
### <a name="remarks"></a>Poznámky  
 `CComBSTR`s jsou porovnávány textový v kontextu uživatele výchozí národní prostředí. Poslední relační operátor právě porovná obsahují řetězec proti **NULL**.  
  
##  <a name="operator_amp"></a>CComBSTR::operator&amp;  
 Vrátí adresu `BSTR` uložené v [m_str](#m_str) člen.  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 `CComBstr operator &`má speciální assertion přidruženo k identifikaci nevracení paměti. Program bude assert, kdy `m_str` je inicializován. Tento kontrolní výraz součásti byla vytvořena k identifikaci situací, kdy programátorem používá `& operator` přiřadit novou hodnotu na `m_str` člen bez uvolnění první přidělení `m_str`. Pokud `m_str` rovná hodnotu NULL, program se předpokládá, že m_str nebyla přidělena ještě. V takovém případě nebude assert programu.  
  
 Tento kontrolní výraz součásti není povoleno ve výchozím nastavení. Definování `ATL_CCOMBSTR_ADDRESS_OF_ASSERT` povolit tento kontrolní výraz součásti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="operator_add_eq"></a>CComBSTR::operator +=  
 Přidá řetězec do `CComBSTR` objektu.  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [v] A `CComBSTR` objekt, který chcete připojit.  
  
 `pszSrc`  
 [v] Byl ukončen nula řetězec pro připojení.  
  
### <a name="remarks"></a>Poznámky  
 `CComBSTR`s jsou porovnávány textový v kontextu uživatele výchozí národní prostředí. **LPCOLESTR** porovnání se provádí pomocí `memcmp` na nezpracovaných dat v každém řetězci. `LPCSTR` Se porovnání provádí stejným způsobem, jakmile dočasného Unicode zkopírovat z `pszSrc` byla vytvořena. Poslední relační operátor právě porovná obsahují řetězec proti **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="operator_lt"></a>CComBSTR::operator&lt;  
 Porovná `CComBSTR` řetězcem.  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je položka porovnávané méně než `CComBSTR` objektu; jinak vrátí **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání se provádí pomocí výchozí národní prostředí uživatele.  
  
##  <a name="operator_eq"></a>CComBSTR::operator =  
 Nastaví [m_str](#m_str) člena do kopie `pSrc` nebo kopii `BSTR` členem *src*. Operátor přiřazení přesunutí přesune `src` bez kopírování.   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>Poznámky  
 `pSrc` Parametr určuje buď **LPCOLESTR** pro kódování Unicode verze nebo `LPCSTR` pro verze ANSI.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CComBSTR::Copy](#copy).  
  
##  <a name="operator_eq_eq"></a>CComBSTR::operator ==  
 Porovná `CComBSTR` řetězcem. `CComBSTR`s jsou porovnávány textový v kontextu uživatele výchozí národní prostředí.  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [v] A `CComBSTR` objektu.  
  
 `pszSrc`  
 [v] Řetězce ukončené nula.  
  
 `nNull`  
 [v] Musí být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud položka porovnávané rovná `CComBSTR` objektu; jinak vrátí **false**.  
  
### <a name="remarks"></a>Poznámky  
 Poslední relační operátor právě porovná obsahují řetězec proti **NULL**.  
  
##  <a name="operator_gt"></a>CComBSTR::operator&gt;  
 Porovná `CComBSTR` řetězcem.  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud porovnávané položka je větší než `CComBSTR` objektu; jinak vrátí **false**.  
  
### <a name="remarks"></a>Poznámky  
 Porovnání se provádí pomocí výchozí národní prostředí uživatele.  
  
##  <a name="readfromstream"></a>CComBSTR::ReadFromStream  
 Nastaví [m_str](#m_str) člena `BSTR` obsažené v zadaného datového proudu.  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní na datový proud, který obsahuje data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 **ReadToStream** vyžaduje obsah datového proudu na aktuální pozici být kompatibilní s formátem dat naprogramovaný volání [WriteToStream](#writetostream).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="tolower"></a>CComBSTR::ToLower  
 Převede obsažené řetězce na malá písmena.  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 V tématu **CharLowerBuff** Další informace o tom, jak se provádí převod.  
  
##  <a name="toupper"></a>CComBSTR::ToUpper  
 Převede obsažené řetězce na velká písmena.  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 V tématu **CharUpperBuff** Další informace o tom, jak se provádí převod.  
  
##  <a name="writetostream"></a>CComBSTR::WriteToStream  
 Uloží [m_str](#m_str) člena do datového proudu.  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [v] Ukazatel [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034) rozhraní na datový proud.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Můžete znovu vytvořit BSTR z obsahu pomocí datového proudu [ReadFromStream](#readfromstream) funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [ATL a MFC řetězec převodních maker](string-conversion-macros.md)
