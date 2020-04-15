---
title: concurrency – operátory oboru názvů
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374386"
---
# <a name="concurrency-namespace-operators"></a>concurrency – operátory oboru názvů

||||
|-|-|-|
|[operátor!=](#operator_neq)|[Operátor&amp;&amp;](#operator_amp_amp)|[Operátor&gt;](#operator_gt)|
|[Operátor&gt;=](#operator_gt_eq)|[Operátor&lt;](#operator_lt)|[Operátor&lt;=](#operator_lt_eq)|
|[operátor==](#operator_eq_eq)|[operátor&#124;&#124;](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>operátor&#124;&#124; Operátor

Vytvoří úkol, který bude úspěšně dokončen po úspěšném dokončení některého z úkolů zadaných jako argumenty.

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

*Returntype*<br/>
Typ vrácené úlohy.

*Lhs*<br/>
První úkol, který se má spojit do výsledného úkolu.

*rhs*<br/>
Druhý úkol kombinovat do výsledného úkolu.

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí po úspěšném dokončení některého ze vstupních úkolů. Pokud jsou vstupní úkoly typu `T`, výstup em `task<std::vector<T>`této funkce bude . Pokud jsou vstupní úkoly typu, `void` výstupní `task<void>`úloha bude také .

### <a name="remarks"></a>Poznámky

Pokud jsou obě úlohy zrušeny nebo vyvolány výjimky, vrácená úloha bude dokončena v zrušeném stavu a jedna `get()` z `wait()` výjimek, pokud jsou zjištěny, bude vyvolána při volání nebo na tento úkol.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>operátor&amp; &amp; operátor

Vytvoří úkol, který bude úspěšně dokončen po úspěšném dokončení obou úkolů zadaných jako argumentů.

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

*Returntype*<br/>
Typ vrácené úlohy.

*Lhs*<br/>
První úkol, který se má spojit do výsledného úkolu.

*rhs*<br/>
Druhý úkol kombinovat do výsledného úkolu.

### <a name="return-value"></a>Návratová hodnota

Úkol, který je úspěšně dokončen po úspěšném dokončení obou vstupních úkolů. Pokud jsou vstupní úkoly typu `T`, výstup em `task<std::vector<T>>`této funkce bude . Pokud jsou vstupní úkoly typu, `void` výstupní `task<void>`úloha bude také .

### <a name="remarks"></a>Poznámky

Pokud je jeden z úkolů zrušen nebo vyvolá výjimku, vrácená úloha bude dokončena brzy, v zrušeném stavu a `get()` `wait()` výjimka, pokud k ní dojde, bude vyvolána, pokud zavoláte nebo na tento úkol.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>operátor== Operátor

Testy, `concurrent_vector` pokud objekt na levé straně operátoru `concurrent_vector` se rovná objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud se souběžný vektor na levé straně operátoru rovná souběžnému vektoru na pravé straně operátoru; jinak **false**.

### <a name="remarks"></a>Poznámky

Dva souběžné vektory jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="operator-operator"></a><a name="operator_neq"></a>operátor!= Operátor

Testy, `concurrent_vector` pokud objekt na levé straně operátoru `concurrent_vector` není rovna objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud se souběžné vektory nerovnají; **false,** pokud jsou si rovny souběžné vektory.

### <a name="remarks"></a>Poznámky

Dva souběžné vektory jsou stejné, pokud mají stejný počet prvků a jejich příslušné prvky mají stejné hodnoty. V opačném případě jsou nerovné.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>operátor&lt; operátor

Testy, `concurrent_vector` pokud objekt na levé straně operátoru `concurrent_vector` je menší než objekt na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je souběžný vektor na levé straně operátoru menší než souběžný vektor na pravé straně operátoru; jinak **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je shodné s `vector` ekvivalentní `std` operátor pro třídu v oboru názvů.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>operátor&lt;= Operátor

Testy, `concurrent_vector` pokud objekt na levé straně operátoru je `concurrent_vector` menší nebo rovno objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je souběžný vektor na levé straně operátoru menší nebo roven souběžnému vektoru na pravé straně operátora; jinak **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je shodné s `vector` ekvivalentní `std` operátor pro třídu v oboru názvů.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>operátor&gt; operátor

Testy, `concurrent_vector` pokud je objekt na levé straně `concurrent_vector` operátoru větší než objekt na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je souběžný vektor na levé straně operátoru větší než souběžný vektor na pravé straně operátoru; jinak **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je shodné s `vector` ekvivalentní `std` operátor pro třídu v oboru názvů.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>operátor&gt;= Operátor

Testy, `concurrent_vector` pokud je objekt na levé straně operátoru `concurrent_vector` větší nebo rovno objektu na pravé straně.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*A1*<br/>
Alokátor typ prvního `concurrent_vector` objektu.

*A2*<br/>
Alokátor typ druhého `concurrent_vector` objektu.

*_A*<br/>
Objekt typu `concurrent_vector`.

*_B*<br/>
Objekt typu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je souběžný vektor na levé straně operátoru větší nebo roven souběžnému vektoru na pravé straně operátora; jinak **false**.

### <a name="remarks"></a>Poznámky

Chování tohoto operátoru je shodné s `vector` ekvivalentní `std` operátor pro třídu v oboru názvů.

Tato metoda není bezpečné souběžnosti s ohledem na jiné metody, které `_A` `_B`by mohly změnit buď souběžné vektory nebo .

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
