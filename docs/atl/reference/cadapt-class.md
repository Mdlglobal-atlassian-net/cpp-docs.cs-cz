---
title: CAdapt – třída
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 1bae98663b8dc2b09efeff9139e8d028abcd862e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168821"
---
# <a name="cadapt-class"></a>CAdapt – třída

Tato šablona se používá k zabalení tříd, které mění definici operátoru address-of tak, aby vracely něco jiného než adresu objektu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>Parametry

*T*<br/>
Adaptovaný typ

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAdapt:: CAdapt](#cadapt)|Konstruktor|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAdapt:: operator const T&](#operator_const_t_amp)|Vrátí odkaz **const** na `m_T`.|
|[CAdapt:: operator T&](#operator_t_amp)|Vrátí odkaz na `m_T`.|
|[CAdapt:: operator <](#operator_lt)|Porovná objekt přizpůsobeného typu s `m_T`.|
|[CAdapt:: operator =](#operator_eq)|Přiřadí objekt přizpůsobeného typu `m_T`.|
|[CAdapt:: operator = = – operátor](#operator_eq_eq)|Porovná objekt přizpůsobeného typu s `m_T`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAdapt:: m_T](#m_t)|Adaptovaná data|

## <a name="remarks"></a>Poznámky

`CAdapt`je jednoduchá šablona použitá k zabalení tříd, které předefinují operátor address-of (`operator &`), aby vracely jinou hodnotu než adresa objektu. Příklady takových tříd zahrnují knihovny `CComBSTR`ATL, `CComPtr`třídy a `CComQIPtr` a třídu podpory kompilátoru com,. `_com_ptr_t` Tyto třídy předefinují operátor address-of, který vrátí adresu jednoho ze svých datových členů (BSTR v případě `CComBSTR`a ukazatel rozhraní v případě ostatních tříd).

`CAdapt`primární role je skrýt operátor address-of definovaný třídou *T*, ale stále zachovat charakteristiky přizpůsobené třídy. `CAdapt`plní tuto roli držením veřejného člena, [m_T](#m_t), typu *T*a definováním operátorů převodu, operátorů porovnání a kopírovacího konstruktoru, který umožňuje, aby byly specializace `CAdapt` ošetřeny, jako by se jednalo o objekty typu *T*.

Třída `CAdapt` adaptéru je užitečná, protože některé třídy typu kontejneru očekávají schopnost získat adresy jejich obsažených objektů pomocí operátoru address-of. Změna definice operátoru address-of může tento požadavek zmařit a zpravidla způsobí chyby kompilace a zabrání použití neadaptovaného typu s třídami, které očekávají, že bude fungovat. `CAdapt`poskytuje způsob, jak tyto problémy vyřešit.

Obvykle použijete `CAdapt` , pokud chcete uložit `CComBSTR`, `CComPtr`, `CComQIPtr`nebo `_com_ptr_t` objekty ve třídě stylu kontejneru. To bylo nejčastěji nutné pro kontejnery knihovny C++ Standard před podporou standardu C++ 11, ale kontejnery standardní knihovny C++ 11 automaticky pracují s typy, které jsou přetíženy `operator&()`. Standardní knihovna k tomu dosahuje interně pomocí [std:: AddressOf](../../standard-library/memory-functions.md#addressof) pro získání skutečných adres objektů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atlcomcli. h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt:: CAdapt

Konstruktory umožňují, aby byl objekt adaptéru vytvořen jako výchozí, zkopírován z objektu přizpůsobeného typu nebo zkopírován z jiného objektu adaptéru.

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Proměnná typu přizpůsobeného k zkopírování do nově vytvořeného objektu adaptéru.

*rSrCA*<br/>
Objekt adaptéru, jehož obsažená data by se měla zkopírovat (nebo přesunout) do nově vytvořeného objektu adaptéru.

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt:: m_T

Obsahuje data, která jsou přizpůsobená.

```cpp
T m_T;
```

### <a name="remarks"></a>Poznámky

K tomuto **veřejnému** datovému členu lze získat přímý nebo nepřímý pøístup pomocí [operátoru const t&](#operator_const_t_amp) a [operátoru t&](#operator_t_amp).

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt:: operator const T&amp;

Vrátí odkaz **const** na člen [m_T](#m_t) , který umožňuje, aby se objekt adaptéru nacházel jako objekt typu *T*.

```cpp
operator const T&() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na typ **const** na `m_T`.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt:: operator T&amp;

Vrátí odkaz na člena [m_T](#m_t) , který umožňuje, aby se objekt adaptéru nacházel jako objekt typu *T*.

```cpp
operator T&();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `m_T`.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt:: operator&lt;

Porovná objekt přizpůsobeného typu s [m_T](#m_t).

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi `m_T` a *RSRC*.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt:: operator =

Operátor přiřazení přiřadí argument, *RSRC*, datovému členu [m_T](#m_t) a vrátí aktuální objekt adaptéru.

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt přizpůsobeného typu, který má být zkopírován.

*rSrCA*<br/>
Odkaz na objekt, který má být přesunut.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální objekt.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt:: operator = = – operátor

Porovná objekt přizpůsobeného typu s [m_T](#m_t).

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odkaz na objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Výsledek porovnání mezi *m_T* a *RSRC*.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
