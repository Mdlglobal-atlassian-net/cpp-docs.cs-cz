---
title: SafeInt – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7715553e17e49ef3c169145abfb49816f6d6dd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891334"
---
# <a name="safeint-class"></a>SafeInt – třída
Rozšiřuje primitiv celé číslo, aby se zabránilo přetečení celé číslo a umožňují porovnat různé typy celých čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Šablony|Popis|  
|--------------|-----------------|  
|T|Typ celé číslo nebo logického parametru, `SafeInt` nahrazuje.|  
|E|Výčtové datový typ, který definuje chyba zpracování zásad.|  
|U|Typ celé číslo nebo číslo logického parametru pro sekundární operand.|  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[rhs v]|Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.|  
|[v] i|Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.|  
|[Služba bits v]|Vstupní parametr, který představuje hodnotu na pravé straně operátoru v několika samostatné funkce.|  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Výchozí konstruktor.|  
  
### <a name="assignment-operators"></a>Operátory přiřazení  
  
|Název|Syntaxe|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>Operátory přetypování  
  
|Název|Syntaxe|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|podepsaný char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|__int16 bez znaménka|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|__int32 bez znaménka|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|__int64 bez znaménka|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>Operátory porovnání  
  
|Název|Syntaxe|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>Aritmetické operátory  
  
|Název|Syntaxe|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>Logické operátory  
  
|Název|Syntaxe|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>Poznámky  
 `SafeInt` Třída chrání před přetečení celé číslo v matematické operace. Zvažte například přidávání dvě celá čísla 8bitové: jeden má hodnota 200 a druhá hodnota je 100. Správné matematické operace by 200 + 100 = 300. Ale kvůli limit 8bitové celé číslo, horní bit budou ztraceny a kompilátor vrátí 44 (300-2<sup>8</sup>) jako výsledek. Všechny operace, které závisí na této matematický rovnice vygeneruje neočekávanému chování.  
  
 `SafeInt` Třída zkontroluje, zda dojde k aritmetického přetečení nebo zda kód pokusí dělení nulou. V obou případech zavolá třídu obslužné rutiny varování před programu potenciální problém.  
  
 Tato třída rovněž umožňuje porovnat dva různé typy celých čísel, dokud jsou `SafeInt` objekty. Obvykle když provedete porovnání, je nutné nejprve převést čísla, která se stejného typu. Kontroluje, ujistěte se, zda nedochází ke ztrátě dat přetypování jedno číslo na jiný typ často vyžaduje.  
  
 Operátory tabulky v tomto tématu jsou uvedeny porovnání a matematické operátory nepodporuje `SafeInt` třídy. Vrátí nejvíce matematické operátory `SafeInt` objektu typu `T`.  
  
 Operace porovnání mezi serverem `SafeInt` a typ integrální lze provést v obou směrech. Například pro obě `SafeInt<int>(x) < y` a `y> SafeInt<int>(x)` jsou platné a vrátí stejné výsledky.  
  
 Binární operátory mnoho nepodporují pomocí dvou různých `SafeInt` typy. Příkladem toho je `&` operátor. `SafeInt<T, E> & int` je podporováno, ale `SafeInt<T, E> & SafeInt<U, E>` není. V druhém příkladu kompilátoru neví, jaký typ parametru vrátit. Jedno řešení tohoto problému je druhý parametr zpět na základní typ přetypování. Pomocí stejné parametry lze to provést pomocí `SafeInt<T, E> & (U)SafeInt<U, E>`.  
  
> [!NOTE]
>  Pro všechny bitové operace dva různé parametry musí mít stejnou velikost. Pokud se liší velikosti, vyvolá výjimku kompilátor [ASSERT](../mfc/reference/diagnostic-services.md#assert) výjimka. Výsledky této operace nemůže zaručit být přesná. Chcete-li vyřešit tento problém, přetypujte parametr menší, dokud nebude stejnou velikost jako parametr větší.  
  
 Pro operátory posunutí další bits než pro typ šablony s posunem vyvolá výjimku ASSERT. V režimu vydání to nebude mít žádný vliv. Kombinování dva typy parametrů SafeInt je možné pro operátory posunutí, protože návratový typ je stejný jako původní typ. Číslo na pravé straně operátoru pouze označuje počet bitů se posunou.  
  
 Při provádění logické porovnání s objektem SafeInt je výhradně aritmetické porovnání. Představte si třeba těchto výrazů:  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 První příkaz přeloží na `true`, ale druhý příkaz přeloží na `false`. Bitovou negaci 0 je 0xFFFFFFFF. Relační operátor výchozí v druhý příkaz, porovná 0xFFFFFFFF na 0xFFFFFFFF a je rovna považuje za. Relační operátor pro `SafeInt` třída rozpoznává druhý parametr je záporná, zatímco první parametr není podepsaný. Proto, i když bitové reprezentaci stejná, `SafeInt` logický operátor rozpoznává, celé číslo bez znaménka je větší než -1.  
  
 Buďte opatrní při použití `SafeInt` třídy společně s `?:` Ternární operátor. Vezměte v úvahu následující řádek kódu.  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 Kompilátor převede na toto:  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 Pokud `flag` je `false`, vyvolá výjimku místo přiřazení hodnotu -1, kompilátor `x`. Chcete-li tomu zabránit, je správný kód, který použije proto následujícího řádku.  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` a `U` lze přiřadit typem logická hodnota, znak typ nebo typ integer. Celé číslo typům podepsané a nepodepsané a jakékoli velikosti z 8 bitů na 64 bitů.  
  
> [!NOTE]
>  I když `SafeInt` třída přijímá jakýkoli druh celé číslo, provede efektivněji s typy bez znaménka.  
  
 `E` Chyba je uvedena mechanismu pro zpracování, `SafeInt` používá. Dvou mechanismů zpracování chyb jsou k dispozici s SafeInt knihovny. Výchozí zásada je `SafeIntErrorPolicy_SafeIntException`, která vyvolává [SafeIntException – třída](../windows/safeintexception-class.md) výjimky, když dojde k chybě. Jiné zásady je `SafeIntErrorPolicy_InvalidParameter`, která zastaví program, pokud dojde k chybě.  
  
 Existují dvě možnosti pro úpravy zásad chyby. První možností je nastavit parametr `E` při vytváření `SafeInt`. Tuto možnost použijte, pokud chcete změnit chyba zpracování zásad pro právě jeden `SafeInt`. Další možností je zadat `_SAFEINT_DEFAULT_ERROR_POLICY` před zahrnete třídě vlastní zpracování chyb `SafeInt` knihovny. Tuto možnost použijte, pokud chcete změnit výchozí chyba zpracování zásad pro všechny instance `SafeInt` – třída v kódu.  
  
> [!NOTE]
>  Vlastní třída, která zpracovává chyby v knihovně SafeInt nesmí vrátit ovládacího prvku na kód, který volá obslužnou rutinu chyby. Poté, co je volána obslužná rutina chyb, výsledek `SafeInt` operaci nelze důvěřovat.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeIntException – třída](../windows/safeintexception-class.md)