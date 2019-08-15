---
title: CComBSTR – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497558"
---
# <a name="ccombstr-class"></a>CComBSTR – třída

Tato třída je obálkou pro [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Syntaxe

```
class CComBSTR
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComBSTR:: CComBSTR](#ccombstr)|Konstruktor|
|[CComBSTR:: ~ CComBSTR](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComBSTR:: Append](#append)|Připojí řetězec k `m_str`.|
|[CComBSTR:: AppendBSTR](#appendbstr)|Připojí BSTR do `m_str`.|
|[CComBSTR:: AppendBytes](#appendbytes)|Připojí zadaný počet bajtů `m_str`.|
|[CComBSTR:: ArrayToBSTR](#arraytobstr)|Vytvoří BSTR z prvního znaku každého prvku v SAFEARRAY a připojí ho k `CComBSTR` objektu.|
|[CComBSTR:: AssignBSTR](#assignbstr)|Přiřadí objekt BSTR `m_str`k.|
|[CComBSTR:: Attach](#attach)|Připojí `CComBSTR` objekt BSTR k objektu.|
|[CComBSTR:: BSTRToArray](#bstrtoarray)|Vytvoří jednorozměrné jednorozměrné pole SAFEARRAY, kde každý prvek pole je znak z `CComBSTR` objektu.|
|[CComBSTR::ByteLength](#bytelength)|Vrátí délku `m_str` v bajtech.|
|[CComBSTR:: Copy](#copy)|Vrátí kopii `m_str`.|
|[CComBSTR:: CopyTo](#copyto)|Vrátí kopii `m_str` přes parametr **[out]** .|
|[CComBSTR::D etach](#detach)|Odpojí `CComBSTR` objekt odobjektu.`m_str`|
|[CComBSTR:: Empty](#empty)|`m_str`Zdarma.|
|[CComBSTR:: Length](#length)|Vrátí délku `m_str`.|
|[CComBSTR:: LoadString](#loadstring)|Načte prostředek řetězce.|
|[CComBSTR::ReadFromStream](#readfromstream)|Načte objekt BSTR z datového proudu.|
|[CComBSTR:: ToLower](#tolower)|Převede řetězec na malá písmena.|
|[CComBSTR:: ToUpper](#toupper)|Převede řetězec na velká písmena.|
|[CComBSTR:: WriteToStream](#writetostream)|Uloží `m_str` se do datového proudu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CComBSTR:: operator BSTR](#operator_bstr)|Přetypování `CComBSTR` objektu na BSTR.|
|[CComBSTR:: operator!](#operator_not)|Vrátí hodnotu true nebo false v závislosti na tom `m_str`, zda je hodnota null.|
|[CComBSTR:: operator! =](#operator_neq)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR:: operator &](#operator_amp)|Vrátí adresu `m_str`.|
|[CComBSTR:: operator + =](#operator_add_eq)|Připojí objekt k objektu. `CComBSTR`|
|[CComBSTR:: operator <](#operator_lt)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR:: operator =](#operator_eq)|Přiřadí hodnotu k `m_str`.|
|[CComBSTR:: operator = = – operátor](#operator_eq_eq)|Porovná `CComBSTR` s řetězcem.|
|[CComBSTR:: operator >](#operator_gt)|Porovná `CComBSTR` s řetězcem.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Obsahuje `CComBSTR` objekt BSTR přidružený k objektu.|

## <a name="remarks"></a>Poznámky

`CComBSTR` Třída je obálkou pro BSTR, což jsou řetězce předpony s délkou. Délka je uložena jako celé číslo v umístění paměti před daty v řetězci.

Hodnota [BSTR](/previous-versions/windows/desktop/automat/bstr) má za poslední zjištěný znak zakončenou hodnotou null, ale může také obsahovat znaky null vložené do řetězce. Délka řetězce je určena počtem znaků, nikoli prvním znakem null.

> [!NOTE]
>  `CComBSTR` Třída poskytuje mnoho členů (konstruktory, operátory přiřazení a operátory porovnání), které jako argumenty přebírají řetězce ANSI nebo Unicode. Verze ANSI těchto funkcí jsou méně efektivní než jejich protějšky Unicode, protože dočasné řetězce Unicode jsou často vytvářeny interně. V případě efektivity používejte verze Unicode, pokud je to možné.

> [!NOTE]
>  Z důvodu vylepšeného chování vyhledávání implementovaného v aplikaci Visual Studio .NET by měl `bstr = L"String2" + bstr;`být kód jako, který mohl být zkompilován v předchozích verzích, implementován jako `bstr = CStringW(L"String2") + bstr`.

Seznam upozornění při použití nástroje `CComBSTR`najdete v tématu [programování pomocí CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="append"></a>CComBSTR:: Append

Připojí buď *lpsz* nebo člen BSTR typu *bstrSrc* do [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
pro `CComBSTR` Objekt, který se má připojit.

*ch*<br/>
pro Znak, který se má připojit.

*lpsz*<br/>
pro Řetězec znaků zakončený nulou pro připojení. Řetězec Unicode můžete předat prostřednictvím přetížení LPCOLESTR nebo pomocí řetězce ANSI prostřednictvím verze LPCSTR.

*nLen*<br/>
pro Počet znaků, které se mají připojit od *lpsz*

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

### <a name="remarks"></a>Poznámky

Před připojením bude řetězec ANSI převeden do kódování Unicode.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>CComBSTR:: AppendBSTR

Připojí zadaný parametr BSTR k [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Parametr BSTR, který se má připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

### <a name="remarks"></a>Poznámky

Nepředávejte do této metody běžný řetězec s velkým znakem. Kompilátor nemůže zachytit chybu a dojde k chybám při spuštění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>CComBSTR:: AppendBytes

Připojí zadaný počet bajtů k [m_str](#m_str) bez převodu.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
pro Ukazatel na pole bajtů, které se má připojit.

*p*<br/>
pro Počet bajtů, které se mají připojit.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>CComBSTR:: ArrayToBSTR

Uvolní všechny existující řetězce uložené v `CComBSTR` objektu a následně vytvoří BSTR z prvního znaku každého prvku v SAFEARRAY a připojí ho `CComBSTR` k objektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
pro Pole SAFEARRAY obsahující prvky použité k vytvoření řetězce.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

##  <a name="assignbstr"></a>CComBSTR:: AssignBSTR

Přiřadí objekt BSTR k [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
pro Objekt BSTR, který má být přiřazen `CComBSTR` k aktuálnímu objektu.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

##  <a name="attach"></a>CComBSTR:: Attach

Připojí BSTR k `CComBSTR` objektu nastavením člena [m_str](#m_str) na *Src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*src*<br/>
pro BSTR pro připojení k objektu.

### <a name="remarks"></a>Poznámky

Nepředávejte do této metody běžný řetězec s velkým znakem. Kompilátor nemůže zachytit chybu a dojde k chybám při spuštění.

> [!NOTE]
>  Tato metoda bude vyhodnotit, pokud `m_str` je hodnota jiná než null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR:: BSTRToArray

Vytvoří jednorozměrné jednorozměrné pole SAFEARRAY, kde každý prvek pole je znak z `CComBSTR` objektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
mimo Ukazatel na SAFEARRAY použitý pro uchování výsledků funkce.

### <a name="return-value"></a>Návratová hodnota

S_OK při úspěchu nebo jakákoli standardní chybová hodnota HRESULT

##  <a name="bytelength"></a>CComBSTR:: ByteLength –

Vrátí počet bajtů v `m_str`, s výjimkou ukončujícího znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člena v bajtech.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu 0 `m_str` , pokud je null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>CComBSTR:: CComBSTR

Konstruktor Výchozí konstruktor nastaví člena [m_str](#m_str) na hodnotu null.

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

*nSize*<br/>
pro Počet znaků, které mají být zkopírovány z formátu *SZ* nebo počáteční velikost znaků pro `CComBSTR`.

*sz*<br/>
pro Řetězec, který má být zkopírován. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*pSrc*<br/>
pro Řetězec, který má být zkopírován. Verze Unicode určuje LPCOLESTR; verze ANSI určuje LPCSTR.

*src*<br/>
pro `CComBSTR` Objekt.

*guid*<br/>
pro Odkaz na `GUID` strukturu.

### <a name="remarks"></a>Poznámky

Konstruktor kopie je nastaven `m_str` na kopii člena BSTR třídy *Src*. Konstruktor převede identifikátor GUID na řetězec pomocí `StringFromGUID2` a uloží výsledek. `REFGUID`

Ostatní konstruktory nastaveny `m_str` na kopii zadaného řetězce. Pokud předáte hodnotu pro *nSize*, zkopírují se pouze *nSize* znaky a za ním následuje ukončující znak null.

`CComBSTR`podporuje sémantiku přesunutí. Můžete použít konstruktor Move (konstruktor, který převezme odkaz rvalue (`&&`) pro vytvoření nového objektu, který používá stejná základní data jako původní objekt, který předáte jako argument, bez režie kopírování objektu.

Destruktor uvolní řetězec, na `m_str`který odkazuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní řetězec, na `m_str`který odkazuje.

##  <a name="copy"></a>CComBSTR:: Copy

Přidělí a vrátí kopii `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Kopie člena [m_str](#m_str) Pokud `m_str` je null, vrátí hodnotu null.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>CComBSTR:: CopyTo

Přidělí a vrátí kopii [m_str](#m_str) prostřednictvím parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
mimo Adresa řetězce BSTR, ve kterém se má vrátit řetězec přidělený touto metodou

*pvarDest*<br/>
mimo Adresa varianty, ve které se má vrátit řetězec přidělený touto metodou

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT, která indikuje úspěch nebo neúspěch kopie.

### <a name="remarks"></a>Poznámky

Po volání této metody bude hodnota VARIANT, na kterou odkazuje *pvarDest* , typu VT_BSTR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>CComBSTR::D etach

Odpojí [m_str](#m_str) od `CComBSTR` objektu a nastaví `m_str` na hodnotu null.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

`CComBSTR` Objekt BSTR přidružený k objektu

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR:: Empty

Uvolňuje člena [m_str](#m_str) .

```
void Empty() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>CComBSTR:: Length

Vrátí počet znaků v `m_str`s výjimkou ukončujícího znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Délka [m_str](#m_str) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>CComBSTR:: LoadString

Načte prostředek řetězce určený parametrem *NID* a uloží jej do tohoto objektu.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Viz [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je řetězec úspěšně načten; v opačném případě vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

První funkce načte prostředek z modulu identifikovaného pomocí parametru *hInst* . Druhá funkce načte prostředek z modulu prostředků přidruženého k objektu odvozenému od [CComModule](../../atl/reference/ccommodule-class.md), který se používá v tomto projektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>CComBSTR:: m_str

Obsahuje `CComBSTR` objekt BSTR přidružený k objektu.

```
BSTR m_str;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: operator BSTR

Přetypování `CComBSTR` objektu na BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Poznámky

Umožňuje předat `CComBSTR` objekty do funkcí, které mají **[in] parametry BSTR** .

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComBSTR:: m_str](#m_str).

##  <a name="operator_not"></a>CComBSTR:: operator!

Kontroluje, zda je řetězec BSTR NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud má člen [m_str](#m_str) hodnotu null. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tento operátor kontroluje pouze hodnotu NULL, nikoli prázdný řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR:: operator! =

Vrátí logický opak operátoru [= =](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
pro `CComBSTR` Objekt.

*pszSrc*<br/>
pro Řetězec zakončený nulou.

*nNull*<br/>
pro Musí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka, která je porovnána `CComBSTR` , nerovná objektu; v opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnány textu v kontextu výchozího národního prostředí uživatele. Koncový operátor porovnání pouze porovná obsažený řetězec s hodnotou NULL.

##  <a name="operator_amp"></a>CComBSTR:: operator&amp;

Vrátí adresu BSTR uloženou v členu [m_str](#m_str) .

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Poznámky

`CComBstr operator &`je spojen speciální kontrolní výraz, který umožňuje identifikovat nevracení paměti. Program bude při `m_str` inicializaci člena vyhodnotit. Tento kontrolní výraz byl vytvořen k identifikaci situací, kde programátor používá `& operator` pro přiřazení nové `m_str` hodnoty členu, aniž by bylo nutné nejprve uvolnit první `m_str`přidělení. Pokud `m_str` je hodnota null, program předpokládá, že m_str nebyl dosud přidělen. V takovém případě program neprovede vyhodnocení.

Tento kontrolní výraz není ve výchozím nastavení povolen. Definujte ATL_CCOMBSTR_ADDRESS_OF_ASSERT pro povolení tohoto kontrolního výrazu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR:: operator + =

Připojí řetězec k `CComBSTR` objektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
pro `CComBSTR` Objekt, který se má připojit.

*pszSrc*<br/>
pro Řetězec zakončený nulou pro připojení.

### <a name="remarks"></a>Poznámky

`CComBSTR`s jsou porovnány textu v kontextu výchozího národního prostředí uživatele. Porovnání LPCOLESTR se provádí pomocí `memcmp` nezpracovaných dat v jednotlivých řetězcích. Porovnání LPCSTR je provedeno stejným způsobem, jakmile je vytvořena dočasná kopie sady Unicode *pszSrc* . Koncový operátor porovnání pouze porovná obsažený řetězec s hodnotou NULL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: operator&lt;

Porovná `CComBSTR` s řetězcem.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud položka, která je porovnána `CComBSTR` , je menší než objekt; v opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Porovnání je provedeno pomocí výchozího národního prostředí uživatele.

##  <a name="operator_eq"></a>CComBSTR:: operator =

Nastaví člena [m_str](#m_str) na kopii *pSrc* nebo na kopii člena BSTR typu *Src*. Operátor přiřazení přesunu se `src` přesune bez jeho zkopírování.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Poznámky

Parametr *pSrc* Určuje buď LPCOLESTR pro verze Unicode, nebo LPCSTR pro verze ANSI.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CComBSTR:: Copy](#copy).

##  <a name="operator_eq_eq"></a>CComBSTR:: operator = = – operátor

Porovná `CComBSTR` s řetězcem. `CComBSTR`s jsou porovnány textu v kontextu výchozího národního prostředí uživatele.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
pro `CComBSTR` Objekt.

*pszSrc*<br/>
pro Řetězec zakončený nulou.

*nNull*<br/>
pro Musí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka, která je porovnána, rovna `CComBSTR` objektu. v opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Koncový operátor porovnání pouze porovná obsažený řetězec s hodnotou NULL.

##  <a name="operator_gt"></a>CComBSTR:: operator&gt;

Porovná `CComBSTR` s řetězcem.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka, která je porovnána, větší než `CComBSTR` objekt; v opačném případě vrátí hodnotu false.

### <a name="remarks"></a>Poznámky

Porovnání je provedeno pomocí výchozího národního prostředí uživatele.

##  <a name="readfromstream"></a>CComBSTR:: ReadFromStream

Nastaví člena [m_str](#m_str) na parametr BSTR obsažený v zadaném datovém proudu.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
pro Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) na datovém proudu, který obsahuje data.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

`ReadToStream`vyžaduje, aby obsah datového proudu na aktuální pozici byl kompatibilní s formátem dat zapsaným voláním [WriteToStream](#writetostream).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>CComBSTR:: ToLower

Převede řetězec obsahující malá písmena.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další `CharLowerBuff` informace o tom, jak se provádí převod, najdete v tématu.

##  <a name="toupper"></a>CComBSTR:: ToUpper

Převede řetězec s omezením na velká písmena.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další `CharUpperBuff` informace o tom, jak se provádí převod, najdete v tématu.

##  <a name="writetostream"></a>CComBSTR:: WriteToStream

Uloží člena [m_str](#m_str) do datového proudu.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
pro Ukazatel na rozhraní [IStream](/windows/win32/api/objidl/nn-objidl-istream) v datovém proudu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pomocí funkce [ReadFromStream](#readfromstream) můžete znovu vytvořit BSTR z obsahu streamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Makra pro převod řetězců ATL a MFC](string-conversion-macros.md)
