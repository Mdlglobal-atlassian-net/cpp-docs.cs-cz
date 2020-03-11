---
title: concurrency – operátory oboru názvů
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 676e1936af317a6ab19959f8fd09b1de06dfaf69
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883769"
---
# <a name="concurrency-namespace-operators"></a>concurrency – operátory oboru názvů

||||
|-|-|-|
|[operator!=](#operator_neq)|[operátor&amp;&amp;](#operator_amp_amp)|[operátor&gt;](#operator_gt)|
|[operátor&gt;=](#operator_gt_eq)|[operátor&lt;](#operator_lt)|[operátor&lt;=](#operator_lt_eq)|
|[operator = = – operátor](#operator_eq_eq)|[podnikatel&#124;&#124;](#operator_lor)| |

## <a name="operator_lor"></a>&#124; &#124; operátor operátora

Vytvoří úkol, který se úspěšně dokončí, když se kterákoli z úkolů dodaných jako argumenty úspěšně dokončí.

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parametry

*ReturnType*<br/>
Typ vráceného úkolu.

*lhs*<br/>
První úkol, který se má zkombinovat do výsledného úkolu.

*zarovnání indirekce RHS*<br/>
Druhý úkol ke sloučení do výsledného úkolu.

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí, když se jedna z vstupních úloh úspěšně dokončí. Pokud jsou vstupní úlohy typu `T`, výstup této funkce bude `task<std::vector<T>`. Pokud jsou vstupní úlohy typu `void` bude výstupní úloha také `task<void>`.

### <a name="remarks"></a>Poznámky

Pokud se obě úlohy zruší nebo vyvolají výjimky, vrácený úkol se dokončí ve zrušeném stavu a jedna z výjimek, pokud existuje, bude vyvolána při volání `get()` nebo `wait()` na tomto úkolu.

## <a name="operator_amp_amp"></a>operator&amp;– operátor &amp;

Vytvoří úkol, který se úspěšně dokončí, když se obě úlohy dodají jako argumenty úspěšně dokončí.

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Parametry

*ReturnType*<br/>
Typ vráceného úkolu.

*lhs*<br/>
První úkol, který se má zkombinovat do výsledného úkolu.

*zarovnání indirekce RHS*<br/>
Druhý úkol ke sloučení do výsledného úkolu.

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí, když se obě vstupní úlohy úspěšně dokončí. Pokud jsou vstupní úlohy typu `T`, výstup této funkce bude `task<std::vector<T>>`. Pokud jsou vstupní úlohy typu `void` bude výstupní úloha také `task<void>`.

### <a name="remarks"></a>Poznámky

Pokud je jedna z úloh zrušena nebo vyvolá výjimku, vrácený úkol bude dokončen v počátečním stavu a výjimka, pokud k ní dojde, bude vyvolána, pokud zavoláte `get()` nebo `wait()` na daném úkolu.

## <a name="operator_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt `concurrent_vector` na levé straně operátoru roven objektu `concurrent_vector` na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný vektor na levé straně operátoru roven souběžnému vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Dva souběžné vektory jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="operator_neq"></a>operator! = – operátor

Testuje, zda `concurrent_vector` objekt na levé straně operátoru není roven objektu `concurrent_vector` na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se souběžné vektory nerovnají; **false** , pokud jsou souběžné vektory stejné.

### <a name="remarks"></a>Poznámky

Dva souběžné vektory jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="operator_lt"></a>operator&lt; – operátor

Testuje, zda je objekt `concurrent_vector` na levé straně operátoru menší než objekt `concurrent_vector` na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný vektor na levé straně operátoru menší než souběžný vektor na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je stejné jako ekvivalentní operátor pro třídu `vector` v oboru názvů `std`.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="operator_lt_eq"></a>operator&lt;= – operátor

Testuje, zda je objekt `concurrent_vector` na levé straně operátoru menší než nebo roven `concurrent_vector`mu objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný vektor na levé straně operátoru menší než nebo roven souběžnému vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je stejné jako ekvivalentní operátor pro třídu `vector` v oboru názvů `std`.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="operator_gt"></a>operator&gt; – operátor

Testuje, zda je objekt `concurrent_vector` na levé straně operátoru větší než objekt `concurrent_vector` na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný vektor na levé straně operátoru větší než souběžný vektor na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je stejné jako ekvivalentní operátor pro třídu `vector` v oboru názvů `std`.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="operator_gt_eq"></a>operator&gt;= – operátor

Testuje, zda je objekt `concurrent_vector` na levé straně operátoru větší než nebo roven `concurrent_vector`mu objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*Typu*<br/>
Typ přidělujícího objektu prvního `concurrent_vector`.

*Buňce*<br/>
Typ přidělování druhého objektu `concurrent_vector`.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný vektor na levé straně operátoru větší než nebo roven souběžnému vektoru na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je stejné jako ekvivalentní operátor pro třídu `vector` v oboru názvů `std`.

Tato metoda není bezpečná pro souběžnost s ohledem na jiné metody, které by mohly změnit jeden ze současných vektorů `_A` nebo `_B`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
