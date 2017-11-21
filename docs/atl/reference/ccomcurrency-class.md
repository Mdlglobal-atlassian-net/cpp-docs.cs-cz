---
title: "Třída CComCurrency | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
dev_langs: C++
helpviewer_keywords: CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e9466c2081b7d9622776702d367ccae64a36b4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcurrency-class"></a>CComCurrency – třída
`CComCurrency`obsahuje operátory a metody pro vytváření a správu objekt měny.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComCurrency
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|V konstruktoru pro `CComCurrency` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Vrátí adresu `m_currency` – datový člen.|  
|[CComCurrency::GetFraction](#getfraction)|Volání této metody vrátit zlomkové komponenta `CComCurrency` objektu.|  
|[CComCurrency::GetInteger](#getinteger)|Volání této metody vrátit komponenta celé číslo `CComCurrency` objektu.|  
|[CComCurrency::Round](#round)|Volat tuto metodu, která má být zaokrouhleno `CComCurrency` objektu na nejbližší celé číslo.|  
|[CComCurrency::SetFraction](#setfraction)|Volat tuto metodu a nastavit komponentu zlomkové `CComCurrency` objektu.|  
|[CComCurrency::SetInteger](#setinteger)|Volat tuto metodu a nastavit komponentu celé číslo `CComCurrency` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|Tento operátor slouží k provádění odčítání na `CComCurrency` objektu.|  
|[CComCurrency::operator! =](#operator_neq)|Porovná dva `CComCurrency` objekty nerovnost.|  
|[CComCurrency::operator *](#operator_star)|Tento operátor slouží k plnění násobení `CComCurrency` objektu.|  
|[CComCurrency::operator * =](#operator_star_eq)|Tento operátor slouží k plnění násobení `CComCurrency` objektu a přiřaďte ho výsledek.|  
|[CComCurrency::operator /](#operator_div)|Tento operátor slouží k provádění dělení na `CComCurrency` objektu.|  
|[CComCurrency::operator / =](#operator_div_eq)|Tento operátor slouží k provádění dělení na `CComCurrency` objektu a přiřaďte ho výsledek.|  
|[CComCurrency::operator +](#operator_add)|Tento operátor slouží k přidání plnění `CComCurrency` objektu.|  
|[CComCurrency::operator +=](#operator_add_eq)|Tento operátor slouží k přidání plnění `CComCurrency` objektu a výsledek přiřadit aktuální objekt.|  
|[CComCurrency::operator <](#operator_lt)|Tento operátor porovná dvě `CComCurrency` objekty, které chcete určit menší.|  
|[CComCurrency::operator < =](#operator_lt_eq)|Tento operátor porovná dvě `CComCurrency` objekty k určení rovnosti nebo menší.|  
|[CComCurrency::operator =](#operator_eq)|Tento operátor přiřadí `CComCurrency` objektu na novou hodnotu.|  
|[CComCurrency::operator-=](#operator_-_eq)|Tento operátor slouží k provádění odčítání na `CComCurrency` objektu a přiřaďte ho výsledek.|  
|[CComCurrency::operator ==](#operator_eq_eq)|Tento operátor porovná dvě `CComCurrency` objekty rovnosti.|  
|[CComCurrency::operator >](#operator_gt)|Tento operátor porovná dvě `CComCurrency` objekty, které chcete určit delší.|  
|[CComCurrency::operator > =](#operator_gt_eq)|Tento operátor porovná dvě `CComCurrency` objekty k určení rovnosti nebo delší.|  
|[CComCurrency::operator měny](#operator_currency)|Přetypování `CURRENCY` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|`CURRENCY` Proměnné vytvořené ve vaší instanci třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CComCurrency`představuje obálku pro **MĚNA** datového typu. **MĚNA** je implementovaný jako celočíselnou hodnotu 8bajtový doplňkem škálovat podle 10 000. To dává číslo s pevnou desetinnou čárkou s 15 číslic nalevo od desetinné čárky a 4 číslic vpravo. **MĚNA** datový typ je velmi užitečná pro peněžních výpočtů, nebo pro všechny výpočty s pevnou desetinnou čárkou kde přesnost je důležité.  
  
 **CComCurrency** obálku implementuje aritmetické, přiřazení a porovnání operací pro tento typ s pevnou desetinnou čárkou. Nebyly vybrány podporovaných aplikací k řízení zaokrouhlení chybách, ke kterým může dojít během výpočty s pevnou desetinnou čárkou.  
  
 `CComCurrency` Objekt poskytuje přístup k čísla na obou stranách od desetinné čárky ve formě dvě součásti: komponentu celé číslo, které ukládá hodnotu směrem doleva od desetinné čárky a zlomkové komponenta, která ukládá hodnotu napravo desetinné čárky. Komponentu zlomkové je uložen interně jako celočíselná hodnota mezi-9999 ( **CY_MIN_FRACTION**) a +9999 ( **CY_MAX_FRACTION**). Metoda [CComCurrency::GetFraction](#getfraction) vrací hodnotu škálovat faktorem 10000 ( **CY_SCALE**).  
  
 Při zadávání celé číslo a zlomkové součásti **CComCurrency** objektu, mějte na paměti, že zlomkové součást je číslo v rozsahu 0 až 9 999. To je důležité při plánování práce s měny například dolaru USA, která vyjadřuje částky pomocí pouze dvě významné číslice za desetinnou čárkou. I když nejsou zobrazeny dvě poslední číslice, musí vzít v úvahu.  
  
|Hodnota|Možné CComCurrency přiřazení|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency(10,5000) *nebo* CComCurrency(10.50)|  
|$10.05|CComCurrency(10,500) *nebo* CComCurrency(10.05)|  
  
 Hodnoty **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, a **CY_SCALE** jsou definovány v atlcur.h.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcur.h  
  
##  <a name="ccomcurrency"></a>CComCurrency::CComCurrency  
 Konstruktor  
  
```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);  
CComCurrency(USHORT usSrc);  
CComCurrency(CHAR cSrc);  
CComCurrency(DOUBLE dSrc);  
CComCurrency(FLOAT fSrc);  
CComCurrency(LONG lSrc);  
CComCurrency(SHORT sSrc);  
CComCurrency(BYTE bSrc);  
CComCurrency(LONGLONG nInteger, SHORT nFraction);  
explicit CComCurrency(LPDISPATCH pDispSrc);  
explicit CComCurrency(const VARIANT& varSrc);  
explicit CComCurrency(LPCWSTR szSrc);  
explicit CComCurrency(LPCSTR szSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `curSrc`  
 Existující objekt `CComCurrency`.  
  
 `cySrc`  
 Proměnné typu **MĚNA**.  
  
 `bSrc`, `dSrc`, `fSrc`, `lSrc`, *sSrc*, *ulSrc usSrc*  
 Počáteční hodnota zadané členské proměnné `m_currency`.  
  
 `cSrc`  
 Znak, který obsahuje počáteční hodnotu na členské proměnné `m_currency`.  
  
 `nInteger`, *nFraction*  
 Celé číslo a zlomkové součástí počáteční peněžní hodnota. Najdete v článku [CComCurrency](../../atl/reference/ccomcurrency-class.md) přehled pro další informace.  
  
 `pDispSrc`  
 `IDispatch` Ukazatel.  
  
 *varSrc*  
 Proměnné typu **VARIANT**. Národní prostředí aktuální vlákno se používá k provádění převod.  
  
 `szSrc`  
 Unicode nebo ANSI řetězec obsahující počáteční hodnota. Národní prostředí aktuální vlákno se používá k provádění převod.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví počáteční hodnotu konstruktoru [CComCurrency::m_currency](#m_currency)a přijímá široké škály datových typů, včetně celá čísla, řetězce, čísla s plovoucí desetinnou čárkou, **MĚNA** proměnné a další `CComCurrency` objekty. Pokud není zadána žádná hodnota, `m_currency` je nastaven na hodnotu 0.  
  
 V případě chyby, jako je přetečení, konstruktory postrádá specifikace prázdný výjimky ( **throw()**) volání `AtlThrow` s HRESULT popisující chybu.  
  
 Při použití hodnoty s plovoucí desetinnou čárkou nebo dvojité o přiřazení hodnoty, Všimněte si, že **CComCurrency(10.50)** je ekvivalentní **CComCurrency(10,5000)** a není **CComCurrency(10,50)**.  
  
##  <a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr  
 Vrátí adresu `m_currency` – datový člen.  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu `m_currency` – datový člen  
  
##  <a name="getfraction"></a>CComCurrency::GetFraction  
 Volání této metody vrátit zlomkové součást `CComCurrency` objektu.  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí komponentu zlomkové `m_currency` – datový člen.  
  
### <a name="remarks"></a>Poznámky  
 Komponentu zlomkové je 4 číslice celočíselná hodnota mezi-9999 ( **CY_MIN_FRACTION**) a +9999 ( **CY_MAX_FRACTION**). `GetFraction`vrací hodnotu této škálovat podle 10000 ( **CY_SCALE**). Hodnoty **CY_MIN_FRACTION**, **CY_MAX_FRACTION**, a **CY_SCALE** jsou definovány v atlcur.h.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>CComCurrency::GetInteger  
 Volat tuto metodu za účelem získání součástí celé číslo `CComCurrency` objektu.  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí komponentu celé číslo `m_currency` – datový člen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>CComCurrency::m_currency  
 **MĚNA** – datový člen.  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen obsahuje měna přístup a manipulovat metody této třídy.  
  
##  <a name="operator_-"></a>CComCurrency::operator-  
 Tento operátor slouží k provádění odčítání na `CComCurrency` objektu.  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CComCurrency` objekt reprezentující výsledek odčítání. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>CComCurrency::operator! =  
 Tento operátor porovná nerovnost dva objekty.  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud položka porovnávané není rovno `CComCurrency` objektu; jinak, **false**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>CComCurrency::operator *  
 Tento operátor slouží k plnění násobení `CComCurrency` objektu.  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Násobitel.  
  
 `cur`  
 `CComCurrency` Objekt použitý jako násobitel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CComCurrency` objekt reprezentující výsledek násobení. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>CComCurrency::operator * =  
 Tento operátor slouží k plnění násobení `CComCurrency` objektu a přiřaďte ho výsledek.  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Násobitel.  
  
 `cur`  
 `CComCurrency` Objekt použitý jako násobitel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>CComCurrency::operator /  
 Tento operátor slouží k provádění dělení na `CComCurrency` objektu.  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Dělitel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CComCurrency` objekt reprezentující výsledek rozdělení. Pokud dělitel je 0, dojde k chybě vyhodnocení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>CComCurrency::operator / =  
 Tento operátor slouží k provádění dělení na `CComCurrency` objektu a přiřaďte ho výsledek.  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>Parametry  
 `nOperand`  
 Dělitel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComCurrency` objektu. Pokud dělitel je 0, dojde k chybě vyhodnocení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>CComCurrency::operator +  
 Tento operátor slouží k přidání plnění `CComCurrency` objektu.  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Objekt, který chcete přidat do původní objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CComCurrency` objekt reprezentující výsledek přidání. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>CComCurrency::operator +=  
 Tento operátor slouží k přidání plnění `CComCurrency` objektu a výsledek přiřadit aktuální objekt.  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>CComCurrency::operator&lt;  
 Tento operátor porovná dvě `CComCurrency` objekty, které chcete určit menší.  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší než druhý, **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>CComCurrency::operator&lt;=  
 Tento operátor porovná dvě `CComCurrency` objekty k určení rovnosti nebo menší.  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší než nebo rovna druhý, **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>CComCurrency::operator =  
 Tento operátor přiřadí `CComCurrency` objektu na novou hodnotu.  
  
```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `curSrc`  
 A **CComCurrency** objektu.  
  
 `cySrc`  
 Proměnné typu **MĚNA**.  
  
 *sSrc*, `fSrc`, `lSrc`, *bSrc*, *usSrc*, `dSrc`, *cSrc*, *ulSrc*,`dSrc`  
 Číselná hodnota pro přiřazení `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>CComCurrency::operator-=  
 Tento operátor slouží k provádění odčítání na `CComCurrency` objektu a přiřaďte ho výsledek.  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComCurrency` objektu. V případě chyby, jako je přetečení, tento operátor volání `AtlThrow` s HRESULT popisující chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>CComCurrency::operator ==  
 Tento operátor porovná dvě `CComCurrency` objekty rovnosti.  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 `CComCurrency` Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud jsou objekty stejné (tedy `m_currency` datových členů, obě celé číslo a zlomkové v obou objekty mají stejnou hodnotu), **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>CComCurrency::operator&gt;  
 Tento operátor porovná dvě `CComCurrency` objekty, které chcete určit delší.  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt větší než druhý, **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>CComCurrency::operator&gt;=  
 Tento operátor porovná dvě `CComCurrency` objekty k určení rovnosti nebo delší.  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parametry  
 `cur`  
 A `CComCurrency` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud se první objekt větší než nebo rovna hodnotě druhého, **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>CComCurrency::operator měny  
 Tyto operátory se používají k přetypování `CComCurrency` do objektu **MĚNA** datového typu.  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na **MĚNA** objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>CComCurrency::Round  
 Volejte tuto metodu, která má být zaokrouhleno měna zadaný počet desetinných míst.  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>Parametry  
 *nDecimals*  
 Počet číslic, na kterou `m_currency` zaokrouhlen, v rozsahu 0 až 4.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>CComCurrency::SetFraction  
 Volat tuto metodu a nastavit komponentu zlomkové `CComCurrency` objektu.  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>Parametry  
 *nFraction*  
 Hodnota pro přiřazení ke zlomkové komponenta `m_currency` – datový člen. Znaménko komponentu zlomkové musíte stejný jako součást celé číslo a hodnota musí být v rozsahu-9999 ( **CY_MIN_FRACTION**) k +9999 ( **CY_MAX_FRACTION**).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>CComCurrency::SetInteger  
 Volat tuto metodu a nastavit komponentu celé číslo `CComCurrency` objektu.  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>Parametry  
 `nInteger`  
 Hodnota, která má být přiřazovány komponenta celé číslo `m_currency` – datový člen. Znaménko komponentu celé číslo se musí shodovat znaménko existující zlomkové součást.  
  
 `nInteger`musí být v rozsahu **CY_MIN_INTEGER** k **CY_MAX_INTEGER** (včetně). Tyto hodnoty jsou definovány v atlcur.h.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [COleCurrency – třída](../../mfc/reference/colecurrency-class.md)   
 [MĚNA.](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Přehled třídy](../../atl/atl-class-overview.md)
