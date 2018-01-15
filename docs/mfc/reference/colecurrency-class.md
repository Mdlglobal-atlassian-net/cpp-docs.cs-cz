---
title: "Třída COleCurrency | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
dev_langs: C++
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d20b0f61fc7773899e671bec5b252ef2af1abf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colecurrency-class"></a>COleCurrency – třída
Zapouzdří `CURRENCY` datový typ automatizace OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleCurrency  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleCurrency::COleCurrency](#colecurrency)|Vytvoří `COleCurrency` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleCurrency::Format](#format)|Generuje formátovaný řetězcovou reprezentaci `COleCurrency` objektu.|  
|[COleCurrency::GetStatus](#getstatus)|Získá stav (platnosti) to `COleCurrency` objektu.|  
|[COleCurrency::ParseCurrency](#parsecurrency)|Přečte **MĚNA** hodnotu z řetězce a nastaví hodnotu `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Nastaví hodnotu této `COleCurrency` objektu.|  
|[COleCurrency::SetStatus](#setstatus)|Nastaví stav (platnosti) pro tento `COleCurrency` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor =](#operator_eq)|Kopie `COleCurrency` hodnotu.|  
|[operátor +, -](#operator_plus_minus)|Přidá, odečte a změní znaménko `COleCurrency` hodnoty.|  
|[Operator +=-=](#operator_plus_minus_eq)|Přidá a odečítá `COleCurrency` hodnotu z tohoto `COleCurrency` objektu.|  
|[operátor * /](#operator_star)|Měřítek `COleCurrency` hodnoty celočíselnou hodnotu.|  
|[Operator * = / =](#operator_star_div_eq)|To škáluje `COleCurrency` hodnoty celočíselnou hodnotu.|  
|[operátor <<](#operator_stream)|Výstupy `COleCurrency` hodnotu `CArchive` nebo `CDumpContext`.|  
|[operátor >>](#operator_stream)|Vstupy `COleCurrency` objektu z `CArchive`.|  
|[operátor měny](#operator_currency)|Převede `COleCurrency` hodnotu do **MĚNA**.|  
|[Operator ==, <, < =, atd.](#colecurrency_relational_operators)|Porovná dva `COleCurrency` hodnoty.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Obsahuje základní **MĚNA** pro tento `COleCurrency` objektu.|  
|[COleCurrency::m_status](#m_status)|Obsahuje stav tohoto `COleCurrency` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 **COleCurrency** nemá základní třídu.  
  
 **MĚNA** je implementovaný jako 8 bajtů, škálovat podle 10 000 doplňkem celočíselnou hodnotu. To dává číslo s pevnou desetinnou čárkou s 15 číslic nalevo od desetinné čárky a 4 číslic vpravo. **MĚNA** datový typ je velmi užitečná pro peněžních výpočtů, nebo pro jakékoli řádovou kde přesnost je důležité. Je jedním z možných typů pro `VARIANT` datový typ automatizace OLE.  
  
 **COleCurrency** také implementuje některé základní aritmetické operace pro tento typ s pevnou desetinnou čárkou. Podporované operace byly vybrány pro řízení zaokrouhlovací chyby, ke kterým dochází při výpočty s pevnou desetinnou čárkou.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `COleCurrency`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
  
##  <a name="colecurrency"></a>COleCurrency::COleCurrency  
 Vytvoří **COleCurrency** objektu.  
  
```  
COleCurrency();  
COleCurrency(CURRENCY cySrc);  
  COleCurrency(const COleCurrency& curSrc);  
COleCurrency(const VARIANT& varSrc);

 
COleCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Parametry  
 `cySrc`  
 A **MĚNA** hodnota, která má být zkopírován do nové **COleCurrency** objektu.  
  
 `curSrc`  
 Existující **COleCurrency** objekt, který má být zkopírován do nové **COleCurrency** objektu.  
  
 *varSrc*  
 Existující **VARIANT** datové struktury (pravděpodobně `COleVariant` objektu) má být převeden na hodnotu měny ( `VT_CY`) a zkopírovat do nové **COleCurrency** objektu.  
  
 `nUnits`, `nFractionalUnits`  
 Označení jednotky a zlomkové části (v 1/10, 000's) hodnoty, které se mají zkopírovat do nové **COleCurrency** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořit nový **COleCurrency** objekty inicializovat se zadanou hodnotou. Následuje stručný popis každého z těchto konstruktorů. Pokud není uvedeno jinak, stav nové **COleCurrency** položka je nastavena na platný.  
  
- Konstrukce COleCurrency() **COleCurrency** objekt hodnotu 0 (nula).  
  
- COleCurrency (`cySrc`) vytvoří **COleCurrency** objektu z [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) hodnotu.  
  
- COleCurrency (`curSrc`) vytvoří **COleCurrency** objekt z existující **COleCurrency** objektu. Nový objekt má stav stejný jako zdrojový objekt.  
  
- COleCurrency (`varSrc`) vytvoří **COleCurrency** objektu. Pokusí se převést [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) struktura nebo `COleVariant` objekt, který chcete měny ( `VT_CY`) hodnotu. Pokud tento převod je úspěšné, převedená hodnota je zkopírovat do nové **COleCurrency** objektu. Pokud ne, je hodnota **COleCurrency** objektu na nula (0) a její stav na neplatnou hodnotu.  
  
- `COleCurrency(`nUnits`, `nFractionalUnits') vytvoří **COleCurrency** z komponenty číselné zadaný objekt. Pokud se absolutní hodnotu zlomkové části je větší než 10 000, příslušné úpravy přišla jednotky. Všimněte si, že jsou podepsané dlouhé hodnoty určené jednotky a zlomkové části.  
  
 Další informace najdete v tématu [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) a [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) položky v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklady ukazují důsledky nula parametr a parametr dva konstruktory:  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>COleCurrency::Format  
 Volání této funkce člen vytvořit formátovaný reprezentace hodnoty měny.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Určuje příznaky pro nastavení národního prostředí. Pouze následující příznak je relevantní pro měny:  
  
- **LOCALE_NOUSEROVERRIDE** používá výchozí nastavení národního prostředí systému, namísto vlastní uživatelská nastavení.  
  
 `lcid`  
 Určuje ID národního prostředí pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující hodnotu formátovaný měny.  
  
### <a name="remarks"></a>Poznámky  
 Formátuje hodnotu pomocí specifikace jazyce (ID národního prostředí). Hodnota vrácená není součástí symbolu měny. Pokud se stav tohoto **COleCurrency** objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec určeného řetězce prostředků **IDS_INVALID_CURRENCY**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>COleCurrency::GetStatus  
 Volání této funkce člen získat stav (platnosti) danou **COleCurrency** objektu.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí stav tohoto **COleCurrency** hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratová hodnota je definované `CurrencyStatus` výčtového typu, který je definován v rámci **COleCurrency** třídy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleCurrency::valid** -označuje, že tato **COleCurrency** je objekt platný.  
  
- **COleCurrency::invalid** -označuje, že tato **COleCurrency** objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleCurrency::null** -označuje, že tato **COleCurrency** objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
 Stav **COleCurrency** objekt je neplatný v následujících případech:  
  
-   Pokud je jeho hodnota v rozsahu **VARIANT** nebo `COleVariant` hodnotu, kterou nelze převést na hodnotu měny.  
  
-   Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, například `+=` nebo  **\* =** .  
  
-   Pokud je neplatná hodnota byl přiřazen k tomuto objektu.  
  
-   Pokud se stav tohoto objektu se explicitně nastavit na neplatné použití [SetStatus](#setstatus).  
  
 Další informace o operacích, které může nastavit stav na neplatné najdete následující členské funkce:  
  
- [COleCurrency](#colecurrency)  
  
- [operátor =](#operator_eq)  
  
- [operátor + -](#operator_plus_minus)  
  
- [+= – operátor a-=](#operator_plus_minus_eq)  
  
- [operátor * /](#operator_star)  
  
- [Operator * = a / =](#operator_star_div_eq)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="m_cur"></a>COleCurrency::m_cur  
 Základní [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) struktury pro tuto **COleCurrency** objektu.  
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Změna hodnoty v **MĚNA** struktura přístup ukazatele, vrátí tato funkce se změní hodnota této **COleCurrency** objektu. Nezmění stav tohoto **COleCurrency** objektu.  
  
 Další informace najdete v tématu [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) položku v sadě Windows SDK.  
  
##  <a name="m_status"></a>COleCurrency::m_status  
 Typ této – datový člen je Výčtový typ `CurrencyStatus`, která je definována v rámci **COleCurrency** třídy.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Poznámky  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleCurrency::valid** -označuje, že tato **COleCurrency** je objekt platný.  
  
- **COleCurrency::invalid** -označuje, že tato **COleCurrency** objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleCurrency::null** -označuje, že tato **COleCurrency** objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
 Stav **COleCurrency** objekt je neplatný v následujících případech:  
  
-   Pokud je jeho hodnota v rozsahu **VARIANT** nebo `COleVariant` hodnotu, kterou nelze převést na hodnotu měny.  
  
-   Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, například `+=` nebo  **\* =** .  
  
-   Pokud je neplatná hodnota byl přiřazen k tomuto objektu.  
  
-   Pokud se stav tohoto objektu se explicitně nastavit na neplatné použití [SetStatus](#setstatus).  
  
 Další informace o operacích, které může nastavit stav na neplatné najdete následující členské funkce:  
  
- [COleCurrency](#colecurrency)  
  
- [operátor =](#operator_eq)  
  
- [operátor +, -](#operator_plus_minus)  
  
- [Operator +=-=](#operator_plus_minus_eq)  
  
- [operátor * /](#operator_star)  
  
- [Operator * = / =](#operator_star_div_eq)  
  
    > [!CAUTION]
    >  Tento člen dat je pro pokročilé programovací situace. Měli byste použít vložené funkce člen [GetStatus](#getstatus) a [SetStatus](#setstatus). V tématu `SetStatus` pro další upozornění týkající se explicitně nastavení tohoto člena data.  
  
##  <a name="operator_eq"></a>COleCurrency::operator =  
 Tyto operátory přetížené přiřazení zkopírujte hodnotu měny zdroje do této **COleCurrency** objektu.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Poznámky  
 Následuje stručný popis jednotlivých operátor:  
  
- **Operator = (** `cySrc` **)** `CURRENCY` hodnota zkopírována do **COleCurrency** nastavena na platný objekt a jeho stav.  
  
- **Operator = (** `curSrc` **)** hodnota a stav operand, existující **COleCurrency** objektu se zkopírují do této **COleCurrency** objekt.  
  
- **operátor = (** *varSrc* **)** Pokud převod `VARIANT` hodnotu (nebo [COleVariant](../../mfc/reference/colevariant-class.md) objekt) pro měny ( `VT_CY`) je úspěšné, převedená hodnota se zkopíruje do této **COleCurrency** nastavena na platný objekt a jeho stav. Pokud není úspěšné, převod hodnotu **COleCurrency** objektu je nastavena na 0 a její stav na neplatný.  
  
 Další informace najdete v tématu [MĚNA](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) a [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) položky v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>COleCurrency::operator +, -  
 Tyto operátory umožňují sčítání a odečítání dva **COleCurrency** hodnoty ke a od sebe navzájem a chcete-li změnit znaménko **COleCurrency** hodnotu.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud některý z operandy je null, stav výsledná **COleCurrency** hodnota je null.  
  
 Pokud operace aritmetické přetečení, výsledná **COleCurrency** hodnota je neplatná.  
  
 Pokud operand je neplatný a druhá není null, stav výsledná **COleCurrency** hodnota je neplatná.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>COleCurrency::operator +=-=  
 Umožňují sčítání a odečítání **COleCurrency** hodnotu do a z tohoto **COleCurrency** objektu.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud některá z operandy null, stav tohoto **COleCurrency** je nastavena na hodnotu null.  
  
 Pokud aritmetické operace přesahuje, stav tohoto **COleCurrency** je nastavena na neplatný.  
  
 Pokud některý z operandy je neplatný a dalších nemá hodnotu null, stav tohoto **COleCurrency** je nastavena na neplatný.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>COleCurrency::operator * a /  
 Umožňuje škálovat **COleCurrency** hodnotu podle celočíselné hodnoty.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud **COleCurrency** operand má hodnotu null, stav výsledná **COleCurrency** hodnota je null.  
  
 Pokud Přetečení aritmetické operace nebo underflows, stav výsledná **COleCurrency** hodnota je neplatná.  
  
 Pokud **COleCurrency** operand je neplatná, stav výsledná **COleCurrency** hodnota je neplatná.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>COleCurrency::operator * = / =  
 Umožňuje škálovat to **COleCurrency** hodnotu podle celočíselné hodnoty.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud **COleCurrency** operand má hodnotu null, stav tohoto **COleCurrency** je nastavena na hodnotu null.  
  
 Pokud aritmetické operace přesahuje, stav tohoto **COleCurrency** je nastavena na neplatný.  
  
 Pokud **COleCurrency** operand je neplatná, stav tohoto **COleCurrency** je nastavena na neplatný.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>COleCurrency::operator &lt; &lt;,&gt;&gt;  
 Podporuje diagnostiky vypsání a ukládání do archivu.  
  
```  
friend CDumpContext& operator<<(
    CDumpContext& dc,  
    COleCurrency curSrc);
 
friend CArchive& operator<<(
    CArchive& ar,  
    COleCurrency curSrc);
 
friend CArchive& operator>>(
    CArchive& ar,  
    COleCurrency& curSrc);
```  
  
### <a name="remarks"></a>Poznámky  
 Extrahování (  **>>** ) operátor podporuje načítání z archivu.  
  
##  <a name="operator_currency"></a>COleCurrency::operator měny  
 Vrátí `CURRENCY` struktura, jehož hodnota je zkopírována z tohoto **COleCurrency** objektu.  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="parsecurrency"></a>COleCurrency::ParseCurrency  
 Volání této funkce člen k analýze řetězec číst hodnotu měny.  
  
```  
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,  
    DWORD dwFlags = 0,  
    LCID lcid = LANG_USER_DEFAULT);
 
throw(CMemoryException*); 
throw(COleException*);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszCurrency*  
 Ukazatel na řetězce ukončené hodnotou null, který má být analyzován.  
  
 `dwFlags`  
 Určuje pro nastavení národního prostředí, které by mohly mít příznak následující příznaky:  
  
- **LOCALE_NOUSEROVERRIDE** používá výchozí nastavení národního prostředí systému, namísto vlastní uživatelská nastavení.  
  
 `lcid`  
 Určuje ID národního prostředí pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je řetězec byl úspěšně převést na hodnotu měny, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Význam číselného typu znaků v řetězci zdroj používá místní jazyk specifikace (ID národního prostředí).  
  
 Informace hodnot ID národního prostředí, naleznete v [podpora více jazyků](http://msdn.microsoft.com/en-us/47dc5add-232c-4268-b977-43e12da81ede).  
  
 Pokud řetězec byl úspěšně převeden na měny hodnotu, hodnotu této **COleCurrency** objektu je nastaven na tuto hodnotu a její stav na platný.  
  
 Pokud řetězec nelze převést na hodnotu měny, nebo pokud došlo k přetečení číselné, stav tohoto **COleCurrency** objekt je neplatný.  
  
 Pokud převod řetězce se nezdařilo z důvodu chyby přidělení paměti, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md). V jiných chybový stav, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>COleCurrency relační operátory  
 Porovnání dvou hodnot měny a vrácení nenulové hodnoty, pokud je podmínka vyhodnocena jako true; jinak 0.  
  
```  
BOOL operator==(const COleCurrency& cur) const;  
BOOL operator!=(const COleCurrency& cur) const;  
BOOL operator<(const COleCurrency& cur) const;  
BOOL operator>(const COleCurrency& cur) const;  
BOOL operator<=(const COleCurrency& cur) const;  
BOOL operator>=(const COleCurrency& cur) const;  
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Návratová hodnota řazení operace (  **<** ,  **\< =** ,  **>** ,  **>=** ) není definován, pokud je stav buď operandu hodnotu null nebo je neplatný. Operátory rovnosti ( `==`, `!=`) zvažte stav operandy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>COleCurrency::SetCurrency  
 Volání této funkce člen nastavit jednotky a zlomkové části tohoto **COleCurrency** objektu.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Parametry  
 `nUnits`, `nFractionalUnits`  
 Označení jednotky a zlomkové části (v 1/10, 000's) hodnoty, které se mají zkopírovat do této **COleCurrency** objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se absolutní hodnotu zlomkové části je větší než 10 000, příslušné úpravy přišla jednotky, jak je znázorněno v třetí následující příklady.  
  
 Všimněte si, že jsou podepsané dlouhé hodnoty určené jednotky a zlomkové části. Následující příklady čtvrtý zobrazuje, co se stane, když parametry mají rozdílná znaménka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>COleCurrency::SetStatus  
 Volání této funkce člen nastavit stav (platnosti) tohoto **COleCurrency** objektu.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Parametry  
 *Stav*  
 Nový stav **COleCurrency** objektu.  
  
### <a name="remarks"></a>Poznámky  
 *Stav* hodnota parametru je definováno `CurrencyStatus` výčtového typu, která je definována v rámci **COleCurrency** třídy.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleCurrency::valid** -označuje, že tato **COleCurrency** je objekt platný.  
  
- **COleCurrency::invalid** -označuje, že tato **COleCurrency** objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleCurrency::null** -označuje, že tato **COleCurrency** objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
    > [!CAUTION]
    >  Tato funkce je pro pokročilé programovací situace. Tato funkce nezmění data v tomto objektu. Bude se nejčastěji používá k nastavení stavu na null nebo je neplatná. Všimněte si, že operátor přiřazení ( [operátor =](#operator_eq)) a [SetCurrency](#setcurrency) nastavit stav na objektu podle hodnoty zdroje.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleVariant – třída](../../mfc/reference/colevariant-class.md)
